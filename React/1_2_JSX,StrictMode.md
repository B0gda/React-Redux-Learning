## Работа с JSX-препроцессором
В `Index.js` в первую очередь идут импорты: `React` (отвечает за внутреннюю работу и взаимосвязь файлов в реакт библиотеке), `ReactDOM` (позволяет работать с DOM структурой на странице), далее импорт стилей.

`JSX` – синтаксический сахар функции `React.createElement()`. Это расширение синтаксиса `JavaScript`. Обычно оно используется с `React` для описания элементов пользовательского интерфейса. Для `JSX` импортируем `REACT` лишь в `index.js` (с 17 версии).

---

Рендер переменной на страницу через ReactDOM

```
// const elem = <h2> Hello world</h2>;
const elem = React.createElement('h2', {classname: 'greetings'}, 'Hello World!');

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  // <React.StrictMode>
  //   <App />
  // </React.StrictMode>
  elem
);
//17 - версия
// ReactDOM.render(
//   <React.StrictMode>
//     <App />
//   </React.StrictMode>,
//   document.getElementById('root')
// );

```
У elem будут: свойства(props)( classname и children(Hello world)), type ‘h2’.

---

Пример реакт элемента-интерфейса

```const elem = <h2> Hello world</h2>;```
Нельзя вставлять обьекты лишь в элементы! (как {new Date()})
Атрибуты записываются в camelCase.
Слова `class` и `for` зарезервированы – нужно использовать `className`, `htmlFor`

Многострочная структура:
```
const elem = (
  <div>
    <h2 >Hello {textTest}!</h2>
    <input type=”text” />
    <button tabIndex=”0”></button>
  </div>
);
```

## ReactComponent

**Элементы** – структурные ячейки компонентов. Они неизменяемые. В `React` нужно именно перерисовывать элемент, а не видоизменять.

**Компонент** – блок пользовательского интерфейса, с собственным поведением. Это самостоятельная единица. Компоненты всегда пишутся с большой буквы.

**Компоненты** – это функции, которые могут возвращать `JSX-элементы`.

---

Для классов:

```
class Field2 extends Component {
  render(){
    const text = 'Log in', logged = false;
    return <button>{logged ? 'Enter' : text}</button>
  }
}
```

Для вызовов классов или функций:

```
<Field2/>
```

---

## Strict Mode – компонент

Похож по функционалу на директиву use strict

Добавление StrictMode  с помощью деструктиризации:

```
import React, {StrictMode} from 'react';
```

Активация строгого режима:

```
<React.StrictMode>
    <App />
  </React.StrictMode>
```

Помогает обнаруживать устаревшие конструкции, которые нужно избегать. При переработке проектов со старых версий реакт. Работает лишь в проектах при разработке.
Но часть сторонних библиотек тоже сейчас конфликтует с этим компонентом, например React Router.



