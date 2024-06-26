# Render type `grid_view_card` Properties only

- The `GridViewItem` type please see [here](../README.md)

| Property             | Type                  | Description                                                             | Default | Required | Example               |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`    |
| `label`              | `string`              | Label for component render                                              |         | Yes      |                       |
| `renderType`         | `RenderType`          | For select component to render                                          | `text`  | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                            |         | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                     |         | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                       |         | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                            |         | No       | `{ color: 'red' }`    |
| `items`              | `GridViewItem[]`      | For render items of card                                                |         | Yes      |                       |
| `headers`            | `[string, string]`    | Show just head and hidden value                                         |         | No       |                       |
| `hiddenDivider`      | `boolean`             | Hidden Divider                                                          |         | No       |                       |

## Example

### Simple example

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"],
  "showOnProductTypes": ["motor", "health"],
  "renderType": "grid_view_card",
  "items": [
    {
      "title": "claim",
      "items": [
        { "label": "no_of_claim", "key": "additional_info.claim" },
        { "label": "loss_amount", "key": "loss_amount", "valueType": "price" },
        {
          "label": "date_issuance",
          "key": "additional_info.date_issuance",
          "valueType": "date"
        }
      ]
    }
  ]
}
```

### Example show header label

```json
{
  "key": "label_info",
  "label": "Label Info",
  "renderType": "grid_view_card",
  "headers": ["Old", "New"],
  "items": [
    {
      "title": "claim",
      "items": [
        { "label": "no_of_claim", "key": "additional_info.claim" },
        { "label": "loss_amount", "key": "loss_amount", "valueType": "price" },
        {
          "label": "date_issuance",
          "key": "additional_info.date_issuance",
          "valueType": "date"
        }
      ]
    }
  ]
}
```
