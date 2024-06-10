# Render type `button` Properties only

- The `Button` type please see [here](../json.md)

| Property     | Type         | Description                                                            | Default | Required | Example            |
| ------------ | ------------ | ---------------------------------------------------------------------- | ------- | -------- | ------------------ |
| `key`        | `string`     | Key of the JSON data to component value *`key` must be snake_case only |         | Yes      | `agent.first_name` |
| `renderType` | `RenderType` | For select component to render                                         | `text`  | No       |                    |
| `buttons`    | `Button[]`   | For render button                                                      |         | No       |                    |

## Example

### Simple example `button`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Create"
    }
  ]
}
```

### Simple with custom style and className `button`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Create",
      "style": { "color": "red" },
      "className": "text-primary"
    }
  ]
}
```

### Simple with custom icon `button`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Create",
      "icon": "FiPlus"
    },
    {
      "label": "Create",
      "icon": "FiPlus",
      "isIconLeft": true
    }
  ]
}
```

### Simple with condition `button`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Create",
      "icon": "FiPlus",
      "showOnStatus": ["draft", "processing"],
      "showOnProductTypes": ["motor", "health"],
      "disabled": true
    },
    {
      "label": "Create",
      "icon": "FiPlus",
      "isIconLeft": true,
      "evalHidden": "data.status === '${status}'",
      "evalDisabled": "data.productType.code === '${productType}'"
    }
  ]
}
```

### Simple other `button`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Create",
      "icon": "FiPlus",
      "color": "secondary",
      "width": "wide"
    },
    {
      "label": "Create",
      "color": "success",
      "variant": "ghost",
      "width": "full"
    }
  ]
}
```

### For form submit event action

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Create",
      "action": "internal_submit"
    }
  ]
}
```

### Share button

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Share",
      "action": "share",
      "shareUrl": "https://www.google.com",
      "shareMsg": "Share to Google"
    },
    {
      "label": "Share 2",
      "action": "share",
      "shareUrl": "https://www.google.com/${productType.code}",
      "shareMsg": "Share to ${productType.code}"
    }
  ]
}
```

### Download button

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Download",
      "action": "download",
      "url": "https://eazy.com/downplad/image",
      "fileName": "image.jpg"
    },
    {
      "label": "Download 2",
      "action": "download",
      "url": "https://eazy.com/downplad/image.jpg",
      "fileName": "image.jpg"
    },
    {
      "label": "Download 3",
      "action": "download",
      "url": "https://eazy.com/downplad/${file.0.url}",
      "fileName": "${file.0.name}"
    },
  ]
}
```

### Internal Download button

- The `internal_download` action is used to download the file from our server.
- In the url will be the params of the uri `/api/download/link?url=${url}`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Download",
      "action": "internal_download",
      "url": "https://eazy.com/downplad/image",
      "fileName": "image.jpg"
    },
    {
      "label": "Download 2",
      "action": "internal_download",
      "url": "https://eazy.com/downplad/image.jpg",
      "fileName": "image.jpg"
    },
    {
      "label": "Download 3",
      "action": "internal_download",
      "url": "https://eazy.com/downplad/${file.0.url}",
      "fileName": "${file.0.name}"
    },
  ]
}
```

### Entity button

- The `entity` action is used to update, patch and delete the entity.
- The `entity` has 3 actions `entity_update`, `entity_patch`, `entity_delete`
  - `entity_update` is used to update the entity with method `PUT`
  - `entity_patch` is used to update the entity with method `PATCH`
  - `entity_delete` is used to delete the entity with method `DELETE`
- The `path` will be the path of the entity
  - For example: `/approve/${id}`, `/reject/${id}`, `/cancel/${id}` or `/remove`
  - For example result when path is work
    - `/approve/${id}` > `/eazy_rfq/approve/xxxxxx-xxxx-xxxx-xxxxxx`
    - `/reject/${id}` > `/eazy_rfq/reject/xxxxxx-xxxx-xxxx-xxxxxx`
    - `/cancel/${id}` > `/eazy_rfq/cancel/xxxxxx-xxxx-xxxx-xxxxxx`
    - `/remove` > `/eazy_rfq/remove`
- The value on the key object of `body` have to be the string javascript only
  - because the value will be eval by the javascript
  - in case just want to add the text value, please use single quote(***now 10/06/2567 unnecessary use single quote***)
  - we can use text template in the string javascript
  - The value from eval will begin with `data?.` and `data?.` will be the data from the current entity page
  - In case use text template, the value will come from the `data?.` of the current entity page
  - All Example below
    - example current data 
      - `{ id: "xxxxxx-xxxx-xxxx-xxxxxx", productType: { code: "motor" }, priceList: [{ id: "xxxx" }, ...] }`
    - `"data?.product.code"` > `"motor"`
    - `"data?.priceList?.map((p) => p.id)"` > `["xxxx", "zzzz", "cccc"]`
    - `"confirmed"` > `"confirmed"`
    - `"canceled"` > `"canceled"`
    - `"${id}"` > `"xxxxxx-xxxx-xxxx-xxxxxx"`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Update",
      "action": "entity_update",
      "path": "/approve/${id}", // /current_entity/approve/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "status": "cancel" }
    },
    {
      "label": "Update 2",
      "action": "entity_update",
      "path": "/reject/${id}", // /current_entity/reject/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "productType": "${productType.code}" }
    },
    {
      "label": "Update 3",
      "action": "entity_patch",
      "path": "/cancel/${id}", // /current_entity/cancel/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "status": "cancel" }
    },
    {
      "label": "Delete",
      "action": "entity_delete",
      "path": "/remove/${id}", // /current_entity/remove/xxxxxx-xxxx-xxxx-xxxxxx
    },
  ]
}
```

#### Use with `entityName`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Update",
      "action": "entity_update",
      "entityName": "eazy_digital",
      "path": "/approve/${id}", // /eazy_digital/approve/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "status": "cancel" }
    },
    {
      "label": "Update 2",
      "action": "entity_update",
      "entityName": "eazy_digital",
      "path": "/reject/${id}", // /eazy_digital/reject/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "productType": "'${productType.code}'" } // Use body with text template eval, use single quote
    },
    {
      "label": "Update 3",
      "action": "entity_patch",
      "entityName": "eazy_digital",
      "path": "/cancel/${id}", // /eazy_digital/cancel/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "productType": "data?.productType.code" } // Use body with eval
    },
    {
      "label": "Delete",
      "action": "entity_delete",
      "entityName": "eazy_digital",
      "path": "/remove/${id}", // /eazy_digital/remove/xxxxxx-xxxx-xxxx-xxxxxx
    },
  ]
}
```

#### Use with `redirectUri`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Update",
      "action": "entity_update",
      "entityName": "eazy_digital",
      "path": "/approve/${id}", // /eazy_digital/approve/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "status": "cancel" },
      "redirectUri": "/eazy_digital/${id}" // Redirect to /eazy_digital/xxxxxx-xxxx-xxxx-xxxxxx
    },
    {
      "label": "Update 2",
      "action": "entity_update",
      "entityName": "eazy_digital",
      "path": "/reject/${id}", // /eazy_digital/reject/xxxxxx-xxxx-xxxx-xxxxxx
      "body": { "productType": "'${productType.code}'" }, // Use body with text template eval, use single quote
      "redirectUri": "/eazy_digital/sales/rfqs" // Redirect to /eazy_digital/sales/rfqs
    },
  ]
}
```
