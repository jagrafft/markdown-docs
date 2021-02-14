# [Javascript][javascript]
## `Array`s
### `groupByKey`
```javascript
Array.prototype.groupByKey = function(k) {
    return this.reduce((g, ob) => {
        const v = ob[k];
        if (typeof g[v] === "undefined") g[v] = [];
            g[v].push(ob);
            return g;
        }, {});
    }
```

[javascript]: https://developer.mozilla.org/en-US/docs/Web/JavaScript
