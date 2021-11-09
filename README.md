# nvjdc

Net core5  vue3 puppeteer sharp的一次尝试

## 提示

由于我自己的环境是centos x86，arm并未测试

更新自动五次滑块

就是个文档，请不要Fork

## 支持的架构

![image](https://user-images.githubusercontent.com/87279659/137679751-7c2e901f-0429-4c5c-a6d2-120b8848048f.png)
查看地址:https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md

## 安装教程

1 执行命令

```
yum install wget unzip -y
```

2 创建一个目录放配置以及chromium

```
mkdir nvjdc && cd nvjdc
```

3 下载config.json 配置文件 并且修改自己的配置 不能缺少

```
#国外机
wget -O Config.json  https://raw.githubusercontent.com/King-stark/NvJDCloud/main/Config.json
#国内机
wget -O Config.json   https://ghproxy.com/https://raw.githubusercontent.com/King-stark/NvJDCloud/main/Config.json
```
配置文件大家根据自己的更改。

4 创建子文件夹.local-chromium，再新建子文件夹Linux-884014 （注意都是文件夹下层）

```
mkdir -p  .local-chromium/Linux-884014 && cd .local-chromium/Linux-884014
```

5 下载 chromium 并解压

```
wget https://mirrors.huaweicloud.com/chromium-browser-snapshots/Linux_x64/884014/chrome-linux.zip && unzip chrome-linux.zip
```

6 删除刚刚下载的压缩包

```
rm  -f chrome-linux.zip
```

7 回到最初创建的目录

```
cd .. && cd .. && cd ..
```

8 拉镜像

 持续更新

```
docker pull nolanhzy/nvjdc:latest
```
or 备份版

```
docker pull aaronyyds/nvjdc:(0.8+)
```

9 启动镜像

```
docker run -dit \
  -p 5701:80 \
  --name nvjdc \
  --privileged=true \
  -v $PWD/nvjdc/Config.json:/app/Config/Config.json:ro \
  -v $PWD/nvjdc/.local-chromium:/app/.local-chromium \
  --hostname nvjdc \
  nolanhzy/nvjdc:latest
```

10 查看 日志

```
docker logs -f nolanjdc 

```

出现 NETJDC  started 即可

## 更新

删除容器

```
docker rm -f nolanjdc 
```

删除镜像

```
docker rmi -f nolanhzy/nvjdc:latest
```

进入你以前下载过 Config.json 配置的文件夹中
如原来在 root 下 nvjdc 文件夹中

```
cd /root/nvjdc 
```

然后重复后续步骤即可

## 注意事项

容器启动后第一次获取验证码的时候可能卡住刷新一下即可

Config.json 是配置文件 可以热更新 修改后不用重启容器

## 最后

鸣谢：
原作 Nolanhzy
https://hub.docker.com/r/nolanhzy/nvjdc

备份 aaronyyds (0.8+)
https://hub.docker.com/r/aaronyyds/nvjdc



## 特别声明:

* 本仓库涉仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断.
* 本项目内所有资源文件，禁止任何公众号、自媒体进行任何形式的转载、发布。
* Nolan对任何代码问题概不负责，包括但不限于由任何脚本错误导致的任何损失或损害.
* 间接使用本仓库搭建的任何用户，包括但不限于建立VPS或在某些行为违反国家/地区法律或相关法规的情况下进行传播, Nolan对于由此引起的任何隐私泄漏或其他后果概不负责.
* 请勿将本项目的任何内容用于商业或非法目的，否则后果自负.
* 如果任何单位或个人认为该项目的脚本可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关代码.
* 任何以任何方式查看此项目的人或直接或间接使用本仓库项目的任何脚本的使用者都应仔细阅读此声明。Nolan 保留随时更改或补充此免责声明的权利。一旦使用并复制了任何本仓库项目的规则，则视为您已接受此免责声明.

**您必须在下载后的24小时内从计算机或手机中完全删除以上内容.**  </br>

> ***您使用或者复制了本仓库且本人制作的任何脚本，则视为`已接受`此声明，请仔细阅读***

## 多谢
