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

## If / Else Statements

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
