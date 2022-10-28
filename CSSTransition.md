```js
import React, { Componenet } from 'react';
import { CSSTransition } from 'react-transition-group';

export default Transition from Componenet {

  render() {
    const { show, timeout, children, unmountOnExit = true } = this.props;
    return  (<CSSTransition
      in={show}
      unmountOnExit={unmountOnExit}
      timeout={timeout}
      classNames="transition"
    >
      { children }
    </CSSTransition>)
  }

}

```

```css
.transition-enter {
    opacity: 0;
    -webkit-transform: translate(-50%, -100%) translateZ(0);
    transform: translate(-50%, -100%) translateZ(0);
  }

  .transition-enter-active {
    opacity: 1;
    -webkit-transform: translate(-50%, -50%) translateZ(0);
    transform: translate(-50%, -50%) translateZ(0);
    -webkit-transition: opacity 200ms ease-out, -webkit-transform 200ms ease-out;
    transition: opacity 200ms ease-out, transform 200ms ease-out;
  }

  .transition-exit {
    opacity: 1;
    -webkit-transform: translate(-50%, -50%) translateZ(0);
    transform: translate(-50%, -50%) translateZ(0);
  }
  .transition-exit-active {
    opacity: 0;
    -webkit-transform: translate(-50%, -100%) translateZ(0);
    transform: translate(-50%, -100%) translateZ(0);
    -webkit-transition: opacity 200ms ease-in, -webkit-transform 200ms ease-in;
    transition: opacity 200ms ease-in, transform 200ms ease-in;
  }
```
