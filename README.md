> 注意
> 
> 因为ChatGPT、Cursor等各种辅助工具的出现，自己维护一个通用知识文档的投入产出比越来越低，继续维护非常困难，于是Archive此项目。

# bunnyxt's cheat sheet

本书为[bunnyxt](https://www.bunnyxt.com)的技术备忘录，即bunnyxt's cheat sheet(bcs)，基于[GitBook](https://github.com/GitbookIO/gitbook)，使用MarkDown语法编写。

您可以在我的个人网站[https://bcs.bunnyxt.com/](https://bcs.bunnyxt.com/)阅读到本书的最新内容（推荐），或在[本书的GitHub页面](https://github.com/bunnyxt/bcs)上查看、下载原文件（md格式）。**希望这份cheat sheat能帮到你，弱弱地求个Star！谢谢~**

## 何为cheat sheet

Cheat sheet类似技术博客(blog)，是个人技术内容的记录与分享，但又与博客不同。Cheat sheet有以下特性：
- 主要供自己查阅备忘
- 检索方便，快速定位到所需信息
- 篇幅较短，信息密度高，追求效率而不是大而全
- 主要记录个人使用频率不高，需要用的时候记不清，得上网再重新查的代码片段/配置信息等
- 技术点不会很全面，描述不那么严谨，甚至会有错，还请见谅

## 编写规则

本书编写过程中遵循以下几条规则：
- 不同类别的笔记放在不同的文件夹中
- 文件夹中该类别的目录与其他未分类信息放在`README.md`中
- md中出现的图片与md文件放在同一目录下，尽量不使用外链
- 参考链接统一放在文末，用`ref`形式标记

## 开发与构建

本书基于GitBook开发与构建，流程如下：
- 安装node与npm。注意：新版node中无法使用gitbook，因此需要安装旧版本的node；强烈推荐使用nvm管理多版本node
  - [下载](https://github.com/coreybutler/nvm-windows/releases)并安装nvm
  - `nvm install 10.21.0`安装指定的旧版本node（经测试10.21.0版本可用）
  - `nvm use 10.21.0`切换到此版本node环境
- `npm install -g gitbook-cli`全局安装`gitbook-cli`
- `cd bcs`进入文件夹
- `gitbook install`安装插件
- `gitbook serve`启动本地开发实时预览，默认在`http://localhost:4000/`
  - Windows下存在无法热更新的问题，解决方法参考[此处](https://juejin.cn/post/6844903840332939277)，在执行`gitbook serve`之后，立刻手动删除`_book`文件夹即可
- `gitbook build`构建生成可直接部署的静态网站，存放于`_book`文件夹中

## 关于bunnyxt

业余全栈工程师，业余站长，联系方式：[bunnyxt@outlook.com](mailto:bunnyxt@outlook.com)

## 版权声明

若无特殊说明，本cheat sheet所有条目采用[知识共享署名-相同方式共享 4.0](http://creativecommons.org/licenses/by-sa/4.0/)国际许可协议进行许可。至于为啥没有限制商用...随缘吧，这种东西肯定不会有人拿来商用的对吧x

![by-nc-sa](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)
