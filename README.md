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
Hello! Today we'll learn about electric circuits and learn to detect electric signal with Micro:bit pins.

## Step 1 @showDialog
### Electric circuits
Electric circuit is a closed path connecting electric devices through which a current can flow. In order for an electric circuit to work, it must include a power source (a battery or a powered Micro:bit).
  
Earlier we've [assembled](https://makecode.microbit.org/#tutorial:github:craftandcode/flashing-leds) a simple electric circuit that consisted of Micro:bit and a pair of LEDs. As we know, we can turn the Micro:bit pins on and off with the help of a ``||pins.digital write pin||`` block.

```block
pins.digitalWritePin(DigitalPin.P0, 0)
```
## Step 2 @showDialog
### Digital output
When we use a ``||pins.digital write pin||`` block, the selected pin is set to work in a ``digital output`` mode, meaning it outputs electric signal to power up the connected circuit.

There is another mode which uses the Micro:bit pins as electric signal sensors to tell if there is current in the circuit. This mode is called a ``digital input`` mode.

## Step 3 @showHint
### Reading electric signal
To read electric signal, we use a ``||pins.digital read pin||`` block. This is a value block that has the value ``1`` in case there is elecric signal on the selected pin, or ``0`` if there is no signal.
  
Find this block inside the ``||pins.pins||`` category.
```hint
That's how you can display the value of the pin 0 on screen:
```
```block
    basic.showNumber(pins.digitalReadPin(DigitalPin.P0))
```

## Step 4 @showHint
### Reading electric signal
Let's use all that we've learned! Assemble the code as shown and download it to Micro:bit. What do you see on screen? What does it mean?
```blocks
basic.forever(function () {
    basic.showNumber(pins.digitalReadPin(DigitalPin.P0))
})
```

## Step 7 @showHint
### Reading electric signal
Now, connect the ``0`` and ``3V`` pins with a wire. Did anything change? What does it mean?
```hint
Your circuit should look like this:
```
![](https://github.com/CraftAndCode/team-sports/blob/master/image.png?raw=true)

## Step 8 @showHint
### A door alarm
Now we can know when Micro:bit pin receives signal and when the circuit breaks and the signal is interrupted. Let's use it to make a simple door alarm!
  
When the circuit between the ``0`` and ``3V`` pins breaks, a sound alarm trns on. Think of a way to attach the device to your doorframe so that the circuit breaks when the door is opened!

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
Let's have a test. Make a program that displays a lighting sign if there is signal on pin ``1``.

Also you can make a more difficult program that shows the current state of each pin.
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
All tasks completed! Now you know how to use Micro:bit pins to read electric signal.