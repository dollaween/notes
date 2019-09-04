# Preload на react-loadable
В данном примере подгружаем компонент Bar при наведении курсора на кнопку

### App.js
``` javascript
import React, { Component } from 'react';
import Loadable from 'react-loadable';
import Loading from './components/Loading';

const LoadableBar = Loadable({
    loader: () => import('./components/Bar'),
    loading: Loading,
});

class About extends Component {
    constructor(props) {
        super(props);
        this.state = {
            showBar: false
        };
    }

    onClick = () => {
        this.setState({ showBar: true });
    }

    onMouseOver = () => {
        LoadableBar.preload();
    }

    render() {
        return (
            <div>
                <h4>About</h4>
                <button
                    onClick={this.onClick}
                    onMouseOver={this.onMouseOver}>
                    Загрузить компонент
                </button>
                { this.state.showBar && <LoadableBar /> }
            </div>
        )
    }
}

export default About;
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
        return <div>Загрузка...</div>;
    } else {
        return null;
    }
};

export default Loading;
```

