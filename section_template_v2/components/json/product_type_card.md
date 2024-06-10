# Render type `step` Properties only

- The `FieldData` type please see [here](../json.md)

| Property             | Type                  | Description                                                             | Default | Required | Example               |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`    |
| `label`              | `string`              | Label for component render                                              |         | Yes      |                       |
| `renderType`         | `RenderType`          | For select component to render                                          | `text`  | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                            |         | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                     |         | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                       |         | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                            |         | No       | `{ color: 'red' }`    |
| `hiddenIcon` | `boolean`     | For hide icon                 | `false` | No       |         |
| `left`       | `FieldData[]` | For render left side of card  |         | Yes      |         |
| `right`      | `FieldData[]` | For render right side of card |         | No       |         |

## Example

### Simple example

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"],
  "showOnProductTypes": ["motor", "health"],
  "renderType": "product_type_card",
  "hiddenIcon": false,
  "left": [
    { "key": "productType.code", "valueType": "product_type", "className": "text-xs text-primary font-semibold" },
    { "textTemplate": "${agency.firstName} ${agency.lastName}" },
    { "key": "rfqNo", "valueType": "doc_no", "className": "text-primary" },
    { "key": "updatedAt", "valueType": "date", "label": "last_update", "className": "text-[10px] text-gray-500" }
  ],
  "right": [
    { "type": "blank" },
    { "key": "status", "valueType": "status" }
  ]
}
```
