# Render type `list_log` Properties only

- The `Button`, `ValueType` type please see [here](../README.md)

## Description

The `list_log` component is used to render a list of data from the entity OR from the `data?.${key}` of the current entity page

- **_In case you want to use the list from the `data?.${key}` you just remove the `entityName` properties_**

| Property             | Type                  | Description                                                             | Default | Required | Example                   |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | -------- | ------------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`        |
| `label`              | `string`              | Label for component render                                              |         | Yes      |                           |
| `renderType`         | `RenderType`          | For select component to render                                          | `text`  | No       |                           |
| `showOnStatus`       | `string[]`            | Show component on status ...                                            |         | No       | `['draft', 'submit']`     |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                     |         | No       | `['motor', 'health']`     |
| `className`          | `string`              | Custom class name                                                       |         | No       | `text-primary`            |
| `style`              | `React.CSSProperties` | Custom style                                                            |         | No       | `{ color: 'red' }`        |
| `showOnLength`       | `boolean`             | Show when length more than 0                                            |         | No       |                           |
| `entityName`         | `string`              | Entity name to get data                                                 |         | Yes      | `eazy_rfq`                |
| `entityQsFilter`     | `string`              | Entity filter string(query string url)                                  |         | No       | `$and[0][rfq][$in]=${id}` |
| `entityLimit`        | `number`              | Limit of entity data                                                    | `10`    | No       |                           |
| `entityFields`       | `string[]`            | Fields to get from entity                                               |         | No       |                           |
| `entitySort`         | `string`              | Sort of entity data                                                     |         | No       |                           |
| `buttons`            | `Button[]`            | For render button to the right of label                                 |         | No       |                           |
| `leftKey`            | `string`              | Left key                                                                |         | No       |                           |
| `leftValueType`      | `ValueType`           | Type of value to render                                                 |         | No       |                           |
| `rightKey`           | `string`              | Right key                                                               |         | No       |                           |
| `rightValueType`     | `ValueType`           | Type of value to render                                                 |         | No       |                           |

## Example

### Simple example

```json
{
  "renderType": "list_log",
  "key": "emailLog",
  "leftKey": "sendTime",
  "leftValueType": "date_time",
  "rightKey": "message",
  "rightValueType": "text"
}
```

### Simple with condition

```json
{
  "renderType": "list_log",
  "key": "emailLog",
  "showOnLength": true,
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```

### Advance list setting with specific entity name

```json
{
  "renderType": "list_log",
  "leftKey": "sendTime",
  "leftValueType": "date_time",
  "rightKey": "message",
  "rightValueType": "text",
  "entityName": "eazy_digital",
  "entityQsFilter": "$and[0][rfq][$in]=${id}",
  "entityLimit": 10,
  "entityFields": ["id", "status", "rfq_no", "updatedAt"],
  "entitySort": "updatedAt=desc"
}
```

### Simple with buttons

```json
{
  "renderType": "list_log",
  "key": "emailLog",
  "leftKey": "sendTime",
  "leftValueType": "date_time",
  "rightKey": "message",
  "rightValueType": "text",
  "buttons": [...]
}
```
