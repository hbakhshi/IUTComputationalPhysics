# نکات مهم<p dir="rtl">
در این بخش، ما برخی از ابزارهای ضروری را بررسی خواهیم کرد که به طور گسترده در توسعه نرم‌افزار و علوم داده مورد استفاده قرار می‌گیرند. این ابزارها شامل موارد زیر هستند:
<p dir="rtl">
  <ul dir="rtl">
  <li> Bash: 
یک  (Shell) یونیکس و زبان دستوری که قابلیت‌های قدرتمند پردازش متن و اسکریپت‌نویسی را ارائه می‌دهد Bash برای خودکارسازی وظایف تکراری، مدیریت عملیات سیستم و پردازش کارآمد متن ضروری است.
    </li>
<li>
    Git: یک سیستم کنترل نسخه توزیع‌شده که به شما کمک می‌کند تغییرات کد خود را پیگیری کرده و با دیگران همکاری کنید. Git برای حفظ تاریخچه پروژه، همکاری بین اعضای تیم و مدیریت نسخه‌های مختلف کد بسیار حیاتی است.
</li>
<li>
    Python: یک زبان برنامه‌نویسی همه‌منظوره که به دلیل سادگی و خوانایی بالا محبوب است و به طور گسترده در تحلیل داده، یادگیری ماشین و توسعه وب استفاده می‌شود. کتابخانه‌ها و فریمورک‌های گسترده‌ی Python آن را به گزینه‌ای ایده‌آل برای کاربردهای مختلف، از اسکریپت‌نویسی تا ساخت برنامه‌های پیچیده، تبدیل کرده‌اند.
    </li>

با تسلط بر این ابزارها، شما قادر خواهید بود جریان کاری خود را بهینه کنید، پروژه‌های خود را به طور مؤثرتری مدیریت کرده و بهره‌وری خود را افزایش دهید. این بخش فرض می‌کند که شما درک اولیه‌ای از مفاهیم برنامه‌نویسی داشته و با استفاده از خط فرمان آشنا هستید.

</ul>

# Bash
دستورات پایه
<p dir="rtl">
  <code>ls</code> : محتوای پوشه را فهرست می‌کند. 
  

 -  مثال: <code>ls -l</code> فایل‌ها را در قالب طولانی نمایش می‌دهد.
 - مثال:   <code>ls -a</code> تمام فایل‌ها، از جمله فایل‌های مخفی را نمایش می‌دهد.

  ```{code-cell}
ls -l
ls -a
```
<p dir="rtl">
<code>cd</code>: تغییر پوشه جاری.  
  مثال: <code>cd /path/to/directory</code> به پوشه مشخص‌شده تغییر می‌کند.

```{code-cell}
cd /path/to/directory
```
<p dir="rtl">
<code>pw</code>: آدرس پوشه جاری را نمایش می‌دهد
</p>

```{code-cell}
pw
```
<p dir="rtl">
  <code>cp</code>: کپی کردن فایل‌ها و پوشه‌ها.  
 
  مثال: <code>cp source.txt destination.txt</code> فایل مبدا را به فایل مقصد کپی می‌کند.
</p>

```{code-cell}
cp source.txt destination.txt
```

<p dir="rtl">
  <code>mv</code>: جابجا کردن یا تغییر نام فایل‌ها و دایرکتوری‌ها.  
 
  مثال: <code>mv oldname.txt newname.txt</code> فایل را تغییر نام می‌دهد.
</p>

```{code-cell}
mv oldname.txt newname.txt
```
<p dir="rtl">
  <code>rm</code>: پاک کردن فایل یا پوشه مشخص شده

مثال: <code>rm file.txt</code> فایل مشخص شده را پاک می‌کند.

مثال: <code>rm -r directory</code> پوشه مشخص شده را پاک می‌کند.


   ```{code-cell}
  rm file.txt
  rm -r direcrory
   ```
<p dir="rtl">
  <code>echo</code>: نمایش یک خط متن.  
 
  مثال: <code>echo "Hello, World!"</code> متن را در ترمینال چاپ می‌کند.
</p>

```{code-cell}
echo "Hello, World!"
```

<p dir="rtl">
<code>cat</code>: برای ترکیب و نمایش محتوای فایل.  
 
  مثال: `<code>cat file.txt</code> محتوای فایل را نمایش می‌دهد.  
  ```{code-cell}
  cat file.txt
```

<p dir="rtl">
<code>mkdir new_directory</code>: برای ترکیب و نمایش محتوای فایل.  
 
  مثال: <code>mkdir mydir</code> پوشه‌ای جدید با نام mydir ایجاد می‌کند.  
  ```{code-cell}
  mkdir mydir
