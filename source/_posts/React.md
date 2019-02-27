---
title: React
date: 2019-01-14 11:45:52
tags:
---

```
$ create-react-app my-app
$ cd my-app/
$ npm start
```

## Deployment
`npm run build`

**Static Server:**
```
npm install -g serve
serve -s build
```

## Integrate Bootstrap
```
npm install bootstrap

import "bootstrap/dist/css/bootstrap.css";
```

## React Plugin for Visual Studio Code
* Simple React Snippets
* Prettier - Code formatter


## React计时器
计时器要在componentDidMount生命周期方法挂上，然后在componentWillUnmount生命周期方法清除。  
下面是ES6(Class)的语法范例:
```
class Timer extends React.Component {
  constructor(props) {
    super(props);
    this.state = {secondsElapsed: 0};
  }

  tick() {
    this.setState((prevState) => ({
      secondsElapsed: prevState.secondsElapsed + 1
    }));
  }

  componentDidMount() {
    this.interval = setInterval(() => this.tick(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.interval);
  }

  render() {
    return (
      <div>Seconds Elapsed: {this.state.secondsElapsed}</div>
    );
  }
}

ReactDOM.render(<Timer />, mountNode);
```
