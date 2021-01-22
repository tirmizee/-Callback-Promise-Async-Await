# Callback-Promise-Async-Await




https://stackblitz.com/edit/react-callback?file=src%2FApp.js

```javascript

import React, { Component } from "react";

export default class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      name: "Anonymous"
    };
  }

  loadData1() {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve("1");
      }, 3000);
    });
  }

  loadData2() {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve("2");
      }, 2000);
    });
  }

  loadData3() {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve("3");
      }, 1000);
    });
  }

  async main() {
    // async
    this.loadData1().then(res => {
      this.setState({ name: res });
    });
    this.loadData2().then(res => {
      this.setState({ name: res });
    });
    this.loadData3().then(res => {
      this.setState({ name: res });
    });

    // sync
    await this.loadData1().then(res => {
      this.setState({ name: res });
    });
    await this.loadData2().then(res => {
      this.setState({ name: res });
    });
    await this.loadData3().then(res => {
      this.setState({ name: res });
    });

    // sync
    const n1 = await this.loadData1();
    this.setState({ name: n1 });
    const n2 = await this.loadData2();
    this.setState({ name: n2 });
    const n3 = await this.loadData3();
    this.setState({ name: n3 });
  }

  componentDidMount() {
    this.main();
  }

  render() {
    const { name } = this.state;
    return (
      <div>
        <h1>Hello {name}</h1>
        <p>Start sto see some magic happen :)</p>
      </div>
    );
  }
}

```

### Reference

- https://javascript.info/promise-chaining