```

<p dir="rtl">
<code>mkdir -p /path/to/new_directory</code>: برای ایجاد یک پوشه جدید و هر پوشه والد مورد نیاز.  
 
  مثال: <code>mkdir -p /path/to/new_directory</code>` پوشه مشخص‌شده را به همراه هر پوشه والد گم‌شده ایجاد می‌کند.  
 
  ```{code-cell}
  mkdir -p /path/to/new_directory
```

<p dir="rtl">
<code>touch newfile.txt</code>: برای ایجاد یک فایل خالی جدید یا به‌روزرسانی زمان‌نگاری یک فایل موجود.  
  
  مثال: <code>touch newfile.txt </code>یک فایل خالی با نام مشخص شده ایجاد می‌کند.  
 
  ```{code-cell}
  touch newfile.txt
  ```

<p dir="rtl">
<code>touch file1.txt file2.txt file3.txt</code>: شما می‌توانید از دستور <code>touch</code> همراه با سایر دستورات برای ایجاد چندین فایل به‌طور هم‌زمان یا ایجاد فایل‌ها در دایرکتوری‌های خاص استفاده کنید.  
 
  مثال: <code>touch file1.txt file2.txt file3.txt</code> چندین فایل جدید ایجاد می‌کند.  
  ```{code-cell}
  touch file1.txt file2.txt file3.txt
```

<p dir="rtl">

مثال: <code>touch /path/to/directory/newfile.txt</code>: ایجاد یک فایل در یک دایرکتوری خاص.

```{code-cell}
touch /path/to/directory/newfile.txt
```
# Scripting

<p dir="rtl"> 
   یک اسکریپت Bash فقط یک فایل متنی است که شامل مجموعه‌ای از دستورات است و به شما این امکان را می‌دهد که کارهای تکراری را با نوشتن اسکریپت‌ها خودکار کنید.
 
  مثال:   
  ```{code-cell}
  #!/bin/bash
  echo "Hello, World!
```
<p dir="rtl">
  برای اجرای اسکریپت، آن را در یک فایل ذخیره کنید (مثلاً <code>hello.sh</code>)، آن را اجرایی کنید (<code>chmod +x hello.sh</code>) و سپس آن را اجرا کنید (<code>./hello.sh</code>).  
 
  مثال:  
  ```{code-cell}
  chmod +x hello.sh
  ./hello.sh
```

<p dir="rtl">

  # پردازش متن  
  بش از دستورات قدرتمندی برای پردازش متن مانند <code>grep</code>، <code>awk</code> و <code>sed</code> برخوردار است. این ابزارها به شما این امکان را می‌دهند که داده‌های متنی را به‌طور کارآمد جستجو، فیلتر و تغییر دهید. در اینجا چند مثال آورده شده است:
 
<p dir="rtl">
<code>grep</code>: جستجو برای الگوها در فایل‌ها.  
 
  مثال: <code>grep 'pattern' file.txt</code> برای جستجوی واژه ‘pattern’ در فایل استفاده می‌شود.  
  ```{code-cell}
  grep 'pattern' file.txt
```

<p dir="rtl">
  <code>awk</code>: یک زبان برنامه‌نویسی برای پردازش متن.  
 
  مثال: <code>awk '{print $1}' file.txt</code> ستون اول هر خط را از فایل چاپ می‌کند.  
  ```{code-cell}
  awk '{print $1}' file.tx
```

<p dir="rtl">
  <code>sed</code>: ویرایشگر جریانی برای فیلتر کردن و تبدیل متن.  
  
  مثال: <code>sed 's/old/new/g' file.txt</code> کلمه "old" را با "new" در فایل جایگزین می‌کند.  
  ```{code-cell}
  sed 's/old/new/g' file.txt
```

# Using Wildcards
<p dir="rtl">
  <code>*</code>: برای تطبیق با هر تعداد کاراکتر (شامل هیچ کاراکتری).  
 
  مثال: <code>*.txt</code> تمامی فایل‌های با پسوند ".txt" را پیدا می‌کند.  
  ```{code-cell}
  ls *.txt
```


<p dir="rtl">
  <code>?</code>: برای تطبیق با یک کاراکتر تنها.  
 
  مثال: <code>ls file?.txt</code> فایل‌هایی مانند file1.txt، file2.txt و غیره را پیدا می‌کند.  
  ```{code-cell}
  ls file?.txt
```

<p dir="rtl">
  <code>[]</code>: برای تطبیق با هر یک از کاراکترهای داخل براکت‌ها.  
  
  مثال: <code>ls file[12].txt</code> فایل‌هایی مانند file1.txt و file2.txt را پیدا می‌کند.  
  ```{code-cell}
  ls file[12].txt
```

