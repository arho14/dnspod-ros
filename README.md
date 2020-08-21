## 使用方法

### 1.打开winbox 在system→scripts 点击”+“

**name**:dnspod_updater

**source**:填入脚本内容

### 2.ppp→profiles 点击”+“

**name**:pppoe-clien-profile

**Scripts**:
```
delay 5s
:execute "dnspod_updater"
```
### 3.Interface List→Interface 编辑 pppoe-out1(此处根据实际情况选择)→Dial Out
**Profile**:pppoe-clien-profile

