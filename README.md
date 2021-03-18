# vue3-mermaid

> flowchart of mermaid with vue componet

## Requirements

- [Vue.js](https://github.com/vuejs/vue)
- [mermaid](https://github.com/knsv/mermaid)

## Install Setup

```bash
# install dependencies
npm install --save vue3-mermaid

```

## Usage

### Register component

```js
import Vue3Mermaid from "vue3-mermaid";
Vue.use(Vue3Mermaid);
```

### Use component

```js
export default {
  data: function() {
    return {
      data: [
        {
          id: "11",
          text: "A",
          link: "---",
          next: ["2"],
          editable: true,
          style: "fill:#f9f,stroke:#333,stroke-width:4px",
        },
        { id: "22", text: "B", edgeType: "circle", next: ["3"] },
        { id: "33", text: "C", next: ["4", "6"] },
        { id: "44", text: "D", link: "-- This is the text ---", next: ["5"] },
        { id: "55", text: "E" },
        { id: "66", text: "F" }
      ]
    };
  },
  methods: {
    editNode(nodeId) {
      alert(nodeId);
    }
  }
};
```
#### Different link values of next:

```vue
nodes: [
        {
          id: "1",
          text: "A",
          link: ["-- yes -->", "-- no -->"],
          linkNumber: 1,
          linkStyle: "fill:none,stroke:red,stroke-width:1px;",
          next: ["2", "3"],
          editable: true
        },
        { id: "2", text: "B" },
        { id: "3", text: "C"}
      ],
```

### Template

```vue
<template>
  <vue3-mermaid
    :nodes="data"
    type="graph LR"
    @nodeClick="editNode"
  ></vue3-mermaid>
</template>
```

### Group Type

```js
export default {
  data: function() {
    return {
      data: [
        {
          id: "1",
          text: "A",
          link: "---",
          next: ["2"],
          group: "one"
        },
        { id: "2", text: "B", edgeType: "circle", next: ["3"], group: "one" },
        { id: "3", text: "C", next: ["4", "6"], group: "two" },
        {
          id: "4",
          text: "D",
          link: "-- This is the text ---",
          next: ["5"],
          group: "two"
        },
        { id: "5", text: "E", group: "three" },
        { id: "6", text: "F", group: "three", , url: "http://www.github.com" }
      ]
    };
  }
};
```

### Theme

- To change theme, you can pass in a config object, for available themes, you can refer to [mermaidjs themes](https://github.com/mermaid-js/mermaid/tree/master/src/themes)

```vue
<template>
  <vue3-mermaid
    type="graph LR"
    :config="config"
  ></vue3-mermaid>
</template>
```

```js
export default {
  data: function() {
    return {
      config: {
        theme: 'neutral'
      }
    };
  }
};
```


## Build Setup

```bash
# install dependencies
npm install

# build for production with minification
npm run build
```
