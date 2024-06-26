# Render type `alert` Properties only

- The `SemanticColor`, `Button` type please see [here](../README.md)

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

## Example

### Simple example `alert`

```json
{
  "renderType": "alert"
}
```

### Simple with condition

```json
{
  "renderType": "alert",
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```

### Simple with eval condition

```json
{
  "renderType": "alert",
  "evalHidden": "!data?.renewals?.length",
  "evalDisabled": "!data?.renewals?.find(({ status }) => status[0] === 'pending')"
}
```

### Simple with content and change box color

```json
{
  "renderType": "alert",
  "color": "danger",
  "content": "This is an alert content"
}
```

### Default open alert

```json
{
  "renderType": "alert",
  "defaultOpen": true
}
```
