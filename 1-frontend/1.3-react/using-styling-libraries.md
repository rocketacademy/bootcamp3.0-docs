# Using Styling Libraries

Learning Objectives

1. Understand what React-Bootstrap is
2. Implement React-Bootstrap into React Applications
3. Using React-Bootstrap pre-styled components

### React Bootstrap

React Bootstrap is a popular frontend styling library, it contains pre-built style and functionalities for out of the box easy implementation. This tool is integrated well with ReactJs and is geared for beginners to test out and implement styling libraries. Developers are even able to customize Bootstrap within custom scss stylesheets, feel free to learn more about it [here](https://react-bootstrap.github.io/getting-started/introduction#customize-bootstrap).&#x20;

To implement React Bootstrap into a React application open a CLI interface and change directory to your current project. Here you can run this command:

```
npm install react-bootstrap bootstrap
```

This will install React Bootstrap and the bootstrap package within the application, there is still one more step that must be taken before you can utilise all of React-Bootstrap in your app.

Go to the index.js within your React application and this line at the top of the file:

```jsx
import 'bootstrap/dist/css/bootstrap.min.css';
```

This line imports the CSS for bootstrap into your application, any child components of this file will be able to access and utilise React-Bootstrap styling, pre-made components, utilities and alignment system.&#x20;

Now that Bootstrap has been implemented in your application it might be a good idea to look at some of the pre-styled components you can implement, look at some examples and usage [here](https://react-bootstrap.github.io/components/alerts/).

To showcase implementing React Bootstrap into a React Application we will implement some new styled buttons on our previously edited boilerplate code from our previous section.

We will import Button from react-bootstrap such that we get pre-styled buttons without much effort. Alter the App.js file to reflect code below:

{% code lineNumbers="true" %}
```jsx
import logo from "./logo.svg";
import "./App.css";
import { Button } from "react-bootstrap";

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p style={{ color: "Red", fontWeight: "bold" }}>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <Button variant="primary">Bootstrap Button</Button>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```
{% endcode %}

The output on the browser is as follows:

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-15 at 3.25.08 PM.png" alt=""><figcaption><p>React Bootstrap Button</p></figcaption></figure>

From the image above we can see a new blue button has been added into the application, we didnt style this button, it was all React-Bootstrap. This is how you can utilise React-Bootstrap within a React application. Utilise more complex components using this styling library to save yourself time during development.

One of the most powerful features of React-Bootstrap is its grid system, which facilitates mobile responsive websites without having to restyle every single element on your page. Learn more about the grid system:

{% embed url="https://react-bootstrap.netlify.app/layout/grid/#auto-layout-columns" %}
React-Bootstrap Grid System
{% endembed %}

When implementing the grid system be sure to:

1. Use a react-bootstrap container
2. Use rows and columns to display your information
   1. Note that each row could be broken into 12 columns
   2. Each section can take up multiple spaces
3. Wire-framing and planning out how your component will look will make using grid easier



Checkout more React-Bootstrap Components [here](https://react-bootstrap.netlify.app/components/alerts/). Use a combination of pre-styled and custom components to quickly develop applications that can be tailored to your need, be aware of the props that you can pass. Constantly run your React application to see whether or not your application is being styled appropriately. And remember when styling with React-Bootstrap you just need to import the component's that you need at the top of the page, then you can use them like normal HTML tags in your JSX.





###
