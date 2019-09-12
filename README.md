# WaterMarkAndroid
Android平台基于freetype和opencv实现视频水印

本工程包括如下部分

1 主工程

2 freetype-2.10.1子工程 \
  1 下载freetype库版本为2.10.1,地址为 \
     http://sourceforge.net/projects/freetype/files/freetype2/

  2 解压后将源码拷贝到freetype子工程jni目录下

  3 cd jni/freetype-2.10.1/

  4 编译toolchain \
	android-ndk-r17b/build/tools/make-standalone-toolchain.sh --platform=android-22 \
	   --install-dir=/home/zhongjihao/freetype/ --arch=arm --force
  
  5 设置环境变量PATH \
	export PATH=$PATH:/home/zhongjihao/freetype/bin \
	export CC=arm-linux-androideabi-gcc \
	export CXX=arm-linux-androideabi-g++

  6 配置freetype编译参数
 
    ./configure --host=arm-linux-androideabi --prefix=/freetype --without-zlib --with-png=no --with-harfbuzz=no

  7 编译,编译出来的文件会在jni/freetype-2.10.1/freetype/目录下 \
	  make -j4 \
	  make install DESTDIR=$(pwd)

  8 将编译出来的freetype目录拷贝到jni/下
	
    

3 opencv_java子工程 \
  1 下载opencv-3.4.3-android-sdk版本，地址为 \
    https://jaist.dl.sourceforge.net/project/opencvlibrary/opencv-android

  2 解压,将解压后的sdk目录java/src/org全部拷贝到opencv_java子工程java目录下 \
	同时将sdk目录native/libs全部拷贝到freetype/src/main/libs下
	