# esoteric-hello-world-v2
This is esoteric "hello world" program (Version 2) made in Python3.
The first version of this program is [Esoteric python hello world](https://github.com/VelikiFeniks0/esoteric-python-hello-world) and version 2 works on the same principle.

It imports `os` module, uses write method, and this time instead of having a list of ASCII characters, it is a list of ordinal numbers of ASCII characters, for example "h" in ASCII table is 104.

In this code we do not have lots of booleans, instead we have lambda arguments.
Like this:
```py
(lambda arg1, arg2:
  ...
)(True, False)
```
It looks cleaner than spamming lots of booleans.

Remember that list of ASCII ordinal numbers I mentioned earlier?
It's just a list that has ordinal numbers for each character in string "hello world".
```py
l = [104, 101, 108, 108, 111, 32, 119, 111, 114, 108, 100] # hello world
```
We have to obfuscate it more so we just use booleans to act as numbers. True is equal to 1 and False is equal to 0, but how do we get larger numbers such as 104?
We can use bitwise operators and bit shifting. 
Bit shifting in Python works in a way where you write a number, write a bitwise operator for bit shifting and another number.
There are two bitwise operators for bit shifting in Python, which are left shift [`<<`] and right shift [`>>`].

## How bit shifting works?
Let's say, you have a number 2, which in binary is 10.
If you left shift it by one, you'll get 4 in binary.

`2 << 1 -> 4`

Because in binary, you move 10 (number 2) by one bit, and it becomes 100 (4 in binary). You move that 10 to left.
Same thing for right shift.

`7 >> 1 -> 3`

7 in binary is 111 and 3 in binary is 11, and you move 111 by one bit to the right.

That's how you can get larger or smaller numbers with bit shifting.

## The code
Here's the obfuscated version of a list of ASCII ordinal numbers.
```py
_=bool(-~([]>[]));__=False;___=[((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)),
    ((((_<<_)**(_<<_<<_))*(_<<_<<_<<_))-(_<<_<<_<<_<<_<<_)+(_<<_<<_<<_)-(_<<_<<_)+(_^__%_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)),
    (_<<_<<_<<_<<(_&(_+(_<<_))&_)<<(_^__//_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)+(_<<_<<_<<_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)+(_<<_<<_)-_),
    ((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)),
    (((((_<<(_^__))**(_<<(_&_//(_^__//_))<<_))*(_<<_<<_<<_))-(_<<(_//_^__)<<_<<(_//_^__//_)<<_<<_)+(_<<(_//_^__)<<_<<_)+(_<<_<<_)+(_<<_)+(__^_&_)+(_<<_<<_)+_)-(_<<_<<_<<_<<_))]
```
I know it looks messy and complicated, but trust me, it's not that complicated. First what we have is two weird variables called `_` and `__` and a list of ASCII ordinal numbers, it's all in one line. Those first two variables are basically just one True and one False value, The first variable has some weird, but small code in it, it's literally just some random stuff that returns `True` as an output, so we have bool type and inside we see `-~([]>[])`. `[]>[]` returns `False` as an output because first list is not larger than the second one, they are equally empty, `-~` is there because when you use `~` bitwise operator that stands for NOT bitwise operator, since []>[] is False, bitwise NOT should make it the opposite from False and become True, but there's a sequence, it does not result in `True`, instead it displays `-1` and then we add `-` in front of bitwise NOT (~) to make it a 1. But 1 is not a boolean type (`True`), in that situation we just use `bool()` to make it a bool type and not an integer.

That list looks complicated, but every element is just a number that we got by bit shifting numbers, there are many other bitwise operator, but they are there just to make it more obfuscated and confusing. The first two variables are mentioned here in the elements of the list many times, but those are just booleans, True and False. Those bitwise operators like `^` and `&` are just to make it more confusing, `^` is XOR, and `&` is AND. XOR means if only one of the inputs is true, then the output is also true, AND means if both inputs are true, then the output is also true, otherwise it's not true on the output.

Now we want to print all those characters, we can simply use `print` function, but that's not esoteric nor obfuscated. We have to obfuscate it more. `os˙ module is a great way to output some text on terminal, it's the lowest-level way to output text in Python.

To do that, we have to write this simple chunk of code:
```py
import os
os.write(1, b"hello world")
```
As you can see, `os.write` requires two arguments, a file decriptor, and bytes-like object, which in this case is a "hello world" string, but encoded.
File decriptor has to be 1 in this code, but in general it represents the target file where the bytes will be written, and yes, the string has to be bytes-like object.

We could obfuscate it a little more and use `getattr` function and maybe some anonymous functions (lambdas).

getattr example:
```py
getattr(
  __import__("os"), "write"
)(1, b"hello world")
```
You know that `print` by default ends with `\n` (newline)?, well `os.write` doesn't. And that's good because we can just output multiple characters on the same line.
We could use a for loop, there are many other ways to do that, but we will use a for loop this time.

```py
for char in character_list:
  os.write(1, chr(char).encode())
```
Instead of `chr` we could go lower level and use `bytes` object to turn a number into ASCII character. And we can do it by writing
```py
for char in character_list:
  os.write(1, bytes([char])
```
It must be inside square brackets like this `bytes([char])`.

And now let's obfuscate it much more, there are a few rules, no strings, no numbers. Booleans are allowed.
We have our list, we have our module we are going to use, we know basic bit shifting and bitwise operators, we have our output part of code, now just replace all the numbers and strings with something else.

for example, when you import `os` here:
```py
getattr(
  __import__("os"), "write"
)(1, b"hello world")
```
we can use class names of Python objects, you can get the letter "o" from word "bool" that you get by doing `True.__class__.__name__`, it doesn't have to be `True`, it can be `False` too, it doesn't matter as long as it is boolean. And the letter "s" you can get from "list", you get it by doing `[].__class__.__name__`, simple, right? Now you've got "o" and "s" and just combine them to import `os`. The word "write" you can get from `__builtins__` and similar ways, I got "wr" from the word "wrapper" and "ite" from the word "iter". You can tinker yourself and find your own ways to get those words and letters-
And of course, obfuscate it as much as you want. Just tinker and make everything confusing.
This is what I ended up with:
```py
for ____ in ___:
    (lambda _, __: (lambda ___:
                    getattr(
                        __import__([_.__class__.__name__[_]+[].__class__.__name__[_<<_]][_>>_]), 
                        str(((_|_).__class__.__eq__.__class__.__name__[:(__builtins__.len((_^__).__class__.__name__)//(-~~-_-~~-_))]))+
                        bytes([(((_ << _ << _) ** _ << _ <<_<<_<<_<<_) - (_<< _<<_<<_<<_) + (_<<_))]).decode()+
                        (str({}.__iter__)[(((_ << _) << (_ << _) << (_ << _))  - (_ << _ << _ << _ << _) + ((_ << _)+_)):
                                        (((_ << _) << (_ << _) << (_ << _)) -(_ << _ << _ << _ << _) + ((_ << _ << _)+(_<<_)))])
    )(___,bytes([____])))(__builtins__.len(type([]).__repr__([(_^__&_%_%_%_//__-+~__**~__)])[__//__&_<<_])))(_:=bool(-~([]<[])),~_)
```
Just remember all the basics I have talked about here, and keep obfuscating, also that big and confusing chunk of code is just importing `os` and writing "hello world".




Thank you for reading, and have fun with making weird programs!
Have a great time!


Oh also, feel free to do whatever you want with this code, it's public domain!
