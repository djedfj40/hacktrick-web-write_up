Hacktrick ctfinde web sorularından biri olan ve sadece 2 takımın çözebildiği bir web sorusu. Sadece 1.olan takım ve bizim takımımız çözebilmiştir.

![1](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/2027f7b5-5b85-4d57-81de-2f928fe6080f)

Öncelikle ilk olarak soruyu açtığımzda register ve login ekranıyla karşılaşıyoruz

![2](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/4ebde4a0-a44e-42f0-9150-702df6097287)


Kayıt olup giriş yaptıktan sonra readme.md dosyasını ?file parametresi ile okunduğu anlaşılıyor.

![3](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/088ac4fa-fdbf-4dcd-b6bc-20d54ec8bb11)

Tabii ki aklıma direk LFI (local file inclusion) denemek geliyor ve başarılı oluyorum.


![4](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/7e285f4b-29c0-4cf4-b3a3-1ac1a48080ca)

PHPSESSID session bilgimi /tmp dosyasının içinde buluyorum ve session bilgilerimi okumaya çalıştığımda başarılı oluyorum.

Şimdi bu LFI açığını RCE açığına yani komut çalıştırma açığına döndürmeyi deneyeceğim. Bunun içinde ilk kayıt olduğumuz yere dönüp name parametresine php kodu eklemeyi deniyorum
![5](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/1501b60e-f302-4854-9de0-58067b684653)

eğer başarılı olursak "ls" komutunu çalıştırıp bana bulunduğumuz dizindeki dosyaların ismini vermesi gerekiyor.

![6](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/03d4ab62-e611-4446-89a2-e0dee323906e)

Tekrar login olup session değerimi okumya çalıştığımda, yazdığım php kodunun başarıyla çalıştığını ve dosyaları bana getirdiğini görüyorum.

Şimdi sıra tekrar kayıt olup "flag.php" dosyasını okumakta

![7](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/abe383d3-cc80-4658-b399-00abfe1be4a9)

cat flag.php diyorum ve flag.php dosyasının içeriğini bana getirmesini istiyorum.

![8](https://github.com/djedfj40/hacktrick-web-write_up/assets/24505484/e548084b-239c-499a-b003-654fb6e8ab90)

tekar giriş yapıp tekrar session bilgilerimi okumaya çalıştığımda flag direk karşıma çıkıveriyor.


