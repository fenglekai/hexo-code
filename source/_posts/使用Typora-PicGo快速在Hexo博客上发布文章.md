---
thumbnail: 'https://picsum.photos/1280/720?random=3 #111'
title: 使用Typora+PicGo快速在Hexo博客上发布文章
date: 2021-11-30 23:07:35
tags:
- 🍉教程
- 💖分享
---
**Typora第一版发布了也开始收费了，不过0.11版本还是可以用的，介意的朋友可以不看了哈~**

**历史版本的链接：**https://typora.io/windows/dev_release.html

博客搭好了，接下来就是要发布文章啦~什么？你还没搭过博客？那你肯定没看过我[快速搭建博客](https://fenglekai.github.io/2021/11/14/%E5%A6%82%E4%BD%95%E5%BF%AB%E9%80%9F%E6%90%AD%E5%BB%BA%E4%B8%80%E4%B8%AA%E5%8D%9A%E5%AE%A2)的教程。

最近在参考我关注的一个b站up主[鱼皮](https://space.bilibili.com/12890453)分享的一篇[提升写作效率](https://www.bilibili.com/read/cv8131025)的文章。

然后，我就开始踩坑了哈，开启我的分享之路。

### 安装软件

在你还在懵逼.md后缀是什么东西？它的语法怎么用？这时候已经有大佬帮你铺好路，你只需要下载软件直接开启你的写作之旅。

我们先要安装[Typora](https://www.typora.io/)和[PicGo](https://github.com/Molunerfinn/PicGo/releases)，然后你就可以用Typora先熟悉一下界面，当你想在文章中插入图片时，这就需要另一个软件PicGo了。

### Typora和PicGo的配置

这里踩个坑哈，之前跟着用七牛云的存储对象实现图片存储读取，但是！因为，本人比较懒，没有申请域名，刚在七牛云注册一个帐号就使用免费的空间和临时域名。在配置好后使用chrome访问页面图片发现加载不出来，后来才知道chrome会强制转换http为https...找了几个解决办法都没啥用。

![](https://gitee.com/feng-lekai/blog-image/raw/master/img/share_1.png)

之后我就改用gitee图床了，这个搭建也是非常简单的，参考知乎一篇文章[PicGo + Gitee(码云)实现markdown图床](https://zhuanlan.zhihu.com/p/102594554)。

首先在PicGo最下方插件设置安装gitee-uploader。

![](https://gitee.com/feng-lekai/blog-image/raw/master/img/share_2.png)

等待安装的时候，我们可以先去gitee去新建一个仓库，如图设置好后创建。



![](https://gitee.com/feng-lekai/blog-image/raw/master/img/share_3.png)

然后回到PicGo查看插件是否安装完成，完成后在图床设置找到gitee选项如图设置。

![](https://gitee.com/feng-lekai/blog-image/raw/master/img/share_4.png)

- repo：新建仓库的部分路径，比如，我的是https://gitee.com/feng-lekai/blog-image，那我的repo就是feng-lekai/blog-image
- branch：分支就不用我多说了吧~
- token：没用的小伙伴需要自己去右上角自己头像那找到设置-私人令牌生成新令牌，权限选择projects就行，然后生成令牌。记得复制哈，它只会显示一次，如果没复制成功就要重新生成了（小问题）。
- path：图片存储路径

接着点击确定，设置默认图床就ok了，可以在PicGo上传区去上传图片试试啦~



**接着回到Typora**菜单找到文件-偏好设置-图像，选择上传服务。

![](https://gitee.com/feng-lekai/blog-image/raw/master/img/share_5.png)

设置好就可以在Typora随时插入图片啦，然后share你的文章~希望这篇文章对你有点帮助，致力于简洁快速的教程。