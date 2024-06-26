# Render type `input_upload` Properties only

| Property             | Type                  | Description                                                             | Default | Required | Example               |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`    |
| `label`              | `string`              | Label for component render                                              |         | Yes      |                       |
| `renderType`         | `RenderType`          | For select component to render                                          | `text`  | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                            |         | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                     |         | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                       |         | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                            |         | No       | `{ color: 'red' }`    |
| `placeholder`        | `string`              |                                                                         |         | No       |                       |
| `name`               | `string`              |                                                                         |         | No       |                       |
| `center`             | `boolean`             | Show input is center of container                                       |         | No       |                       |
| `disabled`           | `boolean`             |                                                                         |         | No       |                       |
| `required`           | `boolean`             |                                                                         |         | No       |                       |
| `evalDisabled`       | `string`              |                                                                         |         | No       |                       |
| `multiple`           | `boolean`             | Multiple upload                                                         | `false` | No       |                       |
| `limit`              | `number`              | Limit upload                                                            | `5`     | No       |                       |
| `acceptFileType`     | `string`              | File types for allow upload                                             |         | No       |                       |

## Example

### Simple example `input_upload`

```json
{
  "renderType": "input_upload"
}
```

### Simple with condition

```json
{
  "renderType": "input_upload",
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```

### Multiple upload

```json
{
  "renderType": "input_upload",
  "multiple": true
}
```

### Specific limit upload

```json
{
  "renderType": "input_upload",
  "multiple": true,
  "limit": 10
}
```

### Set accept file type

```json
{
  "renderType": "input_upload",
  "acceptFileType": "image/*"
}
```
