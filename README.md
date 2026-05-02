LuminaUI

LuminaUI is a lightweight, Flutter-inspired UI library for building web interfaces using vanilla JavaScript and HTML.

It provides a structured, composable layout system—similar to Flutter’s widget tree—while staying close to the DOM with zero dependencies.

---

✨ Why LuminaUI?

Modern web UI development often becomes:

- fragmented (HTML + CSS + JS everywhere)
- inconsistent (different layout patterns across components)
- overly complex (heavy frameworks for simple apps)

LuminaUI focuses on:

- Clarity — predictable, composable UI structure
- Consistency — unified layout system (Column, Row, etc.)
- Simplicity — no build tools, no framework overhead
- Control — direct DOM output using vanilla JavaScript

---

🧱 Core Concepts

LuminaUI follows a widget-based composition model:

Column([
  Text("Hello World"),
  Button({ text: "Click Me", onClick: handleClick })
])

Instead of mixing HTML, CSS, and JS, you build UI using pure JavaScript functions.

---

🚀 Example

import { Column, Row } from "./widgets/layout.js";
import { Button } from "./widgets/controls.js";
import { Text } from "./widgets/text.js";
import { createState } from "./core/state.js";
import { mount } from "./core/renderer.js";

const [count, setCount, subscribe] = createState(0);

function App(update) {
  subscribe(update);

  return Column([
    Text("Count: " + count()),

    Row([
      Button({
        text: "+",
        onClick: () => setCount(count() + 1)
      }),
      Button({
        text: "-",
        onClick: () => setCount(count() - 1)
      })
    ])
  ]);
}

const root = document.getElementById("app");

let update;
update = mount(() => App(update), root);

---

📦 Project Structure

lumina-ui/
│
├── core/
│   ├── element.js      # DOM creation utilities
│   ├── renderer.js     # mount/update logic
│   └── state.js        # reactive state system
│
├── widgets/
│   ├── layout.js       # Column, Row, layout primitives
│   ├── controls.js     # Button, Input, etc.
│   └── text.js         # Text rendering
│
├── app/
│   └── App.js          # application code
│
├── main.js             # entry point
└── index.html

---

🧩 Available Widgets

Layout

- "Column(children)"
- "Row(children)"

Basic

- "Text(value)"
- "Button({ text, onClick })"

«More widgets (Padding, Expanded, Stack) are planned.»

---

⚙️ How It Works

LuminaUI is built on three core primitives:

- Element factory → creates DOM nodes
- Renderer → mounts and updates UI
- State system → triggers re-renders

There is:

- no virtual DOM
- no compilation step
- no external dependencies

---

🛠️ Getting Started

1. Clone the repository:

git clone https://github.com/<your-username>/lumina-ui.git
cd lumina-ui

2. Open "index.html" in your browser

«No build step required.»

---

📌 Design Goals

- Minimal surface area
- Predictable behavior
- Framework-like structure without framework complexity
- Easy to read and reason about

---

⚠️ Current Limitations

LuminaUI is experimental and currently lacks:

- partial DOM diffing (full re-render on update)
- component-level state isolation
- advanced layout primitives
- lifecycle management

These are active areas of development.

---

🧭 Roadmap

- [ ] Padding, Expanded, Center widgets
- [ ] Improved rendering (diffing)
- [ ] Component isolation
- [ ] Theming system
- [ ] Basic routing

---

🤝 Contributing

Contributions, ideas, and feedback are welcome.

Please open an issue or submit a pull request.

---

📄 License

MIT License

---

💡 Vision

LuminaUI aims to bring a structured, Flutter-inspired development model to the web—without abandoning the simplicity and power of vanilla JavaScript.
