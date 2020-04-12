<img src="https://github.com/metemu/PyOSM/blob/master/images/intro.PNG" width="800" height="400">

# OpenStreetMap (OSM)

OSM, Wikipedia'nın başarısından esinlerek tüm dünyanın haritasını üretmek amacıyla 2004 yılında başlatılan katılımcı bir projedir. OSM'nin genel kullanım amaçları harita servisi, geocoding, reverse geocoding, rota planlama olarak sıralanabilir.

https://www.openstreetmap.org

<img src="https://github.com/metemu/PyOSM/blob/master/images/osm.PNG" width="800" height="400">

# OSM Veri Modelleri

OSM'de veriler node, way, relation şeklinde tutulmaktadır. Node türü koordinat (lat,lon) bilgisi olan nokta veri tipini ifade ederken, way türü ise düğümlerden oluşan çizgi veri tipini temsil eder. Relation ise çoklu node, way ve relation içeren karma bir veri tipidir.

<img src="https://github.com/metemu/PyOSM/blob/master/images/node.jpg" width="400" height="200">

# OSM'ye nasıl katkı sunulur?
OSM'nin veri kaynağı gönüllü kullanıcılarıdır. OSM'ye katkı sunmak için yeni bir veri ekleyebilir ya da mevcut eksik/hatalı veriyi düzenleyebiliriz. Bu kapsamda tarayıcı editöreri iD ve Potlach 2 veya masaüstü uygulaması JOSM kullanılabilir.

# OSM'den nasıl veri indirilir?

OSM'den veri indirmenin bir çok yolu vardır. OSM veritabanındaki tüm dünyaya ait haftalık güncellenen veriyi sıkıştırılmış XML dosyası olarak paylaşmaktadır (https://planet.openstreetmap.org). Fakat bu yüksek boyutlu (~87 GB) dosyayı indirmek ve gereken veriyi süzmek oldukça zahmetli bir iştir.

Sadece kullanıcının ihtiyaç duyduğu bölgedeki ilgili veri türünü indirilebilmesi amacıyla çeşitli sorgularla veri çekilebilen OSM Overpass API geliştirilmiştir. wget/curl komutlarıyla script içerisinde OSM verisini aşağıdaki şekilde çekmek mümkündür.

wget -O target.osm "https://overpass-api.de/api/interpreter?data=node[name=\"Gielgen\"];out;"

Ayrıca https://overpass-turbo.eu/ adresinden web tarayıcısı ile sorgulama yaparak da istenen veri filtrelenerek harita üzerinde görülebilir ve JSON/GeoJSON, GPX, KML, raw OSM data formatlarında indirilebilir. Örneğin; İstanbul iline ait yol verisini indirmek için sorgu kısmına aşağıdaki komutlar yazılmalıdır:

[out:json][timeout:25];
(
  area[name="İstanbul"];
  way(area)[highway][name];
);
out body;
>;
out skel qt;

# İstanbul İline ait yol verisi

https://overpass-turbo.eu/

<img src="https://github.com/metemu/PyOSM/blob/master/images/overpass-turbo.PNG" width="800" height="400">

Overpass API sorgu örnekleri için:
https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_API_by_Example

OSM Feature Types için:
https://wiki.openstreetmap.org/wiki/Map_Features

# OSM'den nasıl veri indirilir?

Veri indirmenin bir başka yolu ise günlük olarak güncellenen ülke/bölge verilerinin indirilebildiği Geofabrik veri sunucusu sayfasıdır. Anasayfada bulunan kıta, ülke, bölge isimlerine göre verileri çeşitli formatlarda indirmek mümkündür.

https://download.geofabrik.de

<img src="https://github.com/metemu/PyOSM/blob/master/images/geofabrik.PNG" width="800" height="400">

# OSM'den nasıl veri indirilir?

Eğer veriler sorgulama yapılmadan il/ilçe/mahalle ölçeğinde indirilmek istenirse BBBike web sayfası üzerinden OSM verilerinin indirme isteği gerçekleştirilebilir. Veri isteği sunucu tarafından hazırlandıktan sonra kullanıcının mail adresine bildirim ile birlikte indirme linki gönderilmektedir.

https://extract.bbbike.org/

<img src="https://github.com/metemu/PyOSM/blob/master/images/bbbike.PNG" width="800" height="400">

## Python ile OSM Overpass API üzerinden veri indirme yöntemleri için <a href="https://nbviewer.jupyter.org/github/metemu/PyOSM/blob/master/PyOSM.ipynb">PyOSM.pynb</a> dosyasına göz atabilirsiniz.
