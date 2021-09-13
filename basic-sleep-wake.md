# Save power by putting your micro:bit to sleep and waking it up later

## Introduction Step @showdialog
You can use the ``||power:Power||`` blocks to control when your micro:bit goes to sleep in low power mode and wakes up to full power mode. 
This will help save on batteries when you are running a progarm for a long time.

We know the micro:bit is saving power when the red power LED on the rear of the board is off (on battery) or blinking (on usb). 

![micro:bit power LED](https://microbit-foundation.github.io/pxt-microbit-v2-power/docs/static/power-led.png)

## Step 1: Start with a basic program
Let's start with a simple program to show the temperature on the display in a continuous forever loop.

```template
basic.forever(function () {
    basic.showNumber(input.temperature())
})
```

## Step 2: Put the micro:bit to sleep
Reading and displaying the temperature forever is going to use up energy pretty quickly. Let's use our ``||power:Power||`` blocks to put the micro:bit to sleep until we want to read the temperature again.

Drag a ``||power:request low power||`` block underneath the ``||basic:show number||`` block. Now when the micro:bit shows us the temperature it will then try to go to sleep.

```blocks
basic.forever(function () {
    basic.showIcon(IconNames.Heart)
    basic.showNumber(input.temperature())
    power.lowPowerRequest()
})
```

## Step 3: Tell the micro:bit how to wake up
Good work. You've now told the micro:bit when to go to sleep, but it doesn't yet know how to wake up. When you use the ``||Power||`` blocks to put the micro:bit to sleep, you will always need to tell it how to wake up again, otherwise it will just ignore you and stay awake!

Drag a ``||power:full power on button A||`` block into ``||basic:on start||`` to complete your program.

```blocks
power.fullPowerOn(FullPowerSource.A)
basic.forever(function () {
    basic.showIcon(IconNames.Heart)
    basic.showNumber(input.temperature())
    power.lowPowerRequest()
})
```

## Step 4: Try it out
Click ``|Download|`` to transfer your code. 

When the micro:bit has displayed the temperature it will enter low power mode until you press button ``A`` to wake it up again.