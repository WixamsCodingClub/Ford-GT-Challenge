# Lego Technic Ford GT Challenge

This project is a challenge for club members who want to try out their skills with the BBC micro:bit. Using the details below, the challenge is to get the Lego Technic Ford GT to work as a remote controlled car. 

![Image of the Lego Technic Ford GT](/assets/Lego-Technic-Ford-GT.png)

## Ford GT Car
The project is based on a genuine [Lego Technic Ford GT (42154)](https://www.lego.com/en-gb/product/2022-ford-gt-42154) which has been converted to include a motor to drive the rear wheels, and a servo to control the steering. The motor and servo are from GeekServo and are the same style as used in the [32-in-1 Wonder Building Kit from ElecFreaks](https://shop.elecfreaks.com/products/elecfreaks-micro-bit-32-in-1-wonder-building-kit-without-micro-bit-board). 

![Image of GeekServo motor](/assets/GeekServo-Motor.jpg)

The motor and servo are driven by the [Motor Driver for micro:bit from Waveshare](https://www.waveshare.com/wiki/Motor_Driver_for_micro:bit).

![Image of Waveshare Motor Driver](/assets/Waveshare-Motor-Driver.jpg)

## Controller
Two type of controllers are available in the coding club for this project, the [Kitronik :GAME Controller for micro:bit](https://kitronik.co.uk/products/5644-game-controller).

![Image of Kitronik :GAME controller](/assets/Kitronik-GAME-Controller.jpg)

or the [Kitronik :GAME ZIP 64 for the BBC micro:bit](https://kitronik.co.uk/products/5626-game-zip-64-for-the-bbc-microbit).

![Image of Kitronik :GAME ZIP 64 controller](/assets/Kitronik-GAME-ZIP-64.jpg)

## Requirements
To accomplish the challenge the following requirements should be completed:

1. Pressing the joypad Left button moves the steering left.
2. Pressing the joypad Right button moves the steering right.
3. Releasing both joypad buttons moves the steering to the centre.
4. Pressing the Fire 1 button moves the car forwards.
5. Pressing the Fire 2 button moves the car backwards at a slower rate.
6. Releasing both fire buttons stops the car.

Optional requirements:

1. When the car bumps into something the controller should vibrate momentarily (100 ms)
2. Add a horn to the car by making a beep noise (from the micro:bit itself) when pressing the down button on the controller joypad.
3. To better simulate a radio controlled car it should speed up progressively.
4. To better simulate a radio controlled car, when the car is travelling at full speed and the user releases the forwards/backwards button, the car should slow to a stop in a natural way.

> [!Note]
> If the :GAME ZIP 64 controller is used the LEDs can also be programmed to improve the user experience.

Tips:

* Consider what should happen if the user presses both joypad or both fire buttons together, what should happen?
* The car’s steering can become misaligned, meaning it doesn’t go straight. An offset is used to ensure it goes straight and a calibration mode can be used to tweak this offset if needed.
* A `current_speed` parameter can be used to keep track of the car’s speed, this can then be used to set the motor speed. It’s recommended that `current_speed` uses a negative integer to indicate reverse.

## Parameters

The following parameters are required to be followed to operate the car.

> [!CAUTION]
> Using the wrong parameters may damage the car.

### Set the Steering

The steering servo is a 180 degree servo, meaning the normal central point is at 90 degrees. Set the steering direction by setting the servo `S0` to the correct angle, there is a maximum of 27 degrees of movement in either direction.

> [!NOTE]
> There is an offset of -6 degrees for the centre point as installed in the car.

| Steering Direction  | Servo `S0` Angle     |
| ------------------- | -------------------- |
| Straight            | 90 - 6 degrees       |
| Steer left          | 90 - 6 - 27 degrees  |
| Steer right         | 90 - 6 + 27 degrees  |

### Drive Forwards or Backwards

The Motor Driver controls the motor by setting a speed of 1-16 forwards or backwards to motor `A`. There is a dedicated command to stop the motor. A maximum speed of 11 is recommended for reverse.

| Drive Direction  | Motor `A` Command  | Motor Speed |
| ---------------- | ------------------ | ----------- |
| Forwards         | `Forward`          | 1-16        |
| Reverse          | `Backward`         | 1-11        |
| Stop             | `Stop`             | N/A         |

## Resources

Makecode Extensions:
* **Motor Driver:** [https://github.com/waveshare/pxt-Motor](https://github.com/waveshare/pxt-Motor)
* **:GAME controller:** Search for Kitronik, select ‘kitronik-game-controller’
* **:GAME ZIP 64 controller:** Search for Kitronik, select ‘kitronik-zip-64’

Datasheets:
* [Motor Driver](https://www.waveshare.com/wiki/Motor_Driver_for_micro:bit)
* [:GAME controller datasheet (pdf)](/assets/5644-game-controller-microbit-datasheet.pdf)
* [:GAME ZIP 64 controller datasheet (pdf)](/assets/5626-game-zip-64-microbit-datasheet.pdf)
