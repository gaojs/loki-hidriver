# loki-hidriver
Virtual mouse and keyboard driver for Windows 7 and higher.

## Usage
1. Disable Driver Signature Enforcement.
2. Install the driver using `devcon.exe` or manually.
3. Use the driver just like it is used in the [example](https://github.com/hedgar2017/loki-example).



虚拟鼠标键盘驱动程序，使用驱动程序执行鼠标键盘操作。
注意这个驱动目前使用的是测试证书，还没有微软颁发的正式证书，在win10和win11测试模式下执行。

一、项目编译：
建议使用Visual Studio 2022；

二、驱动安装：
1)关闭签名校验，开启调试模式：
在win10和win11中，管理员模式的命令行中，执行如下命令：
1. bcdedit /set nointegritychecks on
2. bcdedit /set testsigning on
然后重启电脑，进入测试模式

2)使用devcon安装驱动，最好先关闭360等杀毒软件：

1. cd loki-hidriver\x64\Debug\KMDFDriver
2. & devcon find root\hidriver
3. & devcon remove root\hidriver
4. & devcon install hidriver.inf root\hidriver

3)安装驱动的日志文件，可以在这里检查驱动安装的明细日志：
1. %windir%\inf\setupapi.dev.log
2. C:\Windows\INF\setupapi.dev.log

三、项目来源：
目前只是针对win10和win11做些兼容性调整，主体代码来源于loki-hidriver项目，感谢原开发者：
https://github.com/hedgar2017/loki-hidriver
