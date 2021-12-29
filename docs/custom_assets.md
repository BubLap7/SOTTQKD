## Resources

If you are not able to make your own assets or find what you're looking for in the **Community Asset Hub**, have a look at the following sites:

___

**Paid Resources**

 * [Audio Jungle](https://audiojungle.net/) - Audio, Music, Ambience
 * [3d Ocean](https://3docean.net/) - 3D Assets, Textures
 * [Turbosquid](https://www.turbosquid.com/) - 3D Assets, Textures

___

**Free Resources**

 * [Quaternius](https://quaternius.com/index.html) - 3D Assets, Animations, Textures
 * [ZapSplat](https://www.zapsplat.com/) - Audio, Music, Ambience
 * [Freesound](https://freesound.org/) - Audio, Music, Ambience
 * [Pmdndrs](https://market.pmnd.rs/) Market - 3D Models
 * [Free3D](https://free3d.com/) - 3D Assets, Textures
 * [FlatIcon](https://www.flaticon.com/) - Vectors, Icons

___

When uploading any custom assets or using them in your game, make sure that you have the legal right to do so. Its always better to check the license.

## 3D Models

You can upload custom 3D Models to use in your scene. Currently only .obj and .gltf are supported. You can load a 3D asset into your scene using KrunkScript:

<p class="hidep"><strong class="client-side">client-side</strong></p>

```krunkscript
# add object
obj model = GAME.SCENE.addAsset(
    aid, # str assetID
    x, # num x position
    y, # num y position
    z, # num z position
    scl, # num scale
    colr, # str color (optional)
    data # obj additional data (optional)
);
```

## Textures & Images

Textures & Images can be used to render an image on a 3D asset or on the [Overlay Canvas](./files/rendering_2d?id=overlay-canvas). Currently only .png images are supported.

--- 

You can update an objects texture using KrunkScript:

<p class="hidep"><strong class="client-side">client-side</strong></p>

```krunkscript
# add object
obj cube = GAME.SCENE.addCube("", "#fff", 0, 0, 0, 10, 10, 10);

# update texture
cube.texture = "assetID"; # new asset id
```

## Animations

Animations can be used to add life to your scene.\
To use animations on models, please use the .gltf format.\
For an asset to use animations it must have clips attached to the model.\
When attempting to play an animation, make sure you're using the correct name of the clip.\
You have a few options for playing animations on an asset:

---

**Using KrunkScript:**

<p class="hidep"><strong class="client-side">client-side</strong></p>

```krunkscript
# create an object
obj object = GAME.SCENE.addAsset("11441g", 0, 0, 0, 1);

# play animation on object:
object.playAnim(
	"Jump", # str clip name
	1 # num repetitions (0 = infinite loop)
);

# stop animations on object:
object.stopAnim();

# this also works on the built-in player & AI objects
player.playAnim("Jump");
aiBot.playAnim("Jump");
```

___

**Using Triggers:** You can use the following [Trigger Actions](./files/trigger_logic?id=trigger-actions) to interact with animations:
 * **Play Animation:** Plays a clip by name on interface objects


For more information on using triggers, refer to the [Triggers](./files/trigger_logic) section.

___

**Override:** Krunker also has a few default animations that are linked to player events:

 * **Idle:** Loops while player is idle
 * **Move:** Loops while player is moving
 * **Crouch:** Loops while player is crouched
 * **Jump:** Plays when player jumps
 * **Melee:** Plays when player melees
 * **Shoot:** Plays when player shoots
 

These animations will play automatically if you assign a [Custom Model](./files/custom_assets?id=_3d-models) to the player model that contains those clips. Check the **Class Config** documentation to learn how.

___

If you want to play animations through the server and all clients, please refer to the [Multiplayer & Networking](./files/multiplayer_&_networking) section.

## Sounds & Music

Sound is a very important aspect of any game. In Krunker you have a few options when it comes to playing sounds (only .mp3 is supported):

___

**Using KrunkScript:**

<p class="hidep"><strong class="client-side">client-side</strong></p>

```krunkscript
# play sound in 2D space (sound id, volume, looping)
obj sound = GAME.SOUND.play2D(
    id, # num
    vol, # num (0-1)
    rate, # num (0-1)
    loop # bool
);

# play sound in 3D space (sound id, volume, looping, position)
obj sound = GAME.SOUND.play3D(
    id, # num
    vol, # num
    x, # num
    y, # num
    z, # num
    rate, # num
    loop # bool
);

# alter rate & volume
sound.rate = 0.5;
sound.volume = 0.2;

# mute, unmute, play, stop & pause
sound.mute();
sound.unmute();
sound.play();
sound.stop();
sound.pause();

# fade
sound.fade(
    0.1, # from volume
    0.1, # to volume
 	0, # duration
);
```

___

**Using Triggers:** You can use the following [Trigger Actions](./files/trigger_logic?id=trigger-actions) to interact with sounds:
 * **Broadcast Sound**: Emit sound to entire server
 * **Send Sound**: Emit sound to specific player
 * **Stop Sound**: Stop sound by id
 

For more information on using triggers, refer to the [Triggers](./files/trigger_logic) section.

___

Krunker also has a few default sounds such as footsteps, jumping sounds etc. If you want to override or disable them, you can use a [Resource Pack](./files/mod-resource_packs?id=custom-css).

___

If you want to play sounds/audio through the server and all clients, please refer to the [Multiplayer & Networking](./files/multiplayer_&_networking) section.

## Scripts

A script is used to calculate and apply logic to your game.

```krunkscript
num test = 10;
num action calc(num val) {
    return test * val;
}
GAME.log(calc(5)); # logs 50
```

To learn more about scripts, refer to the [Scripting](./files/scripting) section of the documentation.
