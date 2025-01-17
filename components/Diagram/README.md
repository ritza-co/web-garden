# 🚀  Astro — Diagrams with Mermaid JS 🧜🏻‍♀️

[![NPM](https://img.shields.io/npm/v/astro-diagram)](https://www.npmjs.com/package/astro-diagram)
![Downloads](https://img.shields.io/npm/dt/astro-diagram.svg)
[![ISC License](https://img.shields.io/npm/l/astro-diagram)](https://github.com/JulianCataldo/web-garden/blob/develop/LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://makeapullrequest.com)  
[![Astro](https://img.shields.io/badge/Astro-333333.svg?logo=astro)](https://astro.build)
[![TypeScript](https://img.shields.io/badge/TypeScript-333333.svg?logo=typescript)](http://www.typescriptlang.org/)
[![Prettier](https://img.shields.io/badge/Prettier-333333.svg?logo=prettier)](https://prettier.io)
[![EditorConfig](https://img.shields.io/badge/EditorConfig-333333.svg?logo=editorconfig)](https://editorconfig.org)
[![ESLint](https://img.shields.io/badge/ESLint-3A33D1?logo=eslint)](https://eslint.org)

Embed your Mermaid diagrams in no time inside your Astro templates.  
Features **server-side rendering** and **smart caching**.  
Available as a stand-alone component or as an MDX plugin, replacing `mermaid` code blocks on-the-fly.

---

Uses the [`mermaid`](https://github.com/mermaid-js/mermaid) library and puppeteer under the hood.

> **Warning**  
> 🚧  Still in **beta**.

## 📦  Installation

```sh
pnpm i mermaid astro-diagram
```

## 🛠  Usage

```astro
---
import { Diagram, type Config } from 'astro-diagram';

const config = {
  theme: 'forest',
  // ...
} as Config;

const code = `
sequenceDiagram
Alice ->> Bob: Hello Bob, how are you?
Bob-->>John: How about you John?
Bob--x Alice: I am good thanks!
Bob-x John: I am good thanks!
Note right of John: Bob thinks a long<br/>long time, so long<br/>that the text does<br/>not fit on a row.

Bob-->Alice: Checking with John...
Alice->John: Yes... John, how are you?`;

// ...
---
```

```astro
<!-- ... -->
<body>
  <!-- Place component inside `BODY` tag -->

  <Diagram config={config} code={code /* required */} />

  <!-- ... -->
</body>
```

### With MD(X) code block

> **Warning**  
> This is still a work-in-progress.  
> Some rendering bugs and inconsistencies remain.

In your `astro.config.{ts,mjs}`:

```js
import remarkMermaid from 'astro-diagram/remark-mermaid';
// ...

export default defineConfig({
  // ...
  markdown: {
    remarkPlugins: [
      // remarkGfm,

      remarkMermaid,

      // ...
    ],
  },
  // ...
});
```

Then, in your MD(X), use the `mermaid` language for your code fences, exactly like you would on GitHub flavored Markdown for example.

<div class="git-only">

## 🎉  Result

```mermaid
sequenceDiagram
Alice ->> Bob: Hello Bob, how are you?
Bob-->>John: How about you John?
Bob--x Alice: I am good thanks!
Bob-x John: I am good thanks!
Note right of John: Bob thinks a long<br/>long time, so long<br/>that the text does<br/>not fit on a row.

Bob-->Alice: Checking with John...
Alice->John: Yes... John, how are you?
```

</div>

## To do

- [x] Offline / Node package import of mermaid instead of CDN (`headless-mermaid` related).
      [See Issue #43](https://github.com/JulianCataldo/web-garden/issues/43)
- [x] Improve Astro **MDX** integration  
       Refs.:  
       See https://github.com/sjwall/mdx-mermaid  
       Unist visit: https://github.com/sjwall/mdx-mermaid/blob/main/src/mdxast-mermaid.ts
- [ ] Fix styling and layout bugs
- [ ] Support dark / light color mode
- [ ] Full TypeScript compliance
- [ ] Test mermaid configs.

<div class="git-footer">

---

## [LIVE DEMO  🎭  DOCUMENTATION WEBSITE ⎋](https://code.juliancataldo.com/)

[![Live demo website](https://code.juliancataldo.com/poster.png)](https://code.juliancataldo.com)

**_[`code.juliancataldo.com`](https://code.juliancataldo.com/)_**

---

🔗  [JulianCataldo.com](https://www.juliancataldo.com/)

</div>
