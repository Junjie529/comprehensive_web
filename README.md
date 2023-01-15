## Dompurify

<p align=center><img  width=1280 src="./assets/Firstpic.webp"  alt="DOMPurify"/></p>

### 📝فهرست

- [مقدمه](#مقدمه)
- [چرا جاوا اسکریپت؟](#چرا-جاوا-اسکریپت؟)
- [زمان رخ دادن XSS](#زمان-رخ-دادن-XSS)
- [انواع XSS](#انواع-XSS)
- [کاربردهای XSS Attack](#کاربردهای-XSS-Attack)
- [تعریف Document Object Model](#تعریف-Document-Object-Model)
- [حمله‌ی DOM-based XSS](#DOM-based-XSS)
- [حمله‌ی Reflected XSS](#reflected-xss)
- [منابع](#منابع)

### ✍️نویسندگان

- [آرش یادگاری](https://github.com/Arash1381-y)
- [ایمان محمدی](https://github.com/Imanm02)
- [هستی کریمی](https://github.com/HastiKarimi)

<hr>

## مقدمه

اگر شما یک برنامه‌نویس باشید، احتمال زیادی داره که درباره‌ی Cross-site scripting مطالبی خوانده باشید. Cross-site
scripting که معمولاً به اسم XSS شناخته می‌شود، به حملاتی گفته می‌شود که در آن اسکریپت‌های مخرب، به وب‌سایت های بزرگ و
معتبر تزریق می‌شوند.

حملات Cross-site Scripting در HTML، Flash، ActiveX و CSS امکان پذیر هستند، با این حال چون بیشتر کاربران اینترنت از جاوا
اسکریپت استفاده می‌کنند، اکثر هکرها بر روی این گزینه تمرکز دارند.

در این روش هدف هکر بیشتر کاربرانی هستند که به سایت مراجعه کرده‌اند. در واقع هکرها در این نوع حمله، اطلاعات کاربران یک
سایت را بدون اطلاع خودشون، به سرقت می‌برند.

## چرا جاوا اسکریپت؟

جاوا اسکریپت محبوب‌ترین زبان برنامه‌نویسی برای طراحی وب است، به شما این قابلیت‌ها را می‌دهد که هر کاری در صفحه‌ی وب
خودتون انجام دهید و ویژگی‌های پیچیده را به سادگی پیاده‌سازی کنید؛

در مقابل برای آسیب‌رسانی به صفحه‌ی وب و سرقت اطلاعات کاربرها هم از آن استفاده می‌شود و برای ورود به backend سایت و تزریق
اسکریپت‌های مخرب، جاوا اسکریپت محبوب‌ترین میزبان حملات Cross-site Scripting می‌باشد.

## زمان رخ دادن XSS

حمله‌ی Cross-site scripting یا XSS زمانی رخ می‌دهد که هکر یا کاربر مخرب، وب‌سایت یا وب‌اپلیکشن را به شکلی دستکاری می‌کند
تا جاوا اسکریپت مخرب بازگردد به کاربر. زمانی که این کد جاوا اسکریپت مخرب در مرورگر کاربر اجرا می‌شود، تمام ارتباطات
کاربر با وب‌سایت در معرض خطر قرار می‌گیرند و اطلاعات کاربر برای مهاجم، قابل سرقت خواهند بود.

## انواع XSS

سه نوع اصلی از حملات Cross-site Scripting وجود دارد:

۱. حمله‌ی XSS ذخیره شده (Stored cross-site scripting)
۲. حمله‌ی XSS منعکس شده (Reflected)
۳. حمله‌ی XSS مبتنی بر (DOM (Document Object Model
در ادامه هر کدام از انواع حملات XSS بررسی خواهد شد.

## کاربردهای XSS Attack

• هر عملیاتی که کاربران عضو شده در یک سامانه، به ویژه کاربران خاص با دسترسی بالا و premium، می‌توانند انجام دهند را
انجام دهد.

• به همه‌ی داده‌هایی که کاربر عضو می‌تواند به آن‌ها دسترسی پیدا کند، دسترسی داشته باشد؛ آن‌ها را بخواند یا دستکاری کند

• خود را به جای کاربر دیگری جا بزند و به حساب کاربری او نفوذ کند.

• یک بدافزار به وب‌سایت تزریق کند تا مراجعه‌کنندگان نیز آلوده شوند. مهاجم می‌تواند به وسیله‌ی بدافزار جاسوسی کند یا
اطلاعاتی را، حتی بدون آگاهی کاربر قربانی، به دست آورد.

• اطلاعات ورود یا لاگین کاربر را بخواند و ذخیره کند.

• وب‌سایت را Deface کند. (نوعی از حمله بر روی وب‌سایت که ویژگی‌های ظاهری سایت را تحت تاثیر قرار می‌دهد.)

## تعریف Document Object Model

همانطور که می‌دانید، DOM یا Document Object Model مدلی شی‌گرا با ساختاری درختی از اجزای موجود در صفحه می‌باشد. DOM
تقریبا، ظاهری مانند تصویر زیر دارد:

<p align=center><img width=800 src="./assets/DOM.jpg"  alt="DOM"/></p>

## DOM-based XSS

این نوع حمله‌ی XSS زمانی رخ می‌دهد که ورودی کاربر به روش خطرناکی توسط جاوا اسکریپت در Document Object Map دستکاری شود.
برای مثال زمانی می‌تواند رخ دهد که مقداری از یک form خوانده شود و دوباره از جاوا اسکریپت استفاده شود تا مقدار در DOM
تغییر یابد.

برای ارائه‌ی یک حمله Dom based XSS شما باید داده را در یک منبع ذخیره کنید تا در sink پخش و باعث اجرای کد دلخواه شود.
رایج‌ترین منبع برای اجرای حمله‌ی Dom based XSS، یک URL می‌باشد که معمولا به شی window.location دسترسی دارد. نفوذگر
می‌تواند پیوندی را برای قربانی ارسال نماید و قربانی را به یک صفحه آسیب پذیر همراه یک پیلود در query string هدایت کند.

منابع DOM-based XSS معمولاً شامل تابع eval() و ویژگی innerHTML می‌باشند و حمله‌ها به واسطه‌ی یک URL انجام می‌شود.

<div dir="ltr">

  ```js
const username = document.getElementById('username_input');
const username_box = document.getElementById('username_box');
user_name_box.innerHTML = username;
  ```

</div>

برای اجرای این حمله، می‌توانید به input اجرا شده، یک کد مخرب اضافه کنید:

<div dir="ltr">

  ```js
<script>
    window.alert("Cross site scripting has occurred!");
</script>
  ```

</div>

## Reflected XSS

این نوع از حملات رایج ترین شکل از حملات XSS هستند. در این حملات یک کد قابل اجرا درون مرورگر به عنوان یک پارامتر درون یک
HTTP request قرار می‌گیرد. کد تزریق شده درون برنامه ذخیره نمی‌شود و تنها کاربرانی را آلوده می‌کند که بر روی URL
آلوده‌شده کلیک کرده‌اند. برای درک بهتر به مثال زیر دقت کنید.

فرض کنید یک وب اپلیکشین ساده طراحی کرده‌ایم که در آن یک پیام خوش‌آمد گویی و سپس یک لینک برای دریافت و یا دانلود یک
برنامه‌ است.

<p align=center><img  width=344 src="./assets/expBase.png"  alt="DOMPurify"/></p>

همانطور که مشاهده می‌کند درون درخواست یک پارامتر به نام user استفاده شده است. بیایید سعی کنیم بجای نام کاربر یک اسکریپت
ساده را ارسال کنیم.

[//]: # (make code block ltr)
<div dir="ltr">

```html
<!-- Polluted request:-->
https://example.com/index.php?user=
<script> alert(123)</script>
```

</div>

اگر برنامه در برابر این حمله مقاوم نباشند، اطلاعات مشاهده شده در مرورگر به این صورت خواهد بود:

<img  width=586 src="./assets/expURLparam.png"  alt="DOMPurify"/>

این حملات ممکن است باعث اجرای فایل‌های آلوده‌ای در دستگاه کاربر می‌شود.
فرض کنید یک درخواست آلوده به این صورت پیاده کنیم:

<div dir="ltr">

```html
  https://example.com/index.php?user=
<script>window.onload = function () {
    const AllLinks = document.getElementsByTagName("a");
    AllLinks[0].href = "https://badexample.com/malicious.exe";
}</script>
```

</div>

همانطور که مشاهده می‌کنید در صورتی که برنامه در برابر این حمله مقاوم نباشد، بجای لینک اصلی، یک لینک آلوده به یک فایل
اجرایی مخرب جایگزین می‌شود.

حال که چند نمونه از این نوع حملات را دیدیم سوال این هست که چگونه می‌توان جلوی این حملات را گرفت.

#### Preventing reflected XSS

یکی از راه‌های جلوگیری از این حملات استفاده از یک کتابخانه مثل
DOMPurify می‌باشد. این کتابخانه به ما این امکان را می‌دهد که از اسکریپت‌های خطرناک درون متن‌هایی که در
DOM ایجاد می‌شوند جلوگیری کنیم. برای استفاده از این کتابخانه کافیست که کد زیر را در برنامه‌ی خود قرار دهید.

<div dir="ltr">

  ```javascript
  var clean = DOMPurify.sanitize(dirty);
   ```

</div>

به طور مثال در تکه کد زیر URL
آلوده مرحله قبل را به کتابخانه DOMPurify می‌دهیم تا اسکریپت‌های آن را پاک کند و متن نهایی را به ما برگرداند.
تکه کد زیر مقایسه URL وارد شده و خروجی DOMPurify
پس از پاکسازی را نشان می‌دهد.

<div dir="ltr">

```js
const dirty = window.location.href;
console.log(dirty);
// first example: https://example.com/index.php?user=
// <script> alert(123)</script>
// second example: https://example.com/index.php?user=
// <script>window.onload = function () {
//     var AllLinks = document.getElementsByTagName("a");
//     AllLinks[0].href = "https://badexample.com/malicious.exe";
// }</script>
const clean = DOMPurify.sanitize(dirty);
console.log(clean);
//first example (clean): https://example.com/index.php?user=
//second example (clean): https://example.com/index.php?user=
```

</div>

## منابع

- [GitHub - cure53/H5SC](https://github.com/cure53/H5SC)
- [GitHub - cure53/XSSChallengeWiki](https://github.com/cure53/XSSChallengeWiki/wiki)
- [XSS: What it is, how it works, and how to prevent it](https://medium.com/codelighthouse/xss-what-it-is-how-it-works-and-how-to-prevent-it-454629e3a0da)
