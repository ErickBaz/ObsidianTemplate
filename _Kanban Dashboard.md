---
type: Dashboard
author: Erick Baz Hernández
location: Aguascalientes, Aguascalientes
tags:
  - dashboard
  - kanban
created: 2026-02-02T17:16
updated: 2026-02-02T18:06
---

# Efforts Kanban Dashboard

## Kanban-Style View (Grouped)

```dataviewjs
const efforts = dv.pages('"Efforts"').where(p => p.type === "Effort");
const grouped = efforts.groupBy(p => p.ace_bucket);

for (let group of grouped.sort(g => g.key)) {
    dv.header(3, group.key || "No Bucket");
    const sorted = [...group.rows].sort((a, b) => {
        // Sort by file name (descending) which contains timestamp
        return b.file.name.localeCompare(a.file.name);
    });
    dv.list(sorted.map(p => 
        `[[${p.file.name}]] - ${p.updated}`
    ));
}
```
