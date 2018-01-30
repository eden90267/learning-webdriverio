# WebDriverIO 常用指令 (API) 語法

[http://webdriver.io/api.html](http://webdriver.io/api.html)

## 指令種類

- Protocol
- Action
- Utility
- Property
- State
- Mobile

## Protocol

### 選取元素

```javascript
browser.element('div');
$('div');

browser.elements('div');
$$('div');
```

### 前往某網址

```javascript
browser.url('http://www.google.com');
```

## Action

### 設定欄位的值

```javascript
browser.element('.email').setValue('aaa@bbb.com');
// 縮寫
$('.email').setValue('aaa@bbb.com');
```

### 點選欄位的值

```javascript
browser.click('.some-button');

// 縮寫
$('.some-button').click();
$('[title="Sign Out"]').click();
```

## Utility

### 檢查某個元素是否存在

```javascript
browser.waitForExist('.alert-text');

// 縮寫
$('.alert-text').waitForExist();
```

### 暫停

```javascript
browser.pause(5000);
```

### 除錯

```javascript
browser.debug();
```

### 加命令

```javascript
browser.addCommand();
```

### waitForExist

```javascript
browser.element('.notification').waitForExist();
browser.element('.notification').waitForExist(5000);
browser.element('.notification').waitForExist(5000, true);
// 或
browser.waitForExist('.notification');
browser.waitForExist('.notification', 5000);
browser.waitForExist('.notification', 5000, true);
```

### saveScreenshot

```javascript
browser.saveScreenshot('front_page.png');
```

### end

```javascript
client
  .init()
  .url('http://google.com')
  .end();
  // ends session and close browser
```

## Property

### 取得某個元素的文字

```javascript
browser.getText('alert-text');

// 縮寫
$('.alert-text').getText();
```

### 取得某元素的值

```javascript
browser.getValue('input[name=email]');
```

### 取得標題

```javascript
browser.getTitle();
```

### 取得網址

```javascript
browser.getUrl();
```

## State

### isEnabled

```html
<input type="text" name="inputField" class="input1">
<input type="text" name="inputField" class="input2" disabled>
<input type="text" name="inputField" class="input3" disabled="disabled">
```

```javascript
var isEnabled = browser.isEnabled('.input1');
console.log(isEnabled); // true
var isEnabled = browser.isEnabled('.input2');
console.log(isEnabled); // false
var isEnabled = browser.isEnabled('.input3');
console.log(isEnabled); // false
```

### isSelected

```html
<select name="selectbox" id="selectbox">
    <option value="Daisy">Daisy</option>
    <option value="Alin" selected="selected">Alin</option>
    <option value="Andy">Andy</option>
</select>
```

```javascript
$('[value="Layla Terry"]').isSelected(); // true

browser.selectByValue('#selectbox', 'Bill Gilbert');
element.isSelected(); // false
```

### isExisting / isVisible

```html
<select name="selectbox" id="selectbox">
    <option value="Daisy">Daisy</option>
    <option value="Alin" selected="selected">Alin</option>
    <option value="Andy">Andy</option>
</select>
```

```javascript
browser.isExisting(selector);
```