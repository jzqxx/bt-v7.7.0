# 宝塔面板-v7.7.0
宝塔官方原版v7.7.0版本备份

**Centos/Ubuntu/Debian安装命令**

```
curl -sSO https://raw.githubusercontent.com/sunpma/bt-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
```

# 手动破解：

1：屏蔽手机号
```
sed -i "s|bind_user == 'True'|bind_user == 'XXXX'|" /www/server/panel/BTPanel/static/js/index.js
```

2：取消屏蔽手机号
```
sed -i "s|if (bind_user == 'REMOVED') {|if (bind_user == 'True') {|g" /www/server/panel/BTPanel/static/js/index.js
```

3：删除强制绑定手机js文件
```
rm -f /www/server/panel/data/bind.pl
```

4：手动解锁宝塔所有付费插件
文件路径 `/www/server/panel/data/plugin.json`
搜索字符串 `"endtime": -1`
全部替换为 `"endtime": 999999999999`

5：给plugin.json文件上锁防止自动修复为免费版
```
chattr +i /www/server/panel/data/plugin.json
```
