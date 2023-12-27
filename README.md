# Import-blacklist-to-routers
In Linux environment, download the malicious IP list from blacklist.3coresec.net and import it into RouterOS

linux环境下，从blacklist.3coresec.net下载恶意ip列表并导入到RouterOS。

请将你的linux服务器的ssh公钥添加到routeros，确保linux能够ssh到routeros。

使用方法：
git clone https://github.com/tiny-andr/Import-blacklist-to-routers.git

chmod +x ./Import-blacklist-to-routers/get_blockedlist_sendto_routeros

修改脚本中的yourlinuxserver_ip和yourrouterosip为你的服务器ip和routerosip

编辑crontab,每晚22点传输地址表

cronteb -e

00 22 * * * ~/Import-blacklist-to-routers/get_blockedlist_sendto_routeros
