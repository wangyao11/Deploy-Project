## Mac OSX 安装ImageMagick和Jmagick

1. 安装ImageMagick

#### 在mac上安装ImageMagick比较简单。直接使用下面的命令就可以了，brew会自己帮你下载依赖的包：

'brew install imagemagick'

#### 安装完以后执行一下 'brew info imagemagick' 可以看到版本号和一些支持的压缩格式。

2. 安装JmagickMagick

#### 首先要下载Jamgick的安装包

##### 进入到自己想要安装的目录

'wget http://downloads.jmagick.org/6.4.0/jmagick-6.4.0-src.tar.gz'

##### 如果没有安装wget也可以使用 curl

'curl -O http://downloads.jmagick.org/6.4.0/jmagick-6.4.0-src.tar.gz'

#### 开始安装

##### tar xfz jmagick-6.4.0-src.tar.gz                                                                                                                                         
##### mv 6.4.0 jmagick-6.4.0

##### cd jmagick-6.4.0

##### 然后在执行，前提是java环境已经配置好了、ImageMagick已经安装好

##### './configure --with-java-home=/System/Library/Frameworks/JavaVM.framework/Versions/Current --with-magick-home=/usr/local/Cellar/imagemagick/6.7.1-1/'

##### 如果报错找不到java 文件。就将 '--with-java-home=/System/Library/Frameworks/JavaVM.framework/Versions/Current'的路径改成你自己的java_home路径。
##### 如果报错找不到jni.h文件。你要使用 'sudo find / -name jni.h' 查找一下jni.h文件的路径。然后再执行：

##### './configure --with-java-home=/System/Library/Frameworks/JavaVM.framework/Versions/Current --with-magick-home=/usr/local/Cellar/imagemagick/6.7.1-1/ --with-java-includes=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.11.sdk/System/Library/Frameworks/JavaVM.framework/Versions/A/Headers/'

##### '--with-java-includes=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.11.sdk/System/Library/Frameworks/JavaVM.framework/Versions/A/Headers/'这个路径就是查到的jni.h的文件路径

##### 到这一步应该就不会有问题了。

#### 下面就是make了，执行下面的命令：

#####'make'

#####这里有可能会报错：../../Make.rule 175行出错。处理方法：打开Make.rule文件。将175行和176行前面的4个空格删除，换成'tab'遮掩就make成功了

####再执行以下 'make install'

####这样Jamgick就算安装成功了。

#### 最后执行一下 'sudo ln -s /usr/local/lib/libJMagick.so /Library/Java/Extensions/libJMagick.jnilib' 就可以在java里使用Jmagick了


