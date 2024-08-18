# Добавление состояния (практика)

```JSX
class EmployersListItem extends Component {
    constructor(props) {
        super(props);
        this.state = {
            increase: false
        }
    }
    onIncrease = () => {
        this.setState(({increase}) => ({ //Деструктиризация чтобы не писать state.increase
            increase: !increase
        }))
    }
    render() {
        const {name,salary} = this.props;
        const {increase} = this.state;

        return (
            <div><button type="button" onClick={this.onIncrease}></button></div>
        );
    }
}
```

---

## Использование состояний для множественной записи

Чтобы сделать компоненты управляемыми, необходимо поставить атрибут value

```JSX

this.state = {
            increase: false
            name: ''
}

onIncrease = (e) => {
        this.setState({
            [e.target.name] : e.target.value; //Обратить внимание
        })
    }

render() {
    const {increase, name} = this.state;
    return(
        <div>
            <input name="name" value={increase}>
            <input name="increase" value={name}>
        </div>
    );
}
```

---

## Иммутабельность состояния и собственные состояния

### Передача props

```JSX
    App{
        deleteItem = (id) => { //Удаление из state
            this.setState(({data}) => ({
                // 1 вариант
                // const index = data.findIndex(elem => elem.id === id);
                // const before = data.slice(0, index);
                // const after = data.slice(index + 1);
                // const newArr = [...before, ...after];
                // return (
                //     data : newArr
                // )

                // 2 вариант
                return (
                    data : data.filter(item => item.id !== id)
                )
            }))
        }
        <EmployersList data={data}
    onDelete={this.deleteItem}>}  // Передача созданной функции

    // Внутренний компонент

    const EmployersList = ({data, onDelete}) => {
        const elements = data.map(item => {
            const {id, ...itemProps} = item;
            return (
                <EmployersListItem
                key={id}
                {...itemProps}
                onDelete{() => onDelete(id)}>
            )
        });
    }

    // И дальше уже во внутреннем на кнопке вызывать
```
