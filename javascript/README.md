- Question 1: [useRef](#1-script-vs-script-async-vs-script-defer)
- Question 1: [prototypal inheritance](#2-explain-prototypal-inheritance)

## All Questions

### 1. script vs script async vs script defer

<details>
<summary>Answer</summary>

- async scripts fetched in order in order but execute as soon as possible and do not block the HTML parser (no render blocking), so in a sense you cannot guarantee the order of execution

- defer scripts are fetch in order as well but execute only after HTML parsing is complete, so they are executed in order (great for scripts that rely on each other)

- when you have async and defer in the same script, async takes precedence, unless browser does not support async

</details>

### 2. Explain prototypal inheritance

<details>
<summary>Answer</summary>

</details>
