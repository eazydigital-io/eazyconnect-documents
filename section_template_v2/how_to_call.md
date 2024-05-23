# How to Call the Section Template V2 API

## Description

This document provides information on how to call the Section Template V2 API.

## Example

```tsx
// NOTE: SECTION_TEMPLATE_URI => GET: /entities/schema/${entityName}

// NOTE: Get the section template for the entity "eazy_rfq".
// api.ts
const getSectionTemplateV2 = async (entityName) => {
  const SECTION_TEMPLATE_URI = '/entities/schema/eazy_rfq'
  const response = await axios.get(SECTION_TEMPLATE_URI)
  const data = await response.json()

  return data
}

// services.ts
const useSectionTemplate = () => {
  const entityName = 'eazy_rfq'
  const { data } = useQuery({
    queryKey: ['sectionTemplate', entityName],
    queryFn: () => getSectionTemplateV2(entityName),
  })

  return {
    layout: data.layouts?.find(
      (layout) => layout.code === `agent_${entityName}_detail`
    )
  }
}

// components.tsx
const SectionTemplate = () => {
  const { layout } = useSectionTemplate()
  const layouts = useMemo(() => layout?.detail?.blocks || [], [layout]);

  return (
    <div>
      {layouts.map((lo) => (
        <div key={lo.type}>{lo.type}</div>
        // ..................
      ))}
    </div>
  )
}
```
