### 输出输入的倒数
function reverseNumber(num) {
    return parseInt(num.toString().split('').reverse().join(''));
}

### indexOf
indexOf 是 JavaScript 字符串对象的一个方法，用于查找一个字符串在另一个字符串中第一次出现的位置。它的语法是：

javascript
string.indexOf(searchValue[, fromIndex])
searchValue：要在字符串中查找的值。
fromIndex（可选）：开始查找的位置，默认为 0。如果省略 fromIndex，则从字符串的开头开始搜索。

