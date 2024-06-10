# Component: JSON

## Description

Use the JSON Component to Render a Component in the Agent V2.

## Properties

### Types

```ts
type RenderType = 'text' | 'label' | 'button' | 'file' | 'list' | 'step' | 'product_type_card' | 'input_product_type_card' | 'input_select'
type ValueType = 'text' | 'date' | 'date_time' | 'date_status' | 'number' | 'number_no_digit' | 'short_number' | 'price' | 'price_no_digit' | 'short_price' | 'currency' | 'currency_no_digit' | 'short_currency' | 'product_type' | 'status' | 'tag' | 'doc_no' | 'percent' | 'boolean_icon' | 'image' | 'file' | 'link' | 'blank'

type Button = {
  color?: 'primary' | 'secondary' | 'success' | 'danger' | 'warning' | 'info' | 'light' | 'dark' | 'white' // Default: 'primary'
  variant?: 'solid' | 'outline' | 'ghost' // Default: 'solid'
  label?: string
  className?: string
  action?: 'share' | 'download' | 'internal_download' | 'entity_update' | 'entity_patch' | 'entity_delete' | 'form_submit'
  icon?: FeatherIcon // Ex: 'FiX' | 'FiEdit' | 'FiCheck' | ...
  isIconLeft?: boolean
  width?: 'auto' | 'full' | 'wide' | 'fit'
  confirmTitle?: string;
  confirmDesc?: string;
  entityName?: string
  url?: string
  path?: string
  redirectUri?: string
  body?: object // The value on the key object, have to be the string javascript only. please see the example in the button.md
  fileName?: string // can use text template (ex: `${file.0.name}`)
  shareUrl?: string // can use text template (ex: `${url}`)
  shareMsg?: string // can use text template (ex: `${msg}`)
  showOnStatus?: string[]
  showOnProductTypes?: string[]
  evalHidden?: string // This is a string javascript condition, In a code we will use `eval` to execute this condition
  evalDisabled?: string // This is a string javascript condition, In a code we will use `eval` to execute this condition
  style?: React.CSSProperties
  className?: string
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

type ListActionDisabled = {
  view?: string
  create?: string
}

type StepItem = {
  title: string
  oneLineTitle?: boolean
  subTitle?: string
  subTitleValueType?: ValueType
  icon?: FeatherIcon // Ex: 'FiX' | 'FiEdit' | 'FiCheck' | ...
  showOnStatus?: string[]
  showOnProductTypes?: string[]
  evalIsCompleted?: string // This is a string javascript condition, In a code we will use `eval` to execute this condition
}

type DefaultInputProperties = {
  key: string
  label?: string
  placeholder?: string
  center?: boolean
  disabled?: boolean
  evalDisabled?: string // This is a string javascript condition, In a code we will use `eval` to execute this condition
  defaultValue?: any
  evalDefaultValue?: string // This is a string javascript condition, In a code we will use `eval` to execute this condition
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
const percent = '123%'
const product_type = 'Motor'
const doc_no = '#RFQ00001'

// JSX value
const status = <Badge status="success">Success</Badge>
const tag = <Tag color="blue">Tag</Tag>
const image = <img src="https://example.com/image.jpg" alt="Image" />
const file = <img src="https://example.com/file.jpg" alt="File" />
const link = <a href="https://example.com" target="_blank">Link</a>
const boolean_icon = <Icon name="check"/> // true
const boolean_icon = <Icon name="x"/> // false
const blank = <div></div>
```
