# How to connect the arduino 101

## My tty serial cable:

    http://elinux.org/Beagleboard:BeagleBone_Black_Serial#Adafruit_4_Pin_Cable_.28PL2303.29

    Wire    Function
    Black   Ground
    Green   Receive
    White   Transmit

## connect to arduino 101 tutorial:

    https://www.zephyrproject.org/doc/1.7.0/boards/x86/arduino_101/doc/board.html#connecting-serial-output

## In my words:

    Black(cable) -- GND(arduino)
    White(cable) -- TX->1(arduino)
    Green(cable) -- RX<-0(arduino)

# How to configure the zephyr kernel

## set the board

    In sample hello world directory, change the Makefile:

        sed -i -e 's/qemu_x86/arduino_101/' Makefile

    run command: make menuconfig

        -> Debugging Options
           -> Send stdout to console

    select this feature, we can use printf to print some information to console(uart)

# How to flash the zephyr image to arduino 101

## tutorial

    https://www.zephyrproject.org/doc/boards/x86/arduino_101/doc/board.html#programming-and-debugging

## In my words:

    Redescribe the above tutorial is stupid, so after we finish the above, do:

        make flash

    It will issue:

        Flashing arduino_101
        Please reset your board to switch to DFU mode...

    You must press the master reset on arduino 101, only it can works.

# How to see the result on the terminal

    Open minicom, set it to ttyUSB0 115200 8N1
