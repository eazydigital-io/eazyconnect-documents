# Component: JSON

## Description

Use the JSON Component to Render a Component in the Agent V2.

## Properties

### Types

```ts
type RenderType = 'text' | 'label' | 'button' | 'file' | 'list' | 'step' | 'product_type_card'
type ValueType = 'text' | 'date' | 'date_time' | 'date_status' | 'number' | 'number_no_digit' | 'short_number' | 'price' | 'price_no_digit' | 'short_price' | 'currency' | 'currency_no_digit' | 'short_currency' | 'product_type' | 'status' | 'tag' | 'doc_no' | 'image' | 'file' | 'link' | 'blank'

type Button = {
  label?: string
  className?: string
  action?: 'share' | 'download' | 'internal_download'
  icon?: FeatherIcon // Ex: 'FiX' | 'FiEdit' | 'FiCheck' | ...
  isIconLeft?: boolean
  width?: 'auto' | 'full' | 'wide' | 'fit'
  url?: string
  fileName?: string
  shareUrl?: string
  shareMsg?: string
}

type KeyByProductType = {
  [key: string]: string
}

type FieldDataForList = {
  key: string
  label?: string
  textTemplate?: string // Ex: `${agent.firstName} ${agent.lastName}`
  type?: ValueType // Default: 'text'
  className?: string
}

type FieldData = {
  key: string
  label?: string
  textTemplate?: string // Ex: `${agent.firstName} ${agent.lastName}`
  defaultValue?: any
  valueType?: ValueType // Default: 'text'
  className?: string
  style?: React.CSSProperties
}

type ListAction = {
  view?: boolean
  create?: boolean
}

type StepItem = {
  title: string
  subTitle?: string
  subTitleValueType?: ValueType
  icon?: FeatherIcon // Ex: 'FiX' | 'FiEdit' | 'FiCheck' | ...
  showOnStatus?: string[]
  showOnProductTypes?: string[]
  completedCondition?: string // This is a string javascript condition, In a code we will use `eval` to execute this condition
}
```

### Example `ValueType`

```jsx
// String value
const text = 'text'
const date = '12/03/2024'
const date_time = '12/03/2024 00:00:00'
const date_status = 'today' // 'expired' | 'incoming' | 'within_7_days' | 'within_30_days'
const number = '123,456.00'
const number_no_digit = '123,456'
const short_number = '123K'
const price = '$ 123,456.00'
const price_no_digit = '$ 123,456'
const short_price = '$ 123K'
const currency = 'USD 123,456.00'
const currency_no_digit = 'USD 123,456'
const short_currency = 'USD 123K'
const product_type = 'Motor'
const doc_no = '#RFQ00001'

// JSX value
const status = <Badge status="success">Success</Badge>
const tag = <Tag color="blue">Tag</Tag>
const image = <img src="https://example.com/image.jpg" alt="Image" />
const file = <img src="https://example.com/file.jpg" alt="File" />
const link = <a href="https://example.com" target="_blank">Link</a>
const blank = <div></div>
```

### Default Properties

| Property             | Type         | Description                                                            | Default | Required | Example                                |
| -------------------- | ------------ | ---------------------------------------------------------------------- | ------- | -------- | -------------------------------------- |
| `key`                | `string`     | Key of the JSON data to component value *`key` must be snake_case only |         | Yes      | `agent.first_name`                     |
| `label`              | `string`     | Label for component render                                             |         | Yes      |                                        |
| `renderType`         | `RenderType` | For select component to render                                         | `text`  | No       |                                        |
| `defaultValue`       | `any`        | Default value to render                                                |         | No       |                                        |
| `textTemplate`       | `string`     | Text to render instead `key`                                           |         | No       | `${agent.firstName} ${agent.lastName}` |
| `showOnStatus`       | `string[]`   | Show component on status ...                                           |         | No       | `['draft', 'submit']`                  |
| `showOnProductTypes` | `string[]`   | Show component on product types ...                                    |         | No       | `['motor', 'health']`                  |
| `className`          | `string`     | Custom class name                                                      |         | No       | `text-primary`                         |

### Render type `text` Properties only

