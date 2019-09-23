*A talk about*
### State in Apps with 
## **Redux**
Stefan Schwartze<br/><br/>
---

## What is state?
----

### UI State 
* Dropdowns
<!-- .element: class="fragment" -->
* Modals
<!-- .element: class="fragment" -->
* Menus
<!-- .element: class="fragment" -->  
* Forms
<!-- .element: class="fragment" -->
----

### Data State 
* Data from APIs
<!-- .element: class="fragment" -->
* User data
<!-- .element: class="fragment" -->
* Loading state
<!-- .element: class="fragment" -->
* History state
<!-- .element: class="fragment" -->
----

## Sharing state between components
Note:
* Show loading state in different components that display user data
* Integrate user data in whole site
* Close menu when opening a modal
----

### (*React*) Problem: state-lifting
----

![alt Data flow](https://miro.medium.com/max/2374/1*V6uDY-ljsQBBe56Fl3xC-A.png)
---

### Solution: a central 'store'

* Remove logic from components
* Re-use logic among components
* Access from every component
----
  
## Introducing **Redux**
----

* Predictable state container
<!-- .element: class="fragment" -->
* Consistent programming paradigm
<!-- .element: class="fragment" -->
* Persisting state
<!-- .element: class="fragment" -->

Note:
* Predictable: know whats coming next
----

## How it works
----

### Store
* Object describing a state
```js
{
    todos: [{
        text: 'Eat food',
        completed: true
    }, {
        text: 'Exercise',
        completed: false
    }],
    visibilityFilter: 'SHOW_COMPLETED'    
}
```
----

### Actions
----

* Simple object describing **type** of action and (optional) **payload**
```js
{ type: 'ADD_TODO', text: 'Go to swimming pool' }
{ type: 'TOGGLE_TODO', index: 1 }
{ type: 'SET_VISIBILITY_FILTER', filter: 'SHOW_ALL' }
```
----

### Reducers 
----
* Creates a new state with modifications as described in action
```js
function todos(state = [], action) {
  switch (action.type) {
    case 'ADD_TODO':
      return state.concat([{ text: action.text, completed: false }])
    case 'TOGGLE_TODO':
      return state.map((todo, index) =>
        action.index === index
          ? { text: todo.text, completed: !todo.completed }
          : todo
      )
    default:
      return state
  }
}
```
----

### Dispatcher
* Provided by Redux
* Used to call actions
```js
store.dispatch({
    type: 'SET_VISIBILITY_FILTER',
    filter: 'SHOW_COMPLETED'
})
```
----

### Three principles
* Single source of truth
<!-- .element: class="fragment" -->
* State is read-only
<!-- .element: class="fragment" -->
* Changes are made with pure functions
<!-- .element: class="fragment" -->
---

### Integrating with React

* `Provider` as wrapper
* `connect()` to access
  * mapStateToProps
  * mapDispatchToProps
---

### How does it look? 

* [An Todo example](http://zalmoxisus.github.io/examples/todomvc/)
Note:
* [Codesandbox](https://codesandbox.io/s/github/reactjs/redux/tree/master/examples/todomvc)
----

### Pros

* Straight-forward way to do things
<!-- .element: class="fragment" -->
* Easily testable (actions, reducers, selectors)
<!-- .element: class="fragment" -->
* Reduces logic in components
<!-- .element: class="fragment" -->
* Time traveling
<!-- .element: class="fragment" -->
* Easy plugging of middlewares
<!-- .element: class="fragment" -->

Note:
* Runs environment independently (client, server)
* Not dedicated to a specific library
----

### Cons

* Very much boilerplate code
<!-- .element: class="fragment" -->
* Restricted way of doing things
<!-- .element: class="fragment" -->
---

### Usage in Linus.de

* Managing article data
* Maintaining UI state (modals etc.)
* Sharing user-generated state (sharing, bookmarking)
* Loading states
---

## When do I not need Redux?

* Never-changing data
<!-- .element: class="fragment" -->
* When data is not necessarily shared (isDropdownOpen))
<!-- .element: class="fragment" -->
---

## Sources

* [Thinking in React](https://medium.com/@nimelrian/thinking-in-react-a-paradox-statement-33c19e2eb9e2)
* [Getting started with Redux](https://redux.js.org/introduction/getting-started)






