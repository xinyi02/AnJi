## 特别声明: 

* 本仓库仅仅为自用备份仓库，不是什么魔改版什么升级版，后续也不会维护更不会升级.

* 本仓库菜单默认包含敏感内容，如不需要，请修改conf/reply.php内删除 `姐姐` => ``该行，然后重启机器人.

* 本仓库发布的项目中涉及的任何解锁和解密分析脚本，仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断.

* 本项目内所有资源文件，禁止任何公众号、自媒体进行任何形式的转载、发布。

* 本仓库拥有者对任何脚本问题概不负责，包括但不限于由任何脚本错误导致的任何损失或损害.

* 间接使用脚本的任何用户，包括但不限于建立VPS或在某些行为违反国家/地区法律或相关法规的情况下进行传播, 本仓库拥有者对于由此引起的任何隐私泄漏或其他后果概不负责.

* 请勿将项目的任何内容用于商业或非法目的，否则后果自负.

* 如果任何单位或个人认为该项目的脚本可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关脚本.

* 任何以任何方式查看此项目的人或直接或间接使用该MyActions项目的任何脚本的使用者都应仔细阅读此声明。本仓库拥有者保留随时更改或补充此免责声明的权利。一旦使用并复制了任何相关脚本或MyActions项目的规则，则视为您已接受此免责声明.

 **您必须在下载后的24小时内从计算机或手机中完全删除以上内容.**  </br>
 ***您使用或者复制了本仓库且本人制作的任何脚本，则视为`已接受`此声明，请仔细阅读*** 


## 即日起，本仓库仅用于个人学习使用，如若想详细了解，请往下看。

## 数据库教程[点此查看](https://docs.qq.com/doc/DREdJWHRtQUpoUlNO)

```
cd /anji/ql/  ##cd到青龙容器映射的ql目录，根据自己的路径改
git clone https://ghproxy.com/https://github.com/xinyi02/xdo.git  #此时你的ql目录下会新增文件夹xdi
cd xdo ##cd到xdo目录
go build ##开始编译，稍微等一下，让它跑一会儿
chmod 777 xdi ##给权限
./xdo ##初始化并生成配置文件
./xdo -d ##静默运行模式
ps -ajx|grep xdo ##查看原程序PID
kill -9 *** ##结束程序（***改为你的PID）,结束后无任何提示，不放心再输入一下，会提示无此进程。
 ```
## go环境安装
 ```
sudo -i ##root权限
cd /usr/local && wget https://golang.google.cn/dl/go1.16.7.linux-amd64.tar.gz -O go1.16.7.linux-amd64.tar.gz ##local目录下载⏬
tar -xvzf go1.16.7.linux-amd64.tar.gz ##解压
vi /etc/profile ##打开文件，设置环境变量，输入“i”进行编辑文件，最后一行输入下面的变量，全选复制进去。（下方左图）
export GO111MODULE=on
export GOPROXY=https://goproxy.cn
export GOROOT=/usr/local/go
export GOPATH=/usr/local/go/path
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
##输入后，按“Esc”，再输入":wq",按"Enter"，保存并退出。
source /etc/profile
go env #运行后，查看变量一样就设置对了。
 ```
