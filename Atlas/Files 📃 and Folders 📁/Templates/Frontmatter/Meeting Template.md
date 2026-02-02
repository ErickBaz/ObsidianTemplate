---
type: Meeting
date: 2026-02-01
last_modified: 2026-02-01
author: Erick Baz Hernández
participants: []
location: Aguascalientes, Aguascalientes
agenda: ""
decisions: ""
tags:
  - meeting
project: ""
related: []
summary: ""
links: []
---
<%*
	const today = tp.date.now("YYYY-MM-DD HHmmss")
	let title = tp.file.title
	if (title.startsWith("Untitled")) {
		title = await tp.system.prompt("Title", today + ' meeting ');
		await tp.file.rename(`${title}`);
	}
-%>
---
type: "Meeting"
date: "<% today %>"
last_modified: "<% today %>"
author: "Erick Baz Hernández"
participants: []
location: "Aguascalientes, Aguascalientes"
agenda: ""
decisions: ""
tags: [meeting]
project: ""
related: []
summary: ""
links: []
---
<% tp.file.cursor() %>