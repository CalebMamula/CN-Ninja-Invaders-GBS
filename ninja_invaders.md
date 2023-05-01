### @explicitHints true
# Code Ninjas Unofficial GBS (Ninja Invaders)


```assetjson
{
  "README.md": " ",
  "assets.json": "",
  "images.g.jres": "{\n    \"P4(`CNLh^)P:D9Kpa+R5\": {\n        \"data\": \"hwQMABAAAAAADw8AAAAAAADwAAAA8A8AAP//APAPAADwv/0P//8P8P//Ef/////////x/////////9v/////AP//8f////////8R///////wv/0P//8P8AD//wDwDwAAAAAAAADwDwA=\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"displayName\": \"ninjaSprite\"\n    },\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myImages\"\n    }\n}",
  "images.g.ts": "// Auto-generated code. Do not edit.\nnamespace myImages {\n\n    helpers._registerFactory(\"image\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"P4(`CNLh^)P:D9Kpa+R5\":\n            case \"ninjaSprite\":return img`\n. . . . f f f f f . . . \n. . . f f f f f f f . . \nf . f f f f f f f f f . \n. f f b f f f f f b f . \nf . f d 1 1 b 1 1 d f . \n. . f f 1 f d f 1 f f . \n. . . f f f f f f f . . \n. . . . f f f f f . . . \n. . . f f f f f f f . . \n. . f f f f f f f f f . \n. . f f f f f f f f f . \n. f . f f f f f f f . f \n. f . f f f f f f f . f \n. . . . f f f f f . . . \n. . . . f f . f f . . . \n. . . f f f . f f f . . \n`;\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"animation\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"song\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n",
  "main.blocks": "<xml xmlns=\"https://developers.google.com/blockly/xml\"><variables><variable id=\"W)t)RD5T*{kylRj-;L]a\">mySprite</variable><variable type=\"KIND_SpriteKind\" id=\"5bdv9B~8K.:##DQEJ`|g\">Player</variable><variable type=\"KIND_SpriteKind\" id=\"HLjMyi$oA.5AZIiJn#i;\">Projectile</variable><variable type=\"KIND_SpriteKind\" id=\"$n4#WqCz^D~`PmLUo]tx\">Food</variable><variable type=\"KIND_SpriteKind\" id=\"(uYX/Oj@Oq5d3SRMzGa8\">Enemy</variable></variables><block type=\"pxt-on-start\" x=\"0\" y=\"0\"><statement name=\"HANDLER\"><block type=\"variables_set\"><field name=\"VAR\" id=\"W)t)RD5T*{kylRj-;L]a\">mySprite</field><value name=\"VALUE\"><shadow xmlns=\"http://www.w3.org/1999/xhtml\" type=\"math_number\"><field name=\"NUM\">0</field></shadow><block type=\"spritescreate\"><value name=\"img\"><shadow type=\"screen_image_picker\"><field name=\"img\">assets.image`ninjaSprite`</field><data>{\"commentRefs\":[],\"fieldData\":{\"img\":\"P4(`CNLh^)P:D9Kpa+R5\"}}</data></shadow></value><value name=\"kind\"><shadow type=\"spritekind\"><field name=\"MEMBER\">Player</field></shadow></value></block></value></block></statement></block></xml>",
  "main.ts": "let mySprite = sprites.create(assets.image`ninjaSprite`, SpriteKind.Player)\n",
  "pxt.json": "{\n    \"name\": \"Ninja Sprite\",\n    \"description\": \"\",\n    \"dependencies\": {\n        \"device\": \"*\"\n    },\n    \"files\": [\n        \"main.blocks\",\n        \"main.ts\",\n        \"README.md\",\n        \"assets.json\",\n        \"images.g.jres\",\n        \"images.g.ts\"\n    ],\n    \"targetVersions\": {\n        \"branch\": \"v1.12.30\",\n        \"tag\": \"v1.12.30\",\n        \"commits\": \"https://github.com/microsoft/pxt-arcade/commits/33228b1cc7e1bea3f728c26a6047bdef35fd2c09\",\n        \"target\": \"1.12.30\",\n        \"pxt\": \"8.5.41\"\n    },\n    \"preferredEditor\": \"blocksprj\"\n}\n"
}






```






```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    projectile = sprites.createProjectileFromSprite(img`
        . . . . . . . 6 6 . . . . . . .
        . . . . . . . 6 6 . . . . . . .
        . . . . . . 6 6 3 6 . . . . . .
        . . . . . . 6 3 3 6 . . . . . .
        . . . . . . 6 3 3 6 . . . . . .
        . . . . . . 6 3 3 6 . . . . . .
        . . . . . 6 6 3 3 3 6 . . . . .
        . . . . . 6 3 3 3 3 6 . . . . .
        . . . . . 6 3 3 3 3 6 . . . . .
        . . . . . 6 3 3 3 3 6 . . . . .
        . . . . 6 3 3 3 3 3 6 . . . . .
        . . . . 6 3 3 3 3 3 6 . . . . .
        . . . . 6 3 3 3 3 3 3 6 . . . .
        . . . . 6 3 3 3 3 3 3 6 . . . .
        . . . . 6 3 3 3 3 3 3 6 . . . .
        . . . . 6 6 6 6 6 6 6 6 . . . .
        `, mySprite, 0, -100)
})
sprites.onOverlap(SpriteKind.Projectile, SpriteKind.Enemy, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.spray, 200)
    info.changeScoreBy(1)
})
mySprite.setKind(SpriteKind.Player)
sprite.setKind(SpriteKind.Player)
let mySprite: Sprite = null
scene.setBackgroundColor(4)
mySprite = sprites.create(assets.image`ninja`, SpriteKind.Player)
mySprite.setPosition(76, 101)
controller.moveSprite(mySprite, 100, 0)
mySprite.setStayInScreen(true)
info.setScore(0)
game.onUpdateInterval(1000, function () {
    alien = sprites.createProjectileFromSide()
    alien.setKind(SpriteKind.Enemy)
    alien.setPosition(randint(0, 160), 0)
})
mySprite.setPosition(randint(0, 10), 0)


