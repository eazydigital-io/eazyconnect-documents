# Render type `list` Properties only

- The `Button` type please see [here](../json.md)

| Property             | Type                  | Description                                                             | Default | Required | Example                               |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | -------- | ------------------------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`                    |
| `label`              | `string`              | Label for component render                                              |         | Yes      |                                       |
| `renderType`         | `RenderType`          | For select component to render                                          | `text`  | No       |                                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                            |         | No       | `['draft', 'submit']`                 |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                     |         | No       | `['motor', 'health']`                 |
| `className`          | `string`              | Custom class name                                                       |         | No       | `text-primary`                        |
| `style`              | `React.CSSProperties` | Custom style                                                            |         | No       | `{ color: 'red' }`                    |
| `action`             | `ListAction`          | For render action button                                                |         | No       | `{ "create": true }`                  |
| `evalActionDisabled` | `ListActionDisabled`  | For disable action button                                               |         | No       | `{ "create": "${type} === 'motor'" }` |
| `entityName`         | `string`              | Entity name to get data                                                 |         | Yes      | `eazy_rfq`                            |
| `entityStrFilter`    | `string`              | Entity filter string(query string url)                                  |         | No       | `$and[0][rfq][$in]=${id}`             |
| `entityLimit`        | `number`              | Limit of entity data                                                    | `10`    | No       |                                       |
| `entityFields`       | `string[]`            | Fields to get from entity                                               |         | No       |                                       |
| `entitySort`         | `string`              | Sort of entity data                                                     |         | No       |                                       |
| `toView`             | `string`              | URL to click view entity data                                           |         | No       | `/sales/policies/${id}`               |
| `displayField`       | `FieldDataForList[]`  | Fields to display in the list                                           |         | Yes      |                                       |
| `buttons`            | `Button[]`            | For render button to the right of label                                 |         | No       |                                       |

## Example

### Simple example

```json
{
  "renderType": "list",
  "action": {
    "view": true,
    "create": true,
  },
  "entityName": "eazy_digital",
  "displayField": [
    { "key": "policyNo", "type": "doc_no", "className": "font-semibold" },
    { "key": "updatedAt", "type": "date", "label": "policy_create_at" }
  ]
}
```

### Simple with condition

```json
{
  "renderType": "list",
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```

### Advance list setting

```json
{
  "renderType": "list",
  "action": {
    "view": true,
    "create": true,
  },
  "entityName": "eazy_digital",
  "displayField": [
    { "key": "policyNo", "type": "doc_no", "className": "font-semibold" },
    { "key": "updatedAt", "type": "date", "label": "policy_create_at" }
  ],
  "evalActionDisabled": {
    "view": "${type} === 'motor'",
    "create": "${type} === 'motor'",
  },
  "entityStrFilter": "$and[0][rfq][$in]=${id}",
  "entityLimit": 10,
  "entityFields": ["id","status","rfq_no","updatedAt"],
  "entitySort": "updatedAt=desc",
  "toView": "/sales/policies/${id}",
}
```

### Simple with buttons

```json
{
  "renderType": "list",
  "action": {
    "view": true,
    "create": true,
  },
  "entityName": "eazy_digital",
  "displayField": [
    { "key": "policyNo", "type": "doc_no", "className": "font-semibold" },
    { "key": "updatedAt", "type": "date", "label": "policy_create_at" }
  ],
  "evalActionDisabled": {
    "view": "${type} === 'motor'",
    "create": "${type} === 'motor'",
  },
  "entityStrFilter": "$and[0][rfq][$in]=${id}",
  "entityLimit": 10,
  "entityFields": ["id","status","rfq_no","updatedAt"],
  "entitySort": "updatedAt=desc",
  "toView": "/sales/policies/${id}",
  "buttons": [...]
}
```
