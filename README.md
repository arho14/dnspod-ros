## DNSPOD Updater

通过 PPPoE 拨号配置文件激发 DNSPOD API 查询域名解析来变更A记录。

正常 PPPoE 拨号会改变 IP ，感觉作者很棒，比利用 System/Scheduler 定时轮询好的多。



## Winbox 操作

1，在左侧 `System` 选单中寻找 `Scripts` 打开选卡后 点击 ”+“

**Name 栏填入**: `dnspod_updater`

**Source 栏填入**: <u>dnspod_updater 脚本内容并且按脚本提示更改</u>

然后 Apply 后 OK 。



2，打开左侧 `PPP` 选单，打开 `Profiles` 选卡后 点击 ”+“

**选卡 General/Name 填入**: `pppoe-clien-profile`

**选卡 Scripts/On UP 填入**: 

```
delay 5s
:execute "dnspod_updater"
```

该选卡的其他选项可以参考 `Profiles` 选卡下默认的 `default` 条目。  

然后 Apply 后 OK 。



3，打开左侧 `Interface`  选单，在 `Interface` 选卡中寻找 PPPoE 拨号项目 ( Type为PPPoE Client 那项 ) 双击打开，在选卡 Dial Out 中

**Profile 栏选择**: `pppoe-clien-profile`

然后 Apply 后 OK 。注意：此操作会导致重新拨号。



4，打开左侧 Log 查看，看到类似记录

`PPPoE: authenticated
PPPoE: connected
[www.abc.com]成功更新IP为:1.1.1.1
... ... ... `

表示操作成功。
