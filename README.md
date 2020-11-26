# Fang die Elfen 
## ~avatar avatar @unplugged
Die Elfen sind außer Rand und Band. Sie flitzen wie wild über dan Calliope Bildschirm! <br>
Deine einzige Chance, wenn Sie in der Mitte des Bildschirms sind Drücke die Taste A um einen zu fangen. <br>
![ElfenFangen](https://github.com/r00b1nh00d/fang-die-elfen/blob/master/ElfenFangen.gif?raw=true)

## Schritt 1
Erstelle ``||basic:beim Start||`` eine Variable ``||variables:Elfen||`` und eine namens ``||variables:Zeit||`` und Stelle eine Zeit von 22 ein <br>
Hier kannst du auch gleich noxh den Block ``||game: setze Anzahl Leben||`` einfügen.

## Schritt 2
Um die Elfen über den Bildschirm flitzen zu lassen, sollen Sie sich zu Beginn des ``||basic:dauerhaft||`` Blocks ``||game: um 1 bewegen||``. <br>
Anschließend soll mit einer ``||logic:wenn-dann||`` - Bedingung geprüft werden ob der Elf schon den Rand berührt. <br>
Sollte er den Rand Berühren kannst du mithilfe von weiteren ``||logic:wenn-dann||`` - Bedingung und einer ``||math:zufälligen||`` Zahlden Elfen in eine immer wieder andere ``||game:Richtung||`` abprallen lassen. 

**Probere dies am besten erstmal selbst aus bevor du in die Lösung schaust!**


## Schritt 3
Ich hoffe du hast es erstmal selbst versucht. Sollte es noch kleinere Buggs geben wäre hier auch eine Lösungsmöglichkeit.

```blocks 
input.onButtonPressed(Button.A, function () {
    if (Elfen.get(LedSpriteProperty.X) == 2 && Elfen.get(LedSpriteProperty.Y) == 2) {
        game.addScore(1)
        zeit = Math.max(50, 200 - 5 * game.score())
    } else {
        game.removeLife(1)
    }
})
let zeit = 0
let Elfen: game.LedSprite = null
Elfen = game.createSprite(2, 2)
zeit = 200
game.setLife(10)
basic.forever(function () {
    Elfen.move(1)
    if (Elfen.isTouchingEdge()) {
        if (Elfen.get(LedSpriteProperty.Y) == 2) {
            if (Elfen.get(LedSpriteProperty.X) > 2) {
                Elfen.set(LedSpriteProperty.Direction, randint(-1, -3) * 45)
            } else {
                Elfen.set(LedSpriteProperty.Direction, randint(1, 3) * 45)
            }
        } else {
            if (Elfen.get(LedSpriteProperty.Y) > 2) {
                Elfen.set(LedSpriteProperty.Direction, randint(-1, 1) * 45)
            } else {
                Elfen.set(LedSpriteProperty.Direction, randint(3, 5) * 45)
            }
        }
        basic.pause(100)
        Elfen.move(1)
    }
    basic.pause(zeit)
})
```
