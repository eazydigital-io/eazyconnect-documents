# Document for JSON Components

## Introduction

This document provides the information about the input text.
The input text is used to get the text input from the user.

| Property             | Type                  | Description                                                                                   | Default   | Required | Example               |
| -------------------- | --------------------- | --------------------------------------------------------------------------------------------- | --------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only                       |           | Yes      | `agent.first_name`    |
| `label`              | `string`              | Label for component render                                                                    |           | Yes      |                       |
| `renderType`         | `RenderType`          | For select component to render                                                                | `text`    | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                                                  |           | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                                           |           | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                                             |           | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                                                  |           | No       | `{ color: 'red' }`    |
| `defaultOpen`        | `boolean`             | Set first render to show alert box                                                            |           | No       |                       |
| `color`              | `SemanticColor`       | Box color                                                                                     | `default` | No       |                       |
| `content`            | `string`              | Alert content                                                                                 |           | No       |                       |
| `evalHidden`         | `string`              | This is a string javascript condition, In a code we will use `eval` to execute this condition |           | No       |                       |
| `evalDisabled`       | `string`              | This is a string javascript condition, In a code we will use `eval` to execute this condition |           | No       |                       |
| `buttons`            | `Button[]`            | For render button to the right of label                                                       |           | No       |                       |
