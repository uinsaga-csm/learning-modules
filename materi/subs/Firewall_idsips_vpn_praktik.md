# **PRAKTIKUM MANAJEMEN KEAMANAN SIBER**

**Firewall, IDS/IPS, dan VPN dengan Linux**

---

## **PENDALUAN PRAKTIKUM**

### **Tujuan Praktikum**

1. Memahami implementasi firewall menggunakan `iptables` dan `ufw`
2. Mampu menginstal dan mengkonfigurasi Snort sebagai IDS/IPS
3. Dapat membuat VPN server menggunakan OpenVPN dan WireGuard
4. Mengintegrasikan semua komponen keamanan dalam satu arsitektur

### **Peralatan yang Diperlukan**

- VirtualBox/VMware
- 2 VM Linux (Ubuntu 20.04/22.04)
- Koneksi internet
- Minimal 2GB RAM per VM

---

## **BAGIAN 1: IMPLEMENTASI FIREWALL DENGAN iptables & ufw**

### **Praktikum 1.1: Dasar-dasar iptables**

**Tujuan:** Memahami konsep dasar packet filtering dengan iptables

```bash
# Login sebagai root atau gunakan sudo
sudo -i

# 1. Melihat rules iptables saat ini
iptables -L -v -n
iptables -t nat -L -v -n

# 2. Reset semua rules (hati-hati!)
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X

# 3. Set policy default
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# 4. Allow loopback interface
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# 5. Allow koneksi established dan related
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# 6. Allow SSH (port 22)
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# 7. Allow HTTP (port 80) dan HTTPS (port 443)
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# 8. Allow ICMP (ping)
iptables -A INPUT -p icmp -j ACCEPT

# 9. Block IP tertentu (contoh: 192.168.1.100)
iptables -A INPUT -s 192.168.1.100 -j DROP

# 10. Simpan rules (tergantung distribusi)
# Untuk Ubuntu/Debian:
apt-get install iptables-persistent
netfilter-persistent save

# Lihat rules akhir
iptables -L -v -n --line-numbers
```

**Latihan:**

1. Coba akses SSH dari komputer lain
2. Test koneksi HTTP ke web server
3. Coba ping ke mesin tersebut

### **Praktikum 1.2: Firewall dengan UFW (Uncomplicated Firewall)**

**Tujuan:** Menggunakan UFW yang lebih user-friendly

```bash
# 1. Install UFW (jika belum ada)
sudo apt update
sudo apt install ufw

# 2. Reset dan set default policy
sudo ufw --force reset
sudo ufw default deny incoming
sudo ufw default allow outgoing

# 3. Allow services
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw allow 53/tcp   # DNS
sudo ufw allow 53/udp   # DNS

# 4. Allow port range
sudo ufw allow 8000:8080/tcp

# 5. Deny specific IP
sudo ufw deny from 192.168.1.100

# 6. Enable UFW
sudo ufw enable

# 7. Check status
sudo ufw status verbose
sudo ufw status numbered

# 8. Monitoring
sudo ufw show added
sudo tail -f /var/log/ufw.log
```

---

## **BAGIAN 2: IMPLEMENTASI IDS/IPS DENGAN SNORT**

### **Praktikum 2.1: Instalasi dan Konfigurasi Snort**

**Tujuan:** Menginstal dan mengkonfigurasi Snort sebagai NIDS

```bash
# 1. Update system dan install dependencies
sudo apt update
sudo apt install -y build-essential libpcap-dev libpcre3-dev libdumbnet-dev \
bison flex zlib1g-dev liblzma-dev openssl libssl-dev libnghttp2-dev \
autoconf libtool libluajit-5.1-dev pkg-config

# 2. Download dan install Snort
cd /tmp
wget https://www.snort.org/downloads/snort/snort-2.9.20.tar.gz
tar -xvzf snort-2.9.20.tar.gz
cd snort-2.9.20

# 3. Configure dan compile
./configure --enable-sourcefire --disable-open-appid
make
sudo make install

# 4. Update shared libraries
sudo ldconfig

# 5. Create symbolic links
sudo ln -s /usr/local/bin/snort /usr/sbin/snort

# 6. Verify installation
snort -V
```

### **Praktikum 2.2: Konfigurasi Snort sebagai IDS**

