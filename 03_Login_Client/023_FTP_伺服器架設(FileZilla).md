# FTP 伺服器架設(FileZilla)

# 天堂私服 | FTP 伺服器架設(FileZilla)

    
    
      📑 目錄
      

1. [環境說明](#環境說明)
2. [Windows 7 更新](#Windows-7-更新)
3. [下載 FileZilla](#下載-FileZilla)
4. [安裝 FileZilla](#安裝-FileZilla)
5. [啟動 FileZilla 伺服器](#啟動-FileZilla-伺服器)
6. [建立 FTP 專用資料夾](#建立-FTP-專用資料夾)
7. [新增 FTP 使用者帳戶/設定專用資料夾](#新增-FTP-使用者帳戶-設定專用資料夾)
8. [測試 FTP 連線是否正常](#測試-FTP-連線是否正常)
9. [FTP 伺服器 Log/連線](#FTP-伺服器-Log-連線)
10. [限制上/下載速度](#限制上-下載速度)
11. [結語](#結語)
12. [免責聲明](#免責聲明)

    
    
    

## 環境說明

此處使用`Oracle VM VirtualBox`虛擬機軟體，下載安裝了一個純淨的`Windows 7 x64 旗艦版`。
![天堂私服 - 圖 1 (01)](../images/private-lineage/chapter4/01.png)
如果需要安裝虛擬機，可以參考此篇文章[VirtualBox Windows 7 安裝](../01_Getting_Started/003_VirtualBox_Windows_7_安裝.md)。

## Windows 7 更新

* 更新

  * 最少更新：<快速，建議>

    * [KB2533623 - x64](http://web.archive.org/web/20200203192654/http://download.microsoft.com/download/f/1/0/f106e158-89a1-41e3-a9b5-32feb2a99a0b/windows6.1-kb2533623-x64.msu)

  * 完整更新：<費時，不建議>

    * [Windows 7 SP1 Update Package 微軟更新修正包 (2020.01月份)](https://wmos.info/archives/18340)

  * 開啟 Windows Update：<已關閉>

    * [Windows 7 已於 2020 年 1 月 14 日終止支援](https://support.microsoft.com/zh-tw/windows/windows-7-%E5%B7%B2%E6%96%BC-2020-%E5%B9%B4-1-%E6%9C%88-14-%E6%97%A5%E7%B5%82%E6%AD%A2%E6%94%AF%E6%8F%B4-b75d4580-2cc7-895a-2c9c-1466d9a53962)

> 註：KB2533623 是一定要安裝的，因為後面再安裝其他 FileZilla 軟體時，才不會發生無法加載TLS庫的問題。
> 注：安裝完更新後，請務必重新啟動虛擬機。

## 下載 FileZilla

首先，我們進入下載 FileZilla 的網站：[連結](https://filezilla-project.org/)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​​​​‌‌​​​​​​‌‌​‌​​​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​‌‌

* 點擊`Download FileZilla Server`。
![天堂私服 - 圖 2 (01)](../images/private-lineage/chapter23/01.png)

* 點擊`Download FileZilla Server`，便會開始下載；這以 Microsoft Windows 示範。
![天堂私服 - 圖 3 (02)](../images/private-lineage/chapter23/02.png)

## 安裝 FileZilla

此處安裝的版本為`FileZilla_Server-0_9_60_2.exe`來做安裝示範。
**<font color="gray"><2021-08-04當時下載的最新版></font>**

* 滑鼠左鍵雙擊`FileZilla_Server-0_9_60_2.exe`檔案。

* 跳出安全提示`您是否要允許下列成是變更這部電腦？`請點擊`是`。
![天堂私服 - 圖 4 (03)](../images/private-lineage/chapter23/03.png)

* 請繼續點擊`I Agree`。
![天堂私服 - 圖 5 (04)](../images/private-lineage/chapter23/04.png)

* 請繼續點擊`Next`。
![天堂私服 - 圖 6 (05)](../images/private-lineage/chapter23/05.png)

* 可以自行選擇安裝位置。

* 請繼續點擊`Next`。
![天堂私服 - 圖 7 (06)](../images/private-lineage/chapter23/06.png)

* 此步驟是詢問是否要讓`FTP伺服器`在電腦開機時自動啟動，請點選`Install as service, started with Windows (default)`請繼續點擊`Next`。

> 註：這樣`FTP伺服器`便會自動被安裝成系統的`Service`，每次開機後便會自動再背景中啟動並執行`FTP伺服器`的功能。
> ![天堂私服 - 圖 8 (07)](../images/private-lineage/chapter23/07.png)

* 此步驟是詢問是否要讓`FTP伺服器管理介面`在什麼情況下開啟，

  * `Start if user log on, apply all users (default)`所有使用者都會開啟。

  * `Start if user long on, apply only to current user`此安裝的使用者才會開啟。

  * `Start manually`手動啟動。

* `Start Interface after setup completes`勾選表示安裝完成後，開啟`FTP伺服器管理介面`。

* 依照自己需求做選擇，請繼續點擊`Install`。
![天堂私服 - 圖 9 (08)](../images/private-lineage/chapter23/08.png)

* 安裝進度條…請等待安裝完畢至下一流程。
![天堂私服 - 圖 10 (09)](../images/private-lineage/chapter23/09.png)

* 恭喜您已經安裝完畢，請點擊`Close`結束安裝程序。
![天堂私服 - 圖 11 (10)](../images/private-lineage/chapter23/10.png)

* 如果前面有勾選`Start Interface after setup completes`，會自動開啟`FTP伺服器管理介面`。
![天堂私服 - 圖 12 (11)](../images/private-lineage/chapter23/11.png)

## 啟動 FileZilla 伺服器

* 啟動`FTP伺服器管理介面`時，會開啟`Connect to Server`視窗
![天堂私服 - 圖 13 (11)](../images/private-lineage/chapter23/11.png)

* `Host`預設`localhost`。

* `port`設定為安裝時的`post`預設`14147`。

* 在`password`欄位中輸入管理員的密碼<自定>。

* 勾選`Always connect to this server`，儲存以上設定，之後開啟不會再次詢問。

* 再按下`Connect`，設定好管理員密碼並自動連上`FTP伺服器`。
![天堂私服 - 圖 14 (12)](../images/private-lineage/chapter23/12.png)

* 登入成功後，可見`Logged on`
![天堂私服 - 圖 15 (13)](../images/private-lineage/chapter23/13.png)

```plain
FileZilla Server 0.9.60 beta
Copyright 2001-2016 by Tim Kosse (tim.kosse@filezilla-project.org)
https://filezilla-project.org/
Connecting to server localhost:14147...
Connected, waiting for authentication
Logged on
You appear to be behind a NAT router. Please configure the passive mode settings and forward a range of ports in your router.
Warning: FTP over TLS is not enabled, users cannot securely log in.
```

* 紅色字體警告：

  * 您似乎在 NAT 路由器後面。 請配置被動模式設置並轉發路由器中的一系列端口。

    * 此是在說明需要使用[虛擬服務器和通訊埠轉發](../02_Networking/015_虛擬服務器和通訊埠轉發.md)方式針對`21`port設定

  * 警告：FTP over TLS 未啟用，用戶無法安全登入。

    * 此是在說明無法使用 SSL/TLS 連線方式做登入。

> 註：此處不會針對SSL/TSL做教學設置。​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​​​​‌‌​​​​​​‌‌​‌​​​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​‌‌

## 建立 FTP 專用資料夾

此處只是個示範，可根據自己需求去建立。
說明：建立一個專門給FTP伺服器所使用的資料夾，資料夾內再根據FTP使用者的需求去建立對應的資料夾，方便區分和管理。

* 於`C磁區`建立`FTP`名的資料夾。
![天堂私服 - 圖 16 (14)](../images/private-lineage/chapter23/14.png)

* 於`FTP`資料夾內建立針對使用者名的資料夾。

* 此處範例為`LineageServerList`。<天堂模擬器清單>
![天堂私服 - 圖 17 (15)](../images/private-lineage/chapter23/15.png)

* 建議在`LineageServerList`目錄內，先放一個`test.txt`檔案。

該`LineageServerList`目錄，將會給`Lineage`FTP使用者做使用。

## 新增 FTP 使用者帳戶/設定專用資料夾

* 啟動`FTP伺服器管理介面`，並點擊新增使用者圖示![天堂私服 - 圖 18 (16)](../images/private-lineage/chapter23/16.png)。
![天堂私服 - 圖 19 (17)](../images/private-lineage/chapter23/17.png)

* 開啟`Users`視窗，並點擊`Add`。
![天堂私服 - 圖 20 (18)](../images/private-lineage/chapter23/18.png)

* 開啟`Add User account`視窗，輸入要建立的使用者帳號，並點擊`OK`。
![天堂私服 - 圖 21 (19)](../images/private-lineage/chapter23/19.png)

* 建立成供使用者。
![天堂私服 - 圖 22 (20)](../images/private-lineage/chapter23/20.png)

* 點選右邊「Users」中的使用者名稱`Lineage`，然後再勾選`Password`，然後在`Password`右邊輸入該使用者的密碼，並點擊`OK`。
![天堂私服 - 圖 23 (21)](../images/private-lineage/chapter23/21.png)

* 會彈出警告`You need to share at least one directory and set it as home directory.`，請點擊`確定`。

> 註：這是在說必需配置一個目錄給這位使用者做使用。
> ![天堂私服 - 圖 24 (22)](../images/private-lineage/chapter23/22.png)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​​​​‌‌​​​​​​‌‌​‌​​​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​‌‌

* 請點擊`Add`。
![天堂私服 - 圖 25 (23)](../images/private-lineage/chapter23/23.png)

* 瀏覽資料夾選擇剛剛建立的`C:\FTP\LineageServerList`資料夾，並點擊`確定`。
![天堂私服 - 圖 26 (24)](../images/private-lineage/chapter23/24.png)

* 設定此此使用者針對此目錄的權限；這邊預設勾選即可。

  * Files → Read：可下載檔案。

  * Files → Write：可上傳檔案。

  * Files → Delete：可刪除檔案。

  * Directories → Creat：可新增子資料夾。

  * Directories → Delete：可刪除子資料夾。

  * Directories → List：可列出資料夾中的檔案。

  * Directories → +Subdirs：可列出資料夾中的子資料夾。

* 最後點擊`OK`及新增完成。
![天堂私服 - 圖 27 (25)](../images/private-lineage/chapter23/25.png)

## 測試 FTP 連線是否正常

測試之前，建議先參考[防火牆輸入輸出規則](../02_Networking/014_防火牆輸入輸出規則.md)，把`所有port`設定TCP/UDP兩個的輸入規則，或是直接將防火強先行關閉也行。

> 註：另外可以[參考](https://www.efroip.com/efroip/publish_page/1190/?cid=40461)針對程式做設定。

1. 使用`Internet Explorer`測試，URL = `ftp://{User}:{Password}@{IP Address}`

```plain
ftp://Lineage:123456789@127.0.0.1/
```

![天堂私服 - 圖 28 (26)](../images/private-lineage/chapter23/26.png)

> 註：Google Chrome 從 88 版本開始，已不再支援 ftp：// 開頭網址。​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​​​​‌‌​​​​​​‌‌​‌​​​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​‌‌

1. 使用`FileZilla Client`，模擬外部網路連線測試。

![天堂私服 - 圖 29 (27)](../images/private-lineage/chapter23/27.png)

> 註：此處使用另一台電腦做連線測試，而`FPT 伺服器`內部IP為`192.168.1.105`，固`IP 位址`填寫`192.168.1.105`。
> 註：如果連線出現Server端出現`425 Can't open data connection for transfer of "/"`錯誤，請設定`主動模式`。[參考](https://www.cpjh.ntpc.edu.tw/p/404-1000-785.php)

## FTP 伺服器 Log/連線

* `FTP 伺服器`端，可以看到有哪些`IP`使用此帳號連入中，右鍵可以對其做一些操作。

  * Kick <踢除>

  * Ban user’s IP address <將IP加入黑名單>
![天堂私服 - 圖 30 (28)](../images/private-lineage/chapter23/28.png)

## 限制上/下載速度

* 點擊新增使用者圖示![天堂私服 - 圖 31 (16)](../images/private-lineage/chapter23/16.png)。

* 左邊選單切換到`Speed Limits`功能頁面。

* 右邊`Users`點選你要設定的使用者帳戶後，再點選中間的「Constant Speed Limit of」，並輸入該使用者的速度上限，如「50」kB/s。
![天堂私服 - 圖 32 (29)](../images/private-lineage/chapter23/29.png)

## 結語

最後建議回顧一下首章[天堂私服 | 天堂私服架設教學](/private-lineage-20210712-private-lineage-0/#教學章節)，了解其章節目錄。​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌‌​​​​​‌‌​​​​​​‌‌​‌​​​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​‌‌

## 免責聲明

* 本部落格文章中皆<font color="red"><u>**不提供**</u></font>任何所謂的遊戲「主程式」、「模擬器」、「登入器」…等等相關程式的下載點。

* 本部落格文章中所見之遊戲主程式和服務器端程序均來自網路發佈，<font color="red"><u>版本歸**原作者**</u>所有</font>。

* 本部落格文章為研究SQL資料庫與修改JAVA語法使用，<font color="red">並<u>**非商業用途**</u>，亦<u>**無做營運事實等任何一切商業行為**</u>。</font>

* 本部落格文章內容是為研究學習設計思想和原理為目的，<font color="red"><u>**絕沒有故意侵權或惡意抄襲、篡改其他遊戲內容**</u></font>！

> 註：以上參考了
> [FileZilla](https://filezilla-project.org/)
> [重灌狂人 - [免費] 用 FileZilla Server v0.9.60.2 架設 FTP 站 （FTP伺服器）](https://briian.com/4618/)
> [Tse先生 - File Zilla server安装完报错could not load TLS libraries. aborting start of administration interface](https://www.cnblogs.com/Sungeek/p/11887625.html)
> [FileZilla Server設定Windows的防火牆](https://www.efroip.com/efroip/publish_page/1190/?cid=40461)

---

- **原文連結**：[J.J.'s Blogs - FTP 伺服器架設(FileZilla)](https://morosedog.gitlab.io/private-lineage-20210804-private-lineage-23/)
