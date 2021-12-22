---
sidebar_position: 5
---

# 3D Models

Filter is a ***molecule*** typically used to refine your search results in CDF. It can be a date field or even a text field. 

## Code Blocks


```tsx title="Interface"
export interface IFilter {
    name: string;
    limit: number;
    sdate : Date;
    edate : Date;
    publish : boolean;
}
```

```tsx title="Sample Code"
 const fieldsFilter = [
    {
      label: "Asset Name",
      type: "text",
      mask: null,
      value: name,
      keyDown: null,
      onChangeFunction: setName,
    },


    const filterFieldsPages: typeFieldsFiltersPage = { 
      "/assets": ["Asset Name", "Limit"] 
      };

```



