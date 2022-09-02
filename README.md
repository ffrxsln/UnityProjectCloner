![cloner](https://user-images.githubusercontent.com/30280876/48310703-37780100-e561-11e8-8319-0ecbaeb8c8e4.gif)
# UnityProjectCloner
Çok oyunculu testler için kullanıcının unity projesini *tüm varlıkları kopyalamadan* hızlı bir şekilde çoğaltmasını sağlayan bir araç

# Neden?
Çok oyunculu kodda hızlı bir şekilde hata ayıklamanın bir yöntemi, aynı projenin birden fazla unity düzenleyicisini çalıştırmak ve sunucu/istemci işlevleri boyunca ilerlerken her örneği incelemektir. Bu, dosya IO endişeleri nedeniyle bir unity projesi için tasarım gereği devre dışı bırakılmıştır, bu nedenle bu araç, unity projenizi klonlayarak ve yeni klonlanmış klasörünüzde bir dizi sabit bağlantı / bağlantı oluşturarak bunu aşmanıza olanak tanır. Bu bağlantılar orijinali işaret eder, bu da kodu düzenlemenize ve sonuçları her klonlanmış unity'de oldukça hızlı bir şekilde görmenize olanak tanır.

# Nasıl?
Bunu bir unity projesine eklemenin birkaç yolu vardır:
1. Bu kodu projenizde herhangi bir yere yerleştirin!
2. Bu projeyi başka bir yerde kontrol edin ve Unity paket manifestonuzla ona işaret edin:
``"com.hwaet.projectcloner":  "file:../../../../[manifesto dosyanızdan package.json'a giden göreli yol]"``
3. Makinenizde git yüklüyse (ve unity > 2018.3.0b7 ise) paket bildiriminize doğrudan burayı işaret eden bir satır ekleyin!
``"com.hwaet.projectcloner": "https://github.com/hwaet/UnityProjectCloner.git"``
4. Son unity sürümlerinde, yukarıdaki git bağlantısını manifestonuzu manuel olarak düzenlemeden doğrudan düzenleyiciye ekleyebilirsiniz:
![image](https://user-images.githubusercontent.com/30280876/132378040-9d985e3b-634b-46ee-a0c5-5fd52cf37f0b.png)


# Nereye?
Yeni klonlanmış proje orijinalinin hemen yanına yerleştirilecektir. Böylece klasör yapınız şöyle görünecektir:
- Kök/ProjeAdı
- Root/ProjectName_clone_0
- Root/ProjectName_clone_1
...

Bir klon oluşturmaya ve onu yönetmeye izin veren pencereyi açmak için Unity Editor'de "Araçlar/Proje Klonlayıcı "ya gidin. Klon oluşturulduktan sonra, aynı pencereden başlatabilirsiniz ("Klon projeyi aç" düğmesi orada görünecektir). Klonu Unity Hub'a veya başka bir yere eklemenize gerek yok.

# Gelecek Planları:
- Şu anda kernel32 yerine klasör bağlantılarını oluşturmak için bir terminal komutu kullanıyorum ve bu çok daha akıllıca olacaktır. Bu yüzden bunun gelecekteki geçişlerinde uygulanacak.
- Mac ve linux desteği harika olurdu.

# Bilinen Sorunlar:
- Bir Editör örneğinde kodlanabilir nesneler kullanıldığında, klonun bu değişikliği fark etmesi için kullanıcının bir kaydetmeyi tetiklemesi gerekir (sahne veya proje kaydetmeleri işe yarıyor gibi görünüyor). Aksi takdirde, kodlanabilir nesnenin değerleri önbelleğe alınmış gibi görünür. SO'larla çalışırken sık sık kaydedin!
