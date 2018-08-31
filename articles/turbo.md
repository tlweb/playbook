# Яндекс Turbo

На ряду с технологией [AMP](https://github.com/tlweb/playbook/blob/master/amp.md) на разрабатываемых сайтах мы применяем технологию Turbo от Яндекс.
Turbo страницы загружаются примерно в 15 раз быстрее обычных, хранятся на серверах поисковика и для привлечения внимания в поисковой выдаче помечены значком с ракетой.
Также такие страницы ранжируются в мобильной поисковой выдаче Яндекса выше обычных.

Turbo страницы формируются через RSS-канал, т.е на сайте необходимо создать точку доступа к контенту и указать её в Яндекс.Вебмастере.

Мы применяем Turbo только для простых, не интерактивных страниц, таких как, например, новости. Помимо самого контента на странице можно отобразить: логотип, url сайта, меню.

Для сайтов на CMS Bitrix использован следующий подход:
1. Для нужного компонента создаётся новый шаблон;
2. В заголовке шаблона указывается:
```
header('Content-type: text/xml');
header('Pragma: public');
header('Cache-control: private');
header('Expires: -1');
```
3. Вывод данных формируется как RSS-канал с указанием version и атрибута turbo:
```
$page = "<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<rss
    xmlns:yandex=\"http://news.yandex.ru\"
    xmlns:media=\"http://search.yahoo.com/mrss/\"
    xmlns:turbo=\"http://turbo.yandex.ru\"
    version=\"2.0\"
>";

$page .= "<channel>";

foreach($arResult["ITEMS"] as $arElement):
  $name = preg_replace('/&(?!#?[a-z0-9]+;)/', '&amp;', $arElement["NAME"]);
  $image = $arElement["PREVIEW_PICTURE"]["SRC"];
  $page .= "<item turbo=\"true\">";
  $page .= "<link>".SITE_URL.$arElement["DETAIL_PAGE_URL"]."</link>";
  $page .= "<title>".$name."</title>";
  $page .= "<description>".$arElement["PROPERTIES"]["DESCRIPTION"]["VALUE"]."</description>";
  $page .= "<pubDate>".date(DATE_RFC822, strtotime($arElement["ACTIVE_FROM"]))."</pubDate>";
  $page .= "<turbo:content>
                <![CDATA[
                    <header>
                        <h1>".$name."</h1>";
                        if ($image):
                          $page .= "<figure><img src=\"".$image."\" /></figure>";
                        endif;
                    $page .= "<menu>
                      <a href=\"#\">Пункт меню 1</a>
                      <a href=\"#\">Пункт меню 2</a>
                      <a href=\"#\">Пункт меню 3</a>
                      <a href=\"#\">Пункт меню N</a>
                    </menu>";
                    $page .= "
                    </header>
                    ".$arElement["DETAIL_TEXT"]."
                 ]]>
            </turbo:content>";
  $page .= "</item>";
endforeach;

$page .= "</channel>";
$page .= "</rss>";

echo $page;
```

Яндекс развивает механизм автопарсинга Турбо-страниц и увеличивает количество типов доступных полей, что делает использования этой технологии достпной.  