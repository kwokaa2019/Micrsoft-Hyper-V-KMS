KMS搭建環境
1. Micrsoft Windwos 10 ，Micrsoft Windwos Server 2016、Micrsoft Windwos Server 2019
   
   Micrsoft Windwos 內建的 Hyper-V(Virtual Machine) 虛擬機器軟體〈Windwos 家用版無此功能〉
   
  
2. 防火牆設定放行1688端口


1.在「開始」按滑鼠右鍵，選擇「程式和功能」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/0.png

2.點選「開啟或關閉Windws功能」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/2.png

3.勾選「Hyper-V」，點選「確定」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/3.png

4.正在啟用Hyper-V。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/4.png

5.啟用完成，點選「立即重新啟動」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/5.png

6.重新開機以後，點選「開始」，在「Windows系統管理工具」選擇「Hyper-V管理員」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/6.png

7.開啟的Hyper-V管理員如下圖所示。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/7.png

8.選擇電腦，點選「虛擬交換器管理員」。必須建立虛擬交換器，安裝的虛擬機器才能連結到網際網路。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/8.png

9.點選「新增虛擬交換器」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/9.png

10.選擇「外部」，點選「建立虛擬交換器」。這個方式會使用實體網路的IP連結到網際網路，你的連線設定是DHCP，虛擬機器會自動取得IP；如果是使用固定IP，必須自己設定連線的IP，虛擬機器才能上網。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/10.png

11.建立虛擬交換器的視窗如下圖所示。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/11.png

12.輸入名稱〈自訂〉，選擇連線到網際網路的網卡。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/12.png

13.點選「套用」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/13.png

14.在套用網路的時候，網路可能會暫時不通，點選「是」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/14.png

15.已經建立外部網路，點選「新增虛擬交換器」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/15.png

16.選擇「內部」，點選「建立虛擬交換器」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/16.png

17.輸入名稱，點選「套用」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/17.png

18.已經建立內部網路，點選「新增虛擬交換器」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/18.png

19.選擇「私人」，點選「建立虛擬交換器」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/19.png

20.輸入名稱，點選「確定」。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/20.png

21.虛擬交換器建立完成以後，點選「新增」，選擇「虛擬機器」，開始建立虛擬機器。

http://0.blog.xuite.net/0/9/c/9/17510967/blog_815913/txt/459512721/21.png

