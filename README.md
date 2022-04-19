# Digital input
```package
core
radio
microphone
proportionalFont=github:lwchkg/pxt-proportional-font
```

```template
basic.forever(function () {
})
```
```blocks

```
## Step 0 @showDialog
Hello! Today we're going to learn about electrical circuits and how to detect an electric signal with Micro:bit pins.

## Step 1 @showDialog
### Electrical circuits
An electrical circuit is a closed path connecting electrical devices, through which a current can flow. In order for an electrical circuit to work, it must have a power source (a battery or a powered Micro:bit).
  
Earlier we [assembled](https://makecode.microbit.org/#tutorial:github:craftandcode/flashing-leds) a simple electrical circuit that consisted of the Micro:bit and a pair of LEDs. As we learned, we can turn the Micro:bit pins on and off with the help of a ``||pins.digital write pin||`` block.

```block
pins.digitalWritePin(DigitalPin.P0, 0)
```
## Step 2 @showDialog
### Digital output
When we use a ``||pins.digital write pin||`` block, the selected pin is set to work in a ``digital output`` mode, meaning that it outputs an electrical signal to power up the connected circuit.

There is another mode that uses the Micro:bit pins as electrical signal sensors to detect if there is a current in the circuit. This mode is called a ``digital input`` mode.

## Step 3 @showHint
### Reading electrical signals
To read an electrical signal, we use a ``||pins.digital read pin||`` block. This is a value block that has the value ``1`` if there is an electrical signal on the selected pin, or ``0`` if there is no signal.
  
Find this block inside the ``||pins.pins||`` category.
```hint
This is how you can display the value of the pin 0 on screen:
```
```block
    basic.showNumber(pins.digitalReadPin(DigitalPin.P0))
```

## Step 4 @showHint
### Reading electrical signals
Now let's use what we've learned! Assemble the code as shown and download it to the Micro:bit. What do you see on the screen? What does it mean?
```blocks
basic.forever(function () {
    basic.showNumber(pins.digitalReadPin(DigitalPin.P0))
})
```

## Step 7 @showHint
### Reading electrical signals
Now, connect the ``0`` and ``3V`` pins with a wire. Did anything change? What does that mean?
```hint
Your circuit should look like this:
```
![](https://github.com/CraftAndCode/team-sports/blob/master/image.png?raw=true)

## Step 8 @showHint
### A door alarm
Now we can know when the Micro:bit pin receives a signal and when the circuit is broken and the signal is interrupted. Let's use this knowledge to make a simple door alarm!
  
When the circuit between the ``0`` and ``3V`` pins is broken, an audible alarm turns on. Think of a way to attach the device to your doorframe so that the circuit is broken when the door is opened!

```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P0) == 0) {
        music.playMelody("C C C5 C5 C C C5 C5 ", 120)
    } else {
        music.stopAllSounds()
    }
})

```
## Step 9 @showHint
### Now it's your turn!
Let's run a test. Create a program that displays a lighted sign if there is a signal on pin ``1``.

You can also make a more difficult program that shows the current state of each pin.
```hint
```
![](https://github.com/CraftAndCode/team-sports/blob/master/GifLightning.gif?raw=true)
## Answers @showDialog
### Answers: Simple
```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
        basic.showLeds(`
            . . # . .
            . # . . .
            # # # # .
            . . # . .
            . # . . .
            `)
    } else {
        basic.clearScreen()
    }
})
```
### Answers: More difficult
```blocks
basic.forever(function () {
    if (pins.digitalReadPin(DigitalPin.P0) == 1) {
        basic.showNumber(0)
        basic.pause(500)
    } else {
        basic.clearScreen()
    }
    if (pins.digitalReadPin(DigitalPin.P1) == 1) {
        basic.showNumber(1)
        basic.pause(500)
    } else {
        basic.clearScreen()
    }
    if (pins.digitalReadPin(DigitalPin.P2) == 1) {
        basic.showNumber(2)
        basic.pause(500)
    } else {
        basic.clearScreen()
    }
})
```

## Step 10
All the tasks have been completed! Now you know how to use Micro:bit pins to read electrical signals.