```bash
# 1. Create Snort directories
sudo mkdir -p /etc/snort
sudo mkdir -p /etc/snort/rules
sudo mkdir -p /etc/snort/preproc_rules
sudo mkdir -p /var/log/snort
sudo mkdir -p /usr/local/lib/snort_dynamicrules

# 2. Create basic configuration files
sudo touch /etc/snort/rules/local.rules
sudo touch /etc/snort/rules/white_list.rules
sudo touch /etc/snort/rules/black_list.rules

# 3. Download community rules
cd /tmp
wget https://www.snort.org/downloads/community/community-rules.tar.gz
tar -xvzf community-rules.tar.gz -C /etc/snort/rules

# 4. Create snort.conf
sudo tee /etc/snort/snort.conf > /dev/null << 'EOF'
# Setup network
ipvar HOME_NET 192.168.1.0/24
ipvar EXTERNAL_NET any

# Configure paths
var RULE_PATH /etc/snort/rules
var SO_RULE_PATH /etc/snort/so_rules
var PREPROC_RULE_PATH /etc/snort/preproc_rules
var WHITE_LIST_PATH /etc/snort/rules
var BLACK_LIST_PATH /etc/snort/rules

# Configure preprocessors
preprocessor stream5_global: max_tcp 8192, track_tcp yes, track_udp yes
preprocessor stream5_tcp: policy first, ports both 21 23 25 53 80 110 111 135 136 137 139 143 443 445 513 514 993 995 1433 1521 3306 3389
preprocessor stream5_udp: ports both 53 67 68 69 123 135 136 137 161 162 500 514 1434 5060
preprocessor http_inspect: global iis_unicode_map unicode.map 1252
preprocessor rpc_decode: 111 32771
preprocessor bo

# Include rules
include $RULE_PATH/local.rules
include $RULE_PATH/community-rules/community.rules
EOF

# 5. Create custom rules
sudo tee /etc/snort/rules/local.rules > /dev/null << 'EOF'
# Alert untuk port scanning
alert tcp any any -> $HOME_NET any (msg:"Possible Port Scan"; flags:S; threshold: type both, track by_dst, count 5, seconds 10; sid:1000001; rev:1;)

# Alert untuk SSH brute force
alert tcp any any -> $HOME_NET 22 (msg:"SSH Brute Force Attempt"; flow:established; content:"SSH"; threshold: type threshold, track by_src, count 5, seconds 60; sid:1000002; rev:1;)

# Alert untuk web attack
alert tcp any any -> $HOME_NET 80 (msg:"Web Attack - SQL Injection"; flow:to_server,established; content:"union"; nocase; content:"select"; nocase; sid:1000003; rev:1;)

# Alert untuk ping flood
alert icmp any any -> $HOME_NET any (msg:"ICMP Flood"; threshold: type both, track by_dst, count 20, seconds 10; sid:1000004; rev:1;)
EOF

# 6. Test configuration
sudo snort -T -c /etc/snort/snort.conf -i eth0
```

### **Praktikum 2.3: Menjalankan Snort dalam Berbagai Mode**

```bash
# 1. Mode packet logger
sudo snort -dev -l /var/log/snort -i eth0

# 2. Mode NIDS
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0

# 3. Mode NIDS dengan logging full
sudo snort -c /etc/snort/snort.conf -i eth0 -l /var/log/snort

# 4. Mode IPS (inline) - butuh konfigurasi bridge
# Create bridge interface
sudo brctl addbr snort-bridge
sudo brctl addif snort-bridge eth0
sudo brctl addif snort-bridge eth1
sudo ifconfig snort-bridge up

# Jalankan Snort dalam mode IPS
sudo snort -Q -c /etc/snort/snort.conf -i snort-bridge
```

---

## **BAGIAN 3: IMPLEMENTASI VPN DENGAN OPENVPN & WIREGUARD**

### **Praktikum 3.1: Setup OpenVPN Server**

**Tujuan:** Membuat VPN server menggunakan OpenVPN

