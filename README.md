# m3u8_dl-js_GUI
A simple GUI for m3u8_dl-js...

## 公告(2018年12月25日)
* 由于本人看着这上古渣代码难受，估计程序不会继续更新了。
  
## 如何进行批量下载
#### 方法1
* 将m3u8链接保存为txt文件，每行一个链接。然后将txt文件拖入程序的地址栏，点击下载。程序会自动逐个识别文件名并下载。<br>
<div style="text-align: center;">
<img alt="" src="https://i.loli.net/2018/11/06/5be15568c7802.png" style="display: inline-block;" />
</div> <br>  

#### 方法2(推荐)
* 本地多个m3u8文件，保存在新建文件夹中，将整个文件夹拖入程序的地址栏，点击下载。程序会自动逐个识别文件名并下载。<br>
<div style="text-align: center;">
<img alt="" src="https://i.loli.net/2018/11/06/5be155e63fe88.png" style="display: inline-block;" />
</div><br>

#### 方法3
* 将m3u8链接下载为本地m3u8文件后再使用方法2下载。 ([辅助程序](https://github.com/nilaoda/m3u8_dl-js_GUI/releases/download/v0.4.1/m3u8.exe))

## IDM下载m3u8的几个小贴士
#### 为什么点击后没反应
* 将鼠标停留在按钮上数秒，按照提示操作  
`（若依旧无法下载，请往下看）`
#### 为什么要用IDM下载
* 稳定，基本不会出现花屏等现象
* 强大的队列功能
#### 建议使用IDM的情况

`(除非你特别了解你的操作，否则我都建议先尝试IDM)`
* 腾讯视频的m3u8
* 爱奇艺的m3u8
* 优酷4K的m3u8  `(1080P最好下载分段，m3u8存在问题 )`
* 搜狐的m3u8
* 芒果的m3u8
#### 优酷H264的补充说明  
<b>好久没下优酷，今天（2018年10月8日）发现优酷H264的m3u8也变成真正的TS分片了，可以直接idm下载。（不是全部视频都改了，有的还是分段）</b>  

<del>由于某些原因，优酷H264只建议下载**分段**而不是m3u8：   
可以把优酷网页端appinfo接口中的各个分段url改写为一个“m3u8”然后使用下载器下载并在设置中启用**更慢的合并方式**，或者直接处理m3u8将之变成**分段**形式的“m3u8”以减少不确定性([辅助程序](https://github.com/nilaoda/m3u8_dl-js_GUI/releases/download/v0.3.0/YK-m3u82clip.exe)) </del>
#### 哪些不能下载
* 不能嗅探https开头的m3u8
* 无法直接下载某些禁止二次请求的m3u8
* 无法下载AES-128或任何形式的加密HLS流
#### **奇技淫巧**
先将本地m3u8变成http形式的url，再次尝试调用IDM来下载那些本身无法被嗅探或服务器禁止二次访问的文件。

具体操作如下：
* [下载HFS。](http://www.rejetto.com/hfs/?f=dl)
* 下载url为m3u8文件并进行适当修改  
`（修改操作例如为m3u8文件手动添加Baseurl、加载外部key等. PS:事实上如果你点击过软件中的按钮，程序已经将m3u8文件下载到%temp%目录）`
* 在HFS打开时，默认的IP地址即为你的本地IP地址，你可以随意指定一个端口。`(菜单-限制-防止反复连接 取消勾选)`
* 此时将m3u8文件拖入左边的文件列表，然后右键刚拖入的m3u8，点击复制URL(Copy URL Address)。
* 返回m3u8_dl-js_GUI，粘贴url，再次尝试IDM下载。优酷4K、搜狐的m3u8已测试通过。  
`(如果你有公网地址，在获取外部IP后，可以把URL分享给其他人，让他们使用下载器或IDM下载或使用移动设备直接观看。必要时在路由器端做一下端口映射哦)`

手动批量下载：
* 先将url批量下载为m3u8文件 ([辅助程序](https://github.com/nilaoda/m3u8_dl-js_GUI/releases/download/v0.4.0/m3u8.exe))
* 将m3u8文件放在一个文件夹中并将此文件夹拖入HFS，选择虚拟目录模式，并复制该**文件夹**URL。
* 在Chrome等浏览器中打开复制好的URL，进入HFS的WEB管理界面。
* **顺次**点击(下载)所列出的m3u8文件，如无意外，IDM将自动嗅探并顺序编号，此时点击悬浮框，再点击下载全部即可以队列方式将TS文件添加至IDM。

自动化：
* 暂未公开的程序，敬请期待
#### 下载的TS文件如何批量转换为MP4封装
  使用 [MP4-Tags-Editor](https://github.com/nilaoda/MP4-Tags-Editor/releases)
#### 特别提醒
  在程序设置页的Headers将同样被用于请求URL，以应对某些特殊情况的IDM捕获。



## 关于“更慢的合并方式”的适用情况(#EXT-X-DISCONTINUITY引发)
* 优酷的**由大分段切片的**m3u8
* 搜狐、优酷、哔哩哔哩等的以**H264分段**形式组成的“m3u8”