| Property    | Type        | Description             | Default | Required | Example |
| ----------- | ----------- | ----------------------- | ------- | -------- | ------- |
| `valueType` | `ValueType` | Type of value to render | `text`  | No       |         |

#### Possible Properties of Render type `text`

```json
{
  "key": "agent.first_name",
  "label": "First Name",
  "renderType": "text", // Can `Undefined`
  "defaultValue": "John Doe", // Can `Undefined`
  "textTemplate": "${agent.firstName} ${agent.lastName}", // Can `Undefined`
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary" // Can `Undefined`
}
```

### Render type `button` Properties only

| Property  | Type       | Description       | Default | Required | Example |
| --------- | ---------- | ----------------- | ------- | -------- | ------- |
| `buttons` | `Button[]` | For render button |         | No       |         |

#### Possible Properties of Render type `button`

```json
{
  "renderType": "label", // Required
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary", // Can `Undefined`
  "buttons": [
    // Ex: Button `download`
    {
      "className": "btn-primary", // Can `Undefined`
      "action": "download", // Download file by URL in the JSON data
      "url": "https://example.com/download", // May be you can use key in the JSON data to get the URL
      "fileName": "example.pdf" // May be you can use key in the JSON data to get the URL
    },
    // Ex: Button `internal_download`
    {
      "className": "btn-primary", // Can `Undefined`
      "action": "internal_download", // Download file by URL in the JSON data passed to the Core API
      "url": "${file.0.url}", // May be you can use key in the JSON data to get the URL
      "fileName": "${file.0.name}" // May be you can use key in the JSON data to get the URL
    },
    // Ex: Button `share`
    {
      "className": "btn-primary", // Can `Undefined`
      "action": "share", // Share button can copy URL to clipboard
      "shareUrl": "${file.0.url}", // May be you can use key in the JSON data to get the URL
      "shareMsg": "${file.0.name}" // May be you can use key in the JSON data to get the URL
    },
    // Ex: General Button
    {
      "label": "Button Label", // Can `Undefined`
      "className": "btn-primary", // Can `Undefined`
      "icon": "FiX", // Can `Undefined`
      "isIconLeft": true, // Can `Undefined`
      "width": "full", // Can `Undefined`
    },
  ]
}
```

### Render type `label` Properties only

| Property  | Type       | Description                             | Default | Required | Example |
| --------- | ---------- | --------------------------------------- | ------- | -------- | ------- |
| `buttons` | `Button[]` | For render button to the right of label |         | No       |         |

#### Possible Properties of Render type `label`

```json
// Ex: Label only
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary", // Can `Undefined`
  "renderType": "label", // Required
}

// Ex: Label with buttons
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary", // Can `Undefined`
  "renderType": "label", // Required
  "buttons": [
    ... // Refer to Render type `button` Properties only
  ]
}
```

### Render type `file` Properties only

| Property           | Type               | Description                                    | Default | Required | Example |
| ------------------ | ------------------ | ---------------------------------------------- | ------- | -------- | ------- |
| `keyByProductType` | `KeyByProductType` | For get custom file url from each Product type |         | No       |         |

#### Possible Properties of Render type `file`

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary", // Can `Undefined`
  "renderType": "file", // Required
  "keyByProductType": {
    "motor": "file_url_motor.0.url",
    "health": "file_url_health.0.url"
  },
}
```

### Render type `list` Properties only

| Property          | Type                 | Description                             | Default | Required | Example                   |
| ----------------- | -------------------- | --------------------------------------- | ------- | -------- | ------------------------- |
| `action`          | `ListAction`         | For render action button                |         | No       |                           |
| `entityName`      | `string`             | Entity name to get data                 |         | Yes      | `eazy_rfq`                |
| `entityStrFilter` | `string`             | Entity filter string(query string url)  |         | No       | `$and[0][rfq][$in]=${id}` |
| `entityLimit`     | `number`             | Limit of entity data                    | `10`    | No       |                           |
| `entityFields`    | `string[]`           | Fields to get from entity               |         | No       |                           |
| `entitySort`      | `string`             | Sort of entity data                     |         | No       |                           |
| `toView`          | `string`             | URL to click view entity data           |         | No       | `/sales/policies/${id}`   |
| `displayField`    | `FieldDataForList[]` | Fields to display in the list           |         | Yes      |                           |
| `buttons`         | `Button[]`           | For render button to the right of label |         | No       |                           |

#### Possible Properties of Render type `list`

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary", // Can `Undefined`
  "renderType": "list", // Required
  "action": {
    "view": true, // Can `Undefined`
    "create": true, // Can `Undefined`
  }, // Can `Undefined`
  "entityName": "eazy_rfq", // Required
  "entityStrFilter": "$and[0][rfq][$in]=${id}", // Can `Undefined`
  "entityLimit": 10, // Can `Undefined`
  "entityFields": ["id","status","rfq_no","updatedAt"], // Can `Undefined`
  "entitySort": "updatedAt=desc", // Can `Undefined`
  "toView": "/sales/policies/${id}", // Can `Undefined`
  "displayField": [
    { "key": "policyNo", "type": "doc_no", "className": "font-semibold" },
    { "key": "updatedAt", "type": "date", "label": "policy_create_at" }
  ],
  "buttons": [
    ... // Refer to Render type `button` Properties only
  ]
}
```

