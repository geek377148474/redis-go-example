
## redis请求与回复协议

redis version >1.2

#### 说明
通过简单的封装讲明redis协议

#### 二进制请求
在该协议下所有发送至 Redis 服务器的参数都是二进制安全（binary safe）的

#### 请求协议


```
Redis 请求协议的格式：参数数量:参数1字节数量:参数1数据...参数N的字节数量:参数N数据
*  参数数量
$  某参数字节数量
实际协议值示例：*3\r\n$3\r\nSET\r\n$5\r\nmykey\r\n$7\r\nmyvalue\r\n
```

#### 回复协议
```
在这个回复“协议”中，可以通过检查第一个字节，确定这个回复是什么类型，如下：
状态回复（status reply）的第一个字节是 "+"。
错误回复（error reply）的第一个字节是 "-"。
整数回复（integer reply）的第一个字节是 ":"。
批量回复（bulk reply）的第一个字节是 "$"。
多条批量回复（multi bulk reply）的第一个字节是 "*"
```