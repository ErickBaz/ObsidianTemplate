---
type: Effort
author: Erick Baz Hernández
location: Aguascalientes, Aguascalientes
ace_component: effort
ace_bucket: Hab Module
ace_tags: []
tags:
  - effort
project: ""
related: []
summary: ""
links: []
created: <% tp.date.now("YYYY-MM-DDTHH:mm") %>
updated: 2026-02-02T18:08
---
<%*
	const today = tp.date.now("YYYY-MM-DD HHmmss")
	
	// Base folder where all meeting notes go
	const baseFolder = "Efforts";
	const targetFolder = `${baseFolder}`;
	
	// Ensure folder structure exists
	try {
	  await app.vault.createFolder(targetFolder);
	} catch (e) {
	  // Ignore "Folder already exists" errors
	}
	
	let title = tp.file.title
	if (title.startsWith("Untitled")) {
		title = await tp.system.prompt("Title", today + ' A new effort');
		await tp.file.rename(`${title}`);
	}


	// Build final path + name
	const finalFileName = title;
	const finalPath = `${targetFolder}/${finalFileName}`;
	// Move & rename the note into the new folder
	await tp.file.move(finalPath);
-%>