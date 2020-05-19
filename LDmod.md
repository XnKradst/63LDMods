## The Level Designer mod (LDmodX.swf)
I originally made this mod for a level I called "The Elemental Silver Stars", but I made it in a way that others can also use it if they wanted. I intend to put as much as I can into this one swf file, since the idea was to have just one universal swf file. To load this in your level, open your level's code in a text editor (like Notepad) and paste this at the end of your code, after your level name:

`%3Cimg%20src%3D%22https%3A%2F%2Fraw%2Egithubusercontent%2Ecom%2FXnKradst%2F63LDMods%2Fmaster%2FLDmod4%2Eswf%22%3E`

Now test your level. If done correctly, the mod should load when the level starts, although nothing will happen yet, since you have to instruct the new functions to do various stuff.

---

## Other information
The latest version is **LDmod4.swf**, and I won't be removing the older versions because doing so will break levels that are still using them.

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

### Invisible Sign
Tag: `<invis>`

This is really just a regular sign with its alpha value set to 0. Write whatever you want to write in it, and as long as there's an `<invis>` tag somewhere in the sign, it will be invisible.

Example: `This is an invisible sign...<invis>`

### Customizable Items
Did you know? The 3 base-game Goomba variants are all just one object, only with a different value for the "scale" variable each. Runouw never made that variable (and a few others) customizable. That's what these tags are for.

Note: The giant enemy tags from version 3 and earlier have all been removed, as they're now obsolete. If you used the giant enemies, it's entirely possible to recreate them with these new tags.

To use a custom item, place its tag in a sign, followed by other tags that modify its variables (such as its scale and speed).

As examples, here are the enemies from LDmod3 and earlier:
- `<customgoomba><scale:5>` Giant Goomba 
- `<customkoopa><scale:4>` Giant Koopa Troopa
- `<customkoopa><scale:4><state:Flying>` Giant Flying Koopa Troopa
- `<customkoopa><scale:4><state:Shell>` Giant Koopa Troopa Shell
- `<customshyguy><scale:4>` Giant Shy Guy
- `<customshyguy><scale:4><state:Flying>` Giant Flying Shy Guy
- `<custombobomb><scale:4>` Giant Bob-omb
- `<custombigbully><scale:5>` Giant Bully
- `<customgoomba><scale:12><speed:0.4><distance:100>` "Boss" Goomba
- `<customgoomba><scale:3><speed:1><distance:75><alpha:10>` "Ghost" Goomba
- `<custombobomb><scale:7><speed:1><distance:100>` "Super" Bob-omb

And here's red water:
- `<customwater><red:255><green:0><blue:0><length:300><depth:300>`

As you can see, you only need to include tags for the variables you want to modify. The default value will be used for any missing tag.

#### Goomba
Tag: `<customgoomba>`

Variables:
- `<scale:x>` The size of the Goomba. Default: 1 (Huge Goomba: 2 / Mini Goomba: 0.5)
- `<speed:x>` The Goomba's movement speed. Default: 0.5
- `<distance:x>` The Goomba's back-and-forth distance when idling (as in, when it's not actively chasing Mario). Default: 100
- `<alpha:x>` The sprite's alpha value. Default: 100

#### Koopa Troopa
Tag: `<customkoopa>`

Variables:
- `<scale:x>` The size of the Koopa Troopa. Default: 1
- `<speed:x>` The Koopa Troopa's movement speed. Default: 3
- `<distance:x>` The Koopa Troopa's back-and-forth distance. Default: 100
- `<state:x>` The Koopa Troopa's state. It can be Walk, Flying, or Shell. Default: Walk
- `<alpha:x>` The sprite's alpha value. Default: 100

\- Setting the state to something invalid will cause the Koopa Troopa to walk in place, completely unable to interact with Mario.

#### Shy Guy
Tag: `<customshyguy>`

Variables:
- `<scale:x>` The size of the Shy Guy. Default: 1
- `<speed:x>` The Shy Guy's movement speed when walking. Default: 2
- `<airspeed:x>` The Shy Guy's movement speed when flying. Default: 1
- `<distance:x>` The Shy Guy's back-and-forth distance. Default: 75
- `<idle:x>` The amount of idle time before the Shy Guy turns around and starts moving again. Default: 50
- `<state:x>` The Shy Guy's state. It can be Walk, Flying, Tumble or Squish. Default: Walk
- `<alpha:x>` The sprite's alpha value. Default: 100

\- Setting the state to something invalid will cause the Shy Guy to just stay (not walk) in place, completely unable to interact with Mario.

#### Bob-omb
Tag: `<custombobomb>`

Variables:
- `<scale:x>` The size of the Bob-omb. Default: 1
- `<speed:x>` The Bob-omb's movement speed when walking. Default: 0.5
- `<distance:x>` The Bob-omb's back-and-forth distance when idling (as in, when it's not actively chasing Mario). Default: 100
- `<alpha:x>` The sprite's alpha value. Default: 100

\- While you can change the alpha, the enemy is programmed to reset it when it starts chasing Mario. There really isn't much I can do here, but at least you can use this to make "Bob-omb ambushes".

