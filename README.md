# Arch-Linux-Turkce-Kurulum-Rehberi
Bu rehber, Arch Linux'u hızlı ve kolay bir şekilde kurmanın adımlarını içerir. Temel sistem kurulumundan başlayarak, rehber sayesinde Arch Linux'u kısa sürede kullanmaya başlayabilirsiniz.

# 1) Konu
Bugünkü rehberde, bilgisayarlar için Arch Linux kurulumunu anlatan bir rehber yazıyorum. İlk defa rehber yazıyorum, bu nedenle eğer hatalarım varsa kusuruma bakmayın; beni uyarabilirsiniz ve önerilere açığım. Bu rehberde, sizin Windows'tan Linux'a geçtiğinizi varsayıyorum ve AMD, Intel, Nvidia gibi tüm donanım tiplerini kapsayacak şekilde hazırlayacağım. Rehber maalesef fotoğraflar içermeyecek, ancak komutlar basit olacak; en azından benim için öyle.

Neyse, konuya geçelim. Linux'da oyun performansı açısından en iyi dağıtımın Arch Linux olduğunu düşünüyorum. Ancak sadece Arch Linux kurulumunu tamamladım, bitti gibi düşünmeyin. Bu dağıtım biraz zorlu bir kurulum sürecine sahiptir. Arch install gibi scriptler var, ancak ben manuel kurulumu öneriyorum.

Neyse, rehbere geçelim.

# 2) İSO imajı hazırlama
Arch Linux kurulumu için size Ventoy'u öneriyorum. Linux dağıtımlarında Rufus kullanmak bazen sorunlara yol açabiliyor. Ventoy'u USB belleğinize kurduktan sonra, normal bir USB bellek gibi kullanabilir veya işletim sistemlerinizi boot edip kullanabilirsiniz. Ayrıca, Ventoy'un daha performanslı olduğunu belirtmek isterim. Bu nedenle, Ventoy'u öneriyorum.

Ventoy'u indirmek için Ventoy resmi sitesine gidip, Windows kullanıyorsanız zip uzantılı dosyayı indirebilirsiniz. Daha sonra, Arch Linux İndirme sayfasından Amerika bölgesinden herhangi bir sunucuyu seçip iso uzantılı dosyayı indirin. Son olarak, indirdiğiniz Arch Linux iso dosyasını Ventoy'un kurulu olduğu USB belleğe atmanız gerekmektedir.

# 3) Kurmaya Başlama
Sisteminizi yeniden başlatın, örneğin Del veya F2 tuşlarına basarak BIOS ekranını açın. Ardından, boot yapılacak olan USB belleğinizi seçin veya üst sıraya koyun. Sonrasında gelen ekranda Enter tuşuna basın.

root@archiso geldiğinde klavye düzenini Türkçe yapmak için loadkeys trq komutuyla klavyenizin düzenini Türkçe'ye çevirebilirsiniz.

# 4) İnternete bağlanma
Bilgisayarınıza kablolu şekilde internet bağlantısı yaptıysanız, otomatik olarak bağlanacaktır. Eğer kablosuz bağlantı yapmak istiyorsanız, iwctl komutunu kullanabilirsiniz.
station wlan0 get-networks komutu ile ağları tespit edebilirsiniz.
station wlan0 connect '[bağlanacağınız ağın ismi]' komutunu yazdıktan sonra, şifre yazma ekranı gelecektir. Şifreyi girip ağa bağlanabilirsiniz.

Sonra, exit komutunu yazıp root@archiso gelince işlemlerimize devam edebiliriz.

# 5) Diskleri hazırlama
lsblk komutunu yazarak depolama birimlerini görebilirsiniz. Buradan, Arch Linux'u kuracağımız diski tanıyabilirsiniz. Depolama boyutlarından kolaylıkla tanıyabileceğinizi düşünüyorum. Örneğin, ben Nvme SSD kullanıyorsam, bu disk genellikle nvme0n1 olarak görünecektir.

Ardından, cfdisk /dev/kuracağınız diskin ismi komutunu kullanın. Örneğin: cfdisk /dev/nvme0n1.

Bu komut sizi bir arayüzle karşılayacaktır. Arayüzü kontrol etmek için üst ve alt tuşlarıyla birimleri seçebilir, yan yön tuşlarıyla işlemleri seçebilirsiniz. Karar vermek ve uygulamak için Enter tuşuna basın

Arayüzdeki bütün birimleri Delete ile silin. Sonra New butonuna basın ve sol alttaki kısma odaklanın. Oradaki sayıyı silin ve 1G yazın. Enter'a basın. Daha sonra Type butonuna basın ve en üstteki EFI System'ı seçin, ardından Enter'a basın. Sonra yeni birim oluşturmak için direkt Enter'a basın. Bu yeni birimin disk formatı Linux Filesystem olmalıdır. Eğer her şey yukarıdaki gibi görünüyorsa, Write'a basın ve "yes" yazın. Ardından Quit komutu ile çıkabilirsiniz.

# 6) Diskleri biçimlendirme
mkfs.fat -F32 /dev/(EFI System) Örnek olarak ben üsttekini EFI olarak ayarladıysam mkfs.fat -F32 /dev/nvme0n1p1 olarak yazmam gerekmekte.
mkfs.ext4 /dev/(Linux Filesystem) Örnek olarak: mkfs.ext4 /dev/nvme0n1p2

# 7) Diskleri bağlama
mount /dev/(Linux Filesystem) /mnt
mkdir -p /mnt/boot/efi
mount /dev/(EFI System) /mnt/boot/efi

# 8) Pacstrap ile gereken paketleri indirmek
pacstrap /mnt base base-devel linux-zen linux-zen-headers linux-firmware amd-ucode git nano 
İntel işlemci kullanıyorsanız amd-ucode yerine intel-ucode yazınız. 

# 9) Genfstab
genfstab -U /mnt  /mnt/etc/fstab

# 10) Timedatectl
timedatectl set-ntp true yazıp ntp etkinleştirmeniz lazım.

# 11) Sisteme giriş
arch-chroot /mnt yazıp sisteme giriş yapın.

# 12) Zaman dilimi ayarlama
ln -sf /usr/share/zoneinfo/Europe/Istanbul /etc/localtime yazıp zaman dilimini ayarlayabilirsiniz.

# 13) Hwclock
hwclock --systohc yazıp saati senkron edin.



