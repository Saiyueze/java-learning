# Docker 挂载 Windows 系统的本地目录  

>Mount current directory as a volume in Docker for Windows 10/11  

使用 Windows 10 或者 Windows 11 体验 Docker 的朋友都曾为 Docker 如何挂载 Windows 本地目录而棘手过，那本文就是为此而生的笔记。  

docker run 使用方法如下：  

```powershell
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```

OPTIONS 会用到的简要说明如下：  

- -i：以交互模式运行容器即允许你对容器内的标准输入(STDIN)进行交互，通常与 -t 一起使用；  
- -t：为容器分配一个伪终端或终端，通常与 -i 一起使用；  
- -v，-volume：绑定挂载卷，在执行挂载宿主主机目录操作时用；  

现在以 Docker 运行 nginx 为例说明并挂载本机 C:\Users\xxx\www 目录静态页面。  

### 方式一：  

```powershell
docker run -it --name my-nginx-01 -p 888:80 -v ${pwd}/www:/usr/share/nginx/html:ro -d nginx
```  

该方法中 ```${pwd}``` 可以替换为 ```${PWD}```。同时也可以直接在 Powershell 窗口中输入 ```${pwd}``` 或 ```${PWD}``` 进行验证，如果打印出文件路径，此种方法就可用。  

**特别提示：此种方法需要保证 Powershell 窗口路径是在 C:\Users\xxx\ 目录打开的**  

### 方式二：

```powershell
docker run -it --name my-nginx-02 -p 808:80 -v /c/Users/xxx/www:/usr/share/nginx/html:ro -d nginx 
```  

**特别提示：此种方法和方法一的不同在 ```/c/Users/xxx``` 此处的写法，注意此处原本为 ```C:\Users\gavin\``` 绝对路径，要写成 ```/c/Users/xxx``` ，否则会报错，错误为 ```Error response from daemon: invalid mode``` ，另外要挂载的路径 ```/usr/share/nginx/html``` 是 ```nginx``` 镜像中安装的路径**  

命令行中 冒号 前后分别为本地路径和要挂载到容器中的路径。  