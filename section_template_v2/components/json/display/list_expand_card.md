# Render type `list_expand_card` Properties only

- The `Button`, `ListSelectCardOption` type please see [here](../README.md)

## Description

The `list_expand_card` component is used to render a list of data from the entity OR from the `data?.${key}` of the current entity page

- **_In case you want to use the list from the `data?.${key}` you just remove the `entityName` properties_**

| Property             | Type                     | Description                                                             | Default | Required | Example                               |
| -------------------- | ------------------------ | ----------------------------------------------------------------------- | ------- | -------- | ------------------------------------- |
| `key`                | `string`                 | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`                    |
| `label`              | `string`                 | Label for component render                                              |         | Yes      |                                       |
| `renderType`         | `RenderType`             | For select component to render                                          | `text`  | No       |                                       |
| `showOnStatus`       | `string[]`               | Show component on status ...                                            |         | No       | `['draft', 'submit']`                 |
| `showOnProductTypes` | `string[]`               | Show component on product types ...                                     |         | No       | `['motor', 'health']`                 |
| `className`          | `string`                 | Custom class name                                                       |         | No       | `text-primary`                        |
| `style`              | `React.CSSProperties`    | Custom style                                                            |         | No       | `{ color: 'red' }`                    |
| `showOnLength`       | `boolean`                | Show when length more than 0                                            |         | No       |                                       |
| `action`             | `ListAction`             | For render action button                                                |         | No       | `{ "create": true }`                  |
| `evalActionDisabled` | `ListActionDisabled`     | For disable action button                                               |         | No       | `{ "create": "${type} === 'motor'" }` |
| `entityName`         | `string`                 | Entity name to get data                                                 |         | Yes      | `eazy_rfq`                            |
| `entityQsFilter`     | `string`                 | Entity filter string(query string url)                                  |         | No       | `$and[0][rfq][$in]=${id}`             |
| `entityLimit`        | `number`                 | Limit of entity data                                                    | `10`    | No       |                                       |
| `entityFields`       | `string[]`               | Fields to get from entity                                               |         | No       |                                       |
| `entitySort`         | `string`                 | Sort of entity data                                                     |         | No       |                                       |
| `evalDisabledAll`    | `string`                 | For disabled all selectable                                             |         | No       | `!data?.priceList?.length`            |
| `cardOption`         | `ListSelectCardOption[]` | Option to display in the list                                           |         | Yes      |                                       |
| `buttons`            | `Button[]`               | For render button to the right of label                                 |         | No       |                                       |
| `lazyLoad`           | `boolean`                | When you want to list is lazy load                                      |         | No       |                                       |

## Example

### Example without entity

- When no fill the `entityName` properties, the component will get the data from the `data?.${key}`

```json
{
  "renderType": "list_expand_card",
  "cardOption": {
    "titleKey": "product",
    "titleType": "text",
    "rightTitleKey": "price",
    "rightTitleType": "price",
    "attributeKey": "relatedProduct.attributes"
  }
}
```

### Simple example

```json
{
  "renderType": "list_expand_card",
  "action": {
    "create": true
  },
  "entityName": "eazy_digital",
  "cardOption": {
    "titleKey": "product",
    "titleType": "text",
    "rightTitleKey": "price",
    "rightTitleType": "price",
    "attributeKey": "relatedProduct.attributes"
  }
}
```

### Simple with condition

```json
{
  "renderType": "list_expand_card",
  "showOnLength": true,
  "showOnStatus": ["draft", "processing"],
  "showOnProductTypes": ["motor", "health"]
}
```

### Advance list setting

```json
{
  "renderType": "list_expand_card",
  "action": {
    "create": true
  },
  "entityName": "eazy_digital",
  "cardOption": {
    "titleKey": "product",
    "titleType": "text",
    "rightTitleKey": "price",
    "rightTitleType": "price",
    "attributeKey": "relatedProduct.attributes"
  },
  "evalActionDisabled": {
    "create": "${type} === 'motor'"
  },
  "entityStrFilter": "$and[0][rfq][$in]=${id}",
  "entityLimit": 10,
  "entityFields": ["id", "status", "rfq_no", "updatedAt"],
  "entitySort": "updatedAt=desc"
}
```

### Simple with buttons

```json
{
  "renderType": "list_expand_card",
  "action": {
    "create": true,
  },
  "entityName": "eazy_digital",
  "cardOption": {
    "titleKey": "product",
    "titleType": "text",
    "rightTitleKey": "price",
    "rightTitleType": "price",
    "attributeKey": "relatedProduct.attributes"
  },
  "evalActionDisabled": {
    "view": "${type} === 'motor'",
    "create": "${type} === 'motor'",
  },
  "entityStrFilter": "$and[0][rfq][$in]=${id}",
  "entityLimit": 10,
  "entityFields": ["id","status","rfq_no","updatedAt"],
  "entitySort": "updatedAt=desc",
  "buttons": [...]
}
```

### Simple with lazy load

```json
{
  "renderType": "list_expand_card",
  "lazyLoad": true,
  "entityName": "eazy_digital",
  "cardOption": {
    "titleKey": "product",
    "titleType": "text",
    "rightTitleKey": "price",
    "rightTitleType": "price",
    "attributeKey": "relatedProduct.attributes"
  }
}
```
