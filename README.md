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
