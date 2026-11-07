# Simple-Arp-Spoofing-python-
Arp protokolünü kötüye kullanarak Man-In-The-Middle saldırısı yapmayı sağlayan arp spoofing aracı. Eğitim amaçlıdır gerçek bir saldırıda kullanılamaz.
Eğer gerçekten sızma testinde kullanacaksanız bettercap kullanınız.
# Nasıl kurulur?
Arpspoof.py dosyasını indiriniz 
Cmd açınız ve
pip install scapy
yazınız 
# Çalıştırma
sudo sysctl -w net.ipv4.ip_forward=1

sudo python3 arpspoof.py -t 192.168.1.50 -g 192.168.1.1

(Eğer windows kullanıyorsanız kontrol panelini yönetici olarak çalıştırın ve komutları başında sudo olmadan yazınız)
# Bilmeniz gereken kritik detaylar
Bilmeniz gerekenler:

    ip_forward=1 olmadan hedefin interneti kesilir (paketler sana gelir ama iletilmez). Sadece dinlemek istiyorsan forwarding'e gerek yok, ama o zaman hedef çevrimdışı kalır.
    Bu sadece aynı L2 ağında çalışır. Wi-Fi'da client isolation açıksa veya hedef farklı VLAN'daysa işe yaramaz.
    HTTPS trafiğini okumak için ayrıca bir proxy (mitmproxy, sslsplit) ve CA sertifikası gerekir; bu script sadece trafiği üzerinden geçirir.
    Yakalanan paketleri görmek için tcpdump -i <iface> -n çalıştırabilirsin.
    Test için arp -a ile hedef makinede ARP tablosunun değiştiğini doğrulayabilirsin.
    Klasik alternatif: dsniff paketindeki arpspoof aracı (arpspoof -i wlan0 -t 192.168.1.50 192.168.1.1), ters yön için ikinci bir instance.
