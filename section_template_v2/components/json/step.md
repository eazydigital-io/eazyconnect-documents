# Render type `step` Properties only

- The `StepItem` type please see [here](./README.md)

| Property             | Type                  | Description                                                             | Default | Required | Example               |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | -------- | --------------------- |
| `key`                | `string`              | Key of the JSON data to component value \*`key` must be snake_case only |         | Yes      | `agent.first_name`    |
| `label`              | `string`              | Label for component render                                              |         | Yes      |                       |
| `renderType`         | `RenderType`          | For select component to render                                          | `text`  | No       |                       |
| `showOnStatus`       | `string[]`            | Show component on status ...                                            |         | No       | `['draft', 'submit']` |
| `showOnProductTypes` | `string[]`            | Show component on product types ...                                     |         | No       | `['motor', 'health']` |
| `className`          | `string`              | Custom class name                                                       |         | No       | `text-primary`        |
| `style`              | `React.CSSProperties` | Custom style                                                            |         | No       | `{ color: 'red' }`    |
| `steps`              | `StepItem[]`          | For render step                                                         |         | Yes      |                       |

## Example

### Simple example

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
      "evalIsCompleted": "['submit', 'processing', 'completed', 'canceled'].includes('${status}')" // Can `Undefined`
    },
    {
      "title": "Title 2",
      "subTitle": "${amount}",
      "subTitleValueType": "number", // Can `Undefined`
      "icon": "FiCheck", // Can `Undefined`
      "showOnStatus": ["new","submit","processing","completed"], // Can `Undefined`
      "evalIsCompleted": "['processing', 'completed'].includes('${status}')" // Can `Undefined`
    },
    {
      "title": "Title 3",
      "subTitle": "${rfq_no}",
      "subTitleValueType": "doc_no", // Can `Undefined`
      "icon": "FiCheck", // Can `Undefined`
      "showOnStatus": ["canceled"], // Can `Undefined`
      "evalIsCompleted": "!!'${process_date}'" // Can `Undefined`
    },
    {
      "title": "Title 4",
      "subTitle": "${completedDate}",
      "subTitleValueType": "date", // Can `Undefined`
      "icon": "FiCheck", // Can `Undefined`
      "showOnStatus": ["new","submit","processing","completed"], // Can `Undefined`
      "evalIsCompleted": "!!'${completedDate}'" // Can `Undefined`
    },
  ],
}
```