### Render type `step` Properties only

| Property | Type         | Description     | Default | Required | Example |
| -------- | ------------ | --------------- | ------- | -------- | ------- |
| `steps`  | `StepItem[]` | For render step |         | Yes      |         |

#### Possible Properties of Render type `step`

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary", // Can `Undefined`
  "renderType": "step", // Required
  "steps": [
    {
      "title": "Title",
      "subTitle": "Sub Title",
      "icon": "FiCheck", // Can `Undefined`
      "completedCondition": "['submit', 'processing', 'completed', 'canceled'].includes('${status}')" // Can `Undefined`
    },
    {
      "title": "Title 2",
      "subTitle": "${amount}",
      "subTitleValueType": "number", // Can `Undefined`
      "icon": "FiCheck", // Can `Undefined`
      "showOnStatus": ["new","submit","processing","completed"], // Can `Undefined`
      "completedCondition": "['processing', 'completed'].includes('${status}')" // Can `Undefined`
    },
    {
      "title": "Title 3",
      "subTitle": "${rfq_no}",
      "subTitleValueType": "doc_no", // Can `Undefined`
      "icon": "FiCheck", // Can `Undefined`
      "showOnStatus": ["canceled"], // Can `Undefined`
      "completedCondition": "!!'${process_date}'" // Can `Undefined`
    },
    {
      "title": "Title 4",
      "subTitle": "${completedDate}",
      "subTitleValueType": "date", // Can `Undefined`
      "icon": "FiCheck", // Can `Undefined`
      "showOnStatus": ["new","submit","processing","completed"], // Can `Undefined`
      "completedCondition": "!!'${completedDate}'" // Can `Undefined`
    },
  ],
}
```

### Render type `product_type_card` Properties only

| Property     | Type          | Description                   | Default | Required | Example |
| ------------ | ------------- | ----------------------------- | ------- | -------- | ------- |
| `hiddenIcon` | `boolean`     | For hide icon                 | `false` | No       |         |
| `left`       | `FieldData[]` | For render left side of card  |         | Yes      |         |
| `right`      | `FieldData[]` | For render right side of card |         | No       |         |

#### Possible Properties of Render type `product_type_card`

```json
{
  "key": "label_info",
  "label": "Label Info",
  "showOnStatus": ["draft", "submit"], // Can `Undefined`
  "showOnProductTypes": ["motor", "health"], // Can `Undefined`
  "className": "text-primary", // Can `Undefined`
  "renderType": "product_type_card", // Required
  "hiddenIcon": false, // Can `Undefined`
  "left": [
    { "key": "productType.code", "valueType": "product_type", "className": "text-xs text-primary font-semibold" },
    { "textTemplate": "${agency.firstName} ${agency.lastName}" },
    { "key": "rfqNo", "valueType": "doc_no", "className": "text-primary" },
    { "key": "updatedAt", "valueType": "date", "label": "last_update", "className": "text-[10px] text-gray-500" }
  ],
  "right": [
    { "type": "blank" },
    { "key": "status", "valueType": "status" }
  ] // Can `Undefined`
}
```
