#### [中文版文档](./Readme-cn.md)

# arsDrive

An Extension of ARS pServer Based on IPFS

arsDrive is designed as an extension of ARS pServer .   Now the source code  open and modify as a website project ，So the Access control is simple——using only an Username。 

demo http://45.76.105.233/

### Usage

##### add a file

Name:      test.jpg

Hash:       QmQNXmFms6MAVv253A5zVW2hCNjc7Uoq6s7Yz4HRwNny1P

##### add a folder

Name:      AAA

Hash:        QmdXGMXJrCgPF8qaAuKZpRQrhnUop1eXnDt7n9Z8QiGH5R

##### Upload、Open、Remove.....



### Environment   and Configuration

##### 1.Download and install 

```
$ go get github.com/arsyun/arsDrive
```

##### 2.Dependencies      

```
$ go get github.com/labstack/echo/... 
```

##### 3.Runtime environment  

install   IPFS node   https://github.com/ipfs/go-ipfs

arsDrive must connect an IPFS node. The IPFS node should set access control .

The steps to configure this are as follows. 

```
$ ipfs config --json API.HTTPHeaders.Access-Control-Allow-Methods '["PUT", "GET", "POST", "OPTIONS"]'
$ ipfs config --json API.HTTPHeaders.Access-Control-Allow-Origin '["*"]'
$ ipfs config Addresses.Gateway /ip4/0.0.0.0/tcp/8080
$ ipfs config Addresses.API /ip4/0.0.0.0/tcp/5001
```

##### 4.configuration file

If The IP of  IPFS node is 192.168.1.25  .so you can set the configuration file as follows.

```
# ./config/conf.json
{
  "title":"arsDrive",                 //HTTP title
  "app_name" :"arsDrive",            //app name
  "httpserver":":80",				//arsDrive server port
  "ipfs_gateway":"192.168.1.56:8080",//IPFS gateway address
  "ipfs_api":"192.168.1.56:5001"	//IPFS API address
 }
```

If IPFS and arsDrive running in one Host，the connent config and access control should be “127.0.0.1”

```
$ ipfs config Addresses.Gateway /ip4/127.0.0.1/tcp/8080
$ ipfs config Addresses.API /ip4/127.0.0.1/tcp/5001
...
# ./config/conf.json
...
  "ipfs_gateway":"127.0.0.1:8080",//IPFS gateway address
  "ipfs_api":"127.0.0.1:5001"	//IPFS API address
```



# License

arsDrive is issued under GPLv3. license. 


