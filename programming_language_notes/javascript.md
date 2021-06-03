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

### `rangedRandom`
See <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random#getting_a_random_number_between_two_values" target=_blank>MDN getting a random number between two values</a>

```javascript
rangedRandom = (min, max) => Math.random() * (max - min) + min
```

### `randomProbArray`
Produce an array of `n` values that sum to 1.0. Uses `rangedRandom` above.

```javascript
randomProbArray = (n) => {
    let prob = 1.0
    let output = []
    
    for (let i = 0; i < n; ++i) {
        if (i === (n-1)) {
            output.push(prob)
        } else {
            const r = rangedRandom(0,prob)
            output.push(r)
            prob -= r
        }
    }
    return output
}
```

## License
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">Creative Commons Attribution-NonCommercial 4.0 International License</a>.

[javascript]: https://developer.mozilla.org/en-US/docs/Web/JavaScript
