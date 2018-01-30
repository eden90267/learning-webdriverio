# 斷言函式庫 Chai

Chai 是一個 BDD/TDD 基於 NodeJS 的斷言函式庫，可以與任何 javascript 測試框架一起使用。

Chai 提供數種 interfaces，供使用者選擇最習慣的方式，chai-capable BDD 風格提供的是豐富的呈現方式跟可讀性，TDD assert 風格則是提供更經典的使用方式。

[http://chaijs.com/](http://chaijs.com/)

## 安裝

```javascript
npm install --save-dev chai
```

## TDD style

### Assert

```javascript
var chai = require('chai');
var assert = chai.assert;

assert.typeOf(foo, 'string');
assert.equal(foo, 'bar');
assert.lengthOf(foo, 3)
assert.property(tea, 'flavors');
assert.lengthOf(tea.flavors, 3);
```

## BDD style

### Should

```javascript
var chai = require('chai');
chai.should();

foo.should.be.a('string');
foo.should.equal('bar');
foo.should.have.lengthOf(3);
tea.should.have.property('flavors').with.lengthOf(3);
```

### Expect

```javascript
var chai = require('chai');
var expect = chai.expect;

expect(foo).to.be.a('string');
expect(foo).to.equal('bar');
expect(foo).to.have.lengthOf(3);
expect(tea).to.have.property('flavors').with.lengthOf(3);
```