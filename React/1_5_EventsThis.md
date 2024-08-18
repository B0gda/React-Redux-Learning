# Events

## Пример установки состояния

```JSX
constructor(props) {
    super(props);
    this.state = {
        years: 27,
        position: ''
    }
}
render(){
    const {position} = this.state; //Также работать с this.props
    <div>
    <h1> Posotion - {position}</h1>
        <input type="text" onChange={this.commitInputChanges}> //Работает в React как onInput
    </div>
}

commitInputChanges = (e, color) => {
    this.setState({ //Передаем обьект
        position: e.target.value;
    })
}
```

### Важно

- Работает в только PreventDefault
- Важно использовать стрелочные функции т.к. у стрелочной функции нет контекста и важно указывать на this класса
- При использовании функции обьявления, можно использовать bind:

```JSX
this.nextYear = this.nextYear.bind(this); //Бинд Функции к классу вручную если не используется стрелочная функция

onClick={() => this.nextYear()} //Но создается каждый раз новый колбек
```

### Передача аргументов

```JSX
    onChange={(e) => this.commitInputChanges(e, 'some color')}
```

---
