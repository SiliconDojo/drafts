# Intro to Python


## Install Python and PIP

**For Ubuntu**
```
sudo apt intall python3
```

```
sudo apt install pip3
```

**For MacOS and Windows**

Make sure to check off to install PIP

```
https://www.python.org/downloads/
```

## Hello World - input()

```
message = 'hello'

name = input('What is your name? ')

print(f'{message} {name}')
```

## While True Loop

```
message = 'hello'

while True:
    name = input('What is your name? ')
    print(f'{message} {name}')
```

## Change Data Types

```
while True:
    num1 = float(input('Number 1: '))
    num2 = float(input('Number 2: '))
    total = num1 + num2
    print(total)

```

## If / Elif /Else Statements

```
import random

number = random.randint(0,10)

while True:
    guess = int(input('Guess a Number: '))

    if guess == number:
        print(f'{guess} was right!')
        break
    elif guess > number:
        print(f'{guess} is too high')
    elif guess < number:
        print(f'{guess} is too low')
    else:
        print(f'problem with {guess}')
```

## Try / Except

```
import random

number = random.randint(0,10)

while True:
    while True:
        try:
            guess = int(input('Guess a Number: '))
            break
        except:
            print(f'{guess} is not a number')

    if guess == number:
        print(f'{guess} was right!')
        break
    elif guess > number:
        print(f'{guess} is too high')
    elif guess < number:
        print(f'{guess} is too low')
    else:
        print(f'problem with {guess}')
```

## Functions

**Simple Function**
```
def my_function():
    print('hello world')

my_function()
```

**Send Value to Function**
```
def my_function(name):
    print(f'hello {name}')

while True:
    name = input('Your Name? ')
    my_function(name)
```

**Send Multiple Values to Function**
```
def my_function(name, age):
    age_minimum = 18
    print(f'hello {name}')
    if age >= age_minimum:
        print(f'{age} is old enough')
    else:
        print(f'{age} is too young')

while True:
    name = input('Your Name? ')
    age = int(input('Your Age? '))
    my_function(name, age)
```

## Write to File

```
import random
from time import sleep

while True:
    number = random.randint(0,100)

    with open('demo.html', 'w') as file:
        file.write(str(number))
    
    print(number)
    sleep(1)
```

```
import random
from time import sleep

while True:
    number = random.randint(0,100)
    color = ''

    if number >= 80:
        color = 'red'
    elif number < 80 and number >= 40:
        color = 'green'
    else:
        color = 'blue'

    with open('demo.html', 'w') as file:
        file.write(f'<h1 style="background-color:{color};">{number}</h1>')
    
    print(number)
    sleep(1)
```
