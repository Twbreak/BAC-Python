# 東吳BAC Python課程環境建置

### 環境架構
- 基礎環境 (Based Environment/Interpreter)
- 虛擬環境 (Virtual Environment/Interpreter)
- 程式碼編輯器 (Visual Studio code)

## 安裝基礎環境
1. 前往[python官網](https://www.python.org/downloads/release/python-3910/)往下拉點擊```Windows installer (64-bit)```下載執行檔
![螢幕擷取畫面 2024-11-11 111345](https://hackmd.io/_uploads/S1SvE-kG1g.png)

2. 下載完畢後點擊執行檔執行安裝
![螢幕擷取畫面 2024-11-11 111448](https://hackmd.io/_uploads/HyS4rZkzye.png)

3. 先勾選```Add Python 3.9 to PATH```再點擊```Install Now```
![螢幕擷取畫面 2024-11-11 111517](https://hackmd.io/_uploads/BJWuvb1zJg.png)

4. 等待安裝
![螢幕擷取畫面 2024-11-11 111533](https://hackmd.io/_uploads/SyCCwZkGJl.png)

5. 安裝完成 點擊```Close```關閉視窗
![螢幕擷取畫面 2024-11-11 111549](https://hackmd.io/_uploads/BJf7_-JM1l.png)


## 安裝虛擬環境
1. 在電腦中建立一個資料夾當作存放BAC的Pyhon課程的**檔案**和**虛擬環境** 我們以```D:\BACpython\```這個資料夾為例
![螢幕擷取畫面 2024-11-11 112551](https://hackmd.io/_uploads/rynZqbkMJl.png)

2. 在```D:\BACpython\```內建立名稱為```venvs```的資料夾 可用來存放多個虛擬環境
![螢幕擷取畫面 2024-11-11 112625](https://hackmd.io/_uploads/rkUh9-1zkx.png)

3. 點擊進入```venvs```資料夾並點擊上方路徑搜尋欄
![螢幕擷取畫面 2024-11-11 112707](https://hackmd.io/_uploads/SkJeibJGkx.png)

4. 輸入```cmd```並按```Enter```
![螢幕擷取畫面 2024-11-11 112733](https://hackmd.io/_uploads/SyOwi-1zyx.png)

5. 輸入```py --list```查看目前電腦有哪些版本的Python基礎環境
-版本後綴有```*```代表為目前電腦使用的的Python版本 可自行切換
-目前只有剛剛裝過的3.9版本的Python基礎環境 同學日後也可以安裝其他版本
```cmd
py --list
```
![螢幕擷取畫面 2024-11-11 112809](https://hackmd.io/_uploads/SJltsWyG1e.png)
