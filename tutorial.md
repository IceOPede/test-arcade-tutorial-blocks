# Block Game Tutorial

## Intro @showdialog

![test image](https://raw.githubusercontent.com/IceOPede/test-arcade-tutorial/master/docs/static/tutorials/img.png)

## Hintergrund zeichnen

Zu beginnen zeichnen wir einen Hintergund öffne ``||scene:Scene||`` und wähle``||scene:set background image||`` aus und ziehe es in den editor.
Auf der linken seite findest du ein icon wähle dieses aus um ein bild aus denn ressourcen zu wählen.

Drücke auf **next** um fortzufahren.

```blocks
scene.setBackgroundImage(img``)
```

## Spieler erstellen

Um den Spieler zu erstellen wählen wir aus den ``||sprites:Sprites||`` die option um einen spieler zu erstellen mit ``||sprites:set spieler to||``
Diesem Spieler kann man wie mit dem hintergrund ein bild hinzufügen.

```blocks
scene.setBackgroundImage(img``)
// @highlight
let spieler = sprites.create(img``, SpriteKind.Player)
```

## Player fallen lassen

Damit der Spieler nun auch fallen kann und nicht aus dem bildschirm fällt kann finded man in ``||sprites:Sprites||`` die optionen 
``||sprites:set spieler ay to||`` und ``||sprites:set spieler stay in screen||``

```blocks
scene.setBackgroundImage(img``)
let spieler = sprites.create(img``, SpriteKind.Player)
// @highlight
spieler.ay = 300
// @highlight
spieler.setStayInScreen(true)
```

## Spieler kontrollieren

Um den Spieler fligen zu lassen öffne ``||controller:Controller||`` und wähle ``||controller:on any button pressed||`` damit falls ein beliebiger Knopf gedrückt wird der spieler fliegt
In diesem Ereignis werden wir die geschwindigkeit um 100 reduzieren ``||sprites:set spieler vy to||``

```blocks
controller.anyButton.onEvent(ControllerButtonEvent.Pressed, function () {
    spieler.vy = -100
})
```

## Step 2

Test 2

## Complete

Finsihed


## Remove 

```blocks
// controller event any button should jump
controller.anyButton.onEvent(ControllerButtonEvent.Pressed, function () {
    player.vy = -100
})
// game over if player overlaps projectile
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    game.over(false)
})
let bottomProjectile: Sprite = null
let topProjectile: Sprite = null
let gap = 0
let player: Sprite = null
scene.setBackgroundImage(img``)
// sound
music.setVolume(0)
player = sprites.create(img``, SpriteKind.Player)
// set player y acceleration to 300
player.ay = 300
player.setStayInScreen(true)
// spawn, move obstacles as projectiles
game.onUpdateInterval(1500, function () {
    gap = randint(0, 3)
    let topImage;
let bottomImage;
if (gap == 0) {
        topImage = img``
        bottomImage = img``
    } else if (gap == 1) {
        topImage = img``
        bottomImage = img``
    } else if (gap == 2) {
        topImage = img``
        bottomImage = img``
    } else {
        topImage = img``
        bottomImage = img``
    }
    topProjectile = sprites.createProjectileFromSide(topImage, -45, 0)
    topProjectile.top = 0
    bottomProjectile = sprites.createProjectileFromSide(bottomImage, -45, 0)
    bottomProjectile.bottom = scene.screenHeight()
})
```