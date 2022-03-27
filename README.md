# React_Store_Middleware

## 3 принципа redux   

-  Единый источник истины (Глобальное состояние вашего приложения хранится в дереве объектов в одном магазине .)  
-  Состояние только для чтения (Единственный способ изменить состояние - вызвать действие , объект, описывающий то, что произошло.)  
-  Изменения вносятся с помощью чистых функций (Чтобы указать, как дерево состояний преобразуется действиями, вы пишете чистые редукторы .)

## как реакт обрабатывает события  

1. React всегда добавляет одно событие для корневого элемента.  
Например у нас может быть много кликов,  но React  не добавляет много кликов , он добавляет одно событие для корневого элемента
Используется для оптимизации  работы с событием.

2. Когда мы получаем  объект события event, реакт  нам даёт обёртку синтэтикИвент.   
синтэтикИвент - это обёртка, которая прдедставляет общий API для всех браузеров   

## зачем делать eject  

## что такое midlleware  какие бывают    


**midlleware   - промежуточное програмное обеспечение которое срабатывает после диспатча и перед редьюсером. midlleware    обрабатывает асинхронную логику
и возвращает результат в редьюсер.**


Посредники (англ. middleware) предоставляют удобный механизм для фильтрации HTTP-запросов вашего приложения  
Middleware — связующее программное обеспечение, которое помогает приложению и серверу обмениваться друг с другом запросами.

https://www.itweek.ru/idea/article/detail.php?ID=51098  
https://www.4stud.info/networking/lecture6.html  
https://surf.ru/chto-takoe-middleware/
 
## разница между  flux  и mvc  

https://www.youtube.com/watch?app=desktop&v=-cZOdWjFwXw  
https://medium.com/@marina.kovalyova/flux-the-react-js-application-architecture-773f515d068d  
https://www.clariontech.com/blog/mvc-vs-flux-vs-redux-the-real-differences

##  отличие thunk  от saga  
https://overcoder.net/q/358476/%D0%B2-%D1%87%D0%B5%D0%BC-%D1%80%D0%B0%D0%B7%D0%BD%D0%B8%D1%86%D0%B0-%D0%BC%D0%B5%D0%B6%D0%B4%D1%83-redux-thunk-%D0%B8-redux-saga#:~:text=%D0%9A%D0%B0%D0%BA%20Redux%20Thunk%2C%20%D1%82%D0%B0%D0%BA%20%D0%B8,%D0%BE%20%D0%B1%D0%BE%D1%80%D1%8C%D0%B1%D0%B5%20%D1%81%20%D0%BF%D0%BE%D0%B1%D0%BE%D1%87%D0%BD%D1%8B%D0%BC%D0%B8%20%D1%8D%D1%84%D1%84%D0%B5%D0%BA%D1%82%D0%B0%D0%BC%D0%B8.&text=%D0%A1%D0%B0%D0%B3%D0%B0%20%D0%B4%D0%B5%D0%BB%D0%B0%D0%B5%D1%82%20%D1%82%D1%80%D0%B8%D0%B2%D0%B8%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%BC%20%D0%BE%D1%82%D0%BC%D0%B5%D0%BD%D1%83%20%D1%8D%D1%84%D1%84%D0%B5%D0%BA%D1%82%D0%B0,%D0%B7%D0%B0%D0%B2%D0%B8%D1%81%D0%B8%D1%82%20(%D1%82%D0%B0%D0%B2%D1%82%D0%BE%D0%BB%D0%BE%D0%B3%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8)%20%D0%BE%D1%82%20%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%B0.   

https://medium.com/@shoshanarosenfield/redux-thunk-vs-redux-saga-93fe82878b2d

https://qna.habr.com/q/407081  

Redux-Thunk, который использует функции обратного вызова, поток Redux-Saga можно запускать, приостанавливать и отменять из основного приложения с помощью обычных действий Redux. 

Преимущество Redux-Saga по сравнению с Redux-Thunk заключается в том, что вы можете избежать ада обратного вызова  
Кроме того, вы можете более легко протестировать свой асинхронный поток данных.  
Redux-Thunk возвращает обещания, которые сложнее проверить.   
Redux-Thunk, однако, отлично подходит для небольших случаев использования  

https://medium.com/@shoshanarosenfield/redux-thunk-vs-redux-saga-93fe82878b2d

сага позволяет контролировать поток запроса за счёт своих методов +  сагах проще делать интеграционные тесты  
redux-thunk  у него нету понятия как поток не контролирует поток запроса

Redux-thunk vs Redux-saga  
https://medium.com/@shoshanarosenfield/redux-thunk-vs-redux-saga-93fe82878b2d

https://russianblogs.com/article/7913978121/

## Redux Toolkit  

https://redux-toolkit.js.org/

Problems which Redux Toolkit solves:  
- Configuring a Redux store is too complicated  
- I have to add a lot of packages to get Redux to do anything useful(Redux-Thunk, DevTools)  
- Redux requires too much boilerplate code            

Redux requires that we write all state updates immutably, by making copies of data and updating the copies.  
However, Redux Toolkit's createSlice and createReducer APIs use Immer inside to allow us to write "mutating"  
update logic that becomes correct immutable updates.  

Immer - https://immerjs.github.io/immer/

Redux Toolkit allows us to write "mutating" logic in reducers. It  
doesn't actually mutate the state because it uses the Immer library,  
which detects changes to a "draft state" and produces a brand new  
immutable state based off those changes

**configureStore** - create an empty Redux store.

