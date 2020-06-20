# Virus Total

Зараженный сайт не продает.  
Сайт у постетителя не откроется в браузере, или откроется, но нанесет вред его устройству.
<p align="center">
  <img src="https://1.downloader.disk.yandex.ru/preview/3553ed75f28f0dacba46a27bbc8de45ae745f7f860a8f190217e4041d117357c/inf/6cc1pmnoLahjlDOT7Ydg3uP3XGbNe8matF6V95BRII4eDRybwR8RGAmQl8Hxw4XBJ19FOu4mSqnVoFTCiHkKEg%3D%3D?uid=31348869&filename=blocked.png">
</p>

Проверить сайт на вирусы можно с помощью <a href="https://www.virustotal.com/ru/">VirusTotal</a>. 
Сервис показывает, числится ли сайт в базах данных антивирусных программ.   
Проверьте ваш сайт на этом сервисе, это быстро.

### Если "Угроз не обнаружено" - можете дальше не читать.
<p align="center">
  <img src="http://atomicdocs.dev2.travelline.ru/resources/images/virus-total/virus-total-after.jpg">
</p>
Ни один из сервисов в Virus Total (Yandex Safebrowsing, Google Safebrowsing, Kaspersky, и другие - ~70 шт.) не выявил заражения.  


### Если "Обнаружено угроз: N"
<p align="center">
  <img src="http://atomicdocs.dev2.travelline.ru/resources/images/virus-total/virus-total-before.jpg">
</p>
Вылечим сайт и отправим заявку в каждый из сервисов на удаление из блек-листа.

#### 0. Смена доступов
 1) Смените пароли доступа к сайту у администраторов и ответственных сотрудников.

 2) Смените пароли доступа по ssh и ftp.
 
#### 1. Поиск вредоносного кода
a) Выкачаем сайт и проверим программами:

- Kaspersky Internet Security
- Dr.Web CureIt!
- Ai-Bolit
b) Проверяем сайт онлайн сервисами
- https://rescan.pro/
- https://online.drweb.com/result2/?lng=en&url=t
c) Проверяем Инструментом, загруженным на хостинг https://revisium.com/ai/

#### 2. Удаление вредоносного кода
Программы или сервисы покажут нам фрагмент вредоносного кода. Теперь мы можем найти эти фрагменты и удалить в файлах сайта.
Следует помнить, что удаление фрагментов и файлов необходимо производить с осторожностью - можно удалить важные файлы и фрагменты, без которых сайт или часть его функционала может не работать. Всегда должна быть резервная копия.

После чистки нужно посмотреть в папки и проверить, не остались ли подозрительные файлы.
В поисках поможет список (https://www.virustotal.com/#/domain/YOUR-DOMAIN.RU) найденных вредоносов 

#### 3. Частые кейсы


#### 4. Теперь расскажем сервисам, что сайт больше не заразный

Вот шаги:
- Если сервиса нет среди часто встречаемых (см. ниже), находим его <a href="https://support.virustotal.com/hc/en-us/articles/115002146809-Contributors)">здесь</a>;
- Находим на сайте email техподдержки, или страницу заполнения заявки;
- Сообщаем им в письме с темой "False positives" просьбу (можете сформулировать по-своему):

Hello, my site YOUR-DOMAIN.RU (заменить на ваш домен) is in the infected list:  
https://www.virustotal.com/#/url/968baed364f2caac4209589e34aea92a86f173da1675156c82423cda2401e213/detection  
We conducted his treatment.  
Can you double-check my site and remove it from the list of viruses of your service (тут название их сервиса, чтобы они понимали, что мы обращаемся именно к ним, а не просим удалить нас из всех среагировавших сервисов)?  
Thank you.

Перевод:  
Привет, мой сайт YOUR-DOMAIN.RU попал в список зараженных:  
https://www.virustotal.com/#/url/968baed364f2caac4209589e34aea92a86f173da1675156c82423cda2401e213/detection    
Мы провели его лечение.  
Можете ли вы перепроверить мой сайт и удалить его из списка вирусных вашего сервиса (Название сервиса)?  
Спасибо.  

#### Кому часто приходится писать по обновлению статуса:

<b><a href="https://secure2.sophos.com/en-us/support/submit-a-sample.aspx">Sophos</a></b> (5 дней на обработку заявки)

<b><a href="https://www.bitdefender.com/submit/">BitDefender</a></b> (1 день)

<b>Emsisoft</b> (1 день) Пишем в support@emsisoft.com с темой "False positives"
или пишем название сайта здесь https://support.emsisoft.com/forum/58-false-positives/

<b>DNS8</b> (1 день) Пишем в dns8@layer8.pt с темой "False positives"

<b>Forcepoint ThreatSeeker</b> (1 день) Пишем в suggest@forcepoint.com с темой "False positives", или на 
<a href="https://www.facebook.com/ForcepointLLC">страницу</a>

<b><a href="https://threatcenter.crdf.fr/false_positive.html" style="color:#24292e;">CRDF</a></b> (4 часа)


