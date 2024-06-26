# Render type `input_product_type_card` Properties only

- The `CardSelectItem` type please see [here](../README.md)

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
| `evalDefaultValue`   | `string`              |                                                                         |         | No       |                       |
| `evalDisabled`       | `string`              |                                                                         |         | No       |                       |
| `singleSelect`       | `boolean`             | Set input to single select instead multiple select                      |         | No       |                       |
| `defaultValue`       | `CardSelectItem`      |                                                                         |         | No       |                       |

## Example

### Simple example `input_product_type_card`

```json
{
  "renderType": "input_product_type_card"
}
```

### Simple with condition

```json
{
  "renderType": "input_product_type_card",
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```

### With default value

```json
{
  "renderType": "input_product_type_card",
  "defaultValue": {
    "key": "motor",
    "label": "Motor"
  }
}
```

### With Eval default value

```json
{
  "renderType": "input_product_type_card",
  "evalDefaultValue": "data?.productType"
}
```

### With single select

```json
{
  "renderType": "input_product_type_card",
  "singleSelect": true
}
```
