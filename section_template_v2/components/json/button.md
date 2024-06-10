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
      "fileName": "file.0.name"
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
      "fileName": "file.0.name"
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
- The url of the entity action will be the uri of the entity
  - For example: `/approve`, `/reject`, `/cancel`
  - The url can be the uri with the params `/approve/${id}`, `/reject/${id}`, `/cancel/${id}`
  - For example result when uri is used in the code
    - `/approve` will be `/eazy_rfq/${rfqNo}/approve`
    - `/approve/${id}` will be `/eazy_rfq/${rfqNo}/approve/${id}`

```json
{
  "renderType": "button",
  "buttons": [
    {
      "label": "Update",
      "action": "entity_update",
      "url": "/approve",
      "body": { "status": "cancel" }
    },
    {
      "label": "Update 2",
      "action": "entity_update",
      "url": "/approve/${id}",
      "body": { "status": "processing" } // Now the body un-support text template and eval function
    },
    {
      "label": "Update 3",
      "action": "entity_patch",
      "url": "/approve",
      "body": { "status": "cancel" }
    },
    {
      "label": "Delete",
      "action": "entity_delete",
      "url": "/delete"
    },
  ]
}
```
