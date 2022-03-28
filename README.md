# React_Redux_Toolkit

### What is Redux?  

**Redux is a pattern and library for managing and updating application state, using events called "actions".**  
 It serves as a centralized store for state that needs to be used across your entire application, with rules ensuring that the state can only be updated in a predictable fashion.
 
### Why Should I Use Redux?  

The patterns and tools provided by Redux make it easier to understand when, where, why,  
and how the state in your application is being updated, and how your application logic will behave when those changes occur.

Redux guides you towards writing code that is predictable and testable, which helps give you confidence that your application will work as expected.

### When Should I Use Redux?

![Screenshot_11](https://user-images.githubusercontent.com/66359081/160364069-37d3c705-3be0-4bb4-9cf6-4786082d1247.png)

**The Redux DevTools Extension shows a history of the changes to the state in your Redux store over time.**

![Screenshot_12](https://user-images.githubusercontent.com/66359081/160364783-90a2130a-27cd-4ae6-aaac-8cf34a944b89.png)

### Action  

An action is a plain JavaScript object that has a type field. You can think of an action as an event that describes something that happened in the application.  
An action object can have other fields with additional information about what happened. By convention, we put that information in a field called payload.

``` 
const addTodoAction = {
  type: 'todos/todoAdded',
  payload: 'Buy milk'
}
``` 

### Action Creators  

An action creator is a function that creates and returns an action object. 

### Reducers 

A reducer is a function that receives the current state and an action object, decides how to update the state if  
necessary, and returns the new state: (state, action) => newState. You can think of a reducer as an event listener  
which handles events based on the received action (event) type.

![Screenshot_13](https://user-images.githubusercontent.com/66359081/160367188-d2100d87-2a0c-4de4-ab17-28144e7df111.png)

### Store 

The current Redux application state lives in an object called the store.  
The store is created by passing in a reducer, and has a method called getState that returns the current state value.

### Dispatch  

The Redux store has a method called dispatch. The only way to update the state is to call store.dispatch() and pass in an action object.

### Selectors  

Selectors are functions that know how to extract specific pieces of information from a store state value.  
As an application grows bigger, this can help avoid repeating logic as different parts of the app need to read the same data  

Selector functions receive the whole state object, and should return a value  
Selectors will re-run whenever the Redux store is updated, and if the data they return has changed, the component will re-render  

**the component will re-render any time the value returned from useSelector changes to a new reference.**

## Redux Application Data Flow  

![Screenshot_14](https://user-images.githubusercontent.com/66359081/160368487-5f803e0c-d66b-4e28-81b8-03d2e2627e69.png)
![Screenshot_15](https://user-images.githubusercontent.com/66359081/160368689-0bccca74-050e-43e8-badf-83e0b9f47610.png)

## 3 принципа redux   

-  Единый источник истины (Глобальное состояние вашего приложения хранится в дереве объектов в одном магазине .)  
-  Состояние только для чтения (Единственный способ изменить состояние - вызвать действие , объект, описывающий то, что произошло.)  
-  Изменения вносятся с помощью чистых функций (Чтобы указать, как дерево состояний преобразуется действиями, вы пишете чистые редукторы .)  
 
## разница между  flux  и mvc  

https://www.youtube.com/watch?app=desktop&v=-cZOdWjFwXw  
https://medium.com/@marina.kovalyova/flux-the-react-js-application-architecture-773f515d068d  
https://www.clariontech.com/blog/mvc-vs-flux-vs-redux-the-real-differences

## Redux Toolkit  

https://redux-toolkit.js.org/

Problems which Redux Toolkit solves:  
- Configuring a Redux store is too complicated  
- I have to add a lot of packages to get Redux to do anything useful(Redux-Thunk, DevTools)  
- Redux requires too much boilerplate code            

Redux Toolkit's createReducer and createSlice automatically use Immer internally to let you write simpler  
immutable update logic using "mutating" syntax. This helps simplify most reducer implementations.  
In order to update values immutably, your code must make copies of existing objects/arrays, and then modify the copies. 

Redux requires that we write all state updates immutably, by making copies of data and updating the copies.  
However, Redux Toolkit's createSlice and createReducer APIs use Immer inside to allow us to write "mutating"  
update logic that becomes correct immutable updates.  

Immer - https://immerjs.github.io/immer/  
Immer is a library that simplifies the process of writing immutable update logic.

Redux Toolkit allows us to write "mutating" logic in reducers. It  
doesn't actually mutate the state because it uses the Immer library,  
which detects changes to a "draft state" and produces a brand new  
immutable state based off those changes

**configureStore** - create an empty Redux store.

### RTK query  

**RTK Query** is an advanced data fetching and caching tool, designed to simplify common cases for loading data in a web application.

## Reducers  

Reducers are the most important Redux concept. A typical reducer function needs to:  
- Look at the type field of the action object to see how it should respond;  
- Update its state immutably, by making copies of the parts of the state that need to change and only modifying those copies

Since the "lookup table" approach is popular, Redux Toolkit includes a createReducer  
function similar to the one shown in the Redux docs. However, our createReducer utility  
has some special "magic" that makes it even better. It uses the Immer library internally,  
which lets you write code that "mutates" some data, but actually applies the updates immutably.  
This makes it effectively impossible to accidentally mutate state in a reducer.

**In turn, createSlice uses createReducer inside, so it's also safe to "mutate" state there as well**

## createSlice  

A function that accepts an initial state, an object of reducer functions, and a "slice name",  
and automatically generates action creators and action types that correspond to the reducers and state.  

Internally, it uses createAction and createReducer, so you may also use Immer to write "mutating" immutable updates:

Each function defined in the reducers argument will have a corresponding action  
creator generated using createAction and included in the result's actions field using the same function name.

![Screenshot_10](https://user-images.githubusercontent.com/66359081/160347852-88bd287a-84c4-4fb1-9258-4b63041fe5e0.png)

**A "slice" is a collection of Redux reducer logic and actions for a single feature in your app**  
Redux Toolkit has a function called createSlice, which takes care of the work of generating action type strings, action creator functions, and action objects.  
createSlice automatically generates action creators with the same names as the reducer functions we wrote.  
We can check that by calling one of them and seeing what it return

## createAction

A helper function for defining a Redux action type and creator.  

## Rules of Reducers 

![Screenshot_17](https://user-images.githubusercontent.com/66359081/160371535-0855d4e5-ef86-4b8c-bbf4-248f49bdd9e9.png)
![Screenshot_18](https://user-images.githubusercontent.com/66359081/160371563-9628e8f4-df40-4960-a146-dd12c2ca5be9.png)