#### Cheep Cheep
Tag: `<customcheep>`

Variables:
- `<scale:x>` The size of the Cheep Cheep. Default: 1 (Mega Cheep Cheep: 2)
- `<idlespeed:x>` The Cheep Cheep's movement speed when idle. Default: 2 (Mega Cheep Cheep: 3)
- `<chasespeed:x>` The Cheep Cheep's movement speed when chasing Mario. Default: 0.5 (Mega Cheep Cheep: 0.7)
- `<alpha:x>` The sprite's alpha value. Default: 100

#### Boo
Tag: `<customboo>`

Variables:
- `<scale:x>` The size of the Boo. Default: 1 (Big Boo: 2)
- `<alpha:x>` The sprite's alpha value. Default: 100


\- The Boo's code is slightly different, so that's all you can customize for now, unfortunately. Like the Bob-omb, you can change the alpha but the Boo's behavior changes it back anyway (and it does that almost instantly, making the alpha tag essentially useless).

#### Bully
Tag: `<custombully>`

Variables:
- `<scale:x>` The size of the Bully. Default: 1
- `<alpha:x>` The sprite's alpha value. Default: 100

#### Big Bully
Tag: `<custombigbully>`

Variables:
- `<scale:x>` The size of the Big Bully. Default: 2
- `<alpha:x>` The sprite's alpha value. Default: 100


\- Yes, unlike the Goombas or Cheep Cheeps, the Big Bully is actually a separate object and not just a variant of the normal Bully.

#### Penguin
Tag: `<custompenguin>`

Variables:
- `<scale:x>` The size of the Penguin. Default: 1
- `<speed:x>` The Penguin's movement speed. Default: 1.5 (Flying Penguin: 0)
- `<distance:x>` The Penguin's back-and-forth distance. Default: 50 (Flying Penguin: 0)
- `<idle:x>` The amount of idle time before the Penguin starts moving again. Default: 50
- `<state:x>` The Penguin's state. `x` can be Walk or Flying. Default: Walk
- `<alpha:x>` The sprite's alpha value. Default: 100

\- Because the normal flying penguin is set to not move at all, it's possible to make a penguin *fly* back and forth. 

#### Skelegoonie
Tag: `<customskelegoonie>`

Variables:
- `<speed:x>` The Skelegoonie's movement speed when it's on the ground. Default: 3
- `<xspeed:x>` The Skelegoonie's horizontal movement speed when flying. Default: ?
- `<yspeed:x>` The Skelegoonie's vertical movement speed when flying. Default: ?
- `<frame:x>` The Skelegoonie's "state". It doesn't have a State variable, and instead uses the sprite's frame for that purpose. The value can be run, flying or a number. If you type a number, its behavior depends on the number given. Refer to the note below. Default: flying
- `<alpha:x>` The sprite's alpha value. Default: 100

\- It's not possible to change the scale for Skelegoonies.

\- The default values for `<xspeed:x>` and `<yspeed:x>` are random numbers, and it's not possible to input random numbers at the moment.

\- Keep in mind that the state names for `<frame:x>` are in lower-case, unlike the other enemies. And as mentioned above, you can set the frame to a number:
- 1 causes the Skelegoonie to fly in place.
- 2 causes it to become wingless and float.
- 3 or higher just kills it immediately, as that'll put it in the death animation.

You *can* still take damage or kill it. You can probably make stationary floating enemies to bounce off of with this.

#### Water
Tag: `<customwater>`

Variables:
- `<length:x>` The water's length. Default: 500
- `<depth:x>` The water's depth. Default: 400
- `<angle:x>` The water's rotation/angle. Default: 0
- `<red:x>` The water's red value. Default: 40
- `<green:x>` The water's green value. Default: 128
- `<blue:x>` The water's blue value. Default: 215
- `<alpha:x>` The water's alpha value. Default: 50

\- Note that even if you change the water's color, the bubbles and "water splash" effects remain blue.

\---

As of version 4, the only enemies I have yet to add are **Goonies**, **Bill Blasters** and... **butterflies** (and technically none of them count as "enemies"; the Bill Blaster just spawns enemies). While it's possible to customize a Bullet Bill by itself, making a Bill Blaster fire customized Bullet Bills would be more complicated, if possible.

### Area Tags
Included in the mod are custom functions that do various things in a given area. While most of them were made for my level, that doesn't mean they can't be used in other levels, so feel free to use them!
Anyway, as you can tell by the name, these functions generally affect an area as a whole. Of course, they're active only when their corresponding tags are used.

Like the backgrounds, the signs containing these tags can be anywhere as long as they're within the right area.

#### Gravity Change
Tag: `<gravity:x>`

Allows you to change the gravity in an area. The larger the number, the higher the gravity. The default value is 1.

Previously, the mod used \<eartharea\> and \<spacearea\> for this purpose. Those have been removed in favor of something more flexible, but just in case you used them, the values are: 2 for eartharea, and 0.5 for spacearea.

