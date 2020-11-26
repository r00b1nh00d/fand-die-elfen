# Fang die Elfen 
## ~avatar avatar @unplugged
gedulde dich noch ein wenig bis es soweit ist :-)

input.onButtonPressed(Button.A, function () {
    if (Spieler.get(LedSpriteProperty.X) == 2 && Spieler.get(LedSpriteProperty.Y) == 2) {
        game.addScore(1)
        zeit = Math.max(50, 200 - 5 * game.score())
    } else {
        game.removeLife(1)
    }
})
let zeit = 0
let Spieler: game.LedSprite = null
Spieler = game.createSprite(2, 2)
zeit = 200
game.setLife(10)
basic.forever(function () {
    Spieler.move(1)
    if (Spieler.isTouchingEdge()) {
        if (Spieler.get(LedSpriteProperty.Y) == 2) {
            if (Spieler.get(LedSpriteProperty.X) > 2) {
                Spieler.set(LedSpriteProperty.Direction, randint(-1, -3) * 45)
            } else {
                Spieler.set(LedSpriteProperty.Direction, randint(1, 3) * 45)
            }
        } else {
            if (Spieler.get(LedSpriteProperty.Y) > 2) {
                Spieler.set(LedSpriteProperty.Direction, randint(-1, 1) * 45)
            } else {
                Spieler.set(LedSpriteProperty.Direction, randint(3, 5) * 45)
            }
        }
        basic.pause(100)
        Spieler.move(1)
    }
    basic.pause(zeit)
})
}");</script>
