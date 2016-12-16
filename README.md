# PHP-RSA

##简介
    实际项目中的登陆认证、web api接口调用、支付接口调用等场合经常涉及到：md5、sh、 rsa等算法。
    各大银行接口中经常使用MD5算法对调用接口参数进行签名防篡改。


### 如果你和我有同样的问题 ：
     web api调用认证中，客户端和服务端通过相同的公钥对提交参数进行MD5加密，进行验证。但
     2014年中国山东大学的王小云教授公布破译了MD5、HAVAL-128、 MD4和RIPEMD算法的报告。通过加
     速的杂凑与冲撞方法破译了MD5算法，MD5还安全吗？
     
# RSA定义：


* RSA为公钥加密体制：

* A.乙方生成两把密钥（公钥和私钥）。公钥是公开的，任何人都可以获得，私钥则是保密的。

* B.甲方获取乙方的公钥，然后用它对信息加密。

* C.乙方得到加密后的信息，用私钥解密。

# RSA使用：
* web 端 见  test_rsa.html
* php 端 见  test_rsa.php


# RSA特点：

## A.便于理解，使用广泛。

* RSA算法是第一个能同时用于加密和数字签名的算法，也易于理解和操作。
RSA是被研究得最广泛的公钥算法，从提出到现今的三十多年里，经历了各种攻击的考验，
逐渐为人们接受，普遍认为是目前最优秀的公钥方案之一。

## B.缺点与不足：
* 加密和解密花费时间长、速度慢，只适合对少量数据进行加密。

* 为提高保密强度，RSA密钥至少为500位长，一般推荐使用1024位。这就使加密的计算量很大。
为减少计算量，在传送信息时，常采用传统加密方法与公开密钥加密方法相结合的方式，
即信息采用改进的DES或IDEA对话密钥加密，然后使用RSA密钥加密对话密钥和信息摘要。
对方收到信息后，用不同的密钥解密并可核对信息摘要。

#需要原型工具：

OpenSSL下载地址：http://slproweb.com/products/Win32OpenSSL.html 


* 安装OpenSSL

    * 随意安装到哪里

* 点击OpenSLL的bin目录下的 openssl.exe 进行私钥和公钥的生成

    1. 生成私钥
    *  genrsa -out rsa_private_key.pem 1024 
    2. 生成公钥
    *  rsa -in rsa_private_key.pem -pubout -out rsa_public_key.pem

* 将生产的私钥、公钥拷贝到你的PHP项目中

* 开启PHP的OpenSSL扩展

1. 将php.ini中的extension=php_openssl.dll开启（去掉;）
    

