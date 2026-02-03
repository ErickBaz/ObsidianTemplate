---
type: Meeting
author: Erick Baz Hernández
location: Aguascalientes, Aguascalientes
ace_component: calendar
participants: []
tags:
  - meeting
project: ""
related: []
summary: ""
links: []
created: <% tp.date.now("YYYY-MM-DDTHH:mm") %>
updated: 2026-02-02T18:09
---
<%*
	const today = tp.date.now("YYYY-MM-DD HHmmss")
	const year  = tp.date.now("YYYY");
	const month = tp.date.now("MM");
	const currentDateTime = tp.date.now("YYYY-MM-DD HH:mm:ss");
	
	// Base folder where all meeting notes go
	const baseFolder = "Calendar/Meetings"; // change if needed
	const targetFolder = `${baseFolder}/${year}/${month}`;
	
	// Ensure folder structure exists
	try {
	  await app.vault.createFolder(targetFolder);
	} catch (e) {
	  // Ignore "Folder already exists" errors
	}
	
	let title = tp.file.title
	if (title.startsWith("Untitled")) {
		title = await tp.system.prompt("Title", today + ' meeting ');
		await tp.file.rename(`${title}`);
	}

	// Build final path + name
	const finalFileName = title;
	const finalPath = `${targetFolder}/${finalFileName}`;
	
	// Move & rename the note into the new folder
	await tp.file.move(finalPath);
-%>