\- With high gravity, you might take fall damage from heights you normally wouldn't expect any. This isn't part of my code, but just the way the game calculates fall damage based on gravity. Just ground pound or spin and you'll be fine!

#### Water Level Change
Tag: `<waterarea>`

Spawns an area-wide body of water in the area. It can be followed by additional tags that modify some of its variables.

Variables:
- `<waterlevel:x>` The initial water level. For reference, place any object at the water level you want and take note of its y value. Default: 100 pixels from the bottom
- `<depth:x>` The water's depth. Default: Half the level's Y size
- `<red:x>` The water's red value. Default: 40
- `<green:x>` The water's green value. Default: 128
- `<blue:x>` The water's blue value. Default: 215
- `<alpha:x>` The water's alpha value. Default: 50

Example: `<waterarea><waterlevel:736><red:0><green:0><blue:0><alpha:80>`

##### Water Signs
Tag: `<watersign>`

Put this in a sign to convert it to a "Water Sign", a special sign that changes the water level when interacted with. This works only in areas where `<waterarea>` is used.

By default, the new water level will be the Water Sign's y position. An optional tag, `<level:x>` can be included if you want the sign to set the water level to a specific level.

Example: `<watersign><level:480>`

\- Make sure the water level (as well as the Water Sign's values) is a multiple of 4, as otherwise the water might "twitch" up and down. This is because of the admittedly dumb way I programmed the water, and I haven't fixed it as of version 4.

#### Raining Fireballs
Tag: `<firearea>`

Constantly spawns raining Bowser fireballs in the area. The fireballs spawn in groups every random number of frames. As you can probably tell, this one's RNG-heavy.

Variables:
- `<timer:x>` The maximum wait time between groups of fireballs spawning. Default: 75
- `<amount:x>` The maximum number of fireballs to spawn in a group. Default: 5
- `<speed:x>` The average speed of the fireballs. Default: 4
- `<angle:x>` The fireballs' directional variance. A low number like 0 means the fireballs are more likely to fall straight down, while a larger number means a greater range of random directions including upwards. Regardless of the direction, the fireballs still spawn on the top of the screen. Default: 20
- `<chase>` If used, the fireballs will chase Mario like Bullet Bills.
- `<bounce>` If used, the fireballs will bounce off the ground instead of exploding.
- `<bouncespeed:x>` The power/speed of the bounce. Default: 0
- `<bouncecount:x>` The number of times a fireball can bounce before it explodes. Default: 3
- `<color:x>` The color/frame of the fireballs. 1 is orange, 2 is purple, 3 is green, 4 is blue, and anything larger than 4 is gray. 0 makes them flicker. Default: 1

Example: `<firearea><amount:1><timer:40><speed:3><angle:50><color:2><chase>`

\- The fireballs only spawn near Mario (or Luigi) directly above him, which means they *can* spawn under a high ceiling. Keep that in mind when using this in caves and interiors!

#### Wind Gusts
Tag: `<airarea>`

Activates wind gusts not unlike those seen in the Japanese version of Super Mario Bros. 2 (aka Lost Levels). With this, you can make extremely large gaps that are only possible with the wind.

Variables:
- `<speed:x>` The maximum speed of the wind. Use a negative number for leftward wind. Default: 3
- `<timer:x>` The time it takes to switch directions. Use -1 if you don't want the wind direction to ever change. Default: 100

Example: `<airarea><speed:1><timer:-1>`

\- Warning: High numbers can cause Mario/Luigi to glitch through walls or out of bounds!

\- Using this function will replace one layer of some backgrounds with the floating leaves effect! I might find some way to fix this in the future though. As of version 4, I haven't fixed this, sorry.

#### Darkness
Tag: `<darkarea>`

Puts an area in total darkness, leaving nothing but a tiny circle around the player visible. You might expect certain things like shine sprites and flames to illuminate the surrounding areas, but unfortunately they don't because it's really just an image superimposed to the screen that follows the player. I'm not experienced enough to do real-time lighting effects yet, if that's even possible with SM63 mods.

\- Remember, the darkness image might take a while to load, which can reveal secrets (if any) in the area for a brief moment.

#### Remove FLUDDs
Tag: `<nofludd>`

Upon entering an area with this tag in a sign, all FLUDDs will be automatically removed. Useful if you want to make FLUDD-less sections in your level.

\- You can still collect FLUDDs in the area and leave with them, as long as you don't come back.

#### Reset Switch Timer
Tag: `<resetswitch>`

Upon entering an area with this tag in a sign, all orange switch blocks will be deactivated.

\- Like the FLUDDs, you can activate a switch in this area and they'll still be active until you revisit this area.


\---

That's all for this section. By the way, you're not limited to one area tag per area, you can use multiple as long as you make sure to put each tag in its own sign (or else only one would activate). That said, certain combinations don't make for fair level design, like Darkness and Fireballs.

### Warp Trigger
Tag: `<warparea>`, plus other tags (details below)

Allows seamless instant teleportation. Well, almost seamless.

Okay, this isn't really an "area tag", but you are currently limited to using only one per area because code reasons.
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
