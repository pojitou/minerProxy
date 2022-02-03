
<h1 align="center">此版本为逆向303自用版本，取消了作者开发费0.3%，不建议使用默认web端口，及常用挖矿端口（例如14444,443,5555,6688等）请自行修改</h1>


```
## Liunx
```bash
git clone https://github.com/pojitou/minerProxy.git
sudo chmod -R 777 minerProxy（获取权限）
cd minerProxy
然后运行
nohup ./minerProxy_web &（注意要后台运行&，不然会断开）
cat  config.yml（这个命令可以查看token）
打开防火墙的36678端口，在网页上输入你的IP:36678，输入token，即可配置
(注意事项，不要使用360等浏览器，使用Chrome或微软Edge浏览器。 
第一次配置后，请修改Token，再请求配置页面，防止别人知道你的IP地址，更换你的抽水钱包)

### 后台运行时关闭


killall minerProxy

### 后台运行时查看

tail -f nohup.out

### 防火墙相关命令
1.防火墙打开
sudo ufw enable
2.防火墙重启
sudo ufw reload
3.打开想要的端口（以9000为例）
ufw allow 9000
4.查看本机端口使用情况
ufw status
5.关闭防火墙
sudo ufw disable

## 提示bash: git: command not found需要先安装git
### ubuntu下

apt update
apt install git

### centos下

yum update
yum install git

## 提示bash: Permission denied是没有权限
```bash
sudo chmod -R 777 minerProxy
```bash
```
## Windows系统
```bash
运行minerProxy.exe
打开防火墙的36678端口，在网页（谷歌浏览器，edeg浏览器）上输入你的IP:36678，输入token，即可配置
```
# 参数说明
```bash
抽水比例   这里是百分比，填入数字1就是1%
抽水矿池  （抽水去的矿池，比方说可以把鱼池的抽去E池，）
自定义矿机名  （抽水工名字）
钱包地址  顾名思义，抽水的钱包地址
代理矿池  （你转发的矿池挖矿地址，官方的）
本地端口  矿工连接你服务器的端口，比方说222.222.222.222:5678，这里就写5678
```
## 如何快速配置

```bigquery
web版本快速设置，如果你下载了新版，又想使用过去的配置，不需要在web界面上一个一个添加端口。
编辑你的config文件，里面有每个端口的详细信息，并且可以修改web端口和token，编辑后保存，运行web进程/web.exe，即会加载所有配置，这时再去web界面会看到所有端口信息。

### 示例

host: 0.0.0.0
port: 36678
token: "123456"
webserver: true
server:
    - port: "8001"
      ssl: 1
      proxypool: tcp://eth.f2pool.com:6688
      devfee: 0.5
      devpool: tcp://asia2.ethermine.org:4444
      addr: 0x292c0bxxxxxxxxxxxxxxxxx
      worker: F2
      reconnect: 20
      clientnum: 0
    - port: "8002"
      ssl: 1
      proxypool: ssl://asia2.ethermine.org:5555
      devfee: 0.5
      devpool: ssl://asia2.ethermine.org:5555
      addr: 0x292c0bxxxxxxxxxxxxxxxxxxx
      worker: Etcp
      reconnect: 20
      clientnum: 0
      
上面的例子，可以看到每个 “- prot  ”下面有它相应的配置，这样可以复制多个- port，修改相应的内容，快速修改，保存后，即可统一加载，无需在web依次添加。 

