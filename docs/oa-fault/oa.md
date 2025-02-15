[[toc]]

## 网页操作无反应

### IE浏览器内网按钮失效

**注意：此方案适用于非调用本地程序的按钮，如查看文档操作之类的按钮**

解决办法：
* 添加兼容性视图、可信任站点
* 在自定义级别处启用所有插件 
* 去掉启用保护模式前面的钩
* 上述操作执行一遍后，资源管理器关闭IE，并任务再重新进入

如若未果，则重置IE浏览器，并咨询其他同事该按钮是否需要内部开通权限

### IE浏览器内网查看文档按钮失效

解决办法：

* 了解查看原文（打开此文件）的程序
* 查看其他同事是否有无异常， 可了解到：
    * 网页代码是否存在错误（其他同事可以打开，排除）
    * 同事的级别权限是否一致（同级同事可以打开，排除）

若是存在相关联的多个打开此类文档的程序需要做兼容设置。

::: tip
**点击管理系统网页 ***模块*** 无反应：是否缺少前置依赖（flash、Java等）**
:::

## 网页站点无法访问

### 内部网页无法访问

经测试，可以进入ip地址的网页，也核对了DNS无误。

* 比对其他同事正常访问的该系统网页是否与其一致
* 权限问题：同级同事正常访问
* 上网认证软件的问题：版本、网络验证检测延迟

解决办法：更新上网认证软件版本

::: tip
**360、腾讯管家等之类安全软件杀毒暗中无提示的劫持网页，推测涉及有关破解软件、金钱操作、弹窗等之类脚本程序而被拦截了。**
:::

### 可以打开内部IP地址网站，但不能打开域名站点

解决办法：检查提供的DNS是否设置错误，拿相同的参照物始终对比不出来的

### 访问网站拒绝了连接请求 ERR_CONNECTION_REFUSED

::: tip
推测：  
有可能办公人员自认为是无关紧要的操作。而做出了选择加载或禁用项，导致该现象的异常。他也自然而然的认为，他什么操作也没做，也就想不起来之前做过误操作。
:::

* ipconfig /flushdns
* 将代理设置清除
* 访问模式http与https测试
* 添加该站的受信任站点，并加载控件

## 网页部分内容异常

### 网页部分内容无法显示

* 是否安装了证书、安装插件
* 是否支持该类型的浏览器
* 可信任站点设置与兼容视图

### IE网页flash异常

1. 以win7兼容模式强制安装IE版本的flash（ActiveX for IE）
2. 进入未加载的页面，调试管理加载项
3. 禁用再启用flash控件，并刷新页面

### 网页资料无法保存问题，显示请关闭正在处理的正文

* 操作界面并未发现相关程序打开文档
    * 排除打开本地文档未关闭
* 重启主机、浏览器，重新登录无效
    * 确定和个人账户有关

解决办法：重置账号信息，删除账号信息配置文件夹，重新生成即可，相当于初始化设置。

### 信款系统网页无法显示

影像控件缺失，安装影像控件

::: tip
询问报障人进入该站目的与站点相关作用，并根据此作用推测需要哪些额外的相关程序控件。
:::

### OA系统资料无法收藏另存为其他盘符路径

* 解决办法：将系统当前用户替换为Administrator
* 触发原因：另存为与本地系统账户操作有关

::: danger
替换 Administrator 账户时，请注意：
* 保存好之前用户名账户的个人资料（桌面、下载、文档、视频、音频）
* IE收藏的网页也会丢失，注意备份
:::

## 虚拟化平台系统报错与输入法异常

### Citrix Receiver虚拟化平台报错

尝试访问请求资源出错，请与管理员联系

解决办法：
点击用户手册（帮助文档），无法打开插件解决办法，下载并安装所有插件

### OA系统输入法异常

::: tip
很多人认为是进入OA的输入法异常，但OA这个词，真的太泛泛了，不过这个问题看起来很像输入法没有被本地系统识别的问题。

所以，有时我们必须确认是进入哪一个页面平台，才会出现的异常，并针对该页面平台进行问题查询。如网上查询或是查找厂商相关的帮助说明文档，是否提供解决方案。
::: 

解决办法：点击用户手册（帮助文档），找到关于输入法的问题链接，并根据提示操作


