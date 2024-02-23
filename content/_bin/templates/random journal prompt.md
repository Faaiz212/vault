<%*

const numberOfPrompts = 3;

const promptsFile = app.metadataCache.getFirstLinkpathDest("journal-prompts","");

const prompts = (await app.vault.read(promptsFile)).split("\n");

tR += "## Random Questions\n";

for(i=0;i<numberOfPrompts;i++) {

  n = Math.floor(Math.random()*prompts.length);

  tR += "### " + prompts[n]+"\n";

}

%>
