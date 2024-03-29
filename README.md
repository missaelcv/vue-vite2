# Vue1

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Presented with prompts for several optional
```sh
✔ Project name: … <your-project-name>
✔ Add TypeScript? … No / Yes
✔ Add JSX Support? … No / Yes
✔ Add Vue Router for Single Page Application development? … No / Yes
✔ Add Pinia for state management? … No / Yes
✔ Add Vitest for Unit testing? … No / Yes
✔ Add an End-to-End Testing Solution? … No / Cypress / Playwright
✔ Add ESLint for code quality? … No / Yes
✔ Add Prettier for code formatting? … No / Yes
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
### Using Vue from CDN​
You can use Vue directly from a CDN via a script tag:

```sh
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```

### Using the Global Build​
The above link loads the global build of Vue, where all top-level APIs are exposed as properties on the global Vue object. Here is a full example using the global build:

```sh
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

<div id="app">{{ message }}</div>
<script>
  const { createApp, ref } = Vue
  createApp({
    setup() {
      const message = ref('Hello vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```

### Using the ES Module Build
Throughout the rest of the documentation, we will be primarily using ES modules syntax. Most modern browsers now support ES modules natively, so we can use Vue from a CDN via native ES modules like this:

```sh
<div id="app">{{ message }}</div>
<script type="module">
  import { createApp, ref } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'
  createApp({
    setup() {
      const message = ref('Hello Vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```

### Enabling Import maps​
In the above example, we are importing from the full CDN URL, but in the rest of the documentation you will see code like this:

```sh
import { createApp } from 'vue'

We can teach the browser where to locate the vue import by using Import Maps:

<script type="importmap">
  {
    "imports": {
      "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js"
    }
  }
</script>

<div id="app">{{ message }}</div>
<script type="module">
  import { createApp, ref } from 'vue'
  createApp({
    setup() {
      const message = ref('Hello Vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```

### Splitting Up the Modules​
As we dive deeper into the guide, we may need to split our code into separate JavaScript files so that they are easier to manage. For example:

```sh
<!-- index.html -->
<div id="app"></div>
<script type="module">
  import { createApp } from 'vue'
  import MyComponent from './my-component.js'
  createApp(MyComponent).mount('#app')
</script>
```

```sh
import { ref } from 'vue'
export default {
  setup() {
    const count = ref(0)
    return { count }
  },
  template: `<div>count is {{ count }}</div>`
}
```

// If you directly open the above index.html in your browser, you will find that it throws an error because ES modules cannot work over the file:// protocol, which is the protocol the browser uses when you open a local file.

Due to security reasons, ES modules can only work over the http:// protocol, which is what the browsers use when opening pages on the web. In order for ES modules to work on our local machine, we need to serve the index.html over the http:// protocol, with a local HTTP server.

To start a local HTTP server, first make sure you have Node.js installed, then run npx serve from the command line in the same directory where your HTML file is. You can also use any other HTTP server that can serve static files with the correct MIME types.

You may have noticed that the imported component's template is inlined as a JavaScript string. If you are using VSCode, you can install the es6-string-html extension and prefix the strings with a /*html*/ comment to get syntax highlighting for them.
// 