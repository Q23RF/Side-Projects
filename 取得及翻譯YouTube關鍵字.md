---
title: 【Side Project】取得及翻譯YouTube關鍵字
tags: Side Project, Python
---

# 需求
**從YouTube使用者介面取得影片設定的搜尋關鍵字**
## 發想
在YouTube上搜尋韓國男團NCT分隊NCT DREAM時會出現另一分隊NCT127的音樂影片，搜尋NCT127卻沒有出現NCT DREAM相關內容。我根據之前GD50課程上傳Demo影片的經驗，推測是搜尋關鍵字設置不同造成，卻發現無法從使用者介面直接查看關鍵字驗證這個猜想，所以開始了這個Side Project。

# 方案

## 方案1: Linux
使用: wget, grep

### 過程
```
wget [目標網址] -O [檔名]
grep keywords [檔名]
```
### 成果
:o: 取得關鍵字

:x: 只取得文字部分

:x: 翻譯非中/英文的關鍵字

---
![](https://i.imgur.com/uQUN3Fm.png)

---


## [方案2: Python BeautifulSoup](https://colab.research.google.com/drive/1z-nZhlRZBnlJOy3xbnOqJfFe3rKqFcMt)
使用: BeautifulSoup, urlopen

### 過程
```python
def GetKeywords(url):
  html = urlopen(url).read().decode()
  soupObj = BeautifulSoup(html, "html.parser")
  keywords = str(soupObj.findAll("meta")[5]).split('"')[1]
  return keywords
```


### 成果
:o: 取得關鍵字

:o: 只取得文字部分

:x: 翻譯非中/英文的關鍵字

---
![](https://i.imgur.com/tBHrwkr.png)

---



## 方案3: Python pytube & googleTrans 
使用: detect, Translator, YouTube object
### 過程
google_trans_new和googleTrans現在pip的版本都有bug，先用可運作的googleTrans 4.0.0-rc1:
```python
!pip install googleTrans==4.0.0-rc1
!pip install langdetect
!pip install pytube
```
載入相依套件:
```python
from langdetect import detect
from googletrans import Translator
from pytube import YouTube
```
取得並翻譯關鍵字:
```python
def kw_trans(url):
  keywords = YouTube(url).keywords
  results = ""
  for w in keywords:
    if detect(w)=='ko':
      results += w + "({})".format(translator.translate(w, dest='en').text) + ", "
    else:
      results += w + ", "
  return results
```

### 成果
:o: 取得關鍵字

:o: 只取得文字部分

:o: 翻譯非中/英文的關鍵字

---
![](https://i.imgur.com/CF2PsQ7.png)

---
