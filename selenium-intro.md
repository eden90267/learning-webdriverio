# 介紹 Selenium

- Open source project
- 可自動化控制使用者介面
- 支援多 browser：Firebox、Chrome、IE、Edge..
- 支援多平台：Mac、Window、Linux
- 支援多語言：Java、Python、Ruby、C#、Javascript、C++
- [](https://github.com/christian-bromann/awesome-selenium)

## 優點

- 支援重複執行測試程式
- 支援並行執行
- 支援背景執行
- 減少人為產生的錯誤
- 省下測試的時間

## 應用領域

- 自動化測試
- 網站擷取 / 網路爬蟲

## 目前有四個主要專案

- Selenium IDE

    Firefox extension

- Selenium Remote Control (RC)

    簡稱 Selenium RC，它提供可遠端執行 Selenium 的 Client/Server 架構

    Selenium Server 是複雜控制瀏覽器行為，Selenium Client 則是用於撰寫測試腳本來跟 Selenium Server 溝通

- Selenium Grid

    主要控制多台機器 (RC Node)，每次測試任務都先呼叫 Hub，然後再由路由 (Hub) 分配給節點 (Node)

    - Selenium Grid Hub
    - Selenium Grid Node

- Selenium WebDriver

    許多網頁自動化測試框架，都是以 Selenium WebDriver API 作為基礎。Selenium 2.0 帶來 WebDriver 的實作，跨越不同瀏覽器的自動化操作，有更清楚定義的標準可循，目前 WebDriver API 規範已提交 W3C，若能夠被標準化且在各大瀏覽器實作，執行跨瀏覽器的自動化測試工作將會被簡化許多。

## 選取元素

### Identifier

identifier=id

```
id=myId
```

```html
<div id="myId">hello</div>
```

### Name

name=name

```
<div name="myName">hello</div>
```

### DOM

dom=javascriptExpression

```
dom=document.getElementById('loginForm')
dom=document.forms['loginForm']
dom=document.forms[0]
document.forms[0].username
document.forms[0].elements['username']
document.forms[0].elements[0]
document.forms[0].elements[3]
```

```html
<html>
  <body>
   <form id="loginForm">
    <input name="username" type="text" />
    <input name="password" type="password" />
    <input name="continue" type="submit" value="Login" />
    <input name="continue" type="button" value="Clear" />
   </form>
 </body>
 <html>
```

### xPath

xpath=xpathExpression

```
xpath=id('myId')
```

### Link Text

link=textPattern

選擇包含指定文字比對模式的連結或錨點元素：

```
link=Continue
link=Cancel
```

```html
<html>
 <body>
  <p>Are you sure you want to do this?</p>
  <a href="continue.html">Continue</a>
  <a href="cancel.html">Cancel</a>
</body>
<html>
```

### Partial Link Text

```html
<html>
 <body>
  <p>Are you sure you want to do this?</p>
  <a href="continue.html">Continue</a>
  <a href="cancel.html">Go Home Page</a>
</body>
<html>
```

### CSS Selector

css=cssSelectorSyntax

```
css=form#loginForm
css=input[name="username"]
css=input.required[type="text"]
css=input.passfield
css=#loginForm input[type="button"]
css=#loginForm input:nth-child(2)
```

```html
<html>
  <body>
   <form id="loginForm">
    <input class="required" name="username" type="text" />
    <input class="required passfield" name="password" type="password" />
    <input name="continue" type="submit" value="Login" />
    <input name="continue" type="button" value="Clear" />
   </form>
 </body>
 <html>
```

## Selenium IDE

操作 Selenium IDE 就像錄影機，在開始錄製後，瀏覽器操作網站的動作就會被捕捉，產生測試案例 (Test Case) 的內容。錄製完成後，可以用播放重新把網站操作過程重播一次。

### Selenium 指令

#### 命令組成

- 指令 (Command)：行為 / 事件
- 目標 (Target)：選取元素
- 值 (Value)

#### 指令種類

- 操作 (Actions)
- 存取 (Accessors)
- 驗證 (Assertions)

### 操作 (Actions)

- open
- click
- clickAndWait
- type (模擬鍵盤輸入)
- typeAndWait
- select
- selectAndWait
- pause

### 存取 (Accessors)

- storeText
- storeTitle
- store

### 驗證 (Assertions)

- 驗證 (assert) / 辨識 (verify)
  - assertText /  verifyText
  - assertTitle /  verifyTitle
  - assertAlert /  verifyAlert
  - assertTextPresent /  verifyTextPresent
  - assertElementPresent /  verifyElementPresent
  - assertTable / verifyTable
- 等待 (waitFor)
  - waitForText
  - waitForPageToLoad
  - waitForElementPresent

#### 驗證 (assert) 與 辨識 (verify)

差別在處理錯誤的方式

- 驗證 (assert)：發生錯誤時，測試將會終止
- 辨識 (verify)：發生錯誤時，只是將錯誤訊息留下紀錄，測試將會繼續執行不會中斷。

#### verifyText
#### verifyAllWindowTitles

### 等待 (waitFor)

等待某些情況發生時才生效，常用於非同步 (AJAX)

#### waitForAllWindowTitle