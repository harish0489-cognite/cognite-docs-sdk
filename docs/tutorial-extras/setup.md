---
sidebar_position: 1
---

# Setup

Setting up with Context, Filter, Files information.


## Code Blocks

```tsx title="src/components/assets.tsx"
 async function searchAsset() {
    const searchAssets = await client.assets.search({
      search: {
        query: filters.name,
      }, limit: filters.limit,
    });

    if (searchAssets !== undefined && typeof searchAssets === "object") {
      let newAssets: any = [];
      searchAssets.map((a: Asset, idx) => {
        newAssets.push({
          id: a.id,
          name: a.name,
          description: a.description,
          created_at: {
            date: moment(a.createdTime).format("DD/MM/YYYY"),
            hour: moment(a.createdTime).format("HH:mm:ss"),
          },
        });
      });
      setAssets(newAssets);
      console.log(newAssets);
    }
  }
```

