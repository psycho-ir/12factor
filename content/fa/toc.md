فاکتور‌های دوازده‌گانه
==================

## [I. کد‌های پروژه](./codebase)
### یک کدبیس در یک سیستم کنترل ورژن اما چندین دپ

## [II. وابستگی‌ها ](./dependencies)
### وابستگی‌ها باید صراحتا تعریف شوند و ایزوله نگهداری شوند

## [III. پیکربندی‌ها](./config)
### پیکربندی‌ها و تنظیمات متغیر پروژه(آن‌هایی که بین دپلوی‌های مختلف ممکن است تغییر کنند) در Environment نگهدارید.

## [IV. سرویس‌های پشتی](./backing-services)
### با سرویسهای پشتی همانند منابع متصل برخورد کنید.

## [V. ساخت، انتشار و اجرا](./build-release-run)
### Strictly separate build and run stages

## [VI. پراسس‌ها](./processes)
### app را با استفاده از یک یا چند پراسس بدون state اجرا کنید

## [VII. سرویس‌دهی با پورت‌ها](./port-binding)
### سرویس‌ها را از طریق پورت‌ها ارائه دهید

## [VIII. Concurrency](./concurrency)
### Scale out via the process model

## [IX. Disposability](./disposability)
### Maximize robustness with fast startup and graceful shutdown

## [X. Dev/prod parity](./dev-prod-parity)
### Keep development, staging, and production as similar as possible

## [XI. Logs](./logs)
### Treat logs as event streams

## [XII. Admin processes](./admin-processes)
### Run admin/management tasks as one-off processes