```bash
# 1. Install OpenVPN dan Easy-RSA
sudo apt update
sudo apt install -y openvpn easy-rsa

# 2. Setup Public Key Infrastructure (PKI)
make-cadir ~/openvpn-ca
cd ~/openvpn-ca

# 3. Edit variabel untuk sertifikat
nano vars
# Edit bagian berikut:
# export KEY_COUNTRY="ID"
# export KEY_PROVINCE="JK"
# export KEY_CITY="Jakarta"
# export KEY_ORG="YourOrg"
# export KEY_EMAIL="admin@yourorg.com"
# export KEY_OU="IT"
# export KEY_NAME="server"

# 4. Source variabel dan clean old keys
source vars
./clean-all

# 5. Build Certificate Authority (CA)
./build-ca

# 6. Build server certificate
./build-key-server server

# 7. Build Diffie-Hellman parameters
./build-dh

# 8. Generate HMAC signature
openvpn --genkey --secret keys/ta.key

# 9. Copy files ke /etc/openvpn
cd ~/openvpn-ca/keys
sudo cp ca.crt server.crt server.key ta.key dh2048.pem /etc/openvpn

# 10. Setup server configuration
sudo cp /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz /etc/openvpn/
sudo gzip -d /etc/openvpn/server.conf.gz

# 11. Edit server configuration
sudo nano /etc/openvpn/server.conf
```

**Isi server.conf:**

```bash
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist /var/log/openvpn/ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
tls-auth ta.key 0
cipher AES-256-CBC
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append /var/log/openvpn/openvpn.log
verb 3
explicit-exit-notify 1
```

### **Praktikum 3.2: Membuat Client Configuration**

```bash
# 1. Generate client certificate
cd ~/openvpn-ca
source vars
./build-key client1

# 2. Create client configuration directory
mkdir -p ~/client-configs/files

# 3. Create base client configuration
nano ~/client-configs/base.conf
```

**Isi base.conf:**

```bash
client
dev tun
proto udp
remote YOUR_SERVER_IP 1194
resolv-retry infinite
nobind
user nobody
group nogroup
persist-key
persist-tun
remote-cert-tls server
cipher AES-256-CBC
verb 3
```

```bash
# 4. Create script untuk generate client config
nano ~/client-configs/make_config.sh
```

**Isi make_config.sh:**

```bash
#!/bin/bash

KEY_DIR=~/openvpn-ca/keys
OUTPUT_DIR=~/client-configs/files
BASE_CONFIG=~/client-configs/base.conf

cat ${BASE_CONFIG} \
    <(echo -e '<ca>') \
    ${KEY_DIR}/ca.crt \
    <(echo -e '</ca>\n<cert>') \
    ${KEY_DIR}/${1}.crt \
    <(echo -e '</cert>\n<key>') \
    ${KEY_DIR}/${1}.key \
    <(echo -e '</key>\n<tls-auth>') \
    ${KEY_DIR}/ta.key \
    <(echo -e '</tls-auth>') \
    > ${OUTPUT_DIR}/${1}.ovpn
```

```bash
# 5. Make script executable dan generate client config
chmod 700 ~/client-configs/make_config.sh
cd ~/client-configs
./make_config.sh client1

# 6. Start OpenVPN server
sudo systemctl enable openvpn@server
sudo systemctl start openvpn@server
sudo systemctl status openvpn@server
```

### **Praktikum 3.3: Setup WireGuard VPN**

**Tujuan:** Membuat VPN yang lebih modern dan cepat dengan WireGuard

```bash
# 1. Install WireGuard
sudo apt update
sudo apt install -y wireguard resolvconf

# 2. Generate server keys
cd /etc/wireguard
umask 077
wg genkey | sudo tee privatekey | wg pubkey | sudo tee publickey

# 3. Create server configuration
sudo nano /etc/wireguard/wg0.conf
```

**Isi wg0.conf (Server):**

```bash
[Interface]
PrivateKey = [SERVER_PRIVATE_KEY]
Address = 10.0.0.1/24
ListenPort = 51820
SaveConfig = true
PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

# Client 1
[Peer]
PublicKey = [CLIENT1_PUBLIC_KEY]
AllowedIPs = 10.0.0.2/32
```

```bash
# 4. Enable IP forwarding
echo 'net.ipv4.ip_forward=1' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

# 5. Start WireGuard
sudo systemctl enable wg-quick@wg0
sudo systemctl start wg-quick@wg0
sudo systemctl status wg-quick@wg0

# 6. Check interface
wg show
ip addr show wg0
```

**Untuk Client:**

```bash
# Generate client keys
umask 077
wg genkey | tee client_privatekey | wg pubkey | tee client_publickey

# Create client configuration
sudo nano /etc/wireguard/wg-client.conf
```

