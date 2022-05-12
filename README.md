# btpanel-v7.7.0
btpanel-v7.7.0-backup  官方原版v7.7.0版本面板备份
---

！官方脚本脚本存在后门，请手动注释相关代码

！官方脚本脚本存在后门，请手动注释相关代码

！官方脚本脚本存在后门，请手动注释相关代码

消息来源：https://hostloc.com/thread-1015644-1-1.html
---


**Centos/Ubuntu/Debian安装命令 独立运行环境（py3.7）**
### 全新安装
```Bash
curl -sSO https://raw.githubusercontent.com/zhucaidan/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
```
### 从宝塔6.x升级
```bash
curl -sSO https://raw.githubusercontent.com/zhucaidan/btpanel-v7.7.0/main/install/update.sh && bash update.sh
```
### 从宝塔5.x升级
```bash
curl -sSO https://raw.githubusercontent.com/zhucaidan/btpanel-v7.7.0/main/install/update_to_6.sh && bash update_to_6.sh
```

# 脚本

### 去除强制绑定手机号

```shell
// 去除授权验证
sed -i "s|if (bind_user == 'True') {|if (bind_user == 'REMOVED') {|g" /www/server/panel/BTPanel/static/js/index.js
rm -rf /www/server/panel/data/bind.pl


// 去除文件检测、去除后门
sed -i "/p = threading.Thread(target=check_files_panel)/, /p.start()/d" /www/server/panel/task.py
sed -i "/p = threading.Thread(target=check_panel_msg)/, /p.start()/d" /www/server/panel/task.py
```

### 插件同步
```shell
vim /www/server/panel/class/panelPlugin.py
```

```python
# 编辑334行
                softList['list'] = tmpList
                softList['pro'] = 1
        for soft in softList['list']:
            soft['endtime'] = 0
```
![image](https://user-images.githubusercontent.com/24518597/156919454-a7b61b77-6f86-418b-a26f-a7514d4e71bc.png)
