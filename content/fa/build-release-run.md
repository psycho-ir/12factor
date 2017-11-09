## V. ساخت، انتشار و اجرا
### مراحل ساخت و اجرا را صراحتا از هم جدا کنید

یک  [کدبیس](./codebase) از طریق گذراندن این سه مرحله به یک دپلوی تبدیل می‌شود(منظور دپلوی غیر از حالت development است) :

* *مرحله ساخت* مرحله‌ای است که کد داخل مخزن(ریپو) را تبدیل می‌کند به یک بسته‌ی(bundle) قابل اجرا به نام *ساخت(build)*. با استفاده از یک کامیت مشخص شده در پروسه‌ی دپلوی که به یک نسخه‌ی بخصوص از کد اشاره می‌کند، مرحله‌ی ساخت [وابستگی‌ها](./dependencies) را دانلود و کد‌ها را کامپایل می‌کند.

* *مرحله‌ی انتشار(ریلیز)* نسخه‌ی ساخته شده (بیلد شده) را به عنوان ورودی دریافت ‌می‌کند و پیکربندی‌ این دپلوی بخصوص را روی آن اعمال‌میکند.*نسخه‌ی ریلیز شده(release)* حاوی فایل‌های بیلد شده و پیکربندی‌هاست و آماده اجرای فوری در محیط اجراست.

* *مرحله‌ی اجرا* (که به ران‌تایم هم معروف است) app را در محیط اجرا، اجرا می‌کند، با اجرا کردن  [پراسس‌های](./processes) app مورد نظر از ریلیز انتخاب شده.


![کد تبدیل به یک بیلد شده، که بعد از اعمال یک کانفیگ یک ریلیز ساخته شده.](/images/release.png)


** یک app که قواعد ۱۲گانه را رعایت کرده همواره صراحتا مراحل بیلد، ریلیز و اجرا  را از هم جدا می‌کند.** به عنوان مثال، این امکان ندارد که در ران‌تایم روی کد تغییری ایجاد کنیم، چون هیچ راهی وجود ندارد که آن تغییرات را به مرحله‌ی بیلد برسانیم.


Deployment tools typically offer release management tools, most notably the ability to roll back to a previous release.  For example, the [Capistrano](https://github.com/capistrano/capistrano/wiki) deployment tool stores releases in a subdirectory named `releases`, where the current release is a symlink to the current release directory.  Its `rollback` command makes it easy to quickly roll back to a previous release.

Every release should always have a unique release ID, such as a timestamp of the release (such as `2011-04-06-20:32:17`) or an incrementing number (such as `v100`).  Releases are an append-only ledger and a release cannot be mutated once it is created.  Any change must create a new release.

Builds are initiated by the app's developers whenever new code is deployed.  Runtime execution, by contrast, can happen automatically in cases such as a server reboot, or a crashed process being restarted by the process manager.  Therefore, the run stage should be kept to as few moving parts as possible, since problems that prevent an app from running can cause it to break in the middle of the night when no developers are on hand.  The build stage can be more complex, since errors are always in the foreground for a developer who is driving the deploy.
