## 青龙2.8面板 & Ninja面板 搭建教程

**看教程之前 你必须拥有一台具备Docker功能的服务器**

**怎么搭建Docker? 参见 [Docker教程](https://www.runoob.com/docker/docker-tutorial.html)**

-------

#### 连接服务器 执行命令

```shell
docker run -dit \
  -v $PWD/ql/config:/ql/config \
  -v $PWD/ql/log:/ql/log \
  -v $PWD/ql/db:/ql/db \
  -v $PWD/ql/repo:/ql/repo \
  -v $PWD/ql/raw:/ql/raw \
  -v $PWD/ql/scripts:/ql/scripts \
  -v $PWD/ql/jbot:/ql/jbot \
  -v $PWD/ql/ninja:/ql/ninja \
  -p 5700:5700 \
  -p 5701:5701 \
  --name qinglong \
  --hostname qinglong \
  --restart unless-stopped \
  whyour/qinglong:latest
```

![image-20210731143900553](http://i0.hdslb.com/bfs/album/c9717b0d556ba2dba4ab30573a40735c1238e40a.png)

***

**这是搭建完成的样子**

输入命令`docker logs -f qinglong`可以查看实时日志

![image-20210731144043403](http://i0.hdslb.com/bfs/album/6e0dd522ac10acacd55f19d379b9c1f9bb877ba0.png)

**当出现容器启动成功的字样再去浏览器访问面板**

![image-20210731144223081](http://i0.hdslb.com/bfs/album/96d10bdaa3fe5ed2e69404020d2621dd26a84f37.png)

进入浏览器输入默认用户名密码 **admin adminadmin**

![image-20210731144320831](http://i0.hdslb.com/bfs/album/bacc87a7ee3a509f4a7f4c76c943331b0a97ec58.png)

回到控制台 输入命令 `cd ~ && cat ql/config/auth.json`

![image-20210731144423574](http://i0.hdslb.com/bfs/album/087b91a91a6650281e31394f7849bcd6a696ec57.png)

查看密码并登录面板

进入之后 最好先点击一下**更新面板** 让面板代码同步最新的

![image-20210731144613514](http://i0.hdslb.com/bfs/album/c9b282d9162627eb2c2344e96c48e5ba299d8a61.png)

#### 为保证代码为最新代码 请点击<u>两次更新面板!!</u>

----

### 到这里 青龙面板搭建完成 现在开始搭建Ninja面板

回到SSH控制台

输入命令 `docker exec -it qinglong bash`

![image-20210731145133936](http://i0.hdslb.com/bfs/album/cc158cf79b037312e50a04c270f863cffe75be77.png)

执行命令

```shell
git clone https://github.com/MoonBegonia/ninja.git /ql/ninja
cd /ql/ninja/backend
pnpm install
pm2 start
cp sendNotify.js /ql/scripts/sendNotify.js
```

![image-20210731145255278](http://i0.hdslb.com/bfs/album/2606abe4c59844588bddf74c3330e3b0862d4c85.png)

**到这一步Ninja面板搭建完成 可以访问IP:5701进入Ninja面板**

![image-20210731145354641](http://i0.hdslb.com/bfs/album/364230cba18dc35328bc5f38f0ca7aa08d99d089.png)

**接着回到控制台**

输入命令

```shell
echo 'cd /ql/ninja/backend' >>/ql/config/extra.sh
echo 'git checkout .' >>/ql/config/extra.sh
echo 'git pull' >>/ql/config/extra.sh
echo 'pnpm install' >>/ql/config/extra.sh
echo 'pm2 start' >>/ql/config/extra.sh
echo 'cp sendNotify.js /ql/scripts/sendNotify.js' >>/ql/config/extra.sh
```

![image-20210731145809786](http://i0.hdslb.com/bfs/album/7fb24c576432a1c070aeefa74075d495cb889300.png)

**这一步是将Ninja面板加入青龙的自动启动项中**

----

## 到这里Ninja也搭建完成

----

### 以下是可选配置项目

* **修改Ninja面板的title**

  ` sed -i 's/Ninja/要替换的内容/' /ql/ninja/backend/static/index.html`

* **修改Ninja面板的顶栏名称**

  > 作者加了一点门槛 不让你乱改 这里只提供一个小方法

  ```shell
  mv index.1a8beb0e.js.gz index.1a8beb0e.js.gz.bak
  sed -i 's/"Ninja"/"标题"/' index.1a8beb0e.js
  ```

  ![image-20210731151531183](http://i0.hdslb.com/bfs/album/e6e31bd65022341924eae0176585e35ff583a94d.png)

* **修改顶栏卡片内容 ~~图一乐~~**

> Ninja作者说后面卡片为自定义内容 这里先给出一个临时的玩法

```html
<script type="text/javascript">
	window.onload=function (){
        var x = document.getElementsByClassName("card-title");x[0].innerHTML="卡片标题"
        var b = document.getElementsByClassName("card-body text-base leading-6");b[0].innerHTML="卡片内容"
}
</script>
```

**修改`/ql/ninja/backend/static/index.html` 引入这段代码就可以修改**

### 最后提示 如果需要修改Ninja资源 请在extra.sh中移除

>git checkout .
>
>git pull
>
>pnpm install



----
