# remove-shell
[Article](https://andy6804tw.github.io/2020/07/21/linux-shell-script/)

## 前言
Shell Script 主要是使用在 Linux 和 MacOS 等 Unix-like 作業系統的自動化操作指令的程式語言。一般我們會使用 `.sh` 副檔名來命名 Shell Script 檔案。然後將該檔案設定為可執行的腳本。這一篇所主要講的內容是當你寫好一個腳本檔案時要執行時去跑出`Permission denied`錯誤訊息。

![](https://i.imgur.com/72ifkYw.png)
## 解決方法
其原因是因為當前目錄下沒有執行`.sh`檔案的權限，導致無法執行該指令腳本。在該目錄下執行，輸入以下指令就可以解決囉！


```sh
chmod u+x *.sh
```

chmod是權限管理命令change the permissions mode of a file的縮寫。 `chmod u+x *.sh` 就表示對當前目錄下的所有副檔名為sh文件的所有者增加可執行權限。

- u代表所有者
- x代表執行權限
- +表示增加權限

## 簡單範例
因為寫程式每次編譯新專案時要把舊的檔案刪除，手動去刪又很麻煩。因此可以寫一個腳本來專門刪除指定資料夾。建立一個 `run_remove.sh` 來執行 `rm` 指令。

![](https://i.imgur.com/D0zJQmP.png)

```
#!/bin/bash

rm -rf build
```

接著第二步給予資料夾權限執行 `.sh` 腳本。

```sh
chmod u+x *.sh
```

最後執行 `.sh` 檔僅需要在終端機輸入檔案名稱+檔名即可(記得加上相對位置)，例如:

```
./run_remove.sh      
```

![](https://i.imgur.com/SmeBl2R.png)