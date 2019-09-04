# Code Splitting

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
