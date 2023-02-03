## Go 练手项目——rpc

**目录结构**

```
├─ hello  -- 代码根目录
│  ├─ go_client
│     ├── main.go
│     ├── proto
│         ├── hello
│            ├── hello.pb.go
│  ├─ go_server
│     ├── main.go
│     ├── controller
│         ├── hello_controller
│            ├── hello_server.go
│     ├── proto
│         ├── hello
│            ├── hello.pb.go
│            ├── hello.proto
```

**hello.proto**

```
syntax = "proto3"; // 指定 proto 版本

package hello;     // 指定包名

// 定义 Hello 服务
service Hello {

	// 定义 SayHello 方法
	rpc SayHello(HelloRequest) returns (HelloResponse) {}

	// 定义 LotsOfReplies 方法
	rpc LotsOfReplies(HelloRequest) returns (stream HelloResponse){}
}

// HelloRequest 请求结构
message HelloRequest {
	string name = 1;
}

// HelloResponse 响应结构
message HelloResponse {
    string message = 1;
}
```

## 效果

首先运行server文件夹中的main.go
然后运行client文件夹中的main.go

输出结果：
```
2019/07/28 17:58:13 Hello World
2019/07/28 17:58:13 Hello World Reply 0
2019/07/28 17:58:13 Hello World Reply 1
2019/07/28 17:58:13 Hello World Reply 2
2019/07/28 17:58:13 Hello World Reply 3
2019/07/28 17:58:13 Hello World Reply 4
2019/07/28 17:58:13 Hello World Reply 5
2019/07/28 17:58:13 Hello World Reply 6
2019/07/28 17:58:13 Hello World Reply 7
2019/07/28 17:58:13 Hello World Reply 8
2019/07/28 17:58:13 Hello World Reply 9
```

## debug过程
1. 在Goland中使用go get，需在设置中开代理，手动配置7890 clash端口
2. 缺少的包也可以直接在对应的文件夹内使用git clone命令下载。注意使用git bash 进行clone时需要关闭代理
3. 运行程序时需要关闭第1步中设置的代理
