# 宝塔面板-v7.7.0
宝塔官方原版v7.7.0版本备份

**Centos/Ubuntu/Debian安装命令**

```
curl -sSO https://raw.githubusercontent.com/jzqxx/bt-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
```

# 手动破解：

**1：取消强制账号登陆**
```
sed -i "s|if (bind_user == 'True') {|if (bind_user == 'REMOVED') {|g" /www/server/panel/BTPanel/static/js/index.js
```

**2：删除强制账号登陆js文件**
```
rm -f /www/server/panel/data/bind.pl
```

**3：手动解锁宝塔所有付费插件**

文件路径：`/www/server/panel/data/plugin.json`

搜索字符串：`"endtime": -1` 全部替换为：`"endtime": 999999999999`

**4：plugin.json文件上锁防止自动修复为免费版**
```
chattr +i /www/server/panel/data/plugin.json
```
