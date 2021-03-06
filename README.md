
# Tutorial
## 网站搭建
#### 1.安装Jekyll
##### (1)安装依赖
```bash
sudo apt-get install ruby ruby-dev build-essential
gem install bundler
gem install jekyll-paginate
```
##### (2)修改.bashrc文件,添加下面的内容
```bash
# Install Ruby Gems to ~/gems
export GEM_HOME=$HOME/gems
export PATH=$HOME/gems/bin:$PATH
```
然后保存,在终端输入
```bash
source ~/.bashrc
```
使配置生效
##### (3)开始安装jekyll:
```bash
gem install jekyll bundler
```
##### (4)升级JekyllPermalink
查询版本:
```bash
jekyll --version
```
升级
```bash
gem update jekyll
```
要升级到最新的Rubygems
```bash
gem update --system
```
#### 2.用jekyll生成网页
```bash
 jekyll server
```
#### 3.解析域名
#### 4.修改CNAME文件
#### 5.修改文件
目录结构如下：`_layouts 内的文件为骨架模板`；`_posts `内的 markdown 文件会转化为我们所需发表的文章；`_config.yml` 为配置文件。
###### `_posts`为博客更新处，照片可以放在`img/in-post/`目录下
###### 如果有中英文版的，．md文件放在`include posts/`目录下，相应修改_posts的文件就行了．
##### 6.添加模块
###### (1)动态鼠标曲线
添加模块`canvas-nest.min.js`到js目录下
修改`layouts/post.html`文件在开始添加下面代码
```xml
    <!-- canvas-nest.min.js -->
<script type="text/javascript" src="../../../../js/canvas-nest.min.js"></script>
```
##### (2)要修改照片的话，把
```xml
background-image: url('{{ site.baseurl }}/{% if page.header-img %}{{ page.header-img }}{% else %}{{ site.header-img }}{% endif %}')
```
改为
```xml
background-image: url({{ site.baseurl }}{% if page.header-img %}{{ page.header-img }}{% else %}{{ site.header-img }}{% endif %})
```
就行了
##### (3)打字特效
```xml
<script src="../../../../js/activate-power-mode.js"></script>
<script>
POWERMODE.colorful = true; // 控制开启/开启礼花特效  
POWERMODE.shake = false; // 控制开启/关闭屏幕震动特效  
document.body.addEventListener('input', POWERMODE);
</script>
```
##### (4)返回顶部
把在rocket.css、signature.css和toc.css下载到css的目录下，然后在   include目录下的head.html文件的头部添加下面代码：
```xml
    <link rel="stylesheet" href="/css/rocket.css">
    <link rel="stylesheet" href="/css/signature.css">
    <link rel="stylesheet" href="/css/toc.css">
```
把在totop.js和toc.js下载到js的目录下，然后在include目录下的footer.html的最后添加下面代码：
```xml
<a id="rocket" href="#top" class=""></a>
<script type="text/javascript" src="/js/totop.js?v=1.0.0" async=""></script>
<script type="text/javascript" src="/js/toc.js?v=1.0.0" async=""></script>
```

##### (5)显示站点总访问量
具体教程参考:[不蒜子](http://ibruce.info/2015/04/04/busuanzi/)