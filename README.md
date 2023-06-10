<p align="center">
  <img src="https://raw.githubusercontent.com/Hidekih/editorjs-viewer-native/0201fbb59a26ca1965dfcb7ef4723079bcc110ed/public/EditorJs%20Native%202.svg" alt="EditorJsNativeViewer logo" />
</p>

[![npm version](https://img.shields.io/npm/v/editorjs-viewer-native?style=flat-square)](https://badge.fury.io/js/editorjs-viewer-native)
[![npm downloads](https://img.shields.io/npm/dm/editorjs-viewer-native.svg?style=flat-square)](https://npm-stat.com/charts.html?package=editorjs-viewer-native)

# About
This lib provide a component to render in a React Native a JSON generated by [`Editor.js`](https://editorjs.io/)!

## Installation
Beta version is now available!
```cmd
npm i editorjs-viewer-native
```
or
```cmd
yarn add editorjs-viewer-native
```

## Current support for editorJs's plugins:
- [`Code`](https://github.com/editor-js/code)
- [`Delimiter`](https://github.com/editor-js/delimiter)
- [`Header`](https://github.com/editor-js/header)
- [`Image`](https://github.com/editor-js/image)
- [`Link`](https://github.com/editor-js/link)
- [`List`](https://github.com/editor-js/list)
- [`Marker`](https://github.com/editor-js/marker)
- [`Paragraph`](https://github.com/editor-js/paragraph)
- [`Personality`](https://github.com/editor-js/personality)
- [`Quote`](https://github.com/editor-js/quote)
- [`Simple Image`](https://github.com/editor-js/simple-image)
- [`Underline`](https://github.com/editor-js/underline)

## Usage
Create a component using function `createEditorJsViewer`.

```tsx
import { ScrollView } from 'react-native';
import { createEditorJsViewer } from "editorjs-viewer-native";

import dataFromEditorJs from "./data.json";

const EditorJsViewerNative = createEditorJsViewer();

export default function App() {
  return (
    <ScrollView>
      <EditorJsViewerNative data={dataFromEditorJs} />
    </ScrollView>
  );
}
```

## Custom component
If you want to use your custom component to render a data, you can define a customComponent in `createEditorJsViewer` config object.
```tsx
import { ScrollView, Text } from 'react-native';
import { createEditorJsViewer, IHeaderProps } from "editorjs-viewer-native";

import dataFromEditorJs from "./data.json";

const MyHeader = ({ data }: IHeaderProps) => {
  return <Text>{data.text}</Text>
}

const EditorJsViewerNative = createEditorJsViewer({
  toolsParser: {
    header: {
      CustomComponent: MyHeader
    }
  }
})

export default function App() {
  return (
    <ScrollView>
      <EditorJsViewerNative data={dataFromEditorJs} />
    </ScrollView>
  );
}
```
Now the component `MyHeader` will render all data of type **header**.

## Fallback for unsupported block types
If you want to show a message for unsupported blocks (good for test, bad for production) set `unknownBlockFallback` as true inside `createEditorJsViewer` config object.

```tsx
const EditorJsViewerNative = createEditorJsViewer({
  unknownBlockFallback: true
})
```



## Update plans
### Support for:
- [`Checklist`](https://github.com/editor-js/checklist)
- [`Raw HTML`](https://github.com/editor-js/raw)
- [`Table`](https://github.com/editor-js/table)
- Custom blocks

### Add more test!

## Open source
Feel free to clone/fork this project!
