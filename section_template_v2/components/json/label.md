# Render type `label` Properties only

- The `Button` type please see [here](../json.md)

| Property             | Type                  | Description                                                            | Default | Required | Example               |
| -------------------- | --------------------- | ---------------------------------------------------------------------- | ------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value *`key` must be snake_case only |         | Yes      | `agent.first_name`    |
| `renderType`         | `RenderType`          | For select component to render                                         | `text`  | No       |                       |
| `buttons`            | `Button[]`            | For render button                                                      |         | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                           |         | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                    |         | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                      |         | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                           |         | No       | `{ color: 'red' }`    |
| `hiddenDivider`      | `boolean`             | For hide divider                                                       | `false` | No       |                       |
| `center`             | `boolean`             | For center text                                                        | `false` | No       |                       |

## Example

### Simple example `label`

```json
{
  "label": "Create", // You can fill the label from first page modal of component form(in CC)
  "renderType": "label",
}
```

### Simple with buttons `label`

```json
{
  "renderType": "label",
  "buttons": [...],
}
```

### Simple with custom style and className `label`

```json
{
  "renderType": "label",
  "style": { "color": "red" },
  "className": "text-primary"
}
```

### Simple with condition `label`

```json
{
  "renderType": "button",
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"],
}
```

### Hidden divider `label`

```json
{
  "renderType": "button",
  "hiddenDivider": true
}
```

### Label center `label`

```json
{
  "renderType": "button",
  "center": true
}
```
