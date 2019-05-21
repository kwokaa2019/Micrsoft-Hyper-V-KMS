KMS模擬器的搭建(Windows激活伺服器）

-----------------------------------------------------------------------------------------------
關於Hyper-V的啟用和設定說明如下：

1.在「開始」按滑鼠右鍵，選擇「程式和功能」。

https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/0.png

2.點選「開啟或關閉Windws功能」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/2.png

3.勾選「Hyper-V」，點選「確定」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/3.png

4.正在啟用Hyper-V。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/4.png

5.啟用完成，點選「立即重新啟動」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/5.png

6.重新開機以後，點選「開始」，在「Windows系統管理工具」選擇「Hyper-V管理員」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/6.png

7.開啟的Hyper-V管理員如下圖所示。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/7.png

8.選擇電腦，點選「虛擬交換器管理員」。必須建立虛擬交換器，安裝的虛擬機器才能連結到網際網路。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/8.png

9.點選「新增虛擬交換器」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/9.png

10.選擇「外部」，點選「建立虛擬交換器」。這個方式會使用實體網路的IP連結到網際網路，你的連線設定是DHCP，虛擬機器會自動取得IP；如果是使用固定IP，必須自己設定連線的IP，虛擬機器才能上網。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/10.png

11.建立虛擬交換器的視窗如下圖所示。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/11.png

12.輸入名稱〈自訂〉，選擇連線到網際網路的網卡。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/12.png

13.點選「套用」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/13.png

14.在套用網路的時候，網路可能會暫時不通，點選「是」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/14.png

15.已經建立外部網路，點選「新增虛擬交換器」。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/15.png

16.虛擬交換器建立完成以後，點選「新增」，選擇「虛擬機器」，開始建立虛擬機器。
https://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/21.png









https://github.com/lixuy/vlmcsd/releases

https://forums.mydigitallife.net/threads/emulated-kms-servers-on-non-windows-platforms.50234/

在Linux伺服器中搭建服務：

[root@neo ~]# wget https://github.com/lixuy/vlmcsd/releases/download/1112/Linux-intel-1112.zip # 下載伺服器客戶端
[root@neo src]# rm -rf Linux-intel-1112.zip
[root@neo ~]# mv Linux-intel-1112.zip /usr/local/src/
[root@neo ~]# ls
anaconda-ks.cfg iperf3.sh list.txt modu.txt passwd shadowsocksr
[root@neo ~]# cd /usr/local/src/
[root@neo src]# ls
Linux-intel-1112.zip
[root@neo src]# chmod +x /usr/local/src/kms-server/
[root@neo static]# pwd
/usr/local/src/kms-server/static
[root@neo static]# chmod +x vlmcsd-x64-musl-static
[root@neo static]# /usr/local/src/kms-server/static/vlmcsd-x64-musl-static # 啟動服務

# 開機自啟

[root@neo static]# echo "/usr/local/src/kms-server/static/vlmcsd-x64-musl-static -l /var/log/vlmcsd.log > /dev/null 2>&1" >> /etc/rc.d/rc.local
[root@neo static]# chmod +x /etc/rc.d/rc.local

# vlmcsd 使用的埠是 1688，如果埠沒有開放請務必開放。如果因為 SElinux 防護而導致 KMS 伺服器無法工作，可以使用以下命令關閉：

[root@neo ~]# sed -i 's/^SELINUX=.*/#&/;s/^SELINUXTYPE=.*/#&/;/SELINUX=.*/a SELINUX=disabled' /etc/selinux/config && /usr/sbin/setenforce 0

KMS模擬器和正版微軟KMS伺服器存在很多差別，KMS模擬器對客戶端的任意激活請求都會返回激活成功的響應。而正版只能對授權的部分產品返回激活成功的響應。

本文所使用的模擬客戶端為vlmcs

vlmcs-Windows-x64.exe -x 說明：查看可以激活的版本對應列表

vlmcs-Windows-x64.exe -v -l 3 itkmi.com

說明： -v輸出詳細信息 -l 3表示發送Windows Server 2019 Datacenter的激活請求 itkmi.com表示KMS伺服器的域名。

vlmcs客戶端的具體詳細命令解釋可以百度。

客戶端激活方法：

激活 Windows：

如果你的 Windows 是 VL 版本，那麼只要在管理員權限的 cmd 或者 powershell 中執行下面兩個命令就可以了。執行完第一個命令後要等彈出提示窗，期間電腦必須聯網。

slmgr /skms itkmi.com #itkmi.com可以替換為你VPS的ip地址或者域名
slmgr /ato #立即嘗試激活當前系統
slmgr /dlv #查看激活信息 或者獲取簡單的信息命令slmgr /xpr
如果不是 VL 版本的，那麼需要更換密鑰獲取你對應版本的 KEY，操作如下：
slmgr /upk #卸載當前系統的key,可以不管，直接添加。
運行以下命令查看系統版本：
wmic os get caption
在文末找到對應的 key，在管理員權限的 cmd 或者 powershell 中執行下面命令安裝 key：
slmgr /ipk xxxxx-xxxxx-xxxxx-xxxxx #xx這裡改為你系統版本對應密鑰
然後跟上面說的一樣設置 kms 伺服器地址，激活

激活 Office：

你安裝的 Office 必須是 VOL 版本，否則無法激活，可以從 msdn.itellyou.cn 上下載。Office 2016 是 Office16，Office 2013 是 Office15，以此類推。

在管理員權限的 cmd 或者 powershell 中執行下面命令，進入 32 位 Office 2016 的安裝目錄：
cd "C:\Program Files (x86)\Microsoft Office\Office16"
在管理員權限的 cmd 或者 powershell 中執行下面命令，進入 64 位 Office 2016 的安裝目錄：
cd "C:\Program Files\Microsoft Office\Office16"
在管理員權限的 cmd 或者 powershell 中執行下面兩個命令。執行完第一個命令後要等待命令行出現反饋提示，期間電腦必須聯網。
cscript ospp.vbs /sethst:itkmi.com #itkmi.com可以替換為你VPS的ip地址或者域名
cscript ospp.vbs /act
如果提示看到 successful 的字樣，那麼就是激活成功了，重新打開 office 就好。
Windows VL 密鑰對照表
Windows Server 2016

作業系統

KMS 激活序列號

Windows Server 2016 Datacenter
CB7KF-BWN84-R7R2Y-793K2-8XDDG
Windows Server 2016 Standard
WC2BQ-8NRM3-FDDYY-2BFGV-KHKQY
Windows Server 2016 Essentials
JCKRF-N37P4-C2D82-9YXRT-4M63B

Windows 10

作業系統

KMS 激活序列號

Windows 10 Professional：W269N-WFGWX-YVC9B-4J6C9-T83GX
Windows 10 Professional N：MH37W-N47XK-V7XM9-C7227-GCQG9
Windows 10 Enterprise：NPPR9-FWDCX-D2C8J-H872K-2YT43
Windows 10 Enterprise N：DPH2V-TTNVB-4X9Q3-TJR4H-KHJW4
Windows 10 Education：NW6C2-QMPVW-D7KKK-3GKT6-VCFB2
Windows 10 Education N：2WH4N-8QGBV-H22JP-CT43Q-MDWWJ
Windows 10 Enterprise 2015 LTSB：WNMTR-4C88C-JK8YV-HQ7T2-76DF9
Windows 10 Enterprise 2015 LTSB N：2F77B-TNFGY-69QQF-B8YKP-D69TJ
Windows 10 Enterprise 2016 LTSB：DCPHK-NFMTC-H88MJ-PFHPY-QJ4BJ
Windows 10 Enterprise 2016 LTSB N：QFFDN-GRT3P-VKWWX-X7T3R-8B639

Windows Server 2012 R2 和 Windows 8.1

作業系統

KMS 激活序列號

Windows 8.1 Professional：GCRJD-8NW9H-F2CDX-CCM8D-9D6T9
Windows 8.1 Professional N：HMCNV-VVBFX-7HMBH-CTY9B-B4FXY
Windows 8.1 Enterprise：MHF9N-XY6XB-WVXMC-BTDCT-MKKG7
Windows 8.1 Enterprise N：TT4HM-HN7YT-62K67-RGRQJ-JFFXW
Windows Server 2012 R2 Server Standard：D2N9P-3P6X9-2R39C-7RTCD-MDVJX
Windows Server 2012 R2 Datacenter：W3GGN-FT8W3-Y4M27-J84CP-Q3VJ9
Windows Server 2012 R2 Essentials：KNC87-3J2TX-XB4WP-VCPJV-M4FWM

Windows Server 2012 和 Windows 8

作業系統

KMS 激活序列號

Windows 8 Professional：NG4HW-VH26C-733KW-K6F98-J8CK4
Windows 8 Professional N：XCVCF-2NXM9-723PB-MHCB7-2RYQQ
Windows 8 Enterprise：32JNW-9KQ84-P47T8-D8GGY-CWCK7
Windows 8 Enterprise N：JMNMF-RHW7P-DMY6X-RF3DR-X2BQT
Windows Server 2012：BN3D2-R7TKB-3YPBD-8DRP2-27GG4
Windows Server 2012 N：8N2M2-HWPGY-7PGT9-HGDD8-GVGGY
Windows Server 2012 Single Language：2WN2H-YGCQR-KFX6K-CD6TF-84YXQ
Windows Server 2012 Country Specific：4K36P-JN4VD-GDC6V-KDT89-DYFKP
Windows Server 2012 Server Standard：XC9B7-NBPP2-83J2H-RHMBY-92BT4
Windows Server 2012 MultiPoint Standard：HM7DN-YVMH3-46JC3-XYTG7-CYQJJ
Windows Server 2012 MultiPoint Premium：XNH6W-2V9GX-RGJ4K-Y8X6F-QGJ2G
Windows Server 2012 Datacenter：48HP8-DN98B-MYWDG-T2DCC-8W83P

Windows 7 and Windows Server 2008 R2

作業系統

KMS 激活序列號

Windows 7 Professional：FJ82H-XT6CR-J8D7P-XQJJ2-GPDD4
Windows 7 Professional N：MRPKT-YTG23-K7D7T-X2JMM-QY7MG
Windows 7 Professional E：W82YF-2Q76Y-63HXB-FGJG9-GF7QX
Windows 7 Enterprise：33PXH-7Y6KF-2VJC9-XBBR8-HVTHH
Windows 7 Enterprise N：YDRBP-3D83W-TY26F-D46B2-XCKRJ
Windows 7 Enterprise E：C29WB-22CC8-VJ326-GHFJW-H9DH4
Windows Server 2008 R2 Web：6TPJF-RBVHG-WBW2R-86QPH-6RTM4
Windows Server 2008 R2 HPC edition：TT8MH-CG224-D3D7Q-498W2-9QCTX
Windows Server 2008 R2 Standard：YC6KT-GKW9T-YTKYR-T4X34-R7VHC
Windows Server 2008 R2 Enterprise：489J6-VHDMP-X63PK-3K798-CPX3Y
Windows Server 2008 R2 Datacenter：74YFP-3QFB3-KQT8W-PMXWJ-7M648
Windows Server 2008 R2 for Itanium-based Systems：GT63C-RJFQ3-4GMB6-BRFB9-CB83V

Windows Vista and Windows Server 2008

作業系統

KMS 激活序列號

Windows Vista Business：YFKBB-PQJJV-G996G-VWGXY-2V3X8
Windows Vista Business N：HMBQG-8H2RH-C77VX-27R82-VMQBT
Windows Vista Enterprise：VKK3X-68KWM-X2YGT-QR4M6-4BWMV
Windows Vista Enterprise N：VTC42-BM838-43QHV-84HX6-XJXKV
Windows Web Server 2008：WYR28-R7TFJ-3X2YQ-YCY4H-M249D
Windows Server 2008 Standard：TM24T-X9RMF-VWXK6-X8JC9-BFGM2
Windows Server 2008 Standard without Hyper-V：W7VD6-7JFBR-RX26B-YKQ3Y-6FFFJ
Windows Server 2008 Enterprise：YQGMW-MPWTJ-34KDK-48M3W-X4Q6V
Windows Server 2008 Enterprise without Hyper-V：39BXF-X8Q23-P2WWT-38T2F-G3FPG
Windows Server 2008 HPC：RCTX3-KWVHP-BR6TB-RB6DM-6X7HP
Windows Server 2008 Datacenter：7M67G-PC374-GR742-YH8V4-TCBY3
Windows Server 2008 Datacenter without Hyper-V：22XQ2-VRXRG-P8D42-K34TD-G3QQC
Windows Server 2008 for Itanium-Based Systems：4DWFP-JF3DJ-B7DTH-78FJB-PDRHK

相關文章
「SVN」centos環境下搭建SVN伺服器

2018-10-02

1.安裝SVN，有些linux發行版自帶SVN，可以用下面方法檢測是否安裝SVN。如果Subversion客戶端沒有安裝，命令將報告svn命令找不到的錯誤。
超詳細KMS激活伺服器windowsVista至windows10 office~2016激活

2018-06-23

什麼是KMS伺服器極其作用這裡不詳細說明，只因為太長；估計又可以寫一篇介紹文章了。實戰環境CentOS7系統win7專業版系統注意：win7專業版有很多版本，N、E、K什麼的，不要管這些，我們到時候選擇就選擇默認，沒有後綴的版本。
KMS 指令激活office

2017-10-09

前段時間總結了一個KMS指令激活 windows 的帖子，但是有人想要office 的所以就整理下kms激活的前提是你的系統是批量授權版本，即VL版，一般企業版都是VL版，專業版有零售和VL版，家庭版旗艦版OEM版等等那就肯定不能用kms激活。
關於windows手動激活的辦法

2017-12-16

事先說明，此辦法屬於KMS激活，只有180天。網上的激活工具大多數都有一些殘留，一般來說，改註冊表，留下一些奇奇怪怪的快捷方式等等，都是很常見的，所以我就找了手動激活的辦法。一、激活操作步驟及說明１.按Win+X ,再按A 以管理員打開cmd2.輸入 slmgr.
KMS伺服器搭建教程

2018-10-23

如在linux中，可以使用wget下載：wgethttps://github.com/Wind4/vlmcsd/releases/download/svn1111/binaries.tar.gz2、解壓我們下載的包，進入對應的目錄。
解決遠程連接mysql出現10038問題心得

2018-08-02

之前在虛擬機搭建lnmp環境，搭建好之後開發3306埠。現在公司就直接一個後端，所有後端工作要自己弄。
Linux運維入門到高級,曉桂科技分享

2018-04-09

1. Linux入門篇 31. 1 Linux作業系統簡介 31. 2 Linux發展趨勢 41. 3 Linux系統安裝 41. 4 Linux學習技巧 2. Linux系統篇 2.1 Linux系統管理 2.1. 1 Linux目錄初識 2.1. 2 Linux常用命令 2.
史上最完整的分布式框架之註冊中心zookeeper集群搭建教程

2018-11-03

zookeeper集群搭建一、單個zookeeper搭建1.準備工作a。這時候你會發現zk並沒有啟動成功，不要著急，你在啟動第二伺服器後再來查看狀態啟動第二個伺服器結果如下。
教你如何使用 Azure CLI 創建 Linux 虛擬機

2018-05-31

Azure CLI 用於從命令行或腳本創建和管理 Azure 資源。 本快速入門教程詳細介紹了如何使用 Azure CLI 部署運行 Ubuntu 伺服器的虛擬機。
三個腳本輕鬆搭建伺服器狀態在線監控

2017-06-03

Stat Hub是一個幫您收集並展示眾多伺服器狀態的服務，優點在於可以設置密碼，支持SSL安全，支持域名訪問。Workerman vmstat則是將vmstat命令的CPU使用率，內存使用，虛擬內存交換情況,IO讀寫情況直接動態地輸出到網頁，方便查看，很形象。
如何在Linux上搭建Git伺服器？

2018-01-31

[root@localhosthome]#chown-Rgit:gitgit/至此，便可以從客戶端連接Git伺服器了從本地push項目到Git伺服器上，首次連接會有下面這個提示，選擇yes即可$gitpushgit@192.168.178.128:/home/gitmaster。
Spring+SpringMVC+MyBatis+easyUI整合基礎篇（十）SVN搭建

2017-03-14

日常囉嗦前面一篇文章講了一下版本控制，但其實這一篇並沒有打算講細節的，感覺應該自己去動手弄一下，後來考慮了一下，版本控制真的挺重要的，如果自己實在搭建不好反而不去使用的話，真的有點可惜，當然這些話是針對初學者來說的，如果已經有這方面經驗的話，可以忽略。
企業自主搭建KMS授權激活伺服器

2018-04-05

網上亦有許多教程，考慮到大家對Windows更為熟悉，故引用一篇基於Windows系統的激活伺服器的搭建教程。
Android App 自動化測試：OPEN-STF環境搭建

2017-10-24

作者 | 舵哥地址 | http://blog.csdn.net/liduolp/article/details/78227923聲明 | 本文是 舵哥 原創，已獲授權發布，未經原作者允許請勿轉載前言背景1、 測試是檢驗程序質量的保證，而自動化測試是提高測試效率的最好方式。
黑客如何攻破一個網站？圖文講解全流程丨新手易懂，長文靜心看

2018-02-01

通過以上代碼我們發現該exp是C語言開發的，我們需要將他編譯成elf格式的,命令如下:gccroro.c–ororo接下來執行編譯好的exp./roro執行完成之後我們輸入id命令id我們發現我們已經是root權限了uid=0gid=0現在我們可以查看/etc/shadow文件c
linux基礎20課19，郵件伺服器 曉桂科技

2018-05-19

POP3=postofficeprotocol郵局協議，連接到MTA，讀取或者下載郵件.埠號110pop3s=pop3+ssl/tls埠995IMAPinternetmessageaccessprotocal網絡報文訪問協議能在下載郵件前先下載郵件頭信息，以供用戶選擇性的下載
Centos7.4/RHEL7.4系統下安裝VMware workstation14

2018-01-11

實驗環境：RHEL7.4/Centos7.4所需軟體包：VMware-Workstation-Full-14.0.0-6661328.x86_64.bundle 可以去VMware官網進行下載，必須註冊帳號。本文採用RHEL7.4作業系統，最小化安裝。建議安裝GUI。
ngrok反向代理

2018-02-14

假設使用域名test.test.com作為提供服務的域名，那麼先到dns解析方添加【A記錄】。編譯Ngrok下載代碼gitclonehttps://github.com/inconshreveable/ngrok。
centos7安裝gitlab

2017-11-30

一、安裝配置依賴項sudo yum install curl openssh-server openssh-clients postfix cronie -ysudo service postfix startsudo chkconfig postfix onsudo lokki
windows10 kms 指令激活 從此告別激活工具的各種捆綁

2017-09-30

方法：在win10桌面狀態下，右擊windows徽標或按快捷鍵windows+x，點擊命令提示符（管理員）用到的命令是slmgr，手動kms激活命令如下：slmgr.
Redis集群的簡單搭建案例

2018-01-19

測試我們選擇2台伺服器，分別為：192.168.1.237，192.168.1.238.每分伺服器有3個節點。
詳述 hosts 文件的作用及修改 hosts 文件的方法

2018-08-28

當用戶在瀏覽器中輸入一個需要登錄的網址時，系統會首先自動從hosts文件中尋找對應的IP位址，一旦找到，系統就會立即打開對應網頁，如果沒有找到，則系統會將網址提交DNS域名解析伺服器進行IP位址的解析。
個人云伺服器建設——（2)Ubuntu16.04安裝LAMP

