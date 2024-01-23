# Signals - Week 1

For all of our activities and code running, we'll be using the [ARM mbed Simulator](http://195.130.59.221/).
Take some time to read over our [Coding Style Guide](https://github.com/Triton-Robotics/TR-mbed/wiki/Very-Short-Coding-Style-Guide)

## Basic Signals

A Signal can be defined as a time-varying quantity that relays some sort of
information.

In robotics and electrical engineering, the “quantity” we are referring to here is most often voltage. (And if not that, then current).

* For the duration of this training program, a signal can be effectively thought of as a voltage that is changing over time.

Signals are passed between devices to send and receive information. We will mostly be working with primitive data types, *integers, strings, etc.*

## Digital Signals

Digital signals must have a finite set of possible values, but in our case we will be primarily working with binary digital signals, either high or low. In software the high is a 1, or true, and the low is a 0, or false.

![](assets/week1_1.png)

This signal is 1100111101101001100100000111111101110010010000011001111100000001111110001.

It is very much so garbage random data, but we will be working with data that hopefully isn't.

## Analog Signals

- Analog signals are signals that are meant to be interpreted in terms of a range.
  
  ![](assets/week1_2.png)
  
  For example, at time 4.34s, we can see that this voltage is 1.935V. The board can read this to a certain level of accuracy.

# 

# Exercise 1: Using Digital Signals

The mbed library allows us to very easily manipulate digital inputs and outputs. You can experiment with this using the [ARM mbed Simulator](http://195.130.59.221/). 

Creating a digital Input can be done using the `DigitalIn` Class. It is constructed as such: 

```cpp
DigitalIn input(PinName);
```

You can get its value the same way you would a variable, or you can use .read()

```cpp
int x = input; 
int x = input.read(); //alternate usage, both work
```

Where `x` will be 1 if the input is high (Button pressed) and 0 if the input is low (Button unpressed).

You can also create a digital output, like an led, simply, with the `DigitalOut` Class

```cpp
DigitalOut output(PinName);
```

like the `DigitalIn`, the `DigitalOut` allows you to get the current value of the out by using it as a variable:

```cpp
int x = output;
int x = input.read(); //again both of these commands will do the same thing
```

However now you can also set the value like a variable

```cpp
output = 1; // setting the output high
```

## Assignment

WIth this information, write a simple program in the simulator that controls the LED with the button. The led pin is `LED1` and the button pin is `BUTTON1`. You can play around with this by pressing the button in the simulator. Once your code is functional, copy it back into the file on github, and then push.

# Exercise 2: Analog Input

Now let's mess around with getting our board to input analog signals. This is basically reading the voltage on a pin relative to ground. The `AnalogIn` has us covered here. `AnalogIn` functions similarly to `DigitalIn` (`AnalogOut` mirrors `DigitalOut` as well).

```cpp
AnalogIn anInput(PinName);

double x = anInput;
double x = anInput.read(); //you can use either of these
```

The nucleo board works on 3.3v logic, that is, when reading and analog input it will map (0, 3.3) volts to a (0, 1) `float`.

You can add a [potentiometer](https://randomnerdtutorials.com/electronics-basics-how-a-potentiometer-works/) using the simulator, by clicking `Add Component`, then selecting Potentiometer.

![](assets/week1_3.png)

## Assignment

Using a potentiometer, have an led flicker with a period of 2s, and be on for that percentage of time (Ex: at 0.3 it will be on 30% of the time, which is 0.6 seconds, and off 70% of the time, 1.4 seconds). `wait_ms(milliseconds)` might come in handy here. Again, once you're done, put this on gituhub and push.
