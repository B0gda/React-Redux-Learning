# Реакт-фрагменты

```JSX
import {Fragment} from 'react';

return(
    <Fragment key='123'> //здесь можем назначить ключ
    </Fragment>
);

// Или

return(
    <>
    </>
)
```

---

## Реализация поиска

```JSX

    onUpdateSearch = (term) => {
        this.setState({term})
    }

    searchEmp = (items, term) => {
        if (term.length === 0) {
            return items;
        }
        return items.filter(elem => {
            return item.name.indexOf(term) > -1;
        })
    }
    return visibleData = this.searchEmp(data, term);

    return(
         <EmployersList data={data}
        onDelete={this.deleteItem}
        onToggleProp={this.onToggleProp}
        visibleData>
    )

```

Внутренний компонент

```JSX
    onUpdateSearch = (e) => {
        const term = e.target.value;
        this.setState({term}); // Установка локального состояния
        this.props.onUpdateSearch(term)
    }

    return(
        <input value={this.state.term} onChange={this.onUpdateSearch}>
    )

```

---

## Фильтры

```JSX

    filterPost = (items, filter) => {
        switch(filter){
            case 'rise':
                return items.filter(item => item.rise);
            case 'more than 1000':
                return items.filter(item => item.salary > 1000);
            default:
                return items
        }
    }

    onFilterSelect = (filter) => {
        this.setState({fiter});
    }

    const visibleData = this.filterPost(this.searchEmp(data,term), filter);

```

Внутренний компонент

```JSX
    const buttonsData = [{
        name: 'all', label: 'Все сотрудники'
    },{
        name: 'rise', label: 'На повышение'
    },{
        name: 'more than 1000', label: 'Больше 1000'
    }];

    const buttons buttonsData.map(({name,label}) => {
        const active = props.filter === name;
        const clazz = active ? 'btn-light' : 'btn-outlibe-line';
        return (
            <button type="button"
            className={`btn ${clazz}`} key={name}
            onClick={() => props.onFilterSelect(name)}> {label}
            </button>
        )
    });

    return(
        {buttons}
    )
```
