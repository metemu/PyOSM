<img src="https://github.com/metemu/PyOSM/blob/master/images/intro.PNG">

# OpenStreetMap

OpenStreetMap (OSM), Wikipedia'nın başarısından esinlerek tüm dünyanın haritasını üretmek amacıyla 2004 yılında başlatılan katılımcı bir projedir. OSM'nin genel kullanım amaçları harita servisi, geocoding, reverse geocoding, rota planlama olarak sıralanabilir.

https://www.openstreetmap.org

<img src="https://github.com/metemu/PyOSM/blob/master/images/osm.PNG">

# OSM Veri Modelleri

OSM'de veriler node, way, relation şeklinde tutulmaktadır. Node türü koordinat (lat,lon) bilgisi olan nokta veri tipini ifade ederken, way türü ise düğümlerden oluşan çizgi veri tipini temsil eder. Relation ise çoklu node, way ve relation içeren karma bir veri tipidir.

<img src="https://github.com/metemu/PyOSM/blob/master/images/node.png">

# OSM'ye nasıl katkı sunulur?
OSM'nin veri kaynağı gönüllü kullanıcılarıdır. OSM'ye katkı sunmak için yeni bir veri ekleyebilir ya da mevcut eksik/hatalı veriyi düzenleyebiliriz. Bu kapsamda tarayıcı editöreri iD ve Potlach 2 veya masaüstü uygulaması JOSM kullanılabilir.

# OSM'den nasıl veri indirilir?

OSM'den veri indirmenin bir çok yolu vardır. OSM veritabanındaki tüm dünyaya ait haftalık güncellenen veriyi sıkıştırılmış XML dosyası olarak paylaşmaktadır (https://planet.openstreetmap.org). Fakat bu yüksek boyutlu (~87 GB) dosyayı indirmek ve gereken veriyi süzmek oldukça zahmetli bir iştir.

Sadece kullanıcının ihtiyaç duyduğu bölgedeki ilgili veri türünü indirilebilmesi amacıyla çeşitli sorgularla veri çekilebilen OSM Overpass API geliştirilmiştir. wget/curl komutlarıyla script içerisinde OSM verisini aşağıdaki şekilde çekmek mümkündür.

    wget -O target.osm "https://overpass-api.de/api/interpreter?data=node[name=\"Gielgen\"];out;"

Ayrıca https://overpass-turbo.eu/ adresinden web tarayıcısı ile sorgulama yaparak da istenen veri filtrelenerek harita üzerinde görülebilir ve JSON/GeoJSON, GPX, KML, raw OSM data formatlarında indirilebilir. Örneğin; İstanbul iline ait yol verisini indirmek için sorgu kısmına aşağıdaki komutlar yazılmalıdır:

```
[out:json][timeout:25];
(
  area[name="İstanbul"];
  way["highway"](area);
);
out body;
(._; >;);
out skel qt;
```

# İstanbul İline ait yol verisi

https://overpass-turbo.eu/

<img src="https://github.com/metemu/PyOSM/blob/master/images/overpass.PNG">

<img src="https://github.com/metemu/PyOSM/blob/master/images/road.PNG">

Ayrıca bknz.

[Overpass API sorgu örnekleri](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_API_by_Example)

[OSM Feature Types](https://wiki.openstreetmap.org/wiki/Map_Features)

# OSM'den nasıl veri indirilir?

Veri indirmenin bir başka yolu ise günlük olarak güncellenen ülke/bölge verilerinin indirilebildiği Geofabrik veri sunucusu sayfasıdır. Anasayfada bulunan kıta, ülke, bölge isimlerine göre verileri çeşitli formatlarda indirmek mümkündür.

https://download.geofabrik.de

<img src="https://github.com/metemu/PyOSM/blob/master/images/geofabrik.PNG">

# OSM'den nasıl veri indirilir?

Eğer veriler sorgulama yapılmadan il/ilçe/mahalle ölçeğinde indirilmek istenirse BBBike web sayfası üzerinden OSM verilerinin indirme isteği gerçekleştirilebilir. Veri isteği sunucu tarafından hazırlandıktan sonra kullanıcının mail adresine bildirim ile birlikte indirme linki gönderilmektedir.

https://extract.bbbike.org/

<img src="https://github.com/metemu/PyOSM/blob/master/images/bbbike.PNG">

## Python ile [OSM Overpass API](https://wiki.openstreetmap.org/wiki/Overpass_API) üzerinden veri indirme yöntemleri için [PyOSM.ipynb](https://nbviewer.jupyter.org/github/metemu/PyOSM/blob/master/PyOSM.ipynb) notebook dosyasına göz atabilirsiniz.

[Muhammed Oğuzhan METE](https://web.itu.edu.tr/metemu) | metemu@itu.edu.tr
