# kc-generator
kindle comic(mobi) generator

usage
===
執行後輸入 _工作根目錄_ 路徑，程式將會根據工作根目錄指定資料夾中的圖片，生成一個mobi檔

工作根目錄結構要求
===
_工作根目錄不一定要和此程式擺在一起_

**工作根目錄必須包含以下結構**

* 工作根目錄
  * **config.json**
  * 圖片根目錄
    * 章節根目錄
      * 圖片...
    * 章節根目錄
      * 圖片...
  * 封面圖檔

章節根目錄名稱會影響mobi檔中的目錄

config.json結構
===
以下皆為必要參數

* `title`:書名
* `language`:語言
* `creator`:作者
* `folder`:圖片根目錄位置
* `width`:頁面寬度
* `height`:頁面高度
* `cover`:封面檔案(可選擇留空，但一定要有鍵)

_*在[此檔案](https://github.com/HSSLC/kc-generator/blob/master/config.json)中有預填好部分內容的JSON_

注意
===
* 因為排序的關係，章節根目錄及內容圖片檔名中，一定要包含阿拉伯數字，否則將程式不知如何排序，就不會繼續運作

* 排序將會依照檔名中第一組阿拉伯數字排序

* 不同章節間的內容圖片檔名可以重複

* 在程式執行過程中，會在 _工作根目錄_ 下生成暫存目錄`proj`，會將工作根目錄的大小幾乎翻倍，執行前請先確認磁碟空間夠用

* 若磁碟空間吃緊，在執行完後可選擇將暫存目錄`proj`刪除

* 可以藉由修改`frames\content_frame.opf`來修改日後生成的書的資訊模板

工作根目錄與config.json的生成結果範例
===

## 工作根目錄範例
_名稱後括號為類型方便理解，實際上不存在_
* `C槽`
  * `測試之書`(目錄)
    * `config.json`(檔案)
    * `jpg`(目錄)
      * `第一章 快狐`(目錄)
        * `image1.jpg`(檔案)
        * `image2.jpg`(檔案)
        * `image3.jpg`(檔案)
      * `第二章 越懶狗`(目錄)
        * `image4.jpg`(檔案)
        * `image5.jpg`(檔案)
    * `cover.jpg`(檔案)

## config.json範例
`
{  
  "title":"測試之書",  
  "language":"zh",  
  "creator":"HSSLC",  
  "folder":"jpg",  
  "width":"800",  
  "height":"1280",  
  "cover":"cover.jpg"  
}  
`
## 執行過程
1. 執行main.py
2. 輸入`C:\測試之書`
3. 程式會在`測試之書`下方生成暫存目錄`proj`
4. 檔案生成完後程式會呼叫kindlegen.exe生成mobi，位於`測試之書`目錄下

## 此範例生成結果
一本名為`測試之書`的書，位於`C:\測試之書\測試之書.mobi`，作者為`HSSLC`，有兩章，分別叫做`第一章 快狐`與`第二章 越懶狗`，第一章中有三頁，分別為`image1.jpg`、`image2.jpg`、`image3.jpg`，第二章中有兩頁，分別為`image4.jpg`、`image5.jpg`，此書封面為`cover.jpg`

絕對是個巧合
===
[manhuagui-dlr](https://github.com/HSSLC/manhuagui-dlr) 做出來的目錄結構剛好符合這個程式...
