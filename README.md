#  Homomorfik Şifreleme Tabanlı Güvenli Veri Analizi: Kapsamlı Bir Bakış
Bu proje, hassas verilerin gizliliğini koruyarak şifreli veriler üzerinde doğrudan analiz yapılmasını sağlayan homomorfik şifreleme tekniklerini araştırıyor. Kısmi ve Tam Homomorfik Şifreleme (PHE/FHE) türleri, hibrit yaklaşımlar, güvenli çok taraflı hesaplama (SMPC) entegrasyonu ve bulut tabanlı analiz gibi çeşitli uygulama senaryoları incelenmektedir.

# Team/Ekip
242******012 Burak Karakoç

242******055 Kübra Fison 

## Features / *Özellikler*

*Şifreli Veri Analizi: Paillier homomorfik şifrelemesi kullanılarak ağdan toplanan veriler (örneğin, cihaz sayısı) şifreli halde analiz edilir, veri gizliliği korunur.*

*SQL Enjeksiyon Tespiti: Otomatik Python scripti, DVWA üzerindeki SQL enjeksiyon zafiyetlerini tespit eder ve sonuçları raporlar.*

*Wireshark ile Ağ İzleme: HTTP trafiği analiz edilerek SQL enjeksiyon payload’ları ve hassas veri sızıntıları tespit edilir.*

## Roadmap / *Yol Haritası*

See our plans in [ROADMAP.md](ROADMAP.md).  
*Yolculuğu görmek için [ROADMAP.md](ROADMAP.md) dosyasına göz atın.*

## Installation / *Kurulum*
Homomorfik Şifreleme Tabanlı Güvenli Veri Analizi projesini gerçekleştirmek için gerekli olan yazılımları, kütüphaneleri ve araçları yüklemeniz gerekiyor. Aşağıda, projede kullanılacak tüm araçların ve bağımlılıkların listesini, indirme linkleriyle birlikte sunuyorum. Proje, Paillier homomorfik şifrelemesi, SQL enjeksiyon testi için Python scripti, Wireshark ile ağ analizi ve LaTeX ile rapor derlemesini içeriyor.

---

### Gerekli Yazılımlar ve Kütüphaneler

#### 1. **İşletim Sistemi ve Test Ortamı**
- **Kali Linux** (Önerilen, sızma testi araçları için optimize edilmiştir)
  - **Link**: [Kali Linux Downloads](https://www.kali.org/get-kali/)
  - **Kurulum**: VirtualBox veya VMware ile sanal makine olarak kurabilirsiniz. Alternatif olarak, Ubuntu veya başka bir Linux dağıtımı da kullanılabilir.
  - **Not**: DVWA ve diğer araçlar için Linux tabanlı bir sistem önerilir.

- **DVWA (Damn Vulnerable Web Application)** (SQL enjeksiyon testi için)
  - **Link**: [DVWA GitHub](https://github.com/digininja/DVWA)
  - **Kurulum Komutları**:
    ```bash
    wget https://github.com/digininja/DVWA/archive/master.zip
    unzip master.zip
    sudo mv DVWA-master /var/www/html/dvwa
    sudo chmod -R 755 /var/www/html/dvwa
    ```

#### 2. **Web Sunucusu ve Veritabanı**
- **Apache2 ve MySQL** (DVWA için gerekli)
  - **Link**: Resmi bir indirme bağlantısı yoktur; Kali Linux’ta aşağıdaki komutlarla kurulur:
    ```bash
    sudo apt update
    sudo apt install apache2 mariadb-server php php-mysql
    ```
  - **Not**: XAMPP alternatifi de kullanılabilir.
    - **Link**: [XAMPP](https://www.apachefriends.org/download.html)

#### 3. **Wireshark** (Ağ trafiği analizi için)
- **Link**: [Wireshark Downloads](https://www.wireshark.org/download.html)
- **Kurulum Komutu** (Kali Linux’ta genellikle önceden yüklüdür):
  ```bash
  sudo apt install wireshark
  ```
- **Not**: Wireshark’ı başlatmak için:
  ```bash
  sudo wireshark &
  ```

#### 4. **Python ve Kütüphaneler**
- **Python 3** (Genellikle Kali Linux’ta yüklüdür)
  - **Link**: [Python Downloads](https://www.python.org/downloads/)
  - **Kurulum Komutu**:
    ```bash
    sudo apt install python3 python3-pip
    ```

- **Paillier Homomorfik Şifreleme Kütüphanesi (phe)**:
  - **Link**: [python-paillier](https://pypi.org/project/phe/)
  - **Kurulum Komutu**:
    ```bash
    pip install phe
    ```

- **Requests Kütüphanesi** (SQL enjeksiyon testi için):
  - **Link**: [requests](https://pypi.org/project/requests/)
  - **Kurulum Komutu**:
    ```bash
    pip install requests
    ```

#### 5. **LaTeX** (Rapor derlemesi için)
- **TeX Live** (LaTeX belgelerini PDF’ye derlemek için)
  - **Link**: [TeX Live](https://www.tug.org/texlive/acquire-netinstall.html)
  - **Kurulum Komutu** (Kali Linux’ta):
    ```bash
    sudo apt install texlive-full latexmk
    ```
  - **Not**: `latexmk` ile LaTeX dosyasını derlemek için:
    ```bash
    latexmk -pdf homomorphic_secure_analysis_report.tex
    ```

#### 6. **Opsiyonel: Microsoft SEAL** (Tam homomorfik şifreleme için, geliştirme önerisi olarak)
- **Link**: [Microsoft SEAL GitHub](https://github.com/microsoft/SEAL)
- **Kurulum Komutları**:
  ```bash
  git clone https://github.com/microsoft/SEAL.git
  cd SEAL
  cmake .
  make
  sudo make install
  ```
- **Not**: SEAL, daha karmaşık homomorfik şifreleme işlemleri için kullanılabilir.

---

### Kurulum Adımları Özeti
1. **Kali Linux Kurulumu**:
   - [Kali Linux](https://www.kali.org/get-kali/) indirin ve bir sanal makineye kurun.
2. **DVWA Kurulumu**:
   - Apache2 ve MySQL’i kurun, DVWA’yı indirin ve yapılandırın.
3. **Wireshark Kurulumu**:
   - Wireshark’ı kurun ve HTTP trafiğini analiz için hazırlayın.
4. **Python ve Kütüphaneler**:
   - Python 3, `phe` ve `requests` kütüphanelerini kurun.
5. **LaTeX Kurulumu**:
   - TeX Live’ı kurun ve rapor derlemesi için `latexmk` kullanın.
6. **Opsiyonel**:
   - Microsoft SEAL’ı kurarak tam homomorfik şifreleme deneyleri yapabilirsiniz.

---

### Önemli Notlar
- **Etik Sınırlar**: Tüm testler yalnızca kendi test ortamınızda (DVWA) yapılmalıdır. İzinsiz testler yasa dışıdır.
- **Aircrack-ng**: Önceki taleplerinizde Aircrack-ng’den bahsettiniz, ancak bu projede doğrudan kullanılmadı. Wi-Fi ağı üzerinden analiz için Aircrack-ng gerekiyorsa, şu linkten indirebilirsiniz:
  - **Link**: [Aircrack-ng](https://www.aircrack-ng.org/downloads.html)
  - **Kurulum Komutu**:
    ```bash
    sudo apt install aircrack-ng
    ```


