# VirtualBox Windows 7 安裝

# 天堂私服 | VirtualBox Windows 7 安裝

    
    
      📑 目錄
      

1. [VirtualBox 是什麼？](#VirtualBox-是什麼？)
2. [為何需要虛擬機？](#為何需要虛擬機？)
3. [下載 VirtualBox](#下載-VirtualBox)
4. [安裝 VirtualBox](#安裝-VirtualBox)
5. [安裝 Windows 7](#安裝-Windows-7)
6. [安裝 Guest Additions](#安裝-Guest-Additions)
7. [Windows 7 授權 & 更新](#Windows-7-授權-amp-更新)
8. [下載 .NET Framework](#下載-NET-Framework)
9. [安裝 .NET Framework](#安裝-NET-Framework)
10. [額外延伸](#額外延伸)
11. [結語](#結語)
12. [免責聲明](#免責聲明)

    
    
    

## VirtualBox 是什麼？

VirtualBox 是一套虛擬機軟體，它提供使用者在 32 位元或 64 位元的Windows、Solaris 及 Linux 作業系統上虛擬其它 x86 的作業系統。
使用者可以在 VirtualBox 上安裝並且執行 Solaris、Windows、DOS、Linux、OS/2 Warp、OpenBSD 及 FreeBSD 等系統作為客戶端作業系統。

最簡單的說法就是，在你的實體電腦的作業系統裡面，再安裝一套作業系統。

## 為何需要虛擬機？

其實最早的虛擬機軟體用途，是用來模擬多台機器之間的測試與連線，還有用來做所謂的病毒、惡意程式分析…等等用途。
到後來虛擬機已經成為一個主流，常常聽到別人說的雲端，其實都是透過虛擬機的技術去建製，然後將這套服務提供並做租售…。​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌‌

那為何在架設天堂私服會需要使用虛擬機？

* 因為當架設過程中有問題或是失敗後，可以快速重新建構、複製一份乾淨的作業系統。

* 因為在開發過程中，可能會用到很多第三方工具，這些工具可能被防毒軟體認定為惡意程式<當然他可能真的是…>。

* 架設好的電腦配置，可以根據需求去調整虛擬電腦的配置<cpu、記憶體>。

根據以上幾種原因，強烈建議在虛擬機裡面去做後續的軟體安裝，私服的架設。

## 下載 VirtualBox

首先，我們進入下載 VirtualBox 的網站：[連結](https://www.virtualbox.org/)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌‌

* 點擊`Download VirtualBox 6.1`進入下載頁面
![天堂私服 - 圖 1 (01)](../images/private-lineage/chapter3/01.png)

* 作者實體機器是 `Windows` 所以就點擊下載 `Windows hosts`。
![天堂私服 - 圖 2 (02)](../images/private-lineage/chapter3/02.png)

## 安裝 VirtualBox

此處安裝的版本為`VirtualBox 6.1.22-144080`來做安裝示範。
<font color="gray"><*2021-07-15當時下載的最新版*></font>

* 滑鼠左鍵雙擊`VirtualBox-6.1.22-144080-Win.exe`檔案。

* 跳出開啟檔案 - 安全性警告，請點擊`執行`。
![天堂私服 - 圖 3 (03)](../images/private-lineage/chapter3/03.png)

* 請點擊`下一步`。
![天堂私服 - 圖 4 (04)](../images/private-lineage/chapter3/04.png)

* 可以選擇您要安裝的路徑位置，建議就預設安裝即可；請點擊`下一步`。
![天堂私服 - 圖 5 (05)](../images/private-lineage/chapter3/05.png)

* 預設都是勾起，請點擊`下一步`。
![天堂私服 - 圖 6 (06)](../images/private-lineage/chapter3/06.png)

* 跳出提示說明，安裝過程中，可以會造成**<font color="red">網路中斷</font>**；如果不影響您，請點擊`是`。
![天堂私服 - 圖 7 (07)](../images/private-lineage/chapter3/07.png)

* 請點擊`安裝`。
![天堂私服 - 圖 8 (08)](../images/private-lineage/chapter3/08.png)

* 安裝進度條…請等待安裝完畢至下一流程。
![天堂私服 - 圖 9 (09)](../images/private-lineage/chapter3/09.png)

* 彈出安裝`Oracle Corporation 通用序列匯流排控制器`，請點擊`安裝`。
![天堂私服 - 圖 10 (10)](../images/private-lineage/chapter3/10.png)

* 彈出安裝`Oracle Corporation 網路介面卡`，請點擊`安裝`。
![天堂私服 - 圖 11 (11)](../images/private-lineage/chapter3/11.png)

* 彈出安裝`Oracle Corporation Network Service`，請點擊`安裝`。
![天堂私服 - 圖 12 (12)](../images/private-lineage/chapter3/12.png)

* 預設勾起`安裝後啟動 Oracle VM VirtualBox`。
![天堂私服 - 圖 13 (13)](../images/private-lineage/chapter3/13.png)

* 至此已經安裝完畢，請點擊`完成`，會開啟`Oracle VM VirtualBox 管理員視窗`。
![天堂私服 - 圖 14 (14)](../images/private-lineage/chapter3/14.png)

## 安裝 Windows 7

安裝前準備：

* Windows 7 x64 的映像檔 ([tw_windows_7_ultimate_with_sp1_x64_dvd_618550.iso](/images/private-lineage/download_not_available.png))

  * 目前無法提供下載點，請根據關鍵字自行上網搜尋。

安裝：​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌‌

* 開啟`Oracle VM VirtualBox 管理員`。

* 點擊`新增`

* 輸入名稱，建議名稱為作業系統與版本。

* 選擇機器資料夾，建議是存放在空間充足的磁碟區。

* 根據要安裝的作業系統選擇類型。

* 根據要安裝的作業系統版本選擇版本。

* 確定後，請點擊`下一個`。
![天堂私服 - 圖 15 (15)](../images/private-lineage/chapter3/15.png)

* 根據自身實體電腦的記憶體配置給虛擬機的記憶體大小。

* 建議配置給虛擬機 4G 的記憶體，如果記憶體不足，預設配置 2G 即可。

* 配置後，請點擊`下一個`。
![天堂私服 - 圖 16 (16)](../images/private-lineage/chapter3/16.png)

* 請點擊`建立`。
![天堂私服 - 圖 17 (17)](../images/private-lineage/chapter3/17.png)

* 請點擊`下一個`。
![天堂私服 - 圖 18 (18)](../images/private-lineage/chapter3/18.png)

* 請點擊`下一個`。
![天堂私服 - 圖 19 (19)](../images/private-lineage/chapter3/19.png)

* 虛擬硬碟的路徑位置預設即可<此處路徑應該與第一步驟是相呼應的>。

* 硬碟大小配置，預設為 32 GB，建議是 64 GB，如空間不足預設即可。

* 請點擊`建立`。
![天堂私服 - 圖 20 (20)](../images/private-lineage/chapter3/20.png)

* 見左邊清單已有虛擬機。
![天堂私服 - 圖 21 (21)](../images/private-lineage/chapter3/21.png)

* 請選擇，點擊`啟動`。
![天堂私服 - 圖 22 (22)](../images/private-lineage/chapter3/22.png)

* 請點擊`瀏覽`。
![天堂私服 - 圖 23 (23)](../images/private-lineage/chapter3/23.png)

* 請點擊`加入`。
![天堂私服 - 圖 24 (24)](../images/private-lineage/chapter3/24.png)

* 瀏覽下載的`Windows 7 x64 的映像檔`，並點擊`選擇`。
![天堂私服 - 圖 25 (25)](../images/private-lineage/chapter3/25.png)

* 請點擊`開始`。
![天堂私服 - 圖 26 (26)](../images/private-lineage/chapter3/26.png)

* 進入Windows 7的安裝程序。

* 請點擊`下一步`。
![天堂私服 - 圖 27 (27)](../images/private-lineage/chapter3/27.png)

* 點擊`立即安裝`。
![天堂私服 - 圖 28 (28)](../images/private-lineage/chapter3/28.png)

* 勾選`我接受授權合約`，並點擊`下一步`。
![天堂私服 - 圖 29 (29)](../images/private-lineage/chapter3/29.png)

* 請點擊`自訂`。
![天堂私服 - 圖 30 (30)](../images/private-lineage/chapter3/30.png)

* 請點擊`磁碟機選項`。
![天堂私服 - 圖 31 (31)](../images/private-lineage/chapter3/31.png)

* 請點擊`新增`。
![天堂私服 - 圖 32 (32)](../images/private-lineage/chapter3/32.png)

* 請點擊`套用`。
![天堂私服 - 圖 33 (33)](../images/private-lineage/chapter3/33.png)

* 請點擊`確定`。
![天堂私服 - 圖 34 (34)](../images/private-lineage/chapter3/34.png)

* 請選擇`主要磁碟`，並點擊`下一步`。
![天堂私服 - 圖 35 (35)](../images/private-lineage/chapter3/35.png)

* 安裝進度條…請等待安裝完畢至下一流程。
![天堂私服 - 圖 36 (36)](../images/private-lineage/chapter3/36.png)

* 進入設定 Windows。

* 請輸入使用者名稱，可自行輸入。
![天堂私服 - 圖 37 (37)](../images/private-lineage/chapter3/37.png)

* 密碼留空即可，並點擊`下一步`。
![天堂私服 - 圖 38 (38)](../images/private-lineage/chapter3/38.png)

* 請**<font color="red">取消</font>**勾選`當我在線上時自動啟用 Windows`，並點擊`略過`。
![天堂私服 - 圖 39 (39)](../images/private-lineage/chapter3/39.png)

* 請點擊`稍後詢問我`。
![天堂私服 - 圖 40 (40)](../images/private-lineage/chapter3/40.png)

* 請點擊`下一步`。
![天堂私服 - 圖 41 (41)](../images/private-lineage/chapter3/41.png)

* 請點擊`家用網路`。
![天堂私服 - 圖 42 (42)](../images/private-lineage/chapter3/42.png)

* 請稍待片刻後，成功進入桌面。

* 最乾淨版的 Windows 7 x64 已安裝完畢。
![天堂私服 - 圖 43 (43)](../images/private-lineage/chapter3/43.png)

* 此時建議重新開機虛擬機，重新開機後視窗大小會自動調整。

## 安裝 Guest Additions

Guest Additions 是什麼？

* 整合主(Host)端和客(Guest)端滑鼠的游標：不需要再按Host Key就可以在真實和虛擬機器之間自動切換滑鼠。

* 分享資料夾：真實和虛擬機器之間可以透過分享的資料夾交換資料。

* 更好的視訊支援：可以支援虛擬機器更高的解析度。

* 時間同步。

* 共享剪貼簿。

安裝與設定：

* 請點擊，`裝置 → 共用剪貼簿 → 雙向`
![天堂私服 - 圖 44 (44)](../images/private-lineage/chapter3/44.png)

* 請點擊，`裝置 → 拖放 → 雙向`
![天堂私服 - 圖 45 (45)](../images/private-lineage/chapter3/45.png)

* 請點擊，`裝置 → 插入 Guest Additions CD 映像...`
![天堂私服 - 圖 46 (46)](../images/private-lineage/chapter3/46.png)

* 請點擊`執行 VBoxWindowsAdditions.exe`
![天堂私服 - 圖 47 (47)](../images/private-lineage/chapter3/47.png)

* 跳出安全提示`您是否要允許下列成是變更這部電腦？`請選擇`是`。
![天堂私服 - 圖 48 (48)](../images/private-lineage/chapter3/48.png)

* 請點擊`Next`。
![天堂私服 - 圖 49 (49)](../images/private-lineage/chapter3/49.png)

* 此處可以選擇您要安裝的路徑位置，建議預設安裝即可；請繼續點擊`Next`。
![天堂私服 - 圖 50 (50)](../images/private-lineage/chapter3/50.png)

* **<font color="red">請取消勾選`Direct3D Support (Experir...`</font>**，並點擊`Install`。

> 注：此處是因為如果勾選安裝後，後面會無法調整顯示卡色彩為 全彩16 位元，會造成無法開啟天堂主程式。
> 註：該問題應該是針對 Win7 系統無法對 VirtualBox Graphics Adapter (WDDM) 顯示卡做驅動的關係。
> ![天堂私服 - 圖 51 (51)](../images/private-lineage/chapter3/51.png)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌‌

* 彈出安裝`Oracle Corporation 系統裝置`，請點擊`安裝`。
![天堂私服 - 圖 52 (52)](../images/private-lineage/chapter3/52.png)

* 彈出安裝`Oracle Corporation 顯示卡`，請點擊`安裝`。
![天堂私服 - 圖 53 (53)](../images/private-lineage/chapter3/53.png)

* 請點擊`Finish`，將會重新啟動虛擬機。
![天堂私服 - 圖 54 (54)](../images/private-lineage/chapter3/54.png)

* 重啟後的虛擬機，可以在實體與虛擬機之間，拖拉檔案、複製貼上。

* 此時在電腦解析度為`1152 x 864`以下，皆可調整顯示卡色彩為 全彩16 位元。
![天堂私服 - 圖 55 (55)](../images/private-lineage/chapter3/55.png)

## Windows 7 授權 & 更新

* 授權

  * 此處無法提供任何授權破解檔案，請自行上網搜尋。

* 更新

  * 最少更新：<快速，建議>

    * [KB4490628 - x64](http://download.windowsupdate.com/c/msdownload/update/software/secu/2019/03/windows6.1-kb4490628-x64_d3de52d6987f7c8bdc2c015dca69eac96047c76e.msu)

    * [KB4474419 - x64](http://download.windowsupdate.com/c/msdownload/update/software/secu/2019/09/windows6.1-kb4474419-v3-x64_b5614c6cea5cb4e198717789633dca16308ef79c.msu)

  * 完整更新：<費時，不建議>

    * [Windows 7 SP1 Update Package 微軟更新修正包 (2020.01月份)](https://wmos.info/archives/18340)

  * 開啟 Windows Update：<已關閉>

    * [Windows 7 已於 2020 年 1 月 14 日終止支援](https://support.microsoft.com/zh-tw/windows/windows-7-%E5%B7%B2%E6%96%BC-2020-%E5%B9%B4-1-%E6%9C%88-14-%E6%97%A5%E7%B5%82%E6%AD%A2%E6%94%AF%E6%8F%B4-b75d4580-2cc7-895a-2c9c-1466d9a53962)

> 註：KB4490628 與 KB4474419 是一定要安裝的，因為後面再安裝其他 Microsoft 軟體時，才不會發生憑證無效或是過期的問題。
> 注：安裝完更新後，請務必重新啟動虛擬機。​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌‌

## 下載 .NET Framework

提供用於 Windows 的 Microsoft .NET Framework 4.8 離線安裝程式
連結：[Microsoft .NET Framework 4.8 離線安裝程式套件](https://download.visualstudio.microsoft.com/download/pr/2d6bb6b2-226a-4baa-bdec-798822606ff1/8494001c276a4b96804cde7829c04d7f/ndp48-x86-x64-allos-enu.exe)

## 安裝 .NET Framework

此處安裝的版本為 `.NET Framework 4.8`來做安裝示範。
**<font color="gray"><2021-07-15當時下載的最新版></font>**

* 滑鼠左鍵雙擊`ndp48-x86-x64-allos-enu.exe`檔案。

* 跳出安全提示`您是否要允許下列成是變更這部電腦？`請選擇`是`。
![天堂私服 - 圖 56 (56)](../images/private-lineage/chapter3/56.png)

* 等待提取檔案…
![天堂私服 - 圖 57 (57)](../images/private-lineage/chapter3/57.png)

* 請勾選`我已閱讀並且接受授權條款`，在點擊`安裝`。
![天堂私服 - 圖 58 (58)](../images/private-lineage/chapter3/58.png)

* 安裝進度條…請等待安裝完畢至下一流程。
![天堂私服 - 圖 59 (59)](../images/private-lineage/chapter3/59.png)

* 恭喜您已經安裝完畢，請點擊`Close`結束安裝程序。
![天堂私服 - 圖 60 (60)](../images/private-lineage/chapter3/60.png)

## 額外延伸

1. 此時可以使用`再製`的功能，對進行複製。

後續就使用再製的虛擬機進行安裝、練習用；如果有問題或是失敗了，想要重新來做，也不必再做一次繁雜的新增虛擬機的步驟過程。
直接刪除再製的虛擬機，重新`再製`對進行複製一個新的虛擬機即可。​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌‌

* 請選擇，右鍵點擊`再製`。
![天堂私服 - 圖 61 (61)](../images/private-lineage/chapter3/61.png)

* 請點擊`下一個`
![天堂私服 - 圖 62 (62)](../images/private-lineage/chapter3/62.png)

* 請點擊`再製`
![天堂私服 - 圖 63 (63)](../images/private-lineage/chapter3/63.png)

* 再製進度條…請等待再製完畢。
![天堂私服 - 圖 64 (64)](../images/private-lineage/chapter3/64.png)

* 列表顯示新的再製虛擬機，可以選擇點擊並啟用。
![天堂私服 - 圖 65 (65)](../images/private-lineage/chapter3/65.png)

5. 關閉虛擬機後，可以對虛擬機做設定：

  * 記憶體大小

  * 處理器數量

  * 顯示卡記憶體

  * 網路卡設定

這些設定請自行摸索或是上網搜尋相關教學文章。

## 結語

上面的安裝教學，基本上是我重複再重複，安裝在安裝才整理出來的完整安裝教學，已經排除了絕大多數的坑。
希望在後續的文章中可以提供給大家一個乾淨的作業環境。
最後建議回顧一下首章[天堂私服 | 天堂私服架設教學](/private-lineage-20210712-private-lineage-0/#教學章節)，了解其章節目錄。

## 免責聲明

* 本部落格文章中皆<font color="red"><u>**不提供**</u></font>任何所謂的遊戲「主程式」、「模擬器」、「登入器」…等等相關程式的下載點。

* 本部落格文章中所見之遊戲主程式和服務器端程序均來自網路發佈，<font color="red"><u>版本歸**原作者**</u>所有</font>。

* 本部落格文章為研究SQL資料庫與修改JAVA語法使用，<font color="red">並<u>**非商業用途**</u>，亦<u>**無做營運事實等任何一切商業行為**</u>。</font>

* 本部落格文章內容是為研究學習設計思想和原理為目的，<font color="red"><u>**絕沒有故意侵權或惡意抄襲、篡改其他遊戲內容**</u></font>！

> 註：以上參考了
> [維基百科 - VirtualBox](https://zh.wikipedia.org/zh-tw/VirtualBox)
> [VirtualBox](https://www.virtualbox.org/)
> [Microsoft](https://www.microsoft.com/zh-tw/)
> [適用於 Windows 7 SP1 和 Windows Server 2008 R2 SP1 的 .NET Framework 4.8 僅限安全性更新 (KB4565589)](https://support.microsoft.com/zh-tw/topic/%E9%81%A9%E7%94%A8%E6%96%BC-windows-7-sp1-%E5%92%8C-windows-server-2008-r2-sp1-%E7%9A%84-net-framework-4-8-%E5%83%85%E9%99%90%E5%AE%89%E5%85%A8%E6%80%A7%E6%9B%B4%E6%96%B0-kb4565589-537d46b9-3dd0-7ec0-6c5b-764a2c98c969)​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌​​​‌‌​​​​​​‌‌​​‌​​​‌‌​​​‌​​‌‌​​​​​​‌‌​‌‌‌​​‌‌​​​‌​​‌‌​‌​‌​​‌​‌‌​‌​‌‌‌​​​​​‌‌‌​​‌​​‌‌​‌​​‌​‌‌‌​‌‌​​‌‌​​​​‌​‌‌‌​‌​​​‌‌​​‌​‌​​‌​‌‌​‌​‌‌​‌‌​​​‌‌​‌​​‌​‌‌​‌‌‌​​‌‌​​‌​‌​‌‌​​​​‌​‌‌​​‌‌‌​‌‌​​‌​‌​​‌​‌‌​‌​​‌‌​​‌‌

---

- **原文連結**：[J.J.'s Blogs - VirtualBox Windows 7 安裝](https://morosedog.gitlab.io/private-lineage-20210715-private-lineage-3/)
