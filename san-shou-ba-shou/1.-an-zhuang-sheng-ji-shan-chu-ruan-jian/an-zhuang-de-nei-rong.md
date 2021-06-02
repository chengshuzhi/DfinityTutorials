# 安装的内容

DFINITY Canister SDK安装脚本会在本地计算机上的默认位置安装多个组件。 下表描述了安装脚本将安装的开发环境组件：

| 组件 | 描述 | 默认位置 |
| :--- | :--- | :--- |
| dfx | DFINITY 可执行命令行接口 \(CLI\) | /usr/local/bin/dfx |
| moc | Motoko运行时编译器 | ~/.cache/dfinity/versions/&lt;VERSION&gt;/moc |
| replica | Internet Computer 本地网络二进制文件 | ~/.cache/dfinity/versions/&lt;VERSION&gt;/replica |
| uninstall.sh | 删除 DFINITY Canister SDK 及其所有组件的脚本 | ~/.cache/dfinity |
| versions | 包含安装的每个DFINITY Canister SDK版本的缓存子目录 | ~/.cache/dfinity/versions |

## 版本目录中的核心组件

~/.cache/dfinity/versions目录存储DFINITY Canister SDK的一个或多个版本子目录。 每个版本的子目录包含特定版本的DFINITY Canister SDK所需的所有目录和文件。

 例如，如果列出~/.cache/dfinity/versions/0.6.26目录的内容，则会看到以下核心组件。

```text
total 349192
drwxr-xr-x  17 pubs  staff       544 Mar 15 11:55 .
drwxr-xr-x   4 pubs  staff       128 Mar 25 14:36 ..
drwxr-xr-x  49 pubs  staff      1568 Mar 15 11:55 base
drwxr-xr-x  20 pubs  staff       640 Mar 15 11:55 bootstrap
-r-x------   1 pubs  staff  66253292 Mar 15 11:55 dfx
-r-x------   1 pubs  staff  10496256 Dec 31  1969 ic-ref
-r-x------   1 pubs  staff   5663644 Dec 31  1969 ic-starter
-r-x------   1 pubs  staff      9604 Dec 31  1969 libcharset.1.0.0.dylib
-r-x------   1 pubs  staff     38220 Dec 31  1969 libffi.7.dylib
-r-x------   1 pubs  staff    668300 Dec 31  1969 libgmp.10.dylib
-r-x------   1 pubs  staff    958248 Dec 31  1969 libiconv.2.4.0.dylib
-r-x------   1 pubs  staff      4200 Dec 31  1969 libiconv.dylib
-r-x------   1 pubs  staff     96900 Dec 31  1969 libz.1.2.11.dylib
-r-x------   1 pubs  staff  15417684 Dec 31  1969 mo-doc
-r-x------   1 pubs  staff  14634020 Dec 31  1969 mo-ide
-r-x------   1 pubs  staff  15111508 Dec 31  1969 moc
-r-x------   1 pubs  staff  49404128 Dec 31  1969 replica
```

## Motoko base 库目录

DFINITY Canister SDK的版本子目录中的主目录包含与该版本的DFINITY Canister SDK兼容的Motoko基础库模块。 由于Motoko基础库的发展迅速，因此，您应仅使用与已安装的DFINITY Canister SDK版本打包在一起的基础模块。

## Bootstrap 目录

Bootstrap目录包含已弃用的Web服务器代码。 从版本0.7.0开始，代理可以调用HTTP中间件服务器代替引导程序代码。 这个更改可使Canister可以直接响应HTTP请求，并且可以像传统基于Web的应用程序一样操作。

