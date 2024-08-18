# Стили

## Inline Стили

Использовать исключительно в динамически изменяемых элементах с JSX.

Пример использования:

```JSX
    style={{fontSize: '40em', WebkitTransition: 'all', msTransition: 'all'}}
```

Важно не забывать, что возможно использование динамических классов прямо в JSX.

---

## Классовые стили (CSS/SASS)

Создание SCSS:

```SCSS
    .add-form{
        margin: auto;
        input{
            margitn-top:20px;
        }
    }
```

---

## Styled Components

```JSX
    const Wrapper = styled.div`
        width: 600px;
        margin: 80px ato 0 auto;
        a {
        display: block;
        color: #000000;
        }
        input {
            display absolute;
        }
    `;

    return (
        <Wrapper>
            <input type="text">
        </Wrapper>
    );
```

---

## React-Bootstrap

Необходимо импортировать `bootstrap.min.css`

```JSX
import {Container, Row, Col} from 'React-Bootstrap';

const BootstrapTest = () => {
    return (
        <Container>
            <Row>
            <Col>First Column</Col>
            </Row>
        </Container>
    )
};

```
