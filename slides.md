#### A talk about
# State in Apps with Redux
Stefan Schwartze<br/><br/>
*All images are under copyright of the authors in sources section*
---



## What is state?

## Sharing state between components

### Problem: state-lifting

### Solution: a central 'store'

* Remove logic from components
* Re-use logic among components
  
## Introducing Redux

* Predictable state container
* Consistent programming paradigm
* Persisting state

## How it works

### Store

### Actions

### Reducers: Creating instead of mutating

### Integrating with React

* `Provider` as wrapper
* `connect()` to access
* mapStateToProps
* mapDispatchToProps

### How does it look? 

* An Todo example

### Pros

* Straight-forward way to do things
* Easily testable (actions, reducers, selectors)
* Reduces logic in components
* Time traveling

### Cons

* Very much boilerplate code

### Usage in Linus.de

* Managing article data
* Maintaining UI state (modals etc.)
* Sharing user-generated state (sharing, bookmarking)
* Loading states

## When do I not need Redux?

* Never-changing data
* When data is not shared (`isDropdownOpen`))








