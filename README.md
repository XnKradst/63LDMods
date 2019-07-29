# 63LDMods
Welcome! This repository exists merely as a place to host my own personal Level Designer mods for the Flash game Super Mario 63.
But since I made the mods with other people using them in mind, I might as well put some guides on how to use them here too. Remember, all of the stuff I put here are Level Designer-specific, so there won't be any mods for Story Mode.

## How mods work
I should briefly explain how mods in Super Mario 63 work. They are loaded in the level designer, either from a sign or the level title. To do that, you simply have to insert an HTML image tag in the title or sign, but pointing to an swf file instead of an image. This will cause the game to load the swf file, and since the swf file shares variables with the main game itself, you can basically write code in those swf files to add or redefine variables, arrays and even functions, allowing for new features, gimmicks, etc.

To load a mod in your level, you would type something like `<img src="http://example.org/mod.swf">` in a sign, then read the sign.

Alternatively, you can put that in the level title and simply run the level to load it. However, keep in mind that for whatever reason, mods won't load unless there's other text in the level title before the tag, so you should write something like `My Level<img src="http://example.org/mod.swf">` instead.

Of course, there's the annoying character limit in the level editor that really shouldn't be there. URLs tend to be very long, and more often than not, they're always far too long to fit within that limit. Luckily, you can bypass that limit by editing the level code, although that might be complicated for some people. I'm not gonna explain how to do that here for now, but I will provide codes that you can simply add to the end of your level code, in case you're not familiar with editing level codes.

Anyway, that's all you need to know to get a mod running in Super Mario 63.

# The Level Designer mod (LDmodX.swf)
The main and probably only mod that I will host here. For instructions, refer to [LDmod.md](/LDmod.md).
