# React_Store_Middleware

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

Each function defined in the reducers argument will have a corresponding action  
creator generated using createAction and included in the result's actions field using the same function name.

![Screenshot_10](https://user-images.githubusercontent.com/66359081/160347852-88bd287a-84c4-4fb1-9258-4b63041fe5e0.png)

## createAction

A helper function for defining a Redux action type and creator.  



