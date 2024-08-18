# Взаимодействие родительской и дочерних компонент

## Подьем состояний

Главный компонент

```JSX
    onToggleProp = (id, prop) => {
        this.setState(({data}) => ({
           data: data.map(item => {
                if (item.id === id) {
                    return {...item,  [prop]: !item[prop]}
                }
                return item;
           })
        })
    }
    const empoyees = this.state.data.length;
    const increased = this.state.data.filter(elem => elem.increase).length;
    return(
        <AppInfo empoyees={empoyees} increased={increased}>
        <EmployersList data={data}
        onDelete={this.deleteItem}
        onToggleProp={this.onToggleProp}>
    )
```

Внутренний компонент

```JSX
     const EmployersList = ({data, onDeleteб onToggleProp}) => {
        const elements = data.map(item => {
            const {id, ...itemProps} = item;
            return (
                <EmployersListItem
                key={id}
                {...itemProps}
                onDelete{() => onDelete(id)}
                onToggleProp={(e) => onToggleProp(id, e.currentTarget.getAttribute('data-toggle'))}
            )
        });
    }
```

Нижний внутренний компонент

```JSX
    const {onToggleProp, increase, rise} = props;

    // data-toggle="rise" onClick={onToggleProp}
    // data-toggle="increase onClick={onToggleProp}
```