<p dir="rtl">
  <strong>نکات و ترفندها برای استفاده پایه از ترمینال</strong>
  <br>
  در اینجا چند نکته و ترفند برای بهبود استفاده شما از ترمینال آورده شده است:
  <ul>
    <li><strong>استفاده از Tab</strong> برای تکمیل خودکار دستورات و نام فایل‌ها.</li>
    <li><strong>استفاده از Ctrl + R</strong> برای جستجو در تاریخچه دستورات.</li>
    <li><strong>استفاده از Ctrl + C</strong> برای لغو دستور جاری.</li>
    <li><strong>استفاده از Ctrl + L</strong> برای پاک کردن صفحه ترمینال.</li>
    <li><strong>استفاده از !!</strong> برای تکرار دستور آخر.</li>
    <li><strong>استفاده از !&lt;command&gt;</strong> برای تکرار آخرین وقوع یک دستور خاص.  
    مثال: <code>!ls</code> آخرین دستور <code>ls</code> را تکرار می‌کند.</li>
  </ul>
</p>


# File Permissions and Ownership
<p dir="rtl">
      <code>chmod</code>: تغییر مجوزهای فایل.

  مثال: <code>chmod 755 file.txt</code> مجوزهای فایل را به صورت خواندن، نوشتن و اجرا برای مالک و خواندن و اجرا برای سایرین تنظیم می‌کند.
 ```{code-cell}
chmod 755 file.txt
```

<p dir="rtl">
  <code>chown</code>: تغییر مالکیت فایل.
  <br>
  مثال: <code>chown user:group file.txt</code> مالک و گروه فایل را تغییر می‌دهد.
</p>

```{code-cell}
chown user:group file.txt
```

# Viewing Running Processes

<p dir="rtl">
  <code>ps</code>: نمایش اطلاعات مربوط به فرآیندهای در حال اجرا.
  <br>
 
  مثال: <code>ps aux</code> اطلاعات دقیق در مورد تمامی فرآیندهای در حال اجرا را نمایش می‌دهد.
</p>

```{code-cell}
ps aux
```
<p dir="rtl">
  <code>top</code>: نمایش اطلاعات بلادرنگ درباره فرآیندهای در حال اجرا.
  <br>
 
  مثال: <code>top</code> و <code>htop</code> یک نمای دینامیک از فرآیندهای سیستم را نمایش می‌دهند.
</p>

```{code-cell}
top
```
یا

```{code-cell}
htop
```

# Creating Aliases

<p dir="rtl">
  <code>alias</code>: به شما این امکان را می‌دهد که برای دستورات پرکاربرد خود میانبر ایجاد کنید.  
  <br>
  
  مثال: ایجاد یک میانبر برای دستور <code>ls -la</code>:  
  ```{code-cell}
  alias ll='ls -la'
```
  این دستور میانبری به نام <code>ll</code> برای نمایش محتوای دایرکتوری به‌صورت جزئی ایجاد می‌کند
</p>


<p dir="rtl">
  <code>alias</code>: برای دائمی کردن میانبر، باید آن را به فایل <code>.bashrc</code> یا <code>.bash_profile</code> خود اضافه کنید:
  <br>
  مثال:
 
  ```{code-cell}
  echo "alias ll='ls -la'" >> ~/.bashrc
```
<p dir="rtl">
  <code>echo "alias ll='ls -la'" >> ~/.bashrc</code>  
  این دستور میانبر را به فایل <code>.bashrc</code> اضافه می‌کند.
  <br>
 
  سپس برای بارگذاری فایل جدید:
 
  ```{code-cell}
source ~/.bashrc
```
  این دستور فایل <code>.bashrc</code> را دوباره بارگذاری می‌کند تا تغییرات اعمال شوند.
</p>

<p dir="rtl">
  <strong>مستندات بیشتر</strong>
  <br>
  برای اطلاعات بیشتر و استفاده پیشرفته، می‌توانید به منابع و مستندات رسمی Bash مراجعه کنید:
  <ul>
    <li><a href="https://www.gnu.org/software/bash/manual/">مستندات رسمی Bash</a></li>
    <li><a href="https://github.com/bminor/bash">کد منبع Bash</a></li>
    <li><a href="https://tldp.org/LDP/abs/html/">راهنمای نوشتن اسکریپت در Bash</a></li>
  </ul>
  <br>
<p dir="rtl">
  <code>man</code>:  صفحات راهنمای دستورات  را نمایش می‌دهد.
  
  
  <br>
  <p dir="rtl">
  مثال:
   
```{code-cell}
man ls
 ```
  <br>
  <p dir="rtl">
  با تسلط بر Bash، می‌توانید به‌طور قابل‌توجهی بهره‌وری خود را افزایش داده و جریان کاری خود را ساده‌سازی کنید.
</p>

# Git

<code>Git</code>: یک سیستم کنترل نسخه توزیع‌شده است که به شما کمک می‌کند تغییرات کد خود را پیگیری کرده و با دیگران همکاری کنید.  
این ابزار برای حفظ تاریخچه پروژه، امکان همکاری بین اعضای تیم و مدیریت نسخه‌های مختلف کد بسیار مهم است

