# Mini Query

A mini element query selector.

```javascript
function $(query) {
  var res = [];
  if (document.querySelectorAll) {
    res = document.querySelectorAll(query);
  } else {
    var firstStyleSheet = document.styleSheets[0] || document.createStyleSheet();
    query = query.split(',');
    for(var i = 0, len = query.length; i < len; i++) {
      firstStyleSheet.addRule(query[i], 'Barret:Lee');
    }
    for (var i = 0, len = document.all.length; i < len; i++) {
      var item = document.all[i];
      item.currentStyle.Barret && res.push(item);
    }
    firstStyleSheet.removeRule(0);
  }
  if(res.item) { /* Fuck IE8 */
    var ret = [];
    for(var i = 0, len = res.length; i < len; i++){
      ret.push(res.item(i));
    }
    res = ret;
  }
  return res;
};
```

## Install 

- `npm install mini-query`
- `git clone https://github.com/barretlee/MiniQuery`

## Usage

```html
<script src="./index.js"></script>
<script>
  console.log($('.box .item a.pink'));
</script>
```

## LICENSE 

MIT.