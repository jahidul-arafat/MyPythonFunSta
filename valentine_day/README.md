# Valentine's Day and Pohela Falgun Python Turtle App 
## By Jahidul Arafat

### A. Setup your environment
```bash
pip3 install turtle               # will install turtle module
sudo apt-get install python3-tk   # will install tkiner module inherited inside the turtle to display
```

### B. Get the Source Code
```python
# 🅹🅰🅷🅸🅳

import turtle
import math
from googletrans import Translator

# Step-1
# Global Variables
# Set then pen, screen, pen-size, screen-title and pen-speed
pen=turtle.Turtle()
screen=turtle.Screen()
screen.title(u"ভালোবাসা দিবস আর পহেলা ফাল্গুনের শুভেচ্ছা | জাহিদ ও রূপমা")
screen.bgcolor("black")
pen.pensize(2)
pen.pencolor("red")
pen.speed(10)

# Step-1.1: google translator
translator = Translator()

# Step-1.2: factor 
# Every returned x and y value will be multiplied with this factor
# for exact placement at 2D dimension.
screen_pos_factor=10


# Step-2.1: Math to draw the love curve
# lovecurve heart curve equation as mentioned in wolfram
# x=16sin^3 t
# y = 13cos(t) -5cos(2t) - 2cos(3t)- cos(4t)
# Get the details of this equation at: https://mathworld.wolfram.com/HeartCurve.html
def get_the_lovecurve_axis(t):
    x=16*(math.sin(t)**3)
    y=13*math.cos(t) - 5*math.cos(2*t)-2*math.cos(3*t)-math.cos(4*t)
    return x,y

# Step-2.2: Draw the full heart.
# Will take the value returned from the lovecurve math equation and
# Multiply it by the factor mentioned above
def full_heart():
    pen.penup()
    for i in range(0,200):
        x,y=get_the_lovecurve_axis(i)
        pen.goto(x*screen_pos_factor,y*screen_pos_factor)
        pen.pendown()

# Step-2.3: Define the method to write your greeting message and valentine's name
# Defining method to write text
# I am greeting in Bangla, that's why use the google translator to convert my english sentence into Bangla with dest set to "bn"
# However, if you are from a different region and language, set your <src> and <dest> according to your preferences
def valentine_name(greet,you,me):
    # google translation
    greet_bn = translator.translate(greet, src="bn",dest="bn")
    you_bn = translator.translate(you, src="bn",dest="bn")
    me_bn = translator.translate(me, dest="bn")

    # Move turtle to air
    pen.up()

    # Move turtle to a given position
    pen.setpos(-98, -30)

    # Move the turtle to the ground
    pen.down()

    # Set the text color to deep pink
    pen.color('deep pink')

    # Write the specified text in
    # specified font style and size
    pen.write(f"{greet_bn.text}\n    {you_bn.text} & {me_bn.text}     ", font=("", 15, "bold"))

# Step-3: The execution
#------------------------------Actual Execution at Here----------------------------------------
# Call the functions
# Draw a heart
full_heart()

# Write Greeting message and valentine name
valentine_name("Pohela Falgun er Shuvechaa","রূপমা","Arafat")

# Hide the turtle after the operation ends
pen.hideturtle()

# Dont let your screen auto exit.
# Let it remain opened
turtle.done()

```

