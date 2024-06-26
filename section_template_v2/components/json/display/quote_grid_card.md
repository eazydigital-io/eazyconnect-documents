# Render type `quote_grid_card` Properties only

- The `FieldData` type please see [here](../README.md)

| Property             | Type                  | Description                                                             | Default | Required | Example               |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`    |
| `label`              | `string`              | Label for component render                                              |         | Yes      |                       |
| `renderType`         | `RenderType`          | For select component to render                                          | `text`  | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                            |         | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                     |         | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                       |         | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                            |         | No       | `{ color: 'red' }`    |
| `items`              | `FieldData[]`         | For render items of card                                                |         | Yes      |                       |
| `isHeadView`         | `boolean`             | Show just head and hidden value                                         |         | No       |                       |
| `hiddenBg`           | `boolean`             | Hidden Background                                                       |         | No       |                       |

## Example

### Simple example

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"],
  "showOnProductTypes": ["motor", "health"],
  "renderType": "quote_grid_card",
  "items": [
    {
      "key": "productType.code",
      "valueType": "product_type",
      "className": "text-xs text-primary font-semibold"
    },
    { "textTemplate": "${agency.firstName} ${agency.lastName}" },
    { "key": "rfqNo", "valueType": "doc_no", "className": "text-primary" },
    {
      "key": "updatedAt",
      "valueType": "date",
      "label": "last_update",
      "className": "text-[10px] text-gray-500"
    }
  ]
}
```

### Example with buttons

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"],
  "showOnProductTypes": ["motor", "health"],
  "renderType": "quote_grid_card",
  "items": [
    {
      "key": "productType.code",
      "valueType": "product_type",
      "className": "text-xs text-primary font-semibold"
    },
    { "textTemplate": "${agency.firstName} ${agency.lastName}" },
    { "key": "rfqNo", "valueType": "doc_no", "className": "text-primary" },
    {
      "key": "updatedAt",
      "valueType": "date",
      "label": "last_update",
      "className": "text-[10px] text-gray-500"
    },
    {
      "buttons": [...]
    }
  ]
}
```

### Example show just header label

```json
{
  "key": "label_info",
  "label": "Label Info",
  "renderType": "quote_grid_card",
  "items": [{ "label": "Policy No" }, { "label": "New Policy No" }],
  "isHeadView": true
}
```

### Example hidden background

```json
{
  "key": "label_info",
  "label": "Label Info",
  "renderType": "quote_grid_card",
  "items": [{ "label": "Policy No" }, { "label": "New Policy No" }],
  "hiddenBg": true
}
```
