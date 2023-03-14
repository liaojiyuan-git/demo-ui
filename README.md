## 环境准备
安装node版本为14.19.0 

下载地址：https://nodejs.org/download/release/v14.19.0/node-v14.19.0-x64.msi

安装时注意勾选“Automatically install the necessary tools.Note that this will also install Chocolatey. The script will pop-up in a new windows after the installation completes.”选项
## 开发

```
# 设置sass_binary_site从国内镜像下载（包较大，从外网下载速度很慢）
npm config set sass_binary_site=https://npm.taobao.org/mirrors/node-sass

# 安装依赖
npm install --registry=http://110.83.51.241:62189/repository/npm-group/

# 启动服务
npm run serve

```
