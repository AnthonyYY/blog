### Vue 响应式系统原理

``` javascript

class Dep {
  constructor() {
    this.subscribers = []
  }

  depend() {
    if (target && !this.subscribers.includes(target)) {
      this.subscribers.push(target)
    }
  }

  notify() {
    this.subscribers.forEach(sub => sub())
  }
}

let data = {
  price: 5,
  quantity: 2
}
let total = 0
let target = null

Object.keys(data).forEach(key => {
  let internalValue = data[key]
  let dep = new Dep()
  Object.defineProperty(data, key, {
    get() {
      dep.depend()
      return internalValue
    },
    set(newVal) {
      internalValue = newVal
      dep.notify()
    }
  })
})

watcher(() => (total = data.quantity * data.price))

console.log(total) // 10

data.price = 20

console.log(total) // 40

function watcher(toWatch) {
  target = toWatch
  target()
  target = null
}

```
