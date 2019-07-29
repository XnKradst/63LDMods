## The Level Designer mod (LDmodX.swf)
I originally made this mod for a level I called "The Elemental Silver Stars", but I made it in a way that others can also use it if they wanted. I intend to put as much as I can into this one swf file, since the idea was to have just one universal swf file. To load this in your level, open your level's code in a text editor (like Notepad) and paste this at the end of your code, after your level name:

`%3Cimg%20src%3D%22https%3A%2F%2Fraw%2Egithubusercontent%2Ecom%2FXnKradst%2F63LDMods%2Fmaster%2FLDmod3%2Eswf%22%3E`

Now test your level. If done correctly, the mod should load when the level starts, although nothing will happen yet, since you have to instruct the new functions to do various stuff.

---

## Other information
The latest version is **LDmod3.swf**, and I won't be removing the older versions because doing so will break levels that are still using them.

---

## Functions
Below is a list of all the things you can do with it so far.

### Background Change
Tag: `<back:x>`, where `x` is a string/keyword (list below)

Let's start off with something relatively simple, changing the area's background. What this means is that you can now change the backgrounds across transitions in a single level! But how do you define the backgrounds in each area? Well, it's easy, all you have to do is put a sign in that area, and write the tag in it. In fact, that's how the majority of the features in this mod work.

Example: `<back:Space>`

The above will change the background of the area where the sign is to the Space background.

**List of available keywords:**

Normal backgrounds
- `Hills`: Hills and Clouds
- `HillsOcean`: Hills and Ocean
- `Secret`: Secret Course
- `Sky`/`Air`/`Wind`: Sky
- `Cave`/`Underground`/`Cave1`: Underground
- `Snow`: Snow
- `FireField`: Fire Field
- `Volcano`: Volcano
- `DesertHills`: Desert and Hills
- `Desert`: Desert
- `FireCastle`: Fire Castle
- `FireCastleOutside`: Fire Castle Outside
- `Space`: Space
- `BowserCastle`/`Bowser`: Bowser's Castle
- `Black`: Black
- `LD`: Level Designer Blue Background

New backgrounds
- `Dark`: Bowser in the Dark World background
- `Boo`: Big Boo's Haunt background
- `Wet1`/`Wet`: Wet Dry World background 1
- `Wet2`: Wet Dry World background 2
- `Ocean`: Hills and Ocean but without the hills
- `Cave2`/`Water`: Underground with only the farthest background
- `Cave3`: Volcano with only the farthest background
- `1Up`: That 1-Up background from Story Mode
- `Fire`: A modified version of the Fire Castle background, made specifically for The Elemental Silver Stars
- `Earth`: A modified version of the Volcano background, made specifically for The Elemental Silver Stars

I may add new backgrounds in the future, since there are a few missing ones like Tick Tock Clock.

**Custom backgrounds**

Last but not least, if you insert a URL to a png image instead of one of the keywords provided above, you can load your own custom backgrounds! However, custom backgrounds take time to load, so you might see the default blue "LD" background for a while. The recommended size for backgrounds is `450x300`.

Example: `<back:https://i.imgur.com/SAvYfaZ.png>`

### Custom Images/Sprites
Tag: `<image:x>`, where `x` is an image URL

Next, we have custom images! This allows you to load external images, and by that I don't mean an image in a sign, but actual sprites. It's now fully possible to place stuff like custom trees, paintings on the walls, and anything you can imagine! Where the image appears depends on where you put the sign containing the tag. Note that any image loaded will have an origin at the top-left corner, so keep that in mind when positioning the sign (whose origin is at the bottom-center). Don't worry, the sign itself will no longer be visible.

Example: `<image:https://i.imgur.com/qXF6PAX.png>`

The above will load an image where the sign is, in this case an image of some spikes, which can be combined with the "invisible flame" trick.

Additionally, you can also load images that always appear in the front by using the `<fimage:x>` tag instead.
It's currently not possible to load images that appear behind the background tiles though. Animated images aren't possible either, because Flash.

### "New" Items
Well, they're not really new considering they're just modified versions of existing items, but at least they're... something?
To spawn these items, simply place a sign where you want them to be and write the respective tag in it.

