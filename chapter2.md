## 第2章 变量

##### 声明变量
使用SET进行声明
```
::变量与赋值直接不能有空格
SET foo=bar
SET foo
//输出
foo=bar

::使用/A进行算数运算
set foo=2+2
set foo
//输出为 foo=2+2

set /A foo=2+2
//输出为 4
```

推荐使用小写字母进行变量声明，windows的实践约定。
可以使用`ECHO %foo%`来查看自己声明的变量是否已经被windows使用了，避免出现bug
```
echo %temp%
C:\Uses\lbc\AppData\Local\Temp

echo %liaobaocheng%
%liaobaocheng%


//一些常见的变量
%DATE%    %RANDOM%     %CD%
```


##### 展示已有的变量
```
set
```

展示动态的变量
```
set /?
```


##### 变量命名空间
全局还是本地
使用TYPE可以输出命令全文
```
// LocalPath.md

SETLOCAL
SET PATH=%SystemRoot%\system32
ECHO %PATH%
```

##### 特殊变量
%0-9表示从命令行传过来的参数

##### 命令行参数技巧
```
%~1         SET myvar=%~1

%~f1

%~fs1

%~dp1

%~nx1
```

##### 一些通用的技巧
在脚本中写如下代码，有助于后面编写脚本
```
SETLOCAL ENABLEEXTENSIONS
SET me=%~n0
SET parent=%~dp0
```
