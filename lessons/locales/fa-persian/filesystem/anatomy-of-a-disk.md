# آناتومی دیسک

## محتویات درس

هاردیسک‌ها می‌توانند به پارتیشن‌ها تقسیم شوند و در‌واقع چندین دستگاهِ بلاک بسازند. بلاک در حقیقت به طول معینی از بیت‌ها یا بایت‌ها گفته می‌شود که در یک دستگاه ذخیره‌سازی قرار می‌گیرد. مثال‌ها در خصوص ‎/dev/sda1 و ‎/dev/sda2 یا ‎/dev/sda را به خاطر می‌آورید؟ ‎/dev/sda کل دیسکِ سخت و ‎/dev/sda1 اولین پارتیشن بر روی همان دیسک سخت است. پارتیشن‌ها در زمانی که به داده‌های مجزا بر روی دیسک نیاز دارید و یا اینکه می‌خواهید در یک دیسک از فایل‌سیستم‌های مختلف بهره ببرید، بسیار کاربردی هستند و به جای اختصاص کل هارد دیسک به یک نوع فایل‌سیستم، می‌توانید با کمک آن‌ها دست و بال بازتری داشته باشید.

**جدول پارتیشن**

هر دیسک سختی، یک جدول پارتیشن دارد، که این جدول به سیستم در خصوص چگونگی پارتیشن‌شدنِ دیسکِ سخت گزارش می‌دهد. این جدول، تشریح جایگاهِ شروع و پایانِ پارتیشن‌ها و اینکه کدامیک از آن‌ها، پارتیشنِ با قابلیت راه‌اندازی است، را بر عهده دارد. همچنین اطلاعاتی را در خصوص اینکه کدامیک از سکتورهای دیسک به کدام پارتیشن تعلق دارد، در خود ذخیره کرده است. دو طرح اصلی برای جدول پارتیشن وجود دارد که یکی ‎Master Boot Record (MBR) و دیگری ‎GUID Partition Table (GPT) نام دارد.

**پارتیشن**

دیسک‌ها از پارتیشن‌هایی تشکیل شده‌اند تا کمکی به ما در مرتب‌سازی و سامان‌دادن به فایل‌ها باشند. شما می‌توانید چندین پارتیشن بر روی یک هارد دیسک داشته باشید، ولی این پارتیشن‌ها نمی‌توانند بر روی هم قرار بگیرند و نهایتاً شانه به شانه‌ی هم در دیسک جای خوش می‌کنند. اگر فضایی بر روی دیسک باشد که به هیچ پارتیشنی تعلق ندارد، آن را فضای خالی می‌نامیم. نوع پارتیشن‌هایتان به جدول پارتیشن بستگی دارد. در درون یک پارتیشن می‌توانید یک فایل‌سیستم داشته باشید و یا حتی آن را به چیزهای دیگری مثل swap اختصاص دهید. در خصوص swap در آینده بیشتر صحبت خواهیم کرد.

*MBR*

+ جدول پارتیشن سابق است که به عنوان استاندارد استفاده می‌شد.
+ می‌تواند پارتیشن‌های اصلی (primary)، گسترده (extended) و منطقی (logical) داشته باشد.
+ MBR محدود به داشتن نهایتاً چهار پارتیشن اصلی است.
+ پارتیشن‌های بیشتر با ساخت یک پارتیشن اصلی به عنوان پارتیشن گسترده، می‌توانند ایجاد شوند (البته هار دیسک می‌تواند تنها یک پارتیشن گسترده داشته باشد). سپس شما می‌توانید پارتیشن‌های منطقی را در داخل پارتیشن گسترده به تعداد دلخواه بسازید. از پارتیشن‌های منطقی هم می‌توان درست شبیه به سایر پارتیشن‌ها بهره برد. مسخره است، می‌دانیم.
+ هارد دیسک‌هایی تا ظرفیت ۲ ترابایت را پشتیبانی می‌کند.

*GPT*

