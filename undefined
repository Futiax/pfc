enum RadioMessage {
    message1 = 49434,
    deux = 3968
}
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == pfc % 3) {
        basic.showLeds(`
            . . . . .
            . # # # .
            . . . . .
            . # # # .
            . . . . .
            `)
    } else if (pfc % 3 == 0 && receivedNumber == 1) {
        basic.showIcon(IconNames.No)
    } else if (pfc % 3 == 1 && receivedNumber == 2) {
        basic.showIcon(IconNames.No)
    } else if (pfc % 3 == 2 && receivedNumber == 0) {
        basic.showIcon(IconNames.No)
    } else {
        basic.showIcon(IconNames.Yes)
        music.playMelody("C D E F G A B C5 ", 120)
        music.playMelody("C D E F G A B C5 ", 180)
        music.playMelody("C D E F G A B C5 ", 120)
    }
})
radio.onReceivedMessage(RadioMessage.deux, function () {
    init = 0
})
radio.onReceivedMessage(RadioMessage.message1, function () {
    init = 1
})
let pfc = 0
let init = 0
init = 0
radio.setGroup(1)
radio.setFrequencyBand(0)
radio.setTransmitPower(7)
basic.forever(function () {
    while (!(input.buttonIsPressed(Button.AB))) {
    	
    }
    while (0 == init) {
        radio.sendMessage(RadioMessage.message1)
    }
    pfc = 1
    while (!(input.buttonIsPressed(Button.AB))) {
        if (pfc % 3 == 1) {
            basic.showString("P")
        } else if (pfc % 3 == 2) {
            basic.showString("F")
        } else if (pfc % 3 == 0) {
            basic.showString("C")
        }
        if (input.buttonIsPressed(Button.A)) {
            pfc += -1
        } else if (input.buttonIsPressed(Button.B)) {
            pfc += 1
        }
        serial.writeNumber(pfc % 3)
    }
    while (1 == init) {
        radio.sendMessage(RadioMessage.deux)
    }
    serial.writeLine("" + (pfc % 3))
    radio.sendNumber(pfc % 3)
})
