#Reveal查看任意APP

在网看到一些资料，有的不完整于是被坑了，手机变白苹果了。折腾了好久才把手机弄好，心灰意冷。本来不愿再试，但是心里有些不甘，决心再尝试一下。结果成功了，欣喜之余，记录下来。以下内容非个人原创，只是稍稍修改了一下，心里非常佩服第一个吃螃蟹的人。路漫漫其修远兮，吾辈需上下而求索！

准备工作

1）已越狱的设备，并且已安装了OpenSSH,MobileSubstrate,Terminal等实用工具(Cydia源里安装)
2）本地已安装了[Reveal](http://pan.baidu.com/disk/home#render-type=grid-view)


操作步骤

1）拷贝framework和dylib到越狱机,iPhone root密码默认是alpine

scp -r /Applications/Reveal.app/Contents/SharedSupport/iOS-Libraries/Reveal.framework root@192.168.0.X:/System/Library/Frameworks

scp /Applications/Reveal.app/Contents/SharedSupport/iOS-Libraries/libReveal.dylib root@192.168.0.X:/Library/MobileSubstrate/DynamicLibraries


2）编辑libReveal.plist

a.可以ssh登录到越狱机上，并且越狱机已安装了编辑器工具例如nano，在/Library/MobileSubstrate/DynamicLibraries/下创建文件libReveal.plist，指定app的Bundle，可以指定多个
{   
    Filter = {  
         Bundles = ("com.netease.news");   
    };   
}  
com.netease.news //网易新闻客户端包名

com.taobao.tmall //天猫

com.tencent.xin //微信

b.也可以在本地创建好libReveal.plist在scp到指定位置/Library/MobileSubstrate/DynamicLibraries/下


3）重启越狱机

a.终端执行 killall SpringBoard
     
b.也可以重启设备


然后就可以到Reveal看看别人的app怎么布局的了，我查看的是网易新闻客户端，最近项目遇到一个问题，想了解一下网易怎么做的。

![mvc_model_image](http://d.pcs.baidu.com/thumbnail/3aaa09cb3a30bf70dd0ce59a5c2976a9?fid=1058376525-250528-539568414531577&time=1440745200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-4ZMkqlvuht1jpyy%2BPOPBjhuaae0%3D&expires=2h&prisign=unkown&chkv=0&chkbd=0&chkpc=&size=c850_u580&quality=100)


