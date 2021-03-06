## VII. سرویس‌دهی با پورت‌ها
### سرویس‌ها را از طریق پورت‌ها ارائه دهید

اپلیکیشن‌های وب گاهی درون کانتینرهای وبسرور اجرا می‌شوند.برای مثلا اپ‌های PHP می‌توانند به عنوان یک ماژول داخل  [Apache HTTPD](http://httpd.apache.org/)، یا اپ‌های جاوا داخل  [Tomcat](http://tomcat.apache.org/) اجرا شوند.

** اپی که قواعد ۱۲گانه را رعایت کرده همیشه کاملا خودمختار عمل‌ می‌کند ** و برای ارائه سرویس وب به محیط اجرای فراهم شده توسط یک وبسرور متکی نیست.اپ وب ** خدمات HTTP خود را به عنوان یک سرویس از طریق یک پورت ارائه می‌دهد**، و روی آن پورت گوش می‌دهد و به درخواست‌های HTTP پاسخ می‌دهد.

در یک محیط توسعه لوکال، یک برنامه‌نویس می‌تواند URL سرویس را مستقیما مشاهده کند، مثلا `http://localhost:5000/` تا به خدمات ارائه شده توسط اپ دسترسی پیدا کند.در محیط دپلوی هم، یک لایه‌ی روتینگ مسئولیت هدایت درخواست‌ها از هاست‌نیم عمومی سرور به پورتی که اپ روی آن سرویس می‌دهد را به عهده می‌گیرد.

این کار معمولا به این شکل پیاده‌سازی می‌شود که یک کتابخانه‌ی وبسرور از طریق [تعریف وابستگی‌ها](./dependencies) به عنوان وابستگی جدید به اپ اضافه می‌شود (م. تا بتواند سرویس‌های خودش را روی پروتکل HTTP ارائه دهد)، مثلا  [Tornado](http://www.tornadoweb.org/) برای پایتون, [Thin](http://code.macournoyer.com/thin/) برای روبی, یا [Jetty](http://www.eclipse.org/jetty/) برای جاوا یا دیگر زبان‌های بر پایه‌ی JVM. تمام این اتفاقات کاملا در *داخل کد اپ* اتفاق می‌افتد.ارتباط بین اپ و محیط اجرا کاملا روی پورتی که در اختیار اپ قرار گرفته تعریف می‌شود و اپ درخواست‌ها را از طریق همان پورت پاسخ می‌دهد.

HTTP تنها سرویسی نیست که می‌تواند از طریق پورت به بیرون از اپ ارائه شود.تقریبا تمام انواع نرم‌افزار‌های سرویس‌دهی می‌توانند از همین روش سرویس‌دهی کنند(م. متصل شدن و گوش دادن به یک پورت و پاسخ دادن به درخواست‌ها) به عنوان مثال می‌توان به  [ejabberd](http://www.ejabberd.im/) (با پروتکل [XMPP](http://xmpp.org/)), و [Redis](http://redis.io/) (با پروتکل [Redis protocol](http://redis.io/topics/protocol)) اشاره کرد.

به این نکته جالب هم توجه کنید که این روش سرویس‌دهی روی پورت می‌تواند منجر به این شود که یک اپ به عنوان  [سرویس پشتی](./backing-services) برای یک اپ دیگر عمل کند، به این شکل که کافیست URL سرویس پشتی را به عنوان آدرس منبع در  [کانفیگ](./config) اپ دیگر قرار دهید.
