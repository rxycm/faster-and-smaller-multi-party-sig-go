本项目基于[multi-party-sig](https://github.com/easedot/multi-party-sig)库进行编写,详见[[multi-party-sig.README](easedot-multi-party-sig-README.md).



## Li24

Li24是基于gg18设计的轻量级的门限签名方案,实现了半诚实敌手假设下的语义安全.相关实现在protocols/Li24目录下,使用了go的测试框架"testing"进行了相关测试.



## 三方签名demo

仿照[multi-party-sig](https://github.com/easedot/multi-party-sig)库,我们给出了使用Li24算法的三方签名演示,如下图所示,两方为服务器,一方为客户端.

![](demo.png)



### 服务端

```
ourexm2p/
go build m2p.go

./m2p -id=0 -srv=127.0.0.1:7001                      //server1
./m2p -id=1 -srv=127.0.0.1:8001 -p2p=127.0.0.1:7001  //server2
```

### 客户端

将ourmobile目录下的mobile_test.go文件中的p2p设置为两台服务器的IP地址+端口.

利用gotest进行测试.



### 性能测试

该demo与[multi-party-sig](https://github.com/easedot/multi-party-sig)库的实现方式一致,只是我们将门限签名算法由CGGMP21换成我们的Li24,通过比较两个demo的运行时间可测试我们的门限签名方案的性能.经测试,我们的方案在性能上有明显提升,大概在百倍左右.
