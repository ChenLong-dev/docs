# grpcurl使用方法

## 安装（<https://github.com/fullstorydev/grpcurl）>

### linux环境安装

```
go get github.com/fullstorydev/grpcurl
go install github.com/fullstorydev/grpcurl/cmd/grpcurl@latest
```

### windows环境安装

[grpcurl_x.y.z_windows_x86_64.zip包下载](https://github.com/fullstorydev/grpcurl/releases)

### 注册reflection服务

grpcurl对于其他grpc服务的感知皆来自reflection服务，所以在注册自己的服务之前需要先注册reflection服务，否则会提示

```
[root@localhost ~]# grpcurl -plaintext  localhost:32101 list
Failed to list services: server does not support the reflection API
```

```
package main

import (
 "google.golang.org/grpc"
 "google.golang.org/grpc/reflection"
 proto "let_me_go/protobuf"
 "log"
 "net"
)

func main() {
 grpcServer := grpc.NewServer()
 // 注册grpcurl的reflection服务
 reflection.Register(grpcServer)
 proto.RegisterHelloServiceServer(grpcServer, new(proto.HelloServiceImpl))

 listen, e := net.Listen("tcp", "localhost:8888")

 if e != nil {
  log.Fatal(e)
 }

 grpcServer.Serve(listen)
}
```

### 使用

#### 查询服务列表

```
[root@localhost ~]# grpcurl -plaintext localhost:32100 list
grpc.reflection.v1alpha.ServerReflection
usersyncorg.AuthSyncOrg
```

#### 查询服务提供的方法

```
[root@localhost ~]# grpcurl -plaintext localhost:32100 list usersyncorg.AuthSyncOrg
usersyncorg.AuthSyncOrg.GetLdapAttr
usersyncorg.AuthSyncOrg.GetLdapBaseDn
usersyncorg.AuthSyncOrg.GetSyncStatus
usersyncorg.AuthSyncOrg.SyncTask
usersyncorg.AuthSyncOrg.TestSvrValid
```

#### 查看更详细的描述

```
[root@localhost ~]# grpcurl -plaintext localhost:32100 describe usersyncorg.AuthSyncOrg
usersyncorg.AuthSyncOrg is a service:
service AuthSyncOrg {
    rpc GetLdapAttr ( .usersyncorg.LdapCommonRequest ) returns ( .usersyncorg.AuthCommonResponse );
    rpc GetLdapBaseDn ( .usersyncorg.LdapCommonRequest ) returns ( .usersyncorg.AuthCommonResponse );
    rpc GetSyncStatus ( .usersyncorg.SyncStatusRequest ) returns ( .usersyncorg.AuthCommonResponse );
    rpc SyncTask ( .usersyncorg.AuthSyncRequest ) returns ( .usersyncorg.AuthCommonResponse );
    rpc TestSvrValid ( .usersyncorg.AuthSvrTest ) returns ( .usersyncorg.AuthCommonResponse );
}
```

#### 获取类型信息

```
[root@localhost ~]# grpcurl -plaintext localhost:32100 describe usersyncorg.LdapCommonRequest
usersyncorg.LdapCommonRequest is a message:
message LdapCommonRequest {
    string reqId = 1;
    uint32 timeout = 2;
    bytes content = 3;
    string extInfo = 4;
}
```

#### 调用服务方法

```
[root@localhost ~]# grpcurl -plaintext -d '{"reqId": "aaaa", "timeout": 200}' localhost:32100 usersyncorg.AuthSyncOrg/GetLdapAttr
{
    "reqId": "aaaa",
    "code": 200,
    "errMsg": "ok"
}

```
