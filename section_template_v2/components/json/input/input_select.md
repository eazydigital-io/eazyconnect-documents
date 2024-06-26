# Render type `input_select` Properties only

- The `SelectItem` type please see [here](../README.md)

| Property             | Type                   | Description                                                             | Default | Required | Example                   |
| -------------------- | ---------------------- | ----------------------------------------------------------------------- | ------- | -------- | ------------------------- |
| `key`                | `string`               | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`        |
| `label`              | `string`               | Label for component render                                              |         | Yes      |                           |
| `renderType`         | `RenderType`           | For select component to render                                          | `text`  | No       |                           |
| `showOnStatus`       | `string[]`             | Show component on status ...                                            |         | No       | `['draft', 'submit']`     |
| `showOnProductTypes` | `string[]`             | Show component on product types ...                                     |         | No       | `['motor', 'health']`     |
| `className`          | `string`               | Custom class name                                                       |         | No       | `text-primary`            |
| `style`              | `React.CSSProperties`  | Custom style                                                            |         | No       | `{ color: 'red' }`        |
| `placeholder`        | `string`               |                                                                         |         | No       |                           |
| `name`               | `string`               |                                                                         |         | No       |                           |
| `center`             | `boolean`              | Show input is center of container                                       |         | No       |                           |
| `disabled`           | `boolean`              |                                                                         |         | No       |                           |
| `required`           | `boolean`              |                                                                         |         | No       |                           |
| `evalDefaultValue`   | `string`               | Default value from state                                                |         | No       |                           |
| `evalDisabled`       | `string`               |                                                                         |         | No       |                           |
| `defaultValue`       | `string`, `SelectItem` |                                                                         |         | No       |                           |
| `options`            | `(string, object)[]`   | Fixed options                                                           |         | No       |                           |
| `evalOptions`        | `string`               | Options from state value                                                |         | No       |                           |
| `entityName`         | `string`               | Entity name to get data                                                 |         | Yes      | `eazy_rfq`                |
| `entityQsFilter`     | `string`               | Entity filter string(query string url)                                  |         | No       | `$and[0][rfq][$in]=${id}` |
| `entityLimit`        | `number`               | Limit of entity data                                                    | `10`    | No       |                           |
| `entityFields`       | `string[]`             | Fields to get from entity                                               |         | No       |                           |
| `entitySort`         | `string`               | Sort of entity data                                                     |         | No       |                           |
| `fieldForLabel`      | `string`               | Field key from entity data to Label                                     |         | No       |                           |
| `fieldForValue`      | `string`               | Field key from entity data to Value                                     |         | No       |                           |
| `fieldTrigger`       | `string`               | Field key from state to trigger                                         |         | No       |                           |

## Example

### Simple example `input_select`

```json
{
  "renderType": "input_select"
}
```

### Simple with condition

```json
{
  "renderType": "input_select",
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```

### With default value

```json
{
  "renderType": "input_select",
  "defaultValue": {
    "value": "motor",
    "label": "Motor"
  }
}
```

### With Eval default value

```json
{
  "renderType": "input_select",
  "evalDefaultValue": "data?.productType"
}
```

### Fixed options

```json
{
  "renderType": "input_select",
  "options": [
    ["motor", { "value": "motor", "label": "Motor" }],
    ["health", { "value": "health", "label": "Health" }]
  ]
}
```

### Options from state

```json
{
  "renderType": "input_select",
  "evalOptions": "data?.productTypes"
}
```

### Options from entity data

```json
{
  "renderType": "input_select",
  "entityName": "eazy_rfq",
  "entityFields": ["id", "productType"],
  "fieldForLabel": "code",
  "fieldForValue": "id"
}
```
