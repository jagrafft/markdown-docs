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

## License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

[javascript]: https://developer.mozilla.org/en-US/docs/Web/JavaScript