**Isi wg-client.conf:**

```bash
[Interface]
PrivateKey = [CLIENT_PRIVATE_KEY]
Address = 10.0.0.2/32
DNS = 8.8.8.8

[Peer]
PublicKey = [SERVER_PUBLIC_KEY]
Endpoint = [SERVER_IP]:51820
AllowedIPs = 0.0.0.0/0
```

---

## **BAGIAN 4: INTEGRASI DAN TESTING**

### **Praktikum 4.1: Arsitektur Terintegrasi**

**Tujuan:** Mengintegrasikan semua komponen keamanan

```bash
# 1. Script startup untuk integrasi
sudo nano /usr/local/bin/security-startup.sh
```

**Isi security-startup.sh:**

```bash
#!/bin/bash

# Start firewall
ufw --force enable

# Start Snort IDS
snort -q -c /etc/snort/snort.conf -i eth0 -D

# Start OpenVPN
systemctl start openvpn@server

# Start WireGuard
systemctl start wg-quick@wg0

# Log status
echo "Security services started at $(date)" >> /var/log/security-services.log
ufw status >> /var/log/security-services.log
```

```bash
# 2. Make executable
sudo chmod +x /usr/local/bin/security-startup.sh

# 3. Create systemd service
sudo nano /etc/systemd/system/security-services.service
```

**Isi service file:**

```bash
[Unit]
Description=Security Services Integration
After=network.target

[Service]
Type=oneshot
ExecStart=/usr/local/bin/security-startup.sh
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

```bash
# 4. Enable service
sudo systemctl enable security-services.service
```

### **Praktikum 4.2: Testing dan Monitoring**

```bash
# 1. Monitoring Snort alerts
tail -f /var/log/snort/alert

# 2. Monitoring UFW logs
tail -f /var/log/ufw.log

# 3. Testing VPN connectivity
ping 10.8.0.1  # OpenVPN
ping 10.0.0.1  # WireGuard

# 4. Test firewall rules
nmap -sS [SERVER_IP]              # Port scanning
hping3 -S -p 22 -c 5 [SERVER_IP]  # TCP SYN flood test

# 5. Check VPN tunnel
wg show                          # WireGuard status
systemctl status openvpn@server # OpenVPN status

# 6. Bandwidth testing melalui VPN
iperf3 -s -p 5201  # Server side
iperf3 -c [VPN_IP] -p 5201 -t 30  # Client side
```

---

## **LAPORAN PRAKTIKUM**

### **Yang Harus Dilaporkan:**

1. **Konfigurasi Firewall:**

   - Screenshot `ufw status verbose`
   - Rules iptables custom yang dibuat

2. **Snort IDS/IPS:**

   - Custom rules yang dibuat di `local.rules`
   - Screenshot alert yang dihasilkan
   - Log analysis dari serangan yang terdeteksi

3. **VPN Implementation:**

   - Konfigurasi OpenVPN server dan client
   - Konfigurasi WireGuard
   - Hasil testing konektivitas

4. **Integrasi:**
   - Arsitektur final yang diimplementasikan
   - Hasil testing comprehensive
   - Performance impact analysis

### **Pertanyaan Analisis:**

1. Mana yang lebih efektif antara iptables dan UFW? Berikan alasan!
2. Bagaimana Snort membedakan antara traffic normal dan serangan?
3. Bandingkan performa OpenVPN vs WireGuard berdasarkan testing Anda!
4. Apa challenges dalam mengintegrasikan ketiga sistem ini?

---

## **KEAMANAN DAN ETIKA**

### **Penting:**

1. **Hanya jalankan praktikum ini di lingkungan lab yang terkontrol**
2. **Jangan gunakan teknik ini pada jaringan produksi tanpa izin**
3. **Selalu backup konfigurasi sebelum melakukan perubahan**
4. **Monitor sistem secara berkala untuk false positive**

### **Tips Troubleshooting:**

```bash
# Check service status
systemctl status [service-name]

# Check logs
journalctl -u [service-name] -f

# Verify configuration
sudo snort -T -c /etc/snort/snort.conf
sudo openvpn --config /etc/openvpn/server.conf --test

# Network debugging
tcpdump -i any -n port 1194  # OpenVPN
tcpdump -i any -n port 51820 # WireGuard
```

**Selamat Mempraktikum!** 🚀
