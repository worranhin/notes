Socket 是计算机之间通信的一种约定。通过 Socket，计算机可以接收其它计算机的数据也能向其它计算机发送数据。

## 数据传输方式

- SOCK_STREAM: 面向连接的数据传输方式。可以保证数据的正确性。用于 http 等需要确保正确性的场合。
- SOCK_DGRAM: 无连接的数据传输方式。不做数据校验，效率提高。用于视频、语音聊天等允许错误且对传输效率要求高的场合。

## 参考

- [一、Socket技术详解 - 简书 (jianshu.com)](https://www.jianshu.com/p/066d99da7cbd)
- [一份用到 Socket 的 python 代码](https://github.com/KikiLetGo/CyberControllerServer/blob/main/TcpServer.py)