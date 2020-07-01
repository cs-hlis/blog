使用 jigdo 下載 Debian DLBD ISO 映像檔 — 去找吧！我把所有的套件都放在那裡了。
===
> [name=Samuel C.A. Lee] [time=Wed, Jul 1, 2020 3:13 AM]

> 目錄：
> [toc]

前言
---

### 什麼是 jigdo

>Jigdo (which stands for "Jigsaw Download") was written by Richard Atterer and is released under the GNU GPL. It's a tool that allows efficient downloading and updating of an ISO image. Any ISO image. Jigdo is not Debian specific, however Debian has chosen it to be the official method of downloading ISO images.
> [name=Debian Jigdo mini-HOWTO]

Jigdo（全名 Jigsaw Download）是由 Richard Atterer 製作並以 GNU GPL 授權釋出的一款工具。讓使用者可以有效率地下載或更新任何的 ISO 映像檔。Jigdo 不是專為 Debian 打造，然而 Debian 將它列為官方推薦的 ISO 映像檔下載工具。

### 什麼是 DLBD ISO

Debian 官方提供的最大的離線安裝光碟，分為兩張，總容量超過 50 GB。包含許多自由軟體，不包含非自由（non-free）軟體。可能是因為檔案太大的關係，在官網上只能透過 jigdo 下載。一般使用者不需要用到 DLBD，用 netinst 即可。此外，Debian DLBD ISO 為技能競賽 — 資訊與網路技術職類所採用的 Linux 安裝光碟，在比賽時會以 ISO 映像檔的形式提供。

### 如何下載

你需要一個 Debian/Ubuntu 系統（WSL 未經測試，不保證可行），強烈建議使用 Desktop 環境。除此之外，你還需要一塊足夠的儲存空間。也許還要一副麻將和三個朋友，因為這通常會下載**很久**。

> 系統資訊：
> 
> OS: Ubuntu 20.04 LTS 64-bit
> 
> 軟體：
> - jigdo-file 0.8.0
> - Mozilla Firefox

正文開始
---

### 安裝

1. 取得 root 權限

    要有 root 權限才能安裝 jigdo。

    ```=shell
    $ sudo su
    ```
    
2. 安裝 jigdo

    先更新套件清單。（好習慣）
    
    ```=shell
    # apt update
    ```
    
    然後才安裝 jigdo。
    
    ```=shell
    # apt install jigdo-file
    ```

3. 檢查
    
    ```=shell
    $ jigdo-file --version
    jigdo-file version 0.8.0
    ```
    
### 下載

1. 執行 jigdo
    
    建議用 root 執行。
    
    ```=shell
    # jigdo-lite
    ```
    
    **是** `-lite` **不是** `-file`。
    
    然後會出現一些資訊，最後叫你輸入 .jigdo 檔案的網址或本機路徑。
    
    ```
    ...
	jigdo: 
    ```
    
2. 取得 .jigdo 檔案網址

    你應該可以在 [這裡](https://cdimage.debian.org/debian-cd/current/amd64/jigdo-dlbd/) 看到最新版本的 Debian DLBD ISO 映像檔的 .jigdo 檔案。對他們按右鍵，選擇  `複製連結網址`，然後貼到 jigdo 視窗，按下 `Enter`。
    
    ![圖檔已死](https://i.imgur.com/sBYuv01.png)
    
    ![圖檔已死](https://i.imgur.com/Gi2ghiM.png)

    接著 jigdo 會開始下載一些資料，下載完後會詢問你是否要掃描現有的 ISO 映像檔（這樣就不用重複下載，節省流量），按下 `Enter` 跳過。
    
    ![圖檔已死](https://i.imgur.com/zReCzjZ.png)

3. 選擇映射站台
    
    接著就會詢問你要從哪一個映射站台（mirror）下載 DLBD。**除非你很想打麻將，不然請不要作死用 Debian 主站當作下載來源。**
    
    ![圖檔已死](https://i.imgur.com/Xu2MROG.png)
    
    輸入 `tw` 取得台灣地區的映設站台清單。

    ![圖檔已死](https://i.imgur.com/FqZBQdb.png)

    理論上是愈靠近所在地的愈快，但其實 NCHC（國網中心）和 NCTU（交大）的速度通常都比其他的快上許多。
    
    本次使用 NCHC 的映射站台，所以輸入 `http://opensource.nchc.org.tw/debian/`。
    
4. 等待
    
    打麻將、泡泡麵、聊天、睡覺、大富翁

### 完成

下載完成後，jigdo 會自動幫你檢查 MD5 雜湊值，確認檔案是完整的。

![圖檔已死](https://i.imgur.com/0n49Jsv.png)

參考資料
---

- [What Is Jigdo?](http://www.tldp.org/HOWTO/Debian-Jigdo/whyjigdo.html#WHATISJIGDO)
- [Index of /debian-cd/current/amd64/jigdo-cd](https://cdimage.debian.org/debian-cd/current/amd64/jigdo-cd/)

***
此文由 Samuel C.A. Lee 寫於 2020/07，歡迎批評及指教。