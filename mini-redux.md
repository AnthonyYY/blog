
#### Mini Redux Implementation

``` javascript
function createStore(reducer, defaultState = {}) {
  let state = defaultState
  const subscribers = []
  return {
    getState() {
      return state
    },
    subscribe(callback) {
      if (!subscribers.includes(callback)) {
        subscribers.push(callback)
      }
    },
    dispatch(action) {
      state = reducer(state, action)
      subscribers.forEach(callback => callback())
    }
  }
}
```

``` javascript
function reducer(todos = [], action) {
  switch (action.type) {
    case 'ADD_TODO':
      return [...todos, { text: action.text, completed: false, id: action.id }]
    case 'TOGGLE_TODO':
      const todo = todos.find(todo => todo.id === action.id)
      const todoIndex = todos.indexOf(todo)
      return [
        ...todos.slice(0, todoIndex),
        Object.assign({}, todo, { completed: !todo.completed }),
        ...todos.slice(todoIndex + 1)
      ]
  }
}

let store = createStore(reducer, [])
store.subscribe(() => {
  console.log('action dispatched')
})
store.dispatch({ type: 'ADD_TODO', text: 'do homework', id: 0 })
store.dispatch({ type: 'TOGGLE_TODO', id: 0 })
console.log(store.getState())
```
