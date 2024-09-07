It is a mechanism for calling a method on another method of the **same** object
`computeTotalAmount().lacs(10).thousand(5).crore(2).value()

```js
const computeTotalAmount = function(){
    let totalAmount = 0;
    return {
        lacs: function(amount){
            totalAmount += amount * 100000
            return this
        },
        thousand: function(amount){
            totalAmount += amount * 1000
            return this
        },
        crore: function(amount){
            totalAmount += amount * 10000000
            return this
        },
        value: function(){
            return totalAmount
        }
    }
}

const result = computeTotalAmount().lacs(10).thousand(5).crore(2).value()
console.log(result);
```