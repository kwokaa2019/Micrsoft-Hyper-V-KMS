KMS搭建環境

Micrsoft Windows 內建的 Hyper-V(Virtual Machine) 虛擬機器軟體

   
注意 : 防火牆要設定放行1688端口


使用方法：首先要在電腦Windows作業系統中打開命令提示符視窗，從工作列中的搜尋框打cmd ，然後按滑鼠右鍵選"以系統管理員身份執行" 就可以很簡單的打開命令提示字元視窗


你會用到的命令是slmgr，手動打

slmgr.vbs /upk                                    用於卸載當前電腦的密鑰

slmgr /ipk *****-*****-*****-*****-*****          安裝Windows產品的密鑰

slmgr /skms Kms.xxxxx.xx                          設置kms伺服器地址

slmgr /ato                                        激活命令，連接到kms伺服器進行windows激活

slmgr.vbs -xpr                                    這條命令 查看何時過期?

slmgr.vbs -dlv                                    條命令 查看詳細激活信



Micrsoft Office 2019 具體步驟：
打開任何一個Office軟件，例如打開Word，點擊“賬戶”⇢“更改產品密鑰”， 輸入XXXXX-XXXXX-XXXXX-XXXXX-XXXXX (產品的密鑰)，即可關閉Word。

首先要在電腦Windows作業系統中打開命令提示符視窗，從工作列中的搜尋框打cmd ，然後按滑鼠右鍵選"以系統管理員身份執行" 就可以很簡單的打開命令提示字元視窗

手動打下列的指令進入ospp.vbs的安裝目錄，

假如係 Microsoft Office 2019 專業增強版，手動打
cd C:\Program Files\Microsoft Office\Office16  （office 2019 x64位默认位置）

假如係 Microsoft Office 2016 專業增強版，手動打

32位office：
cd C:\Program Files (x86)\Microsoft Office\Office16

64位office：
cd C:\Program Files\Microsoft Office\Office16

手動打:cscript ospp.vbs /sethst:kms.xx.com            指定KMS的地址

最后，手動打:cscript ospp.vbs /act, 稍等片刻，即提示激活成功。