2018-01-26

完成伺服器的基本配置後，如果要架設個人網站，還需要安裝一些基本的組件。架設網站通常可以使用PHP，JSP，ASP或者Python等，其中PHP最為常見，也是。
APPIUM自動化測試環境搭建實踐

2018-01-31

注意：node.js的安裝包的下載在官網有兩種版本，建議大家下載LTS版本，按照官方的意思，這個版本應該算是穩定版本。
win10 家庭版升級到專業版 如何成功激活系統

2017-09-06

小編新買的筆記本安裝的是win10家庭版，今天想裝一個破解版的AutoCAD2016,軟體安裝好了之後用Keygen激活時需要登錄計算機的管理員帳號，結果發現win10家庭版竟然沒有用戶組，只有專業版和企業版才有此功能。
使用小米路由器免費激活Win10和Office

2017-09-02

這次的內容也和之前的內容相關聯，建議大家查看一下：使用小米路由器搭建VPN伺服器(1)使用小米路由器搭建VPN伺服器(2)使用小米路由器通過DDNS連接VPN登陸小米路由器：MT工具箱---插件管理，找到KMS伺服器。點擊KMS伺服器，然後開始安裝，如果已經安裝了，這裡顯示卸載。
國慶節送你一份Linux系統運維面試題

2018-10-07

二、Linux命令及文件操作1.在/tmp/目錄下創建test.txt文件，內容為:Hello，World!

