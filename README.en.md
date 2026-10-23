[Polski](README.md) · **English**

---

# Computer Science Matura, extended level - Python course, lesson 3. "Data input, random numbers, number systems and the math module"

> ### 🎬 Video walkthrough
> You can find a full step-by-step walkthrough of this lesson on my YouTube channel:
> **[Watch the video on YouTube](https://youtu.be/RoBpYAWXxas)**
>
> In the video I show how to read data from the keyboard, how to generate random numbers with the `random` module, how to convert values between number systems, how to perform bitwise operations and which functions the `math` module offers. I run all the code live in Python.

---

## Description

Code for the third lesson of a Python course that prepares students for the Polish Matura exam in computer science at the extended level.

The lesson starts with reading data typed on the keyboard and generating random numbers. In the Matura exam, data usually comes from a text file or from sample values given in the task, so both topics are covered briefly. They are still useful when you want to quickly type in or randomize something, or experiment with the language.

The second part of the lesson covers additions that are useful for Matura tasks: number systems, bitwise operations and the `math` module. This lesson is also the first place in the course where the `import` statement appears.

The repository also contains the code from the two previous lessons of the course. The next part of the course covers conditional statements and loops.

## Requirements

- Python 3.8 or newer, because the `f"{x1 = }"` syntax in f-strings and the `math.isqrt` function are available from this version
- No external dependencies, only the `random` and `math` modules from the standard library are used

## Running

```bash
git clone https://github.com/kmprograms/matura-kurs-python-3-pozyskiwanie-danych
cd matura-kurs-python-3-pozyskiwanie-danych
```

Program from this lesson:

```bash
python app-3-pozyskiwanie-danych-systemy-liczbowe-float.py
```

Programs from previous lessons:

```bash
python app-1-pierwszy-program-zmienne.py
python app-2-liczby-calkowite.py
```

In `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py` the part with the `input` statement is commented out. This way you do not have to type the data again on every run. To try it out, remove the `#` characters at the beginning of those lines.

## Project structure

| File | Description |
| --- | --- |
| `app-1-pierwszy-program-zmienne.py` | Code from a previous lesson: the first program, variables and their types, f-strings with value formatting, arithmetic operators, swapping variable values, the `end` and `sep` parameters of `print`, type conversion and the `+=`, `-=` and `*=` operators |
| `app-2-liczby-calkowite.py` | Code from a previous lesson: operations on integers, including `**`, `//` and `%`, parity and divisibility, relational operators, the `and` and `or` connectives, extracting the digits of a number and converting seconds to hours, minutes and seconds |
| `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py` | Code from this video: reading data with `input`, random numbers with the `random` module, number systems, bitwise operations and the `math` module |

## Topics covered

### Reading data from the keyboard

You read data from the user with the `input` statement. In the parentheses you pass a prompt that is displayed before the place where the data is typed.

```python
# imie = input("Podaj imię: ")
# print(imie)
#
# a = int(input("Podaj pierwszą liczbę: "))
# b = int(input("Podaj drugą liczbę: "))
# print(f'a + b = {a + b}')
#
# waga = float(input("Podaj wagę: "))
# print(waga + 10)
```

Everything you read with `input` is a string. You can check this with `type`. If the variables `a` and `b` were read without conversion, then after typing `10` and `20` the result of `a + b` would not be 30. The `+` operator applied to two strings performs concatenation, so we would see the two strings joined together, that is `1020`.

That is why we wrap the entire `input` call in `int`. First `input` returns a string, and then `int` turns it into an integer. Now for `10` and `20` the program prints `a + b = 30`. In the same way, `float` turns a string into a floating-point number. After entering a weight of `12.3` the program prints `22.3`.

If `int` receives something that is not a number, for example a name, the program ends with an error. Such an error can be caught and handled in several ways. For the purpose of Matura preparation, however, we assume that we always enter the data the program expects.

### Random numbers

Generating random numbers requires the `random` module, which has to be imported with `import random`. In Python, some modules are imported only when we need them.

```python
x1 = random.randint(1, 6)  # Wartość od 1 do 6
print(f"{x1 = }")

x2 = random.uniform(2, 19.3)
print(f"{x2 = } lub {round(x2, 2)}")

x3 = random.randrange(0, 100, 2)  # 0, 2, 4, ..., 98
print(f"{x3 = }")
```

| Function | What it does |
| --- | --- |
| `random.randint(1, 6)` | Draws an integer from the range 1 to 6, including both ends of the range |
| `random.uniform(2, 19.3)` | Draws a floating-point number from the range 2 to 19.3 |
| `random.randrange(0, 100, 2)` | Draws a value from the sequence 0, 2, 4, ..., 98 |

A random floating-point number can be rounded with the `round` function. The call `round(x2, 2)` rounds the value to two decimal places.

The `f"{x1 = }"` syntax prints the variable name together with its value, for example `x1 = 5`. This way you can see right away which variable the result refers to.

A computer does not really draw random numbers, it calculates them. Put simply, it does this based on a built-in numerical sequence. The variability of the resulting values is large enough that we can treat them as random. Strictly speaking, these are pseudorandom values.

### Number systems

```python
n = 2026
print(bin(n))
print(oct(n))
print(hex(n))

s1 = 0b10001011
s2 = 0o17
s3 = 0xff

print(int("1101", 2))
print(int("12", 3))
```

The `bin`, `oct` and `hex` functions return the representation of a number in the binary, octal and hexadecimal system. The results are strings.

Python also lets you write numbers directly in other systems. The `0b` prefix means binary, `0o` means octal and `0x` means hexadecimal. The variables `s1`, `s2` and `s3` hold the ordinary integers 139, 15 and 255.

Conversion from any system to decimal is done by `int`, to which you pass the base of the system in addition to the string. `int("1101", 2)` gives 13 and `int("12", 3)` gives 5. The results are ordinary integers, so you can perform arithmetic operations on them.

Converting values between systems by hand and performing operations in them is something we learn at a different stage of Matura preparation.

### Bitwise operations

```python
a = 0b1010
b = 0b1100

print(bin(a & b))
print(bin(a | b))
print(bin(a ^ b))
print(bin(12 << 1))
print(bin(12 >> 1))
```

| Operator | Operation |
| --- | --- |
| `&` | Bitwise AND |
| `\|` | Bitwise OR |
| `^` | Bitwise exclusive OR (XOR) |
| `<<` | Shifting bits to the left |
| `>>` | Shifting bits to the right |

The number on the right side of the `<<` or `>>` operator determines by how many positions the bits are shifted. The `bin` function shows the result in binary form and drops leading zeros, which is why the XOR result `0110` is displayed as `0b110`.

### The math module

The `math` module also has to be imported. It contains many mathematical functions and constants.

```python
print(math.sqrt(19))
print(math.isqrt(19))
print(19 ** 0.5)
print(math.pow(2, 10))
print(math.floor(19 ** 0.5))
print(math.ceil(19 ** 0.5))
```

| Expression | What it does |
| --- | --- |
| `math.sqrt(19)` | Square root |
| `math.isqrt(19)` | Integer part of the square root |
| `19 ** 0.5` | Power with exponent one half, which is also the square root |
| `math.pow(2, 10)` | Exponentiation, the result is a floating-point number |
| `math.floor(19 ** 0.5)` | Rounding down |
| `math.ceil(19 ** 0.5)` | Rounding up |

### Documentation

At the end of the file there are links to the documentation of both modules:

- [The `math` module](https://docs.python.org/3/library/math.html)
- [The `random` module](https://docs.python.org/3/library/random.html)

In the documentation you will find an overview of all functions and constants of a module. When you click on a function, you will see its description and, where possible, a code example that is equivalent to how it works or shows how to use it. The documentation of the `random` module ends with a set of examples. It is worth browsing so that you know where to look for other functions and their descriptions.

## Matura context

In the Matura exam in computer science, data for programming tasks usually comes from a text file. Sometimes you also have to check how an implemented function works for sample values given in the task. Reading data from the keyboard and generating random numbers are useful mainly while learning, experimenting and solving practice tasks.

In the Matura exam, conversions between number systems very often have to be done by hand. The `bin`, `oct` and `hex` functions and `int` with a given base are useful when you are allowed to use the features of Python.

If bitwise operations appear in the Matura exam, it is more likely that you will have to write your own algorithm than that ready-made operators will be enough. However, in programming tasks on text files where there is no clause restricting the allowed language elements, knowing these operators can speed up the solution.

## Results

The first three lines printed by `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py` depend on random draws and change on every run. In the video `random.randint(1, 6)` returned 5 and `random.randrange(0, 100, 2)` returned 6. For `x2` the program prints the drawn value and its rounding to two decimal places.

The part covering number systems and bitwise operations always prints the same output:

```
0b11111101010
0o3752
0x7ea
13
5
0b1000
0b1110
0b110
0b11000
0b110
```

The last six lines are the results of the functions from the `math` module:

| Expression | Result |
| --- | --- |
| `math.sqrt(19)` | 4.3588... |
| `math.isqrt(19)` | 4 |
| `19 ** 0.5` | 4.3588... |
| `math.pow(2, 10)` | 1024.0 |
| `math.floor(19 ** 0.5)` | 4 |
| `math.ceil(19 ** 0.5)` | 5 |

For the square root, Python prints the full floating-point value. In the table it is shortened to four decimal places.

## Implementation notes

The `import random` and `import math` statements are at the beginning of `app-3-pozyskiwanie-danych-systemy-liczbowe-float.py`. This is the first file in the course that imports modules.

The part with `input` is commented out so that the program can be run without typing data on every start.

The results of `bin`, `oct` and `hex` are strings, while the results of `int` with a given base are integers. Strings are covered in more detail later in the course.

`math.isqrt` returns an integer, while `math.pow` returns a floating-point number, hence the result `1024.0`.

The variables `s1`, `s2` and `s3` are not printed. They only show how to write numbers in binary, octal and hexadecimal directly in the code.