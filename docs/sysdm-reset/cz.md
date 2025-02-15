[[toc]]

## GHOST说明

* GHOST备份的系统只适用当前备份系统的机型，不同的主板不通用
* 装载GHO的多个主机的SID一致，因此不适用于系统加域的网络环境
    * 因此不少企业采用WIM格式封装的镜像
* 推荐使用GUI备份还原工具，功能使用面板清晰直观
    * 分区（如C盘）或硬盘备份还原
    * 分区或硬盘克隆
    * 分区或硬盘镜像制作

## WIM封装

### 进入封装和部署操作系统界面

重装系统进入系统区域选择界面`ctrl` + `shift` +`f3`进入封装和部署操作系统界面，正常安装必要的预装软件，如：office、pdf等。

::: tip
安装完预装软件后，也可使用`taskschd.msc`任务计划程序，进行软件及脚本的自启动定制。
:::

`系统准备工具`勾选`通用`，通用模式的好处：

* 只保留win10自带的通用系统硬件支持
* PC各品牌机型的特有软件或驱动将被清除
* 重置并生成新的SID，系统加域不会造成冲突

### 捕获wim镜像

* 重启进入PE，并打开GImageX软件
* 获来源选择系统所在盘符（C盘），并选择新镜像的保存位置
* 点击`新建映像`按钮，即可捕获系统镜像

等待生成wim镜像完成后，对系统盘格式化，使用windows安装器安装wim即可。

:::danger
* 大多数公司对数据的完整性极其严格，务必联系到机主确认备份资料，再进行装机。
* 在主机上找不到机主的所属文件，暂时搁置，不能轻易重装系统
    * 造成的数据丢失，装机作业员负全责
* 禁止使用PE破解密码，这会对内部加密文档资料造成不可逆的破坏    
* 在不知晓用户的密码情况下，用PE记好用户的IP、DNS、计算机名、上网认证账户
* 若是通过注册表找到IP为自动获取的，需联系后台网络管理人员查询 
:::

::: tip
PE查看ip地址方法：
* 选中`HKEY_LOCAL_MACHINE`，点击`文件`选择`加载配置单元`
* 打开 `C:\Windows\System32\config\SYSTEM`文件，命名如：test
* SYSTEM\ControlSet001\Services\Tcpip\Parameters\Interfaces
:::

## 重装常见问题

::: tip
重装系统时，也要记得将BIOS的安全模式关闭
:::

### 0xc00001 蓝屏 Windows多次启动失败，请尝试介质启动

解决办法：MBR直装系统（针对前系统WIN7），引导修复

### 显示黑屏，但左上角边缘处闪烁短横杠

* 注意分区格式
* 注意启动项
* 重建引导

WIN10 MBR转GPT过程：

* 专业版分区工具（**免费版调整格式会格式化硬盘**）调整硬盘格式
* 然后从分区抽出部分内存，做成EFI格式分区，引导修复即可

### an operating system wasn’t found

两种情况：
* 引导问题：重建引导记录，修复引导记录即可
* 硬盘问题：硬盘线没接好，或硬盘坏了

### 开机出现invalid partition table

一些旧主板不支持UEFI当然也就不支持GPT；GPT可以装GHO，前提需要UEFI启动，注意引导修复。

## 电脑组装

### 主板、显卡、CPU

::: tip
主板型号：
* H定位低端，如H81主板（主板上面也有写明）插槽比较少，可扩展性差。
    * 适合DIY入门电脑玩家，适用于进行视频、小游戏等娱乐活动
* B定位中、高端，接口丰富，售价比H系列主板高些，定位消费人群为商用办公人群
* Z定位高端玩家，做工用料较好，可超频，是大型游戏玩家的必备
:::

主板接入高低版本显卡基本没问题，插槽基本一样，但实际性能取决于CPU或显卡的最低短板；不同主板支持CPU协议也不一样：
* 服务器版本CPU需要处理多个并发数据，线程多，但单个线程频率低
* 游戏绝大多数是单线程，游戏运行速度取决于CPU单线程最高频率

CPU安装将散热硅胶膏涂抹均匀到CPU上，并将其涂抹均匀，在其上方接入风扇。

提示：
* 散热硅胶膏用一个注射管装入挺方便的
* 风扇散热片材质，铝制只有铜的百分之五十左右散热性能

### 内存条与硬盘

::: tip
* 更换高频率，低时延的内存条，组建双通道，配上固态硬盘都是为了主机运行的更快更流畅
* 硬盘属于精密设备，硬盘是存储数据资料的东西，果断拒绝翻新硬盘，以免日后维护难度增加
:::

#### 内存条

想要加一条内存条，并组建双通道，必须要知道自己电脑用的是哪一代的内存条与其内存大小

* [UEFIblog-内存系列一：快速读懂内存条标签](https://zhuanlan.zhihu.com/p/26255460)
* [百度经验-如何区分DDR1 DDR2 DDR3内存条？](https://jingyan.baidu.com/article/f3ad7d0fe3df0909c3345b97.html)
* [hack520-插两根内存就是双通道了？](https://www.hack520.com/701.html)

`公式：内存频率=内存基频×倍频`

例如某内存条信息：4GB 2Rx8 PC3-10600S-9-10-F2，它的基频为10600内存频率/(2x8)倍频≈666MHZ


#### 硬盘

::: warning
[硬盘磁头](https://www.cnblogs.com/jswang/p/9071847.html)指的是硬盘内部的转轴指针，而不是插入卡槽的针脚
:::

硬盘是十分精密的存储设备，进行读写操作时，一旦发生较大的震动，就容易造成磁头与资料区相撞击，导致盘片资料区损坏或刮伤磁盘，丢失硬盘内所储存的文件数据。因此，在工作时或关机后主轴电机尚未停顿之前，千万不要搬动。

如果用软件检测出硬盘有问题（健康状态为黄色的警告），直接盘对盘对拷，避免以后硬盘坏死造成数据的丢失；若是听到硬盘像裁缝机一样的声音，说明硬盘有问题，需要更换。

灰尘对硬盘的危害是非常严重的，一旦灰尘接触到硬盘读写的磁头，就会产生无法修复的物理坏道，导致硬盘完全坏死。

硬盘翻新的相关阅读链接推荐：

* [搜狐新闻-再也不敢买了 揭秘固态硬盘翻新清零](https://www.sohu.com/a/252177137_615464)
* [新浪博客-希捷翻新硬盘揭秘](http://blog.sina.com.cn/s/blog_678e9e910100ied7.html)
* [百度贴吧-深度慢扒硬盘翻新清零的秘密](https://tieba.baidu.com/p/5080574289)
* [zol回答-翻新硬盘和新的在用的时候有什么不同](http://ask.zol.com.cn/x/6118821.html)

### 无盘系统

无盘系统可以理解为虚拟桌面，将系统镜像挂载到服务器上，然后服务器根据IP下发到各个主机上，类似于PE加载模式。一些网吧自己组装一台性价比很高的电脑，以此作为批量购买的标配，然后结合使用无盘系统节省了大量主机的维护成本。

注意：后台服务器配置要够强，硬盘要好，网速也要快，才能让用户感觉是本地硬盘启动一样。

相关导读

* [百度知道-家里电脑怎么做无盘系统](https://zhidao.baidu.com/question/5154938.html)
* [51cto-无盘的搭建](https://blog.51cto.com/loveworld/1004838)
* [天下网吧-免费无广告的网咖专用云无盘安装图文教程](http://www.txwb.com/wptx/jc/385258.html)
* [锐起网吧无盘视频教程](http://www.richtech.cn/video.html)


### 网站与软件推荐
* 硬件测试信息：[AIDA64](https://www.aida64.com/)
* CPU、显卡性能评价：[3DMARK网站](https://www.3dmark.com/zh-hans/)
* 驱动及封装：[系统总裁](https://www.sysceo.com/)
* PE工具箱：[微PE工具箱](http://www.wepe.com.cn/)