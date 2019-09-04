# Code Splitting

```javascript
import React from 'react';
import { BrowserRouter, Route, Switch, Link, NavLink } from 'react-router-dom';
import splitter from './core/components/Splitter/Splitter';

const AsyncHome = splitter(() => import('./pages/Home/Home'));

function App() {
    return (
        <BrowserRouter>
            <Switch>
                <Route exact path="/" component={AsyncHome} />
                <Route path="/about" component={AsyncAbout} />
            </Switch>
        </BrowserRouter>
    );
}
```
