# Schema.org
Schema.org - это стандарт семантической разметки данных в сети, объявленный поисковыми системами.

Используя такую разметку можно отобразить больше информации в поисковой выдаче и попасть в дополнительные информационные разделы (при этом страницы с разметкой будет выше в результатах чем обычная).

Для пользователя же сайт с рейтингом, ценой за услуги, количеством отзывов будет привлекательнее пустого.

На наших сайтах мы используем современный формат json-ld, иногда, чтобы отобразить информацию в Яндексе, применяем атрибуты к тегам, так как Яндекс пока не поддерживает json-ld в поиске.

Для главной и страницы контактов подходит @type Hotel:
```
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "Hotel",
  "name": "Название",
  "address": {
    "@type": "PostalAddress",
    "addressCountry": "Страна",
    "addressLocality": "Город",
    "addressRegion": "Регион",
    "postalCode": "Почтовый индекс",
    "streetAddress": "Улица, дом"
  },
  "telephone": "69-79-66",
  "email": "email@hotel.ru",
  "priceRange": "от 2900 руб",
  "image": "picture.jpg",
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.9",
    "reviewCount": "1240"
  }
}
</script>
```

В поисковой выдаче это выглядит примерно так:
![schema1.jpg](http://atomicdocs.dev2.travelline.ru/resources/images/schema1.jpg)

Для страницы номера @type HotelRoom и Product:
```
<script type="application/ld+json">
{
  "@context":"http://schema.org/",
  "@type":["HotelRoom","Product"],
  "name":"Стандарт двухместный с двумя кроватями",
  "image":"picture.jpg",
  "description":"Описание номера",
  "offers":
  {
    "@type":"Offer",
    "businessFunction":"http://purl.org/goodrelations/v1#LeaseOut",
    "priceSpecification":{
      "@type":"UnitPriceSpecification",
      "price":"2820",
      "priceCurrency":"RUB",
      "unitCode":"DAY"
    }
  }
}</script>
```

Существуют аналогичные @type для услуг, ресторанов и прочего.

Ну и конечно нужно структурировать хлебные крошки. Здесь использованы атрибуты к тегам, т.к обязательно требуется поддержка Яндекс поиска:
```
<ul class="breadcrumbs" itemscope="" itemtype="http://schema.org/BreadcrumbList">
    <li class="breadcrumbs__item" itemprop="itemListElement" itemscope="" itemtype="http://schema.org/ListItem">
        <a class="breadcrumbs__link" itemprop="item" href="/" title="Отель">
            <span itemprop="name">Отель</span>
        </a>
        <meta itemprop="position" content="0">
    </li>
    <li class="breadcrumbs__item" itemprop="itemListElement" itemscope="" itemtype="http://schema.org/ListItem">
        <a class="breadcrumbs__link" itemprop="item" href="/rooms/" title="Номера и цены">
            <span itemprop="name">Номера и цены</span>
        </a>
        <meta itemprop="position" content="1">
    </li>
    ...
</ul>
```

Для проверки корректности микроразметки используем [сервис гугла](https://search.google.com/structured-data/testing-tool?hl=ru).