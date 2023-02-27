# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu

Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/] (update, delete, drop sorguları iptal edilmiştir).

### Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını altlarına yazın.

    1) ÖRNEK SORU: Öğrenci tablosundaki tüm kayıtları listeleyin.

    	CEVAP: select * from ogrenci


    2) Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.

    	Cevap :  select ograd, ogrsoyad, sinif from ogrenci

    3) Öğrenci tablosundaki kız öğrencileri listeleyin.

    	Cevap :  select * from ogrenci where cinsiyet = "k"

    4) Öğrenci tablosunda kaydı bulunan sınıfların adını her sınıf bir kez görüntülenecek şekilde listeleyiniz

    	Cevap :  select distinct sinif from ogrenci

    5) Öğrenci tablosunda, 10A sınıfında olan kız öğrencileri listeleyiniz.

    	Cevap :  select * from ogrenci where cinsiyet="k" and sinif="10A"

    6) Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz.

    	Cevap :  select ograd, ogrsoyad, sinif from ogrenci where sinif="10A" or sinif="10B"

    7) Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarası olarak listeleyiniz. (as kullanım örneği)

    	Cevap :  select ograd as adı, ogrsoyad as soyadı, ogrno as okulnumarası from ogrenci


    8) Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (concat, as kullanım örneği)

    	Cevap : select concat(ograd,ogrsoyad) as adsoyad from ogrenci

    9) Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

    	Cevap : select * from ogrenci  where ograd LIKE 'A%'

    10) Kitaplar tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.

    	Cevap :
    		select * from kitap
    		where sayfasayisi
    		between 50 and 200

    11) Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.

    	Cevap :
    		select * from ogrenci
    		where ograd in ('Fidan', 'İsmail', 'Leyla')

    12) Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.

    	Cevap :
    		select * from ogrenci
    		where ograd like 'A%' or
    		ograd like 'D%' or
    		ograd like 'K%'

    13) Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.

    	Cevap :
    		select ograd, ogrsoyad, sinif, cinsiyet from ogrenci
    		where (sinif="9A" and cinsiyet="E")
    		or
    		(sinif="9B" and cinsiyet="K")

    14) Sınıfı 10A veya 10B olan erkekleri listeleyiniz.

    	Cevap :
    		select * from ogrenci
    		where (sinif="10A" or sinif="10B")
    		and cinsiyet= "E"

    15) Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.

    	Cevap :
    		select * from ogrenci
    		where dtarih = 1989

    16) Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.

    	Cevap :
    		select * from ogrenci
    		where ogrno
    		between 30 and 50

    17) Öğrencileri adına göre sıralayınız (alfabetik).

    	Cevap :
    		Select * From ogrenci Order By ograd

    18) Öğrencileri adına, adı aynı olanlarıda soyadlarına göre sıralayınız.

    	Cevap :
    		Select * From ogrenci
    		Order By ograd, ogrsoyad

    19) 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.

    	Cevap :
    		Select * From ogrenci
    		Where sinif = "10A"
    		Order By ogrno
    		DESC

    20) Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.
    [İPUCU: `Select top tüm mysql versiyonlarında düzgün çalışmaz. LİMİT kullanmak daha faydalıdır`]

    	Cevap : Select * From ogrenci Limit 10

    21) Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.

    	Cevap :
    		Select ograd, ogrsoyad, dtarih
    		From ogrenci
    		Limit 10

    22) Sayfa sayısı en fazla olan kitabı listeleyiniz.

    	Cevap :

    		1.Yontem :
    			Select * From kitap
    			Where sayfasayisi =
    			(Select Max(sayfasayisi) From kitap)

    		2.Yontem :
    			Select * From kitap
    			Order By sayfasayisi Desc
    			Limit 1

    		3.Yontem :
    			Select MAX(sayfasayisi) as maxsayfa
    			From kitap

    23) Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.

    	Cevap :
    		Select * From ogrenci
    		Order By dtarih Desc
    		Limit 1

    24) 10A sınıfındaki en yaşlı öğrenciyi listeyin.

    	Cevap :
    		Select * From ogrenci
    		Order By dtarih
    		Limit 1

    25) İkinci harfi N olan kitapları listeleyiniz.

    	Cevap :
    		Select * From kitap
    		Where kitapadi
    		Like "_N%"

    26) Öğrencileri sınıflarına göre gruplayarak listeleyin.

    	Cevap :
    		Select Count(*), sinif From ogrenci
    		Group By sinif

    27) Öğrencileri her sorgulamada sıralaması farklı olacak şekilde rastgele listeleyin.
    [İPUCU: rand() fonksiyonu]

    	Cevap :
    		Select * From ogrenci
    		Order By RAND()

    28) Öğrenci tablosundan Rastgele bir öğrenci seçiniz.

    	Cevap :
    		Select * From ogrenci
    		Order By RAND()
    		Limit 1

    29) 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.

    	Cevap :
    		Select ograd, ogrsoyad, ogrno, sinif From ogrenci
    		Where sinif = "10A"
    		Order By RAND()
    		Limit 1

    # Esnek
    30) Öğrenci tablosunda aynı isimde kaçar öğrenci olduğunu bulmak istiyoruz.
    Öğrenci isimlerinin sayısını "adet" olarak öğrencilerin isimleri "isim" olarak listeleyin.
    [İPUCU: count() ve group by]

    	Cevap :
    		Select Count(ograd) as ogrenciadet, ograd as isim from ogrenci
    		Group By ograd
