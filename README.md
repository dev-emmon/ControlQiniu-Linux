# 七牛云监控

## 一、环境搭建
1. 安装 Nodejs
```bash
# 下 nodejs 二进制包
wget https://nodejs.org/dist/latest-v4.x/node-v4.8.4-linux-armv7l.tar.gz

# 解压
tar zxvf node-v4.8.4-linux-armv7l.tar.gz

# 移动到 /usr/local 目录
sudo mv node-v4.8.4-linux-armv7l /usr/local
sudo mv node-v4.8.4-linux-armv7l node

# 加入到环境
vi ~/.bash_profile

export NODE_HOME=/usr/local/node/ 
export PATH=$NODE_HOME/bin:$PATH

# 安装 插件
cd ~
npm install request --registry https://registry.npm.taobao.org install express
npm install glob --registry https://registry.npm.taobao.org install express
npm install fluent-ffmpeg --registry https://registry.npm.taobao.org install express
```

2. 安装 ffmpeg
```bash
# 下载 ffmpeg 包
wget http://demo.xinqigu.com/ffmpeg-3.2.2.tar.bz2

# 解压
tar jxvf ffmpeg-3.2.2.tar.bz2

# 移动
sudo mv ffmpeg-3.2.2 /usr/local/
sudo mv ffmpeg-3.2.2 ffmpeg
# 加入到环境
vi ~/.bash_profile

export NODE_HOME=/usr/local/node/ 
export PATH=$NODE_HOME/bin:$PATH


## libx264 support
git clone git://git.videolan.org/x264
cd x264
./configure --prefix=/usr/local/x264 --enable-static --disable-opencl
./configure --host=arm-unknown-linux-gnueabi --enable-static --disable-opencl
make
sudo make install

## ffmpeg
git clone git://git.ffmpeg.org/ffmpeg
cd ffmpeg
./configure --prefix=/usr/local/ffmpeg --enable-libx264
sudo ./configure --arch=armel --target-os=linux --enable-gpl --enable-libx264 --enable-nonfree
make # 这一步可能相当相当漫长，在我这里跑了有一个多小时
sudo make install
```