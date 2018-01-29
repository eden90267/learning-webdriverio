# BDD Style - Cucumber

- 行為驅動開發 (Behavior-driven development，縮寫為 BDD)
- 由外而內考量

```
Feature: BMI 計算機
  我想要計算我的 BMI

  Scenario: 我的身高是 "1.8"m , 體重是 "70" kg
    Given 身高是 "1.8"
    And 體重是 "70"
    When 計算兩個值的結果
    Then 結果應該是 "21.6"
```

```javascript
var chai = require('chai');
chai.should();

module.exports = function() {

  this.Given(/^身高是 "([^"]*)"$/, function(height) {
    this.height = +height;
  });

  this.Given(/^體重是 "([^"]*)"$/, function(weight) {
    this.weight = +weight;
  });

  this.When(/^計算兩個值的結果$/, function() {
    this.result = this.weight / (this.height * this.height)
  });

  this.Then(/^結果應該是 "([^"]*)"$/, function(result) {
    this.result.toFixed(1).should.be.equal(result);
  });

};
```