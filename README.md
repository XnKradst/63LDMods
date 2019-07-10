# 63LDMods
This repository exists merely as a place to host my own personal Level Designer mods for the Flash game Super Mario 63.
Since I made the mods with other people using them in mind, I might as well make a documentation on how to use them. Please note that all of the stuff I put here are Level Designer-specific, which means there won't be mods for Story Mode.

## How mods work
Before we get to the actual documentation, I figured I should briefly explain how mods in Super Mario 63 work first. They are loaded in the level designer, either from a sign or the level title. To do that, you simply have to insert an HTML image tag in the title or sign, but pointing to an swf file instead of an image. This will cause the game to load the swf file, and since the swf file shares variables with the main game itself, you can basically write code in those swf files to add or redefine variables, arrays and even functions, allowing for new features, gimmicks, etc.

To load a mod in your level, you would type something like `<img src="http://example.org/mod.swf">` in a sign, then read the sign.

Alternatively, you can put that in the level title and simply run the level to load it. However, keep in mind that for whatever reason, mods won't load unless there's other text in the level title before the tag, so you should write something like `My Level<img src="http://example.org/mod.swf">` instead.

Of course, there's the annoying character limit in the level editor that really shouldn't be there. URLs tend to be very long, and more often than not, they're always far too long to fit within that limit. Luckily, you can bypass that limit by editing the level code, although that might be complicated for some people. I'm not gonna explain how to do that here, as that'll make this doc longer than it should be. However, I will provide codes that you can simply add to the end of your level codes, in case you're not familiar with editing level codes.

Anyway, that's all you need to know to get a mod running in Super Mario 63. I won't go too deep in details about other stuff, since this doc is specifically for the mods that I made.

## The Level Designer mod (LDmodX.swf)
I originally made this mod for a level I called "The Elemental Silver Stars", but I made it in a way that others can also use it if they wanted. I intend to put as much as I can into this one swf file, since the idea was to have just one universal swf file. To load this in your level, open your level's code in a text editor (like Notepad) and paste this at the end of your code, after your level name:

`%3Cimg%20src%3D%22https%3A%2F%2Fraw%2Egithubusercontent%2Ecom%2FXnKradst%2F63LDMods%2Fmaster%2FLDmod3%2Eswf%22%3E`

Now test your level. If done correctly, the mod should load when the level starts, although nothing will happen yet, since you have to instruct the new functions to do various stuff.

### ====== Background changes per area =======
Tag: `<back:x>`, where `x` is a string/keyword (list below)

Let's start off with something relatively simple, changing the area's background. You can change the backgrounds across transitions in a single level now! But how do you define the backgrounds in each area? Well, it's easy, all you have to do is put a sign in that area, and write the tag in it (In fact, that's how the majority of the features here work).

Example: `<back:Space>`

The above will change the background of the area where the sign is to the Space background.

**List of available keywords:**

Normal backgrounds
- `Hills` Hills and Clouds
- `HillsOcean` Hills and Ocean
- `Secret` Secret Course
- `Sky`/`Air`/`Wind` Sky
- `Cave`/`Underground`/`Cave1` Underground
- `Snow` Snow
- `FireField` Fire Field
- `Volcano` Volcano
- `DesertHills` Desert and Hills
- `Desert` Desert
- `FireCastle` Fire Castle
- `FireCastleOutside` Fire Castle Outside
- `Space` Space
- `BowserCastle`/`Bowser` Bowser's Castle
- `Black` Black
- `LD` Level Designer Blue Background

New backgrounds
- `Dark` Bowser in the Dark World background
- `Boo` Big Boo's Haunt background
- `Wet1`/`Wet` Wet Dry World background 1
- `Wet2` Wet Dry World background 2
- `Ocean` Hills and Ocean but without the hills
- `Cave2`/`Water` Underground with only the farthest background
- `Cave3` Volcano with only the farthest background
- `1Up` That 1-Up background from Story Mode
- `Fire` A modified version of the Fire Castle background, made specifically for The Elemental Silver Stars
- `Earth` A modified version of the Volcano background, made specifically for The Elemental Silver Stars

Note that I may add new backgrounds in the future, since there are a few missing ones like Tick Tock Clock.

**Custom backgrounds**

Last but not least, if you insert a URL to a png image instead of one of the keywords provided above, you can load your own custom backgrounds! However, custom backgrounds take time to load, so you might see the default blue "LD" background for a while. The recommended size for backgrounds is `450x300`.

Example: `<back:https://i.imgur.com/SAvYfaZ.png>`

(WIP, to be continued)
