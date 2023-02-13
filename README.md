## 部署遇到的问题
### 1、使用Github Action，生成的所有文件都是0KB?
找了很久都没有找到原因，以为Action脚本有问题，换了好多种脚本方案，然而没有什么用处。
后面改成官方默认的主题，完美的生成网页，可以判断问题是在主题上，查找了一些网站，终于在一个地方
找到了与我相似的小伙伴。其中，有人给出了方案
引用大佬的话，“index生成不成功可能是因为hexo的主题都使用了**子模块**的形式”。

修改步骤中的checkout部份配置，如下所示：
``` yml
steps:
- name: Checkout repository and submodules
  uses: actions/checkout@v2
  with:
    submodules: recursive
```
参考链接如下：https://github.com/theme-keep/hexo-deploy-github-pages-action/issues/1
