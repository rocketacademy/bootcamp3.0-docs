# 2.5: React Higher-Order Components

## Introduction

We use higher-order components (HOCs) like modular wrappers for our app logic. HOCs are components that are passed 1 or more other components as props.

## Example

We'll create a Higher Order Modal component that we can use anywhere. When we want any set of elements to appear inside a modal we can pass that Modal component function the component we want it to surround.

### App.js

On line 9 we pass our HOC the component we want it to surround, `Message`.

```jsx
import "./styles.css";
import Modal from "./components/Modal/Modal.jsx";
import Message from "./components/Message.jsx";

export default function App() {
  return (
    <div className="App">
      <h1>Hello HOC Example</h1>
      {Modal(Message)}
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer libero
        leo, faucibus ac eleifend et, commodo sit amet est. Aliquam gravida ut
        turpis ac ornare. Cras pharetra ornare ultrices. Integer vestibulum
        augue non est scelerisque fermentum. Aenean ipsum nibh, rutrum in
        hendrerit ac, aliquet in est. Nullam tincidunt nibh nunc, vitae viverra
        velit viverra vitae. Nam dictum urna eu purus blandit interdum. Sed sed
        convallis velit. In lobortis aliquam felis, quis convallis eros
        tincidunt faucibus. Morbi laoreet congue ante non posuere.
      </p>
    </div>
  );
}
```

### Message.jsx

`Message` is just a div with text. We want this text inside the modal.

```jsx
export default function Message() {
  return (
    <div>
      i meant to do that now i shall wash myself intently. Your pillow is now my
      pet bed. Kitty poochy catching very fast laser pointer the dog smells bad
      but damn that dog lick the other cats, yet cats are a queer kind of folk
      yet lick the plastic bag. Nyan fluffness ahh cucumber! spill litter box.
    </div>
  );
}
```

### Modal.jsx

`Modal` component has it's own state that determines if it is open or not.

```jsx
import "./styles.css";
import { useState } from "react";

export default function Modal(ChildComponent) {
  const [isVisible, setIsVisible] = useState(true);
  if (isVisible) {
    return (
      <div className="modal-container">
        <div className="modal">
          <button className="modal-close" onClick={() => setIsVisible(false)}>
            x
          </button>
          <ChildComponent />
        </div>
      </div>
    );
  } else {
    return (
      <div>
        <button onClick={() => setIsVisible(true)}>Open Modal</button>
      </div>
    );
  }
}
```

### Modal CSS

```css
.modal-container {
  width: 100%;
  height: 100vh;
  position: absolute;
  top: 0;
}
.modal {
  margin: 30px auto;
  padding: 30px;
  background-color: white;
  width: 70%;
  height: 70vh;
  position: relative;
}
.modal-close {
  position: absolute;
  top: 5px;
  right: 5px;
}
```

See a full working example here: [https://codesandbox.io/s/floral-lake-3ppbd](https://codesandbox.io/s/floral-lake-3ppbd)

## Further Reading

Read more about HOCs in official React documentation [here](https://reactjs.org/docs/higher-order-components.html).
