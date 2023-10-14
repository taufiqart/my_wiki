## mengatasi reverse proxy ssl/https self signed certificate
### add this to /etc/nginx/nginx.conf
proxy_ssl_protocols TLSv1.2 TLSv1.3;

proxy_ssl_ciphers DEFAULT;


## mengatasi ddos attack
https://www.youtube.com/watch?v=oSTXOsE3vv8

### reset iptables
iptables -F

### stop paket kosong
iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP

### stop syn-flood attack
iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP

### set rules port 80
iptables -I INPUT -p tcp --dport 80 -m state --state NEW -m recent --set

### cegah permintaan lebih dari 10 request baru ke server dalam periode waktu 20 detik angka 10 dan 20 dapat diganti sesuai keiinginan dan kemampuan server kalian.
iptables -I INPUT -p tcp --dport 80 -m state --state NEW -m recent --update --seconds 20 --hitcount 10 -j DROP

## mount smb to local linux
sudo mount -t cifs -o credentials=~/.credentials //172.1.1.1/backupdata /mnt/movies_share
