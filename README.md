# StarryOS Source Code Repo Manifest
## 环境依赖安装
```bash
sudo apt update && sudo apt install -y git repo build-essential
```

如果提示E: 无法定位软件包 repo

```bash
# 创建 bin 目录（如果不存在）
mkdir -p ~/bin

# 下载 repo 工具
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

# 赋予执行权限
chmod a+x ~/bin/repo

# 添加到 PATH（如果尚未添加）
echo 'export PATH=~/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# 验证安装
repo --version
```
## 源码拉取
```bash
# 创建工作目录
mkdir -p starryos-workspace && cd starryos-workspace

# 初始化repo清单(starry的main分支)
repo init -u https://github.com/kylin-x-kernel/starryos-manifest -b main

# 同步所有源码 
repo sync -j$(nproc) 
```

## 常用Repo命令
```bash
# 单独更新指定仓库
repo sync arm-gic
repo sync meta-starry

# 强制同步指定仓库（覆盖本地修改）
repo sync --force axcpu

# 查看所有仓库状态
repo status

# 重新初始化清单配置(修改清单文件后/切换清单文件时执行)
repo init  && repo sync -j$(nproc)

```
## 日常开发

```bash
# 日常开发正常进入文件夹，git checkout 、git commit、push等
# repo推荐用来一键从远端同步，源地址等在xml文件里
repo sync
```
