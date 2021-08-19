Task 1: Öncelikle gerekli dockor-compose dosyamı oluşturdum. Elasticsearch ve kibana için ayrı ayrı service entrylerimi girdim. Konfigürasyonu yaml dosyası
içinde yapmamak için ikisi için de ayrı ayrı dosya ve içerlerine config dosyası oluşturdum. O config dosyaları içine birer yml oluşturup konfigüre
edilebilecek değişkenlerimi orada atadım. Port ve network ayarlarını da yapıp "docker-compose up -d" komutuyla çalıştırdım.

Task 2: Filebeat kurulumunu yapmadan önce gereken apt_key ve apt_repository güncellemelerini yaptım. Bir de apt-transport-https paketini yüklemem gerektiğini
söyleyen bir hata mesajı alınca onu yükledim. Sonrasında Filebeat kurulumunu gerçekleştirdim. Çalıştırmadan önce config file'ını bulup oradaki log dosyası
kısmında gerekli değişiklikleri yaptım. Başlatmadan önce "filebeat setup -e" komutuyla setup yapıp ve sunucu tekrar başlayınca da kendiliğinden başlasın diye
enable edip sonrasında Filebeat servisini başlattım.

Task 3: Metricbeat kurulumu Filebeat ile neredeyse aynıydı. Kurulum öncesindeki adımları yapmama gerek kalmadan metricbeat paketini indirdim. Aynı şekilde
config dosyasını bulup değişikliğimi yaptım, setup ve enable komutlarını çalıştırdım. Son olarak da servisimi başlattım.

Task 4: Tüm bunları ortak sunucudan kendi sunucuma remote olarak yapabilmek için ortak sunucuda bir playbook.yml dosyası oluşturdum. Konfigürasyon amaçlı
kullandığım yml dosyalarını (elasticsearch, kibana, filebeat, metricbeat) oraya kopyaladım. Gereken dizinleri oluşturdum. İlk başta Ansible'ın docker_compose
modülünü kullanarak Task 1'i gerçekleştirdim. İlgimi çeken bir hata aldım çünkü docker_compose modülü yanlış anlamadıysam source file olarak kurulum
yapacağımız sunucudan bir dosyayı ve onun dizinini istiyor. Sonrasında Task 2 ve 3'ü aynı şekilde gerçekleştirebilmek için gerekli olan ve yukarıda 
belirttiğim adımları ayrı ayrı task olarak girdim ve isimleriyle tasvir etmeye çalıştım.

Task 5: Kibanaya tarayıcım üzerinden eriştim ve gerekli index pattern oluşturma işlemlerini hem file hem de metricbeat için gerçekleştirdim. Sonrasında yeni
bir dashboard oluşturdum ve iki tool'un da setup'ını yaparken yüklenilen default visualizationları inceledim. Temel olarak gerekli gördüğüm metricleri
ekleyerek bir dashboard oluşturdum. Kaydettikten sonra yukarıdaki Share bölümünden bir permalink oluşturdum ve size göndereceğim mailde ekledim.
