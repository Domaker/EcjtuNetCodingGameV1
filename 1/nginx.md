## 将ecjtu.net重定向到www.ecjtu.net ##

- 1、在域名管理里定义ecjtu.net和www.ecjtu.net都指向主机的ip地址（202.101.208.35）
- 2、检测：用 `nslookup` 命令，输入 `nslookup ecjtu.net`和`nslookup www.ecjtu.net`检测是否指向ip的A记录
- 3、在**nginx**里面配置**rewrite规则**。打开 **nginx.conf** 文件，找到**server配置段**,设置如下：

- `server{` <br />
	 &emsp;`listen 80;`<br />
     &emsp;`server_name www.ecjtu.net ecjtu.net`<br />
     &emsp;&emsp; `if($host = ecjtu.net){`<br />
   	 &emsp;&emsp;&emsp;&emsp;  `rewriter ^/(.*)$ http://www.ecjtu.net/$1 premanent; `<br />
   &emsp;&emsp;  `}`
- `}`
