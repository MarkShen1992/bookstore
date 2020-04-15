### 书籍源码

[CSharp-8.0-and-.NET-Core-3.0](https://github.com/PacktPublishing/CSharp-8.0-and-.NET-Core-3.0-Modern-Cross-Platform-Development-Fourth-Edition)

### Dockerize .NET Core application

```
# 了解 .net core 的运行原理
https://dotnet.microsoft.com/download

# 执行下面的命令就可以完成 .net core 程序的运行了
dotnet demo.dll 

# 其中 dotnet 这个工具来自 .net SDK 
# 除此之外，还需要 .net的运行环境
```

### Dockerfile

```dockerfile
# download the dotnet core sdk
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build-env
WORKDIR /app

# Build runtime image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build-env /app .
COPY /publish /app
ENTRYPOINT ["dotnet", "demo.dll"]
```

```shell
docker run -d -p 8000:80 --name demo demo
```

