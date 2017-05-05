## 返回码

##### 返回码的约定
当状态码是0的时候表示正常，其他表示出错，脚本中判断如下
```
IF %ERRORLEVEL% NEQ 0 (
    REM do something here to address the error
)


//跟上面一样效果
IF ERRORLEVEL 1 (
    REM do something here to address the error
)
```

状态码是9009时表示程序不存在
```
IF %ERRORLEVEL% EQU 9009 (
    ECHO error - SomeFile.exe not found in your PATH
)
```



##### 状态码条件
```
SomeCommand.exe && ECHO SomeCommand.exe succesed!

SomeCommand.exe || ECHO SomeCommand.exe failed will return code %ERRORLEVEL%
```


- 如果程序不存在退出
```
SomeCommand.exe || EXIT /B 1

SomeCommand.exe || GOTO :EOF
```


##### 一个通用的例子
```
@ECHO OFF
SETLOCAL ENABLEEXTENSIONS

SET /A errno=0
SET /A ERROR_HELP_SCREEN=1
SET /A ERROR_SOMECOMMAND_NOT_FOUND=2
SET /A ERROR_OTHERCOMMAND_FAILED=4

SomeCommand.exe
IF %ERRORLEVEL% NEQ 0 SET /A errno^|=%ERROR_SOMECOMMAND_NOT_FOUND%

OtherCommand.exe
IF %ERRORLEVEL% NEQ 0 (
    SET /A errno^|=%ERROR_OTHERCOMMAND_FAILED%
)

EXIT /B %errno%
```
