---
title: 【Side Project】AI詩人
tags: Side Project, AIPoet
---


# 目的
**以python程式生成多首新詩，讓使用者擇一列印。**

2022年10/28~10/29於高雄國際會議中心展出。


# 過程
## [後端程式](https://colab.research.google.com/drive/1fNSIqXDkb-w864nNgniJZbD5-eftrwss#scrollTo=nlW4Hv0LhuqF): Colab Notebook
於「AI詩人初體驗」課程期間完成，執行所有儲存格可產生指定數量的新詩。

## [Prototype](https://aipoet.anvil.app/): Anvil app
僅在Colab Notebook執行期間運行，可輸入數量、字數及選擇詩人(訓練文庫之作者)產生新詩。

## [網站](https://aip-with-flask.elsie094081.repl.co/): 以Flask框架建置
### Main
#### 寫詩
在之前課程中使用的AI詩人函式加入數量、字數及風格等參數，增加使用者互動感。
#### 下載
使用python圖像庫(PIL)產生圖片並自動存入使用者裝置。
#### 影印
以Line notify傳送到操作人員電腦。
### Gallery
展示測試過程產生的部分作品。
### Feedback
反饋以電子信箱接收。

# 發展
## 課程