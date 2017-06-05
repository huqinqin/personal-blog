  ()如何使用grunt的uglify
  1. 安装nodejs
  2. 安装grunt-CLI
     npm install -g grunt -cli
  3. 创建一个简单的网站
    在D:/下建立一个文件夹，包含三个空文件夹，两个空文档，文件夹的名字是：build src test，两个空文档是：gruntfile.js和
    package.json.配置 package.json
    package.json的配置如下：
    {
  "name": "grunt_test",
  "version": "1.0.0",
  "devDependencies": {
   
  }
 }
还有，最后一个“devDependencies”是什么意思？字面意思解释是“开发依赖项”，即我们现在这个系统，将会依赖于哪些工具来开发。现在代码一行都没有写，依赖于谁？谁也不依赖！所以，就先写一个空对象。但是下文会慢慢把它填充起来。
 4 安装grunt
   npm install grunt --save-dev
 “—save-dev”的意思是，在当前目录安装grunt的同时，顺便把grunt保存为这个目录的开发依赖项。看到“开发依赖项”这一次，是不是觉得有些眼熟？上文在配置package.json时，其中的“devDependencies”中就会存储开发依赖项。
 具体保存为开发依赖项是一个什么效果？动手安装一下就是了。首先，在运行安装grunt的命令之前，package.json中的“devDependencies”对应的是空对象现在我们来运行这行命令。你会看到几条warning提示，不用管它。然后接下来就是加载状态，一个旋转的小横线。稍等待一会儿，会提示你安装成功。
 5. 配置Gruntfile.js
　　顾名思义，Gruntfile.js 这个文件，肯定是为了grunt做某种配置的。按照grunt的规定，我们首先把Gruntfile.js配置成如下格式。
   详情请参考网址：http://blog.csdn.net/wangfupeng1988/article/details/46418203/   (这个网址的内容写的很好也很详细)
