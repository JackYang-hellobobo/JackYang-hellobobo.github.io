---
title: Git使用手册
tags: 教程
---

git是一个分布式管理工具，分为remote端和local端，我们需要本地local开发测试好以后，push到remote端，开源协同给伙伴用，是一款比较灵活可玩性高的开发效率工具，如同文件管理工具一样。下面我来简述一下使用git的细节历程。

注意在使用git commit push前 请部署好GPG的Signature key来签名自己的提交，确认为合法本人提交，以便不被hub系统识别为unverify.
{:.warning}

---

### git config --global --list
> jacky@QN8H:~$ git config --global --list 
> 
> user.name=Jack Yang
> 
> user.email=example@outlook.com
> 
> user.signingkey=xxxx （这一步是配置GPG的子钥subkey SinatureKey的指纹fingerprint）
> 
> commit.gpgsign=true (这一步是重点)

### git clone [url.git]
克隆库

### git add [files]
暂存文件

### git commit -m "comment" -S 
git commit -m "注释" -S(签名提交) 

### git push orgin branch
推动到remote端的哪一个分支

### git fetch
git fetch是将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中

### git pull
而git pull 则是将远程主机的最新内容拉下来后直接合并
git pull = git fetch + git merge

### git log
查看日志

### git branch [name]
创建分支 查看分支

### git merge [branch_A] [branch_B]
合并分支

### git switch [branch_name]
切换分支

### git squash 
压缩

### git rebase
变基

---
## 参考文献

1、git merge squash rebase 的区别 [https://blog.csdn.net/wfeng2004/article/details/135971358](https://blog.csdn.net/wfeng2004/article/details/135971358)

2、GPG 配置方法 [https://gitee.com/help/articles/4248#article-header3](https://gitee.com/help/articles/4248#article-header3)

<!--more-->

---

[![Star This Project](https://img.shields.io/github/stars/kitian616/jekyll-TeXt-theme.svg?label=Stars&style=social)](https://github.com/kitian616/jekyll-TeXt-theme/)





