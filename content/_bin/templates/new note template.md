<%*
// Ask the user to input the title if it starts with "Untitled"
let title = tp.file.title;
if (title.startsWith("Untitled")) {
  title = await tp.system.prompt("Title");
  await tp.file.rename(title);
}

// Convert title to uppercase and strip unwanted characters
let title_uppercase = title.replace(/\b\w/g, c => c.toUpperCase());
let result = title_uppercase.replace(/[^a-zA-Z0-9 ]/g, '');

// YAML front matter start
tR += "---\n";
tR += `id: ${tp.file.creation_date("YYYYMMDDHHmmss")}\n`;
tR += `title: "${result}"\n`;
tR += `created: ${moment(tp.file.creation_date("YYYY-MM-DDTHH:mm:ss.SSSZ")).toISOString()}\n`;
tR += "tags:\n";

// Suggester for general categories
let generalTag = await tp.system.suggester(["projects", "areas", "resources", "archives", "meta"], ["projects", "areas", "resources", "archives", "meta"], false);
if (generalTag) {
  tR += `  - ${generalTag}\n`;
}

// Prompt for note type with 'None' as an option
let noteTypeTag = await tp.system.suggester(["type/litnote", "type/evergreen", "type/fleeting", "none"], ["type/litnote", "type/evergreen", "type/fleeting", "None"], false, "Have you decided a type for this note yet?");
if (noteTypeTag && noteTypeTag.toLowerCase() !== "none") {
  tR += `  - ${noteTypeTag}\n`;
}

// YAML front matter end
tR += "---";
%>
