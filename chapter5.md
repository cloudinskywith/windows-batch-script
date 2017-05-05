## 条件判断

##### 检查文件是否存在
```
IF EXIST "temp.txt" ECHO found
IF NOT EXIST "temp.txt" ECHO found


IF EXIST "temp.txt" (
    ECHO found
) ELSE(
    ECHO not found
)
```


##### 检查变量是否设置
```
IF "%var%"=="" (SET var=default value)

IF NOT DEFINED var (SET var=default value)


SET var=hello,world!

IF "%var%=="hello,world!"(
  ECHO found   
)
```

条件判断
```
IF /I "%var%"=="hello,world!"(
    ECHO found
)

SET /A var=1
IF /I "%var%" EQU "1" ECHO equality with 1
IF /I "%var%" NEQ "0" ECHO inequality with 0
IF /I "%var%" GEQ "1" ECHO greater than or equal to 1
IF /I "%var%" LEQ "1" ECHO less than or equal to 1

IF /I "%ERRORLEVEL%" NEQ "0" (
    ECHO execution failed
)
```