Here's a list of available items so far. Currently, it's pretty much nothing but modified enemies, and mostly giant variants at that. Fun fact: Due to how Runouw programmed them, *some* enemies are actually tougher when they're upscaled! Koopa Troopas are an exception though.
- `<giantgoomba>`: A Goomba bigger than the Huge Goomba.
- `<bossgoomba>`: A colossal Goomba far bigger than the previous one (not suitable for tight places due to glitchy collision detection).
- `<ghostgoomba>`: A fast, transparent Goomba about the size of a normal Huge Goomba.
- `<giantkoopa>`: A giant Koopa Troopa. Not any tougher than regular Koopas due to the way they work.
- `<giantflyingkoopa>`: A giant flying Koopa Troopa.
- `<giantkoopashell>`: A giant Koopa Troopa shell.
- `<giantshyguy>`: A giant Shy Guy.
- `<giantflyingshyguy>`: A giant flying Shy Guy.
- `<giantbobomb>`: A giant Bob-omb, complete with a bigger explosion.
- `<superbobomb>`: A giant Bob-omb even bigger, and slightly faster too.
- `<giantbully>`: A giant Bully.
- `<watersign>`: Will be explained in the "Area Attributes" section of this document.


Obviously, there's still work to be done here as there are other enemies (like Boos) with no modified variants yet. If you're wondering why unusual variants like `<ghostgoomba>` and `<superbobomb>` exist, it's because they were originally made specifically for my level, but hey, I thought they'd be cool to share anyway.

(Thinking about it, it would've been much more versatile if I made the tags in a way that lets the user specify the scale, speed and other variables manually... but that would require a complete rewrite, so don't expect that to happen soon, unfortunately.)

### Area Attributes
Included in the mod are custom functions that do various things in a given area. While they were all made for my level, that doesn't mean they can't be used in other levels, so feel free to use them!
Anyway, as you can tell by the name, these functions generally affect an area as a whole. Of course, they're active only when their corresponding tags are used.

Like the backgrounds, the signs containing these tags can be anywhere as long as they're within the right area.

- **Gravity Change**

You can change the gravity in an area with `<eartharea>` and `<spacearea>`. The former increases gravity strength while the latter decreases it. I might replace these in the future with a \<gravity:x\> tag.

With high gravity, you might take fall damage from heights you normally wouldn't expect any. This isn't part of my code, but just the way the game calculates fall damage based on gravity. Just ground pound or spin and you'll be fine!

- **Water Level Change**

The `<waterarea>` tag spawns an area-wide body of water in the area. An optional tag, `<waterlevel:x>` can be written in the same sign where `x` is the water level (for reference, place any object at the water level you want and take note of its y value). If the optional tag isn't used, the water spawns at the bottom by default.

Example: `<waterarea><waterlevel:736>`

Now, remember the `<watersign>` tag I mentioned in the items section? That's used to spawn "Water Signs", special signs that change the water level on interaction. To place a Water Sign, simply place a regular sign with that tag where you want them to be. Water Signs spawn only in areas where this function is active.

Also, I would like to mention this function currently has a few flaws. Firstly, there's a tiny gap to the far left that went unnoticed because my level has a wall there. Secondly, because it's really just a normal water item moving vertically in real time, and while it's always as wide as the area, for reasons related to performance I made it only half the height of the level size, so it'll leave the bottom uncovered if it were to move to the very top of the level.

- **Raining Fireballs**

Areas with the `<firearea>` tag will constantly spawn raining Bowser fireballs. As you can probably tell, this one's RNG-heavy. 

The fireballs only spawn near Mario (or Luigi) directly above him, which means they *can* spawn under a high ceiling. Keep that in mind when using this in caves and interiors!

- **Wind Gusts**

The `<windarea>` tag activates powerful wind gusts not unlike those seen in the Japanese version of Super Mario Bros. 2 (aka Lost Levels). With this, you can make extremely large gaps that are only possible with the wind.

The wind direction changes occasionally, and there's no way to disable that... *yet*. Also, using this function will replace one layer of some backgrounds with the floating leaves effect! I might find some way to fix this in the future though.

- **Darkness**

