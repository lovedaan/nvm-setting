# 配置nvm来管理node版本
nvm可以很方便的来管理我们的node版本，随时切换。
http://blog.csdn.net/tyro_java/article/details/51232458
首先确保你的网络畅通，还有不被墙，如果需要翻墙，请看：
https://github.com/getlantern/lantern

1. 下载 nvm 包 地址：https://github.com/coreybutler/nvm-windows/releases，我们选择第一个：nvm-noinstall.zip 下载完成后解压到一个地方，比如: C:\dev\nvm 里面的文件列表是这样的：elevate.cmd、elevate.vbs、install.cmd、LICENSE、nvm.exe
备注：windows下要设置显示文件类型的扩展名，这样才能看到上述文件的后缀

2. 双击 install.cmd 然后会让你输入”压缩文件解压或拷贝到的一个绝对路径” 先不用管它，直接回车，成功后，会在C盘的根目录生成一个settings.txt的文本文件，把这个文件剪切到C:\dev\nvm目录中，然后我们把它的内容修改成这样：
```
root: C:\dev\nvm
path: C:\dev\nodejs
arch: 64
proxy: none
node_mirror: http://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```
3. 然后我们开始配置环境变量了，因为刚刚点击了install.cmd的文件，那么会在环境变量的系统变量中，生成两个环境变量：NVM_HOME 和 NVM_SYMLINK 我们开始修改这两个变量名的变量值：NVM_HOME的变量值为：C:\dev\nvm； NVM_SYMLINK的变量值为：C:\dev\nodejs
我们还会发现，在Path中也会自动添加上C:\dev\nvm;或者是C:\dev\nodejs，如果有的话，把他们删掉，没有的话更好，我们自己来配置，在Path的最前面输入： ;%NVM_HOME%;%NVM_SYMLINK%;

4. 打开一个cmd窗口输入命令：nvm v ，那么我们会看到当前nvm的版本信息。然后我们可以安装nodejs了。
继续输入命令：nvm install latest 如果网络畅通，我们会看到正在下载的提示，下载完成后 会让你use那个最新的node版本。
如果你是第一次下载，在use之前，C:\dev目录下是没有nodejs这个文件夹的，在输入比如： nvm use 5.11.0 之后，你会发现，C:\dev目录下多了一个nodejs文件夹，这个文件夹不是单纯的文件夹，它是一个快捷方式，指向了 C:\dev\nvm 里的 v5.11.0 文件夹。

5. 同样的咱们可以下载其他版本的nodejs，这样通过命令:nvm use 版本号 比如：nvm use 5.11.0就可以轻松实现版本切换了。
备注： 如果你的电脑系统是32 位的，那么在下载nodejs版本的时候，一定要指明 32 如： nvm install 5.11.0 32 这样在32位的电脑系统中，才可以使用，默认是64位的。