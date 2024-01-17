let hunger: number
hunger = 50
let happy: number
happy = 50
let faceState: number
faceState = 0

serial.writeLine("foobar")

basic.forever(function () {
    loops.everyInterval(1000, function () {

        hunger -= 1
        if (hunger < 0) {
            hunger = 0
        }
    })
loops.everyInterval(1000, function () {

        happy -= 1
        if (happy < 0) {
            happy = 0
        }
    })
input.onButtonPressed(Button.A, function () {
        happy += 10
    })
input.onButtonPressed(Button.B, function () {
        hunger += 10
    })
// Face Code
    // Normal face
    if (happy > 30 && hunger > 30) {
        faceState = randint(0, 2)
        if (faceState == 0) {
            state0()
        }
        if (faceState == 1) {
            state1()
        }
        if (faceState == 2) {
            state2()
        }
        function state0() {
            basic.showLeds(`
                . # . # .
                . # . # .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(500)
            basic.showLeds(`
                . # . # .
                . . . . .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(10)
            basic.showLeds(`
                . . . . .
                . . . . .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(10)
            basic.showLeds(`
                . # . # .
                . . . . .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(5)
        }
function state1() {
            basic.showLeds(`
                . # . # .
                . # . # .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(500)
            basic.showLeds(`
                # . # . .
                # . # . .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(10)
            basic.showLeds(`
                . # . # .
                . # . # .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(10)
            basic.showLeds(`
                . . # . #
                . . # . #
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(5)
        }
function state2() {
            basic.showLeds(`
                . # . # .
                . # . # .
                . . . . .
                # . . . #
                . # # # .
                `)
            basic.pause(500)
            basic.showLeds(`
                . . . . .
                . # . # .
                . # . # .
                # . . . #
                . # # # .
                `)
            basic.pause(10)
            basic.showLeds(`
                . . . . .
                . . . . .
                . # . # .
                # . . . #
                . # # # .
                `)
            basic.pause(10)
            basic.showLeds(`
                . . . . .
                . # . # .
                . # . # .
                # . . . #
                . # # # .
                `)
            basic.pause(10)
        }
    }
    // Mid face
    if (happy >= 15 && happy <= 30 || hunger >= 15 && hunger <= 30) {
        basic.showLeds(`
            . # . # .
            . # . # .
            . . . . .
            # # # # #
            . . . . .
            `)
        basic.pause(500)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            # # # # #
            . . . . .
            `)
        basic.pause(10)
    }
    // sad face
    if (happy < 15 || hunger < 15) {
        basic.showLeds(`
            . # . # .
            . # . # .
            . . . . .
            . # # # .
            # . . . #
            `)
        basic.pause(500)
        basic.showLeds(`
            . . . . .
            . . . . .
            . . . . .
            . # # # .
            # . . . #
            `)
        basic.pause(10)
    }
    // dead
    if (happy == 0 && hunger == 0) {
        basic.showLeds(`
            # # . # #
            # # . # #
            . . . . .
            . # # # .
            # . . . #
            `)
    }
})
