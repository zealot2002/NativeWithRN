# 项目名称
# NativeWithRN
为原生项目集成rn的demo
一、下载RN离线包
http://bbs.reactnative.cn/topic/11/react-native
下载17版本，最新的稳定版本，保存至任意位置。

二、创建android工程，名为：NativeWithRN

三、复制离线包中的node_modules文件夹，index.android.js，package.json到工程根目录下

四、添加RN maven


五、添加测试窗口
为了测试，我们创建一个ReactActivity，并在MainActivity中增加一个按钮，让点击它进入ReactActivity。
ReactActivity的写法是facebook要求的，按照demo的样子写即可，具体每一项的用途这里就不详述了，可以参考官网。

修改AndroidManifest.xml文件，声明<activity android:name=".ReactActivity"/>
另外，千万不要忘记
增加权限<uses-permission android:name="android.permission.INTERNET" />
和<activity android:name="com.facebook.react.devsupport.DevSettingsActivity"/>

没有这个设置server ip的界面，就会报找不到bridge什么东东的异常了。。
因为我们要debug，需要联网，设置server的ip和port；release的时候，不需要。

六、配置js模块，供我们的ReactActivity使用，注意名称一定保持一致，否则找不到。一共3步：
1，index.android.js中：


2，package.json中：

3，这样，在ReactActivity中就可以找到这个js模块了：



七、连接真机，在android stdio中运行程序
出现空白？这是个常见的大坑，坑的打开真机的调试悬浮框、设置server ip和端口
另，这里也有一个坑，在node server打开的时候，android stdio常常会编译失败，说是禁止访问一些路径等等。。
所以，我在编译app的时候，通常关掉server端，等app在真机上跑起来了，再打开server。

八、运行node服务器


九、观看结果


能明显看到，jsx编译成js比较耗时，release时，这项工作是离线时做好的。

十、完。