```




## Introduction @showdialog
In this tutorial, you will create your very own video game. Enemies will be falling from the sky, and it's up to you to shoot them before they can reach you. Follow the instructions, but feel free to be creative and add custom details. Click Ok to get started!
![Image description](https://github.com/CalebMamula/Caleb-CodeNinjas-GBS/blob/1cf49c592b5e93c65eea6b0104407d532019ae2a/images./ninja_invaders.gif%20(2).gif)

## GBS: Ninja Invasion Step 1
### Make Our Background  




First up, our game needs a background. Grab a ``||scene:set background color||`` block from the ``||scene:Scene|`` dropdown and place it inside our ``||loops:on start||`` container already on the screen.


Click the grey bubble in the ``||scene: set background color||`` block and select a color to use as a background.


Chcek the Game Window on the right side of the screen to see the selected background color appear!


Click **Next** to go to the next step.


## GBS: Ninja Invasion Step 2
### Add Our Player Sprite


Now we are going to create our main character. Use a ``||variables:set [mySprite] to||`` block from the ``||sprites:Sprites||`` dropdown and place it at the bottom of the ``||loops: on start||`` container.


Click the grey oval and select the ninja picture under **My Assets**. Feel free to change this sprite and make it your own.


Make sure to change the name of your sprite by clicking on **mySprite** and pressing **Rename variable**. Change the name to Ninja, or something else if you'd like. Just remember what you chose.


## GBS: Ninja Invasion Step 3
### Code Movement


To move our ninja we need to use a ``||controller:move [mySprite] with buttons||`` block. Place this at the bottom of the ``||loops:on start||`` container.


We need to tell the game which sprite we want to move. Make sure to change **mySprite** to **Ninja**. This means the arrow keys and WASD can now move the ninja. Try it out!




## GBS: Ninja Invasion Step 4
### Restrict Movement
Did you notice your character can go off screen? To fix this we are going to use ``||sprites:set [mySprite] stay in screen |``. Once again, be sure to change **mySprite** to **Ninja**.


Next, we need our character to only go back and forth. First, grab ``||sprites:setPosition||`` from ``||sprites:Sprites||``. Set the x around 75 and the y to about 100.


We also need to stop the player from moving up and down. First click the + button on the right side on the block. Now, change the vy box on the ``||controller:move||`` block to 0.


## GBS: Ninja Invasion Step 5
### Spawning The Enemies Part 1
To spawn our enemies go to ``||game:Game||`` and pull the ``||game:on game update every||`` onto the editor. This is a container, so you can place it anywhere you'd like. The code we place here will run on a repeating timer.


Now we are going to create our enemy. Use a ``||variables:set [projectile] to||`` block from the ``||sprites:Sprites||`` dropdown and place it in the ``||game:on game update every||`` container. **There are two ``||variables:projectile||`` blocks. Use the bottom one.**


Click the grey oval and select a sprite of your choice from **Gallery**.


At the end of the ``||variables:projectile||`` block, change the (vx) to 0 and the (vy) to 30. This will make our sprites go straight down. Also make sure to change the name of your sprite by clicking on **mySprite** and pressing **Rename variable**. Pick any name that fits your new enemy.


## GBS: Ninja Invasion Step 6
### Spawning The Enemies Part 2


We will now use a ``||sprites:set [mySprite] position to||`` block to make all enemies start at the top of the screen. Change **mySprite** to the name of your enemy.


Under ``||math:Math||`` grab a ``||math:pick random||`` block and place it into the x oval of our ``||sprites:set  [mySprite] position to ||`` block. Change the range so it goes from 0 to 160. The y oval will stay as 0.


Notice how many enemies are coming down? We can change this by modifying the number at the top of the container. Instead of 500 ms, try 1 Second (1000 ms).


Final thing for our enemies, we need to change their kind. Grab a ``||sprites:set [mySprite] kind to||`` and choose Enemy. We will need this later on. Don't forget to set which sprite we are affecting.


## GBS: Ninja Invasion Step 7
### Ready, Aim, FIRE!
Now we are going to code our projectiles. To start, we are going to need a new container. Let's use the ``||controller:On A button pressed||``. This can be placed anywhere on the coding area. Code we place in this new container will run when we hit the space bar.


In this container we are going to place a ``||variables:set [projectile] to||`` block from the ``||sprites:Sprites||`` dropdown. **There are two ``||variables:projectile||`` blocks. Use the top one.**


Click the grey oval and select a picture from **Gallery** or quickly design your own. Keep it simple.


Change the **mySprite** to **Ninja**, that way it will look like the ninja is firing the shots.


At the end of the ``||variables:projectile||`` block, change the (vx) to 0 and the (vy) to -100. This will make our sprites quickly go straight up.


Open the game and try it out. Our character can now shoot projectiles when you press space.


## GBS: Ninja Invasion Step 8
### Destroy The Enemies Part 1


Almost done. For our next step, go to ``||sprites:Sprites||`` and grab the ``||sprites: on sprite of kind [Player] overlaps otherSprite of kind [Player]||``.


Change the first ``||sprites:Player||`` to ``||sprites:Projectile||``, and the second ``||sprites:Player||`` to ``||sprites:Enemy||``.


Now when our **Projectile** hits the **Enemy**, the code we place in this container will run.
```
## GBS: Ninja Invasion Step 9
### Destroy The Enemies Part 2
Place a ``||sprites:destroy [mySprite]||`` block inside our new overlap container. Drag an ``||variables:otherSprite||`` oval where it says ``||variables:mySprite||``.


Now click the + button on the new destroy block. Pick a fun effect and try it out. It is recommended to change the duration time to either 100 ms or 200 ms.


Last but not least, go to ``||info:Info||`` and grab a ``||info:change score by||`` block. Place this in our overlap container.


Try the game out! When you are ready, move on to the final step.


## GBS: Ninja Invasion Step 10
### ``||variables:C||`` ``||controller:u||`` ``||loops:s||`` ``||animation:t||`` ``||logic:o||`` ``||sprites:m||`` ``||music:i||`` ``||math:z||`` ``||scene:e||``
**The tutorial is finished, but now it's time to customize. Here are a few examples of things to try:**


-Put a dialog box or splash screen for game instructions.


-Customize the sprites and background to your liking. It's your game! (The fill option in the sprite editor can speed this process up)


-Put sound effects in the game for even more fun!


-Allow a way to win. Add a timer, add lives, or some combination. Be creative!


-Add animations. For example, make the projectiles 'spin'.


-Make a new type of enemy. Maybe something that moves faster? Perhaps harder to kill?


*Decide with your Sensei for which customizations you want to make to your game. When you are ready, click **Done**.*



