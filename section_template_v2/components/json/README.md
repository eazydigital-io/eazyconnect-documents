# Document for JSON Components

## Introduction

This document provides the information about the JSON component.
The JSON component is a customize component, used to display the custom component in the UI.

## Description

Use the JSON Component to Render a Component in the Agent V2.

## Table of Contents

- Display type
  - [Alert](./display/alert.md)
  - [Button](./display/button.md)
  - [Divider](./display/divider.md)
  - [File](./display/file.md)
  - [Grid View Card](./display/grid_view_card.md)
  - [Label](./display/label.md)
  - [List Expand Card](./display/list_expand_card.md)
  - [List Log](./display/list_log.md)
  - [List Select Card](./display/list_select_card.md)
  - [List](./display/list.md)
  - [Product Type Card](./display/product_type_card.md)
  - [Quote Card](./display/quote_card.md)
  - [Quote Grid Card](./display/quote_grid_card.md)
  - [Step](./display/step.md)
  - [Text](./display/text.md)
- Input type
  - [Input Date](./input/input_date.md)
  - [Input Product Type Card](./input/input_product_type_card.md)
  - [Input Select](./input/input_select.md)
  - [Input Text](./input/input_text.md)
  - [Input Text Area](./input/input_textarea.md)
  - [Input Upload](./input/input_upload_.md)

### Types

```ts
type SemanticColor =
  | "default"
  | "primary"
  | "secondary"
  | "success"
  | "danger"
  | "warning";
type RenderType =
  | "alert"
  | "button"
  | "divider"
  | "file"
  | "label"
  | "list_log"
  | "list_select_card"
  | "list"
  | "product_type_card"
  | "quote_card"
  | "step"
  | "text"
  | "input_product_type_card"
  | "input_select"
  | "input_text"
  | "input_textarea"
  | "input_upload"
  | "input_date";
type ValueType =
  | "text"
  | "date"
  | "date_time"
  | "date_status"
  | "number"
  | "number_no_digit"
  | "short_number"
  | "price"
  | "price_no_digit"
  | "short_price"
  | "currency"
  | "currency_no_digit"
  | "short_currency"
  | "product_type"
  | "status"
  | "tag"
  | "doc_no"
  | "percent"
  | "boolean_icon"
  | "image"
  | "file"
  | "link"
  | "download"
  | "blank";

type Button = {
  color?:
    | "primary"
    | "secondary"
    | "success"
    | "danger"
    | "warning"
    | "info"
    | "light"
    | "dark"
    | "white"; // Default: 'primary'
  variant?: "solid" | "outline" | "ghost"; // Default: 'solid'
  label?: string;
  className?: string;
  action?:
    | "back"
    | "clone"
    | "download"
    | "entity_create"
    | "entity_delete"
    | "entity_patch"
    | "entity_update"
    | "form_submit"
    | "internal_download"
    | "redirect"
    | "share";
  icon?: FeatherIcon; // Ex: 'FiX' | 'FiEdit' | 'FiCheck' | ...
  isIconLeft?: boolean;
  width?: "auto" | "full" | "wide" | "fit";
  confirmTitle?: string;
  confirmDesc?: string;
  entityName?: string;
  url?: string;
  path?: string;
  redirectUrl?: string;
  body?: object; // The value on the key object, have to be the string javascript only. please see the example in the button.md
  fileName?: string; // can use text template (ex: `${file.0.name}`)
  shareUrl?: string; // can use text template (ex: `${url}`)
  shareMsg?: string; // can use text template (ex: `${msg}`)
  showOnStatus?: string[];
  showOnProductTypes?: string[];
  evalHidden?: string; // This is a string javascript condition, In a code we will use `eval` to execute this condition
  evalDisabled?: string; // This is a string javascript condition, In a code we will use `eval` to execute this condition
  style?: React.CSSProperties;
  className?: string;
};

type KeyByProductType = {
  [key: string]: string;
};

type FieldDataForList = {
  key: string;
  label?: string;
  suffix?: string;
  textTemplate?: string; // Ex: `${agent.firstName} ${agent.lastName}`
  type?: ValueType; // Default: 'text'
  className?: string;
};

type FieldData = {
  key: string;
  label?: string;
  textTemplate?: string; // Ex: `${agent.firstName} ${agent.lastName}`
  defaultValue?: any;
  valueType?: ValueType; // Default: 'text'
  className?: string;
  style?: React.CSSProperties;
  buttons?: Button[];
};

type GridViewItem = {
  title?: string;
  items?: FieldData[];
};

type ListAction = {
  view?: boolean;
  create?: boolean;
};

type ListActionDisabled = {
  view?: string;
  create?: string;
};

type StepItem = {
  title: string;
  oneLineTitle?: boolean;
  subTitle?: string;
  subTitleValueType?: ValueType;
  icon?: FeatherIcon; // Ex: 'FiX' | 'FiEdit' | 'FiCheck' | ...
  showOnStatus?: string[];
  showOnProductTypes?: string[];
  evalIsCompleted?: string; // This is a string javascript condition, In a code we will use `eval` to execute this condition
};

type DefaultInputProperties = {
  key: string;
  label?: string;
  placeholder?: string;
  center?: boolean;
  disabled?: boolean;
  evalDisabled?: string; // This is a string javascript condition, In a code we will use `eval` to execute this condition
  defaultValue?: any;
  evalDefaultValue?: string; // This is a string javascript condition, In a code we will use `eval` to execute this condition
};

type ListSelectCardOption = {
  titleKey: string;
  titleType?: ValueType;
  rightTitleKey: string;
  rightTitleType?: ValueType;
  attributeKey?: string;
  disabled?: boolean;
  evalForceDisabled?: string;
  evalDefaultSelected?: string;
  defaultSelected?: string;
};

type CardSelectItem = {
  key?: string;
  value: string;
  label: string;
  icon?: FeatherIcon; // Ex: 'FiX' | 'FiEdit' | 'FiCheck' | ...
};

type SelectItem = {
  key: string;
  value: string;
  label: string;
} & {
  [key in string]: string | number;
};
```

### Example `ValueType`

```jsx
// String value
const text = "text";
const date = "12/03/2024";
const date_time = "12/03/2024 00:00:00";
const date_status = "today"; // 'expired' | 'incoming' | 'within_7_days' | 'within_30_days'
const number = "123,456.00";
const number_no_digit = "123,456";
const short_number = "123K";
const price = "$ 123,456.00";
const price_no_digit = "$ 123,456";
const short_price = "$ 123K";
const currency = "USD 123,456.00";
const currency_no_digit = "USD 123,456";
const short_currency = "USD 123K";
const percent = "123%";
const product_type = "Motor";
const doc_no = "#RFQ00001";

// JSX value
const doc_no = <Link to="/sales/...">#RFQ00001</Link>; // doc_no with `to` property
const status = <Badge status="success">Success</Badge>;
const tag = <Tag color="blue">Tag</Tag>;
const image = <img src="https://example.com/image.jpg" alt="Image" />;
const file = <img src="https://example.com/file.jpg" alt="File" />;
const link = (
  <a href="https://example.com" target="_blank">
    Link
  </a>
);
const boolean_icon = <Icon name="check" />; // true
const boolean_icon = <Icon name="x" />; // false
const blank = <div></div>;
```