+ GUID Partition Table (GPT) به استاندارد جدیدی برای پارتیشن‌بندی دیسک بدل شده است.
+ تنها یک نوع پارتیشن دارد و شما می‌توانید بسیاری از آن‌ها را بر روی یک دیسک بسازید.
+ هر پارتیشن یک شناسه‌ی عمومیِ یکتا دارد که به آن GUID می‌گویند.
+ GPT در سیستم‌هایی که بر اساس UEFI راه‌اندازی می‌شوند، کاربرد فراوانی دارد (در خصوص UEFI در دوره‌ی دیگری، صحبت خواهیم کرد).

**ساختار فایل‌سیستم**

از خیر سر درس‌های قبل، می‌دانیم که فایل‌سیستم، مجموعه‌ای سامان‌مند از فایل‌ها و دایرکتوری‌هاست. در ساده‌ترین شکلش، یک فایل‌سیستم از یک پایگاه داده که فایل‌ها را مدیریت می‌کند، ساخته شده است. در آینده وارد جزئیات بیشتری خواهیم شد.

+ بلاک راه‌انداز یا بوت‌بلاک – جایگاه بوت‌بلاک در چند سکتور ابتدایی فایل‌سیستم است. این سکتورها شامل اطلاعاتی که برای راه‌اندازی سیستم‌عامل نیاز است، می‌شوند و به کار خود فایل‌سیستم نمی‌آیند. سیستم‌عامل نیز فقط یک بوت‌بلاک، نیاز دارد و اگر شما بیش از یکی دارید، بقیه آن‌ها بی‌استفاده خواهند ماند.
+ سوپر بلاک – یک بلاک بعد از بوت‌بلاک، سوپر بلاک خوانده می‌شود و شامل اطلاعاتی در خصوص خود فایل‌سیستم است. اطلاعاتی مانند اندازه‌ی جدول آی‌نود، اندازه‌ی بلاک‌های منطقی و اندازه‌ی فایل‌سیستم.
+ جدول آی‌نود – اینجور فکر کنید که با یک پایگاه داده‌ای طرفید که وظیفه‌ی مدیریت و سامان دادن به فایل‌های ما را بر عهده دارد. و اینکه اگر نفهمیدید چی شد، نگران نباشید چون ما یک درس کامل برای تشریح آی‌نودها داریم. هر فایل یا دایرکتوری یک ورودی یکتا در جدول آی‌نود دارد و اطلاعات مختلفی در خصوص فایل در این جدول نوشته می‌شود.
+ بلاک داده یا دیتا بلاک – بلاک داده، دقیقاً دیتایی است که برای فایل‌های و دایرکتوری‌ها مورد استفاده قرار می‌گیرد.

حالا بد نیست نگاهی به تفاوت‌های جدول‌های پارتیشن بیندازیم. یک مثال از یک مدل پارتیشن‌بندی که با استفاده از MBR درست شده را در پایین می‌بینید. شما می‌توانید پارتیشن‌های اصلی، گسترده، و منطقی را بر روی دستگاهِ زیر ببینید.

```
pete@icebox:~$ sudo parted -l
Model: Seagate (scsi)
Disk /dev/sda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  6860MB  6859MB  primary   ext4            boot
 2      6861MB  21.5GB  14.6GB  extended
 5      6861MB  7380MB  519MB   logical   linux-swap(v1)
 6      7381MB  21.5GB  14.1GB  logical   xfs
```

و این هم یک مثال از GPT که تنها از یک شناسه‌ی یکتا برای پارتیشن‌ها استفاده می‌کند.

```
Model: Thumb Drive (scsi)
Disk /dev/sdb: 4041MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size     File system  Name        Flags
 1      17.4kB  1000MB  1000MB                first
 2      1000MB  4040MB  3040MB                second
```

## تمرین

فرمان parted -l را اجرا و نتیجه را سبک‌سنگین کنید. خروجی ندارد؟ با استفاده از مجوز روت، فرمان را تکرار کنید.

## سؤال آزمون

در طرح پارتیشن MBR برای ساخت بیش از چهار پارتیشن از چه نوع پارتیشنی استفاده می‌شود؟

## پاسخ آزمون

extended
