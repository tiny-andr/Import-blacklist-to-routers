# Import-blacklist-to-routers
Chinese

linux环境下，从blacklist.3coresec.net下载恶意ip列表并导入到RouterOS。

请将你的linux服务器的ssh公钥添加到routeros，确保linux能够ssh到routeros。

使用方法：
```git clone https://github.com/tiny-andr/Import-blacklist-to-routers.git
chmod +x ./Import-blacklist-to-routers/get_blockedlist_sendto_routeros
```
修改脚本中的yourlinuxserver_ip和yourrouterosip为你的服务器ip和routerosip,以及用于执行导入脚本的账户名称，此处假设是routeros的admin账户

编辑crontab,每晚22点传输地址表

```cronteb -e```

```00 22 * * * ~/Import-blacklist-to-routers/get_blockedlist_sendto_routeros```

确保Routeros有防火墙规则调用此表：
```
/ip firewall raw
add action=drop chain=prerouting comment="block unsafe network traffic" src-address-list=blocked
add action=drop chain=prerouting comment="block unsafe network traffic" dst-address-list=blocked
```

English：

In Linux environment, download the malicious IP list from blacklist.3coresec.net and import it into RouterOS \n\n\n\n\n

Usage:

```git clone https://github.com/tiny-andr/Import-blacklist-to-routers.git
chmod +x ./Import-blacklist-to-routers/get_blockedlist_sendto_routeros
```

Modify yourlinuxserver_ip and yourrouterosip in the script get_blockedlist_sendto_routeros to your server ip and routerosip, and the account name used to execute the import script. It is assumed here that it is the admin account of routers.

Edit crontab and transfer the address table at 22:00 every night

```cronteb -e```

```00 22 * * * ~/Import-blacklist-to-routers/get_blockedlist_sendto_routeros```

Make sure Routeros has a firewall rule calling this table:
```
/ip firewall raw
add action=drop chain=prerouting comment="block unsafe network traffic" src-address-list=blocked
add action=drop chain=prerouting comment="block unsafe network traffic" dst-address-list=blocked
```