Areas with the `<darkarea>` tag will be put in total darkness, leaving nothing but a tiny circle around the player visible.

You might expect certain things like shine sprites and flames to illuminate the surrounding areas, but unfortunately they don't because it's really just an image superimposed to the screen that follows the player. I'm not experienced enough to do real-time lighting effects yet, if that's even possible with SM63 mods.

Remember, the darkness image might take a while to load, which can reveal secrets (if any) in the area for a brief moment.

\---

That's all for this section. By the way, you're not limited to one attribute per area, you can use multiple as long as you make sure to put each tag in its own sign (or else only one would activate). That said, the two gravity tags cancel each other out, and certain combinations don't make for fair level design, like Darkness and Fireballs.

### Warp Trigger
Tag: `<warparea>`, plus other tags (details below)

Allows seamless instant teleportation. Well, almost seamless.

Okay, this isn't really an "area attribute", but you are currently limited to using only one per area because code reasons.
It's basically the endless stairs code made to work in a custom level, so you can now recreate those stairs, make endless hallways, or maybe something similar to the World 4 and 7 castles from Super Mario Bros.

To use this, put the `<warparea>` tag in a sign, then follow it with several other tags in the same sign.

Example: `<warparea><triggerx:496><triggery:704><triggerwidth:64><triggerheight:64><destx:-640><desty:320>`

Think of it like specifying an invisible hitbox's position, size and the target destination. When the player enters this hitbox, the teleportation triggers and the player is warped to the destination. When specifying the width and height, remember that the hitbox has an origin at the top-left.
- `<triggerx:x>` is the x position of the hitbox.
- `<triggery:x>` is the y position of the hitbox.
- `<triggerwidth:x>` is the width of the hitbox.
- `<triggerheight:x`> is the height of the hitbox.
- `<destx:x>` and `<desty:x>` specify the destination. These are *not* absolute coordinates, but are instead relative to the player's position upon triggering the teleportation. The above example warps the player 640 pixels to the left and 320 pixels down.

If you make two identical areas and put a trigger in one of them to send the player to the other, you can create a seamless teleportation! Backgrounds with only one layer in the far back (like Space, Black, Snow, etc.) are recommended, because the parallax layers don't warp with the player and that can break the illusion.

### Level Title Tags

These tags affect the whole level and are therefore placed in the level title instead of signs.
Don't worry about the character limit, I will provide codes that you can simply add to the end of your level code.

- `<preload>`: This is just my way of preloading certain assets like the leaves background, the darkness foreground and the water sign sprite. This works by placing those assets far out of bounds in the first area, but of course this wouldn't work if your level uses those images right away.

Level code version: `%3Cpreload%3E`

- `<ap>`: Stands for "anti-pause". You know, that speedrunning trick known as a "pause-buffered dash"? Levels with this tag will check if the player attempts to do that and if so, kills Mario/Luigi instantly. Use this if you consider that "cheating" and don't want players doing that in your level. Not that they can't just remove the tag if they know what they're doing (hence the tag's vague name), but you know, that itself is still cheating, right?

Level code version: `%3Cap%3E`

### Other (Mostly Useless) Sign Tags

The following tags aren't meant to be used for other levels (if their names didn't already make it obvious), but they are included here for the sake of completion. Maybe someone creative could find a way to use them somehow.
- `<levelspecific_secretdoor>`: Used in my level to spawn a door at a hard-coded location (416, 2256) with a hard-coded destination (17088, 2976), when the player has exactly 4 Silver Stars. The sign containing the tag will now say "Temple of Aether", rather than being removed outright.
- `<levelspecific_swftest:x>`: This moves a rotating block 64 pixels to the left once it loads, and that's as useless as it sounds when you can just move whatever block manually in the level designer. Its purpose in my level was to ensure the mod has successfully loaded, because the block would be in the way otherwise, preventing the player from progressing (without editing the level, at least). `x` is the internal number ID of the block to move, which is almost impossible to know if you're not familiar with modding or how Super Mario 63's code works.
- `<debug>`: Causes whatever sign you put this in to display its own ID number. I originally made this in an attempt to track down the block's ID for the previous tag, although I soon realized block IDs are assigned differently so that didn't work.
