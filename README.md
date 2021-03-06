# context-x

[How to optimize shared states in React](#)

| Table of Contents             |
| :---------------------------- |
| [Examples](#examples)         |
| [Installation](#installation) |
| [Usage](#usage)               |
| [License](#license)           |

## Examples

- [Basic](https://codesandbox.io/s/context-x-example-bp0n1)

## Installation

with Yarn:

```bash
yarn add context-x
```

with npm:

```bash
npm install context-x
```

## Usage

```jsx
import { createContexts } from "context-x";

const states = {
  count: 0
};

export const contexts = createContexts(states);
```

```jsx
import React from "react";
import { Providers } from "context-x";
import { contexts } from "./contexts";
import { Counter } from "./Counter";
import { Increment } from "./Increment";

export default function App() {
  return (
    <Providers contexts={contexts}>
      <Counter />
      <Increment />
    </Providers>
  );
}
```

```jsx
import React from "react";
import { useStateContext } from "context-x";
import { contexts } from "./contexts";

export function Counter() {
  const count = useStateContext(contexts, "count");

  return <span>{count}</span>;
}
```

```jsx
import React from "react";
import { useSetStateContext } from "context-x";
import { contexts } from "./contexts";

export function Increment() {
  const setCount = useSetStateContext(contexts, "count");

  return <button onClick={() => setCount(prev => prev + 1)}>Increment</button>;
}
```

## License

context-x is licensed under the [MIT License](LICENSE)
