# React Loadable
Разбивает бандл на части. Вместо загрузки всего приложения, позволяет загружать только те части, которые используются в данный момент.

### App.js
``` javascript
import React from 'react';
import { BrowserRouter, Switch, Route } from 'react-router-dom';
import Loadable from 'react-loadable';
import Loading from './components/Loading';

const AsyncHome = Loadable({
    loader: () => import('./pages/Home/Home'),
    loading: Loading
});

function App() {
    return (
        <BrowserRouter>
            <Switch>
                <Route exact path="/" component={AsyncHome} />
            </Switch>
        </BrowserRouter>
    );
}
```





### Loading.js
``` javascript
import React from 'react';

const Loading = props => {
    if (props.error) {
        return (
            <div>
                При загрузке произошла ошибка! <button onClick={props.retry}>Повторить</button>
            </div>
        );
    } else if (props.timedOut) {
        return (
            <div>
                Время ожидания истекло... <button onClick={props.retry}>Повторить</button>
            </div>
        );
    } else if (props.pastDelay) {
        return <div>Loading...</div>;
    } else {
        return null;
    }
};

export default Loading;
```





### Home.js
``` javascript
import React, { Component } from 'react';

class Home extends Component {
    render() {
        return (
            <div>
                <h4>Home</h4>
            </div>
        )
    }
}

export default Home;
```
