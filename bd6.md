HTTPS其实是有两部分组成：HTTP + SSL / TLS，也就是在HTTP上又加了一层处理加密信息的模块。服务端和客户端的信息传输都会通过TLS进行加密，所以传输的数据都是加密后的数据。

0. 数字签名的制作过程：

    CA拥有非对称加密的私钥和公钥。

    CA对证书明文信息进行hash。

    对hash后的值用私钥加密，得到数字签名。

    明文和数字签名共同组成了数字证书，这样一份数字证书就可以颁发给网站了。

1. 客户端发起HTTPS请求
    
    用户在浏览器里输入一个https网址，然后连接到server的443端口。请求携带了浏览器支持的加密算法和哈希算法。

2. 服务器传送证书
    
    服务器将数字证书返回给浏览器，这里的数字证书可以是向某个可靠机构申请的，也可以是自制的。

3. 浏览器进入数字证书认证环节，这一部分是浏览器内置的 TSL 完成的

    首先浏览器会从内置的证书列表中索引，找到服务器下发证书对应的机构，如果没有找到，此时就会提示用户该证书是不是由权威机构颁发，是不可信任的。如果查到了对应的机构，则取出该机构颁发的公钥。
    
    用机构的证书公钥和hash算法解密得到证书的内容和证书签名，内容包括网站的网址、网站的公钥、证书的有效期等。浏览器会先验证证书签名的合法性。

    签名通过后，浏览器验证证书记录的网址是否和当前网址是一致的，不一致会提示用户。如果网址一致会检查证书有效期，证书过期了也会提示用户。这些都通过认证时，浏览器就可以安全使用证书中的网站公钥了。

4. 传送加密信息

    如果证书没有问题，那么就生成一个随即值(session key)。然后用证书对该随机值进行加密。

    这部分传送的是用证书加密后的随机值，目的就是让服务端得到这个随机值，以后客户端和服务端的通信就可以通过这个随机值来进行加密解密了。

5. 服务段解密信息
    
    服务端用私钥解密后，得到了客户端传过来的随机值，然后把内容通过该随机值进行对称加密。

![](https.png)