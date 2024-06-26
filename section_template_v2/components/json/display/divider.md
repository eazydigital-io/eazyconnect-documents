# Render type `divider` Properties only

| Property             | Type                  | Description                                                                                   | Default | Required | Example               |
| -------------------- | --------------------- | --------------------------------------------------------------------------------------------- | ------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only                       |         | Yes      | `agent.first_name`    |
| `label`              | `string`              | Label for component render                                                                    |         | Yes      |                       |
| `renderType`         | `RenderType`          | For select component to render                                                                | `text`  | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                                                  |         | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                                           |         | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                                             |         | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                                                  |         | No       | `{ color: 'red' }`    |
| `evalHidden`         | `string`              | This is a string javascript condition, In a code we will use `eval` to execute this condition |         | No       |                       |

## Example

### Simple example `divider`

```json
{
  "renderType": "divider"
}
```

### Simple with condition

```json
{
  "renderType": "divider",
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```
