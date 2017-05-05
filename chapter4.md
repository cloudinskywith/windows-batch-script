## 输入输出
DOS跟Unix一样，也是使用三种标准的文件来表示输入输出

##### 文件编号
Stdin是file 0，stdout是file 1，stderr是file 2

##### 重定向
将输出保存到日志文件中使用`>`，比如下面
使用`>>`则是追加
```
DIR > temp.txt 
DIR >> temp_appends.txt
```

也可以通过声明编号来使用，比如声明2
```
DIR SomeFile.txt  2>> error.txt
```

一起使用stdout和stderr
```
DIR SomeFile.txt 2>&1

DIR SomeFile.txt > output.txt > 2&1
```

##### 不输出
```
PING 127.0.0.1 > NUL
```

##### 将A的输出作为B的输入
```
DIR /B | SORT
```
