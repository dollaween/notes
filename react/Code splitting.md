# Code Splitting
Разбивает общий бандл на куски. Позволяет не загружать все приложение сразу целиком.

Каждый Async*-кусок будет загружен только тогда, когда будет использован (пользователь перейдет на нужную страницу).



### App.js
```javascript
import React from 'react';
import { BrowserRouter, Switch, Route } from 'react-router-dom';
import splitter from './components/Splitter';

const AsyncHome = splitter(() => import('./pages/Home'));

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




### Splitter.js
```javascript
import React, { Component } from "react";

export default function splitter(importComponent) {
  class Splitter extends Component {
    constructor(props) {
      super(props);

      this.state = {
        component: null
      };
    }

    async componentDidMount() {
      const { default: component } = await importComponent();

      this.setState({
        component: component
      });
    }

    render() {
      const C = this.state.component;

      return C ? <C {...this.props} /> : null;
    }
  }

  return Splitter;
}
```




### Home.js
```javascript
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
