# 資料庫 MySQL 5.6.25 的安裝

# 天堂私服 | 資料庫 MySQL 5.6.25 的安裝

    
    
      📑 目錄
      

1. [環境說明](#環境說明)
2. [檢查](#檢查)
3. [下載 MySQL](#下載-MySQL)
4. [安裝 MySQL](#安裝-MySQL)
5. [結語](#結語)
6. [免責聲明](#免責聲明)

    
    
    

## 環境說明

此處使用`Oracle VM VirtualBox`虛擬機軟體，下載安裝了一個純淨的`Windows 7 x64 旗艦版`。
![天堂私服 - 圖 1 (01)](../images/private-lineage/chapter4/01.png)
如果需要安裝虛擬機，可以參考此篇文章[VirtualBox Windows 7 安裝](./003_VirtualBox_Windows_7_安裝.md)。

## 檢查

1. 是否電腦已經有安裝 MySQL？

* 可以至`控制台\所有控制台項目\程式和功能`看是否有`MySQL Server`這個關鍵字的檢查。

![天堂私服 - 圖 2 (01)](../images/private-lineage/chapter7/01.png)

> 註：此處安裝的版本是 MySQL 5.6.25 版本。​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌‌​​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​‌‌‌

1. 是否已經安裝了 `Microsoft .NET Framework 4.0` 以上的版本？

* 可以至`控制台\所有控制台項目\程式和功能`看是否有`Microsoft .NET Framework`這個關鍵字的檢查。

![天堂私服 - 圖 3 (02)](../images/private-lineage/chapter7/02.png)

如果沒有，可以參考此篇文章[安裝 .NET Framework](./003_VirtualBox_Windows_7_安裝.md)。

## 下載 MySQL

首先，我們進入下載 MySQL 的網站：[連結](https://downloads.mysql.com/archives/installer/)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌‌​​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​‌‌‌

* 進入下載頁面

* 選擇 MySQL 版本，這裡選擇 5.6.25。

* 選擇你的作業系統，這以 Microsoft Windows 示範
![天堂私服 - 圖 4 (08)](../images/private-lineage/chapter7/08.png)

* 注意這裡有分成 web 版跟離線安裝版，選擇離線安裝即可，選擇後，便會開始下載。
![天堂私服 - 圖 5 (09)](../images/private-lineage/chapter7/09.png)

## 安裝 MySQL

此處安裝的版本為 `MySQL 5.6.25`來做安裝示範。
<font color="gray"><*由於天堂模擬器使用5.x.x的連線包，故無法使用太新的版本*></font>

* 滑鼠左鍵雙擊`mysql-installer-community-5.6.25.0.exe`檔案。

* 如果跳出如下提示，就表示電腦沒有安裝`.NET Framework`，或是版本不夠高。請參考[安裝 .NET Framework](./003_VirtualBox_Windows_7_安裝.md)。

```plain
This application requires .NET Framework 4.0. Please
install the .NET Framework then ren this installer again.
For more information, please see 
http://go.microsoft.com/fwlink/?LinkId=181012
```

![天堂私服 - 圖 6 (10)](../images/private-lineage/chapter7/10.png)

> 註：如果沒有跳出提示，請忽略繼續往下即可。

* 跳出安全提示`您是否要允許下列成是變更這部電腦？`請點擊`是`。
![天堂私服 - 圖 7 (11)](../images/private-lineage/chapter7/11.png)

* 跳出安全提示`您是否要允許下列成是變更這部電腦？`請點擊`是`。
![天堂私服 - 圖 8 (12)](../images/private-lineage/chapter7/12.png)

* 授權條款，勾選`I accept the license terms`，再點擊`Next`。
![天堂私服 - 圖 9 (13)](../images/private-lineage/chapter7/13.png)

* 選擇`Developer Default`，開發者默認安裝即可，請繼續點擊`Next`。
![天堂私服 - 圖 10 (14)](../images/private-lineage/chapter7/14.png)

* 此處會檢查一些必要的安裝，請繼續點擊`Execute`。
![天堂私服 - 圖 11 (15)](../images/private-lineage/chapter7/15.png)

* 此處會需要安裝`Microsoft Visual C++`

* 勾選`I agree to the license terms and conditions`，再點擊`Install`。
![天堂私服 - 圖 12 (16)](../images/private-lineage/chapter7/16.png)

* 安裝完畢，再點擊`Close`。
![天堂私服 - 圖 13 (17)](../images/private-lineage/chapter7/17.png)

* 此處會需要安裝`Microsoft Visual Studio Tools for Office Runtime 2010`

* 勾選`I have read and accept the license terms.`，再點擊`Install`。
![天堂私服 - 圖 14 (18)](../images/private-lineage/chapter7/18.png)

* 安裝完畢，再點擊`Finish`。
![天堂私服 - 圖 15 (19)](../images/private-lineage/chapter7/19.png)

* 會跳出`Microsoft Visual C++` Modify Setup，再點擊`repair`。
![天堂私服 - 圖 16 (20)](../images/private-lineage/chapter7/20.png)

* 再點擊`Close`。
![天堂私服 - 圖 17 (21)](../images/private-lineage/chapter7/21.png)

* 部分必要安裝軟體並未被勾選，這並不影響後續安裝，請繼續點擊`Next`。
![天堂私服 - 圖 18 (22)](../images/private-lineage/chapter7/22.png)

* 跳出以下警示，這並不影響後續安裝，請點擊`Yes`。

```plain
You still have failing product requirements. If you proceed, those
products will not be installed or upgraded. Is this ok?
```

![天堂私服 - 圖 19 (23)](../images/private-lineage/chapter7/23.png)

* 此處列出會安裝的軟體和他們目前的狀態，請繼續點擊`Execute`。
![天堂私服 - 圖 20 (24)](../images/private-lineage/chapter7/24.png)

* 安裝進度條…請等待安裝完畢至下一流程。
![天堂私服 - 圖 21 (25)](../images/private-lineage/chapter7/25.png)

* 安裝完畢，別急，後續要做些設定，請繼續點擊`Next`。
![天堂私服 - 圖 22 (26)](../images/private-lineage/chapter7/26.png)

* 請繼續點擊`Next`。
![天堂私服 - 圖 23 (27)](../images/private-lineage/chapter7/27.png)

* 預設的 TCP/IP，Port為`3306`，請繼續點擊`Next`。
![天堂私服 - 圖 24 (28)](../images/private-lineage/chapter7/28.png)

* 設定密碼，此處範例是設定`root`會發現這密碼被檢測為`弱`，請繼續點擊`Next`。

> 註：此密碼請務必記住，後面在做資料庫連線的時候都會需要輸入該密碼。
> ![天堂私服 - 圖 25 (29)](../images/private-lineage/chapter7/29.png)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌‌​​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​‌‌‌

* 預設 Windows 啟動時的 Service 名稱設定，請繼續點擊``Next`。
![天堂私服 - 圖 26 (30)](../images/private-lineage/chapter7/30.png)

* 確認一下`Apply Server Configuration`，請繼續點擊`Execute`。
![天堂私服 - 圖 27 (31)](../images/private-lineage/chapter7/31.png)

* 安裝進度條…請等待安裝完畢至下一流程。
![天堂私服 - 圖 28 (32)](../images/private-lineage/chapter7/32.png)

* 設定完成請繼續點擊`Finish`。
![天堂私服 - 圖 29 (33)](../images/private-lineage/chapter7/33.png)

* 接續設定，請繼續點擊`Next`。
![天堂私服 - 圖 30 (34)](../images/private-lineage/chapter7/34.png)

* 輸入設定的密碼`root`，點擊`Check`檢查，可見`Connection succesful.`，請繼續點擊`Next`。
![天堂私服 - 圖 31 (35)](../images/private-lineage/chapter7/35.png)

* 確認一下`Apply Server Configuration`，請繼續點擊`Execute`。
![天堂私服 - 圖 32 (36)](../images/private-lineage/chapter7/36.png)

* 安裝進度條…請等待安裝完畢至下一流程。
![天堂私服 - 圖 33 (37)](../images/private-lineage/chapter7/37.png)

* 設定完成請繼續點擊`Finish`。
![天堂私服 - 圖 34 (38)](../images/private-lineage/chapter7/38.png)

* 請繼續點擊`Next`。
![天堂私服 - 圖 35 (39)](../images/private-lineage/chapter7/39.png)

* 此處預設勾選在後面會啟動`MySQL Workbench`，請繼續點擊`Finish`
![天堂私服 - 圖 36 (40)](../images/private-lineage/chapter7/40.png)

* 然後會彈出下方視窗為`MySQL Workbench`
![天堂私服 - 圖 37 (41)](../images/private-lineage/chapter7/41.png)

> 註：此處其實已經完全將 MySQL 安裝完畢，後續只是要確認是否有安裝成功做的一些簡單連線與語法測試。

* MySQL Workbench 選擇這個我們剛配置好的 MySQL 資料庫。
![天堂私服 - 圖 38 (42)](../images/private-lineage/chapter7/42.png)

* 輸入設定的密碼`root`，並點擊`OK`。
![天堂私服 - 圖 39 (43)](../images/private-lineage/chapter7/43.png)

* Query 1 視窗內，寫下`show databases;`指令，並執行語法。
![天堂私服 - 圖 40 (44)](../images/private-lineage/chapter7/44.png)

* 如果能看到顯示結果(結果可能會不一樣)，那代表我們的資料庫安裝/設定好了。

## 結語

這個 MySQL 安裝步驟應該是最完善的，每一個步驟都沒有漏掉，超多圖片。希望大家可以安裝順利。
如果有其他在此篇文章中沒有出現的問題，網路上也有很多安裝教學，也可以多參考參考。
最後建議回顧一下首章[天堂私服 | 天堂私服架設教學](/private-lineage-20210712-private-lineage-0/#教學章節)，了解其章節目錄。

## 免責聲明

* 本部落格文章中皆<font color="red"><u>**不提供**</u></font>任何所謂的遊戲「主程式」、「模擬器」、「登入器」…等等相關程式的下載點。

* 本部落格文章中所見之遊戲主程式和服務器端程序均來自網路發佈，<font color="red"><u>版本歸**原作者**</u>所有</font>。

* 本部落格文章為研究SQL資料庫與修改JAVA語法使用，<font color="red">並<u>**非商業用途**</u>，亦<u>**無做營運事實等任何一切商業行為**</u>。</font>

* 本部落格文章內容是為研究學習設計思想和原理為目的，<font color="red"><u>**絕沒有故意侵權或惡意抄襲、篡改其他遊戲內容**</u></font>！

> 註：以上參考了
> [MySQL Community Downloads](https://dev.mysql.com/downloads/)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌‌​​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​‌‌‌

---

- **原文連結**：[J.J.'s Blogs - 資料庫 MySQL 5.6.25 的安裝](https://morosedog.gitlab.io/private-lineage-20210719-private-lineage-7/)
