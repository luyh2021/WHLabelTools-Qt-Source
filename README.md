# WHLabelTools Windows — Qt 5.6.3 对应源码

本仓库提供下表所列 WHLabelTools Windows 版本随附的 Qt 开源组件源码和构建说明；不包含 WHLabelTools 应用程序源码。

## 适用版本

| WHLabelTools Windows 版本 | Qt 构建 | 对应源码 |
| --- | --- | --- |
| 2.0.4 | Qt 5.6.3 OpenSource，VS2017 x86，共享 DLL | [Qt 5.6.3 源码 Release](https://github.com/luyh2021/WHLabelTools-Qt-Source/releases/tag/WHLabelTools-2.0.4-Qt-5.6.3) |

后续 WHLabelTools 版本如继续使用相同的 Qt DLL 和插件，可继续引用此源码附件；每次发行前应核对随包二进制文件和对应源码，并在新版本的开源声明中指向本 Release。若 Qt 源码、补丁或构建发生变化，应另行提供与新版本实际二进制文件对应的源码及构建信息，并更新上表。仅应用程序版本号变化不要求重复上传相同的 Qt 源码包。

## 获取源码

请在 [Qt 5.6.3 源码 Release](https://github.com/luyh2021/WHLabelTools-Qt-Source/releases/tag/WHLabelTools-2.0.4-Qt-5.6.3) 下载附件 `qt-everywhere-opensource-src-5.6.3.zip`。该文件 SHA-256：`ffde2181608ab715ba62c1bbb55432c34c734b3ec1e9c71decc59092c1de7df4`，与 [Qt 官方公布的哈希](https://download.qt.io/new_archive/qt/5.6/5.6.3/single/qt-everywhere-opensource-src-5.6.3.zip.mirrorlist) 一致。请下载上述命名的附件；GitHub 自动生成的“Source code (zip)”仅包含本仓库文件。

原构建目录中的 9 个 Qt DLL 与 2.0.4 Windows 版使用的 Qt SDK 对应文件哈希一致。`qtbase`、`qtsvg`、`qtserialport` 中 11,390 个源码及项目文件与上述官方 ZIP 相同。2.0.4 安装包中的 `Qt5Core.dll` 由 Qt 部署工具将内置安装前缀改为当前目录，其余 Qt DLL 与 SDK 原件一致。

## 原构建方式

环境：Visual Studio 2017 v141_xp、x86、Release、共享 DLL、Qt 5.6.3 OpenSource。在 VS2017 x86 开发命令环境中运行；先在 PATH 中提供 jom、Perl 和 Python，设置 `CL=/D_HAS_STD_BYTE=0`。将以下 `-prefix` 改为本机安装目录。

```bat
configure.bat -prefix "C:\Qt\Qt5.6.3_VS2017" -platform win32-msvc2017 -target xp -mp -release -opensource -confirm-license -nomake tests -nomake examples -skip qtwebengine -skip qtwayland -skip qtandroidextras -skip qtmacextras -skip qtx11extras
jom.exe -j4
jom.exe install
```

源码 ZIP 内保留 Qt 的许可证和第三方版权声明。用户关闭应用后，可以备份安装目录中的 Qt DLL 和插件，并用同架构、兼容 ABI 的修改版替换；建议先在独立安装副本中验证。应用程序不应阻止为调试库修改而进行的替换或操作。各模块的具体许可证以源码文件及随安装包提供的许可证文本为准。参见 [Qt 官方 LGPL 发行说明](https://www.qt.io/development/open-source-lgpl-obligations)。
