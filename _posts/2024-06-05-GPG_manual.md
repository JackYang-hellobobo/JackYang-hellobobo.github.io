---
title: GPG(GNU Privacy Guard)使用说明
tags: 教程
---
## 前言

因为考虑到了信息安全前所未有面临的风险还有挑战，以及最近的信息安全事件，作为公民个人的我们更应该保护好自己的隐私信息，个人隐私信息也是资源，需要我们公民保护好。主要了解 加密 解密 签名 校验

## GPG简介

**GNU Privacy Guard** （**GnuPG** 或  **GPG** ）是一个[密码学](https://zh.wikipedia.org/wiki/%E5%AF%86%E7%A0%81%E5%AD%A6 "密码学")软件，用于[加密](https://zh.wikipedia.org/wiki/%E5%8A%A0%E5%AF%86 "加密")、[签名](https://zh.wikipedia.org/wiki/%E6%95%B8%E4%BD%8D%E7%B0%BD%E7%AB%A0 "数码签名")通信内容及管理[非对称密码学](https://zh.wikipedia.org/wiki/%E5%85%AC%E5%BC%80%E5%AF%86%E9%92%A5%E5%8A%A0%E5%AF%86 "公开密钥加密")的密钥。GnuPG 是[自由软件](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E8%BD%AF%E4%BB%B6 "自由软件")，遵循 [IETF](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%B7%A5%E7%A8%8B%E5%B7%A5%E4%BD%9C%E5%B0%8F%E7%BB%84 "互联网工程工作小组") 订定的 [OpenPGP](https://zh.wikipedia.org/wiki/OpenPGP "OpenPGP") 技术标准设计，并与 [PGP](https://zh.wikipedia.org/wiki/PGP "PGP") 保持兼容。

## 使用过程

GnuPG 使用[用户](https://zh.wikipedia.org/wiki/%E4%BD%BF%E7%94%A8%E8%80%85 "用户")自行生成的非对称密钥对来加密资讯，由此产生的公钥可以同其他用户以各种方式交换，如[密钥伺服器](https://zh.wikipedia.org/w/index.php?title=%E5%AF%86%E9%91%B0%E4%BC%BA%E6%9C%8D%E5%99%A8&action=edit&redlink=1 "密钥伺服器（页面不存在）")。他们必须小心交换密钥，以防止得到伪造的密钥。GnuPG 还可以向资讯添加一个[数码签名](https://zh.wikipedia.org/wiki/%E6%95%B0%E4%BD%8D%E7%AD%BE%E5%90%8D "数码签名")，这样，收件人可以验证资讯完整性和发件人。

GnuPG 支持的各种加密算法：

* [对称加密](https://zh.wikipedia.org/wiki/%E5%AF%B9%E7%A7%B0%E5%8A%A0%E5%AF%86 "对称加密")：[CAST5](https://zh.wikipedia.org/w/index.php?title=CAST5&action=edit&redlink=1)、[Camellia](https://zh.wikipedia.org/wiki/Camellia "Camellia")、[Triple DES](https://zh.wikipedia.org/wiki/Triple_DES "Triple DES")、[AES](https://zh.wikipedia.org/wiki/%E9%AB%98%E7%B4%9A%E5%8A%A0%E5%AF%86%E6%A8%99%E6%BA%96 "高级加密标准")、[Blowfish](https://zh.wikipedia.org/wiki/Blowfish "Blowfish")、[Twofish](https://zh.wikipedia.org/wiki/Twofish "Twofish")、[ChaCha20](https://zh.wikipedia.org/wiki/ChaCha20 "ChaCha20")、[IDEA](https://zh.wikipedia.org/wiki/IDEA "IDEA") (从 1.4.13 和 2.0.20 开始被添加)
* [非对称加密](https://zh.wikipedia.org/wiki/%E9%9D%9E%E5%AF%B9%E7%A7%B0%E5%8A%A0%E5%AF%86 "非对称加密")：[ElGamal](https://zh.wikipedia.org/wiki/ElGamal "ElGamal")、[RSA](https://zh.wikipedia.org/wiki/RSA%E5%8A%A0%E5%AF%86%E6%BC%94%E7%AE%97%E6%B3%95 "RSA加密算法")、[DSA](https://zh.wikipedia.org/wiki/%E6%95%B0%E5%AD%97%E7%AD%BE%E5%90%8D%E7%AE%97%E6%B3%95 "数码签名算法")、[ECDSA](https://zh.wikipedia.org/wiki/ECDSA "ECDSA")、[EdDSA](https://zh.wikipedia.org/wiki/EdDSA "EdDSA")
* [密码散列函数](https://zh.wikipedia.org/wiki/%E5%AF%86%E7%A0%81%E6%95%A3%E5%88%97%E5%87%BD%E6%95%B0 "密码散列函数")：[RIPEMD-160](https://zh.wikipedia.org/wiki/RIPEMD-160 "RIPEMD-160")、[MD5](https://zh.wikipedia.org/wiki/MD5 "MD5")、[SHA-1](https://zh.wikipedia.org/wiki/SHA-1 "SHA-1")、[SHA-2](https://zh.wikipedia.org/wiki/SHA-2 "SHA-2")、[Tiger](https://zh.wikipedia.org/w/index.php?title=Tiger&action=edit&redlink=1)
* [数码签名](https://zh.wikipedia.org/wiki/%E6%95%B8%E5%AD%97%E7%B0%BD%E5%90%8D "数码签名")：[DSA](https://zh.wikipedia.org/wiki/%E6%95%B0%E5%AD%97%E7%AD%BE%E5%90%8D%E7%AE%97%E6%B3%95 "数码签名算法")、[RSA](https://zh.wikipedia.org/wiki/RSA%E5%8A%A0%E5%AF%86%E6%BC%94%E7%AE%97%E6%B3%95 "RSA加密算法")、[ECDSA](https://zh.wikipedia.org/wiki/ECDSA "ECDSA")、[EdDSA](https://zh.wikipedia.org/wiki/EdDSA "EdDSA")
* 

## 具体实现步骤  

1、安装

> sudo apt install gnupg  

2、生成GPG Key

> gpg --full-generate-key
>
> ```
> 请选择您要使用的密钥种类：
>    (1) RSA and RSA (default)
>    (2) DSA and Elgamal
>    (3) DSA (仅用于签名)
>    (4) RSA (仅用于签名)
> 您的选择？ 1                                                   <- 选择密钥类型
> RSA 密钥长度应在 1024 位与 4096 位之间。
> 您想要用多大的密钥尺寸？(3072) 3072
> 您所要求的密钥尺寸是 3072 位
> 请设定这把密钥的有效期限。
>          0 = 密钥永不过期
>       <n>  = 密钥在 n 天后过期
>       <n>w = 密钥在 n 周后过期
>       <n>m = 密钥在 n 月后过期
>       <n>y = 密钥在 n 年后过期
> 密钥的有效期限是？(0) 1y                                       <- 有效期
> 密钥于 2020年05月04日 星期一 14时38分48秒 CST 过期
> 以上正确吗？(y/n) y                                            <- 确定
>
> You need a user ID to identify your key; the software constructs the user ID
> from the Real Name, Comment and Email Address in this form:
>     "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"
>
> 真实姓名： YOUR_NAME                                          <- 用户名
> 电子邮件地址： gitee@gitee.com                                 <- 邮箱，需要与 Gitee 提交邮箱保持一致
> 注释： Gitee GPG Key                                          <- 注释
> 您选定了这个用户标识：
>     “YOUR_NAME (Gitee GPG Key) <gitee@gitee.com>”
>
> 更改姓名(N)、注释(C)、电子邮件地址(E)或确定(O)/退出(Q)？ O
> gpg: 密钥 B0A02972E266DD6D 被标记为绝对信任
> gpg: revocation certificate stored as 'xxx'
> 公钥和私钥已经生成并经签名。
>
> pub   rsa3072 2019-05-05 [SC] [有效至：2020-05-04]
>       8086B4D21B3118A83CC16CEBB0A02972E266DD6D                 <- Key ID
> uid                      likui (Gitee GPG Key) <gitee@gitee.com>
> sub   rsa3072 2019-05-05 [E] [有效至：2020-05-04]
> ```

3、导出GPG公钥

> gpg --armor --export 8086B4D21B3118A83CC16CEBB0A02972E266DD6D

## GPG Key 配置与使用

1、配置Git

2、添加到代码托管账户 e.g Github ，Gitlab , Gitee  

![输入图片说明](https://gitee.com/uploads/images/2019/0506/150932_746867da_2118102.png "屏幕截图.png")

GPG 公钥验证状态，**GPG 邮箱为当前用户已激活邮箱**验证才能通过：

![输入图片说明](https://gitee.com/uploads/images/2019/0506/151235_bdda7f4c_340906.png "gpg_gitee_1.png")

* `删除` 仅移除 GPG 公钥，验证通过的 Commit 签名状态保持不变
* `注销` 移除 GPG 公钥并且将已验证的 Commit 签名状态修改为未验证

3、使用GPG签名提交

> git commit -S -m "Messages"
>
> git log --show-signature

### 完毕

## 参考文献

1、如何在Gitee上使用GPG [https://gitee.com/help/articles/4248#article-header6](https://gitee.com/help/articles/4248#article-header6)  

2、使用 GPG Key 来构建签名、加密及认证体系 [https://juejin.cn/post/7075615737015959566](https://juejin.cn/post/7075615737015959566)

3、GPG加密解密与实际应用 [http://pangyi.github.io/blog/20150103/gpgjia-mi-jie-mi-yu-shi-ji-ying-yong/](http://pangyi.github.io/blog/20150103/gpgjia-mi-jie-mi-yu-shi-ji-ying-yong/)

4、GnuPG 维基百科 [https://zh.wikipedia.org/zh-sg/GnuPG](https://zh.wikipedia.org/zh-sg/GnuPG)

5、阮一峰 GPG入门教程 [https://ruanyifeng.com/blog/2013/07/gpg.html](https://ruanyifeng.com/blog/2013/07/gpg.html)



<!--more-->

---

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/kitian616/jekyll-TeXt-theme/)