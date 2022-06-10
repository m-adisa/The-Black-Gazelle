## The Low-Level Programmer

**Bugs... a lot of bugs.**

*I do not write to teach you to avoid bugs. **They are inevitable.** What I hope for is that you get the right bugs.*

I do not think it gets more low-level than C programming, so all my references shall be to code written in C. If you write assembly code or something just as monstrous, then please read, for you might find my musings amusing and childlike.

# The imminent war...

It is the second sprint of the [Software Engineering program at ALX Africa](https://www.alxafrica.com/) and it has been all things Python for the past weeks. Easy.
![c thinking.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1654805100873/0MDYODt86.jpg align="center")

The emails come in around 6:15 each morning and they always describe the day's project and convey other necessary information. On this day, the subject of the email was **"0x17. C - Doubly Linked Lists"**.

I'll skip my reaction when I first saw it for now (you'll figure it out before the end of reading this, I promise). What you need to know is that I immediately realized that war was imminent. The first place I turned to was [Geeks for Geeks](https://www.geeksforgeeks.org/data-structures/).

*And here is your first tip as a low-level programmer:*
> Read first. Always read first, even if you know what to do.

# The flames of war...
To put all this into context, the first sprint of the program I am enrolled in was entirely about C programming. I kid you not, I have journeyed from simply `#include <stdio.h>` to stuff like this
```C
#ifndef _MAIN_H_
#define _MAIN_H_

#include <unistd.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/stat.h>
#include <errno.h>
#include <fcntl.h>
#include <signal.h>
#include <limits.h>

#define BUFSIZE 1024
#define TOK_BUFSIZE 128
#define TOK_DELIM " \t\r\n\a"

extern char **environ;

[some more declarations here]

#endif
```

*It is precisely because I have had this kind of experience that I did not smile when I got that email.*

I know that Google is indispensable, but perhaps one of the most important lessons I have learned is how to responsibly use Google. You might think that since reading has to be your first impulse then you're allowed to Google just about anything. *You can not. You must not.* **Your relevance and livelihood depend on it.**

...

A few hours later and the flames of war are raging; I am locked in battle to safeguard the *struct*, gain more ground by *malloc* to build more *nodes* and eventually defeat the *checker*.

Maybe I have become complacent after a few weeks of Python (no discredit intended), but this challenge crystalized some lessons in my mind. These lessons are the crux of this piece.

## The Foundations
```C
typedef struct builtin_s
{
	char *name;
	int (*f)(data_shell *datash);
    struct builtin_s *next;
    struct builtin_s *prev;
} builtin_t;
```
**Nothing beats a firm foundation**, and that is exactly what will make you use Google responsibly. You won't have to try; it will happen.

The code I have written is a doubly linked list. A doubly linked list is a type of linear data structure that is bi-directional. If you know what the built-in data types are, how to create yours with struct, rename it with typedef and what a pointer is, you should immediately understand what I wrote.

Alright, I agree that it might not immediately jump right at you, but you will recognize the elements and your brain will immediately try to make connections. There is a lot of code internet, badly written ones too. You can not soak it all up like a sponge, you need to be able to discern.

An important part of firmly grasping the basics is **mastering the syntax**. Yes, the syntax; the semi-colons and the asterisks. C does not have the luxury of a beautiful syntax (regardless of what the debate around might be), but you should relish in your dominion. The last bits of memory are firmly in your grasp. You get the most out of the PC architecture without having to resort to the use of assembly code. More importantly, you do not want to have to think about the difference between `h = h->next` and `f.n = 6` while you are trying to figure how to determine if your linked list is a palindrome or not.

Which brings me to the next point...

## The Logic 
I do not believe low-level languages were designed with readability in mind. Mastering the syntax helps in making sense of the elements, but you must master another skill to be adept at grasping the logic at a glance: *PATIENCE*. I get the irony there, but be patient - you'll see what I mean.

Code is read more times than it is written. Since the syntax you're dealing with is not straight forward, it becomes super easy to miss the logic ("algorithm" if you will) as you read. The correct approach is to make simple notes (or diagrams) as you read. Read that again:
> make simple notes (or diagrams) as you read.

This is not an advice to rookies, I mean it. What happens as you write/read longer code and gain more skill is that you will have less and less to write/draw, but you still need to do it. This idea shines most when you are working with indirect reference.

![pointers.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1654854060893/s-nhP6Ghi.jpg align="center")

## Debug
You are armed to the teeth and you have gathered intelligence. War is imminent and you are ready. There's is one last thing you need to know:
> **you will fail.**

Your failure will not be because you are incompetent but because of the first word that appeared in this article (scroll back up and re-read the first 3 lines).

It is a good thing to know that bugs are inevitable. That way, rather than waiting for them to happen, you can create them yourself. I know that there are many approaches to smartly writing code. Agile development and Test Driven Development are real important concepts you should understand. Regardless, you would be safe if you do the following:
* Develop your code incrementally. Each increment must have clear objectives and tests to confirm that the objectives are met.
* For each increment, know all possible syntactic and logical fail-points before you writing any code.
* Fix one bug at a time. Only one.

# Pyrrhic victory...
At the end of the day, the price shall be your comfort. You write code that makes everything else work. You implement the future. This means your imagination has to broad, yet you must be meticulous in your attention to details. A good resource to keep you grounded is the [C library](https://www.gnu.org/software/libc/manual).

C is practically unique in its ability to span two levels of programming; as well as providing high-level control of flow, data structures and procedures—all of the stuff expected in a modern high-level language—it also allows to systems programmer to address machine words, manipulate bits and get close to the underlying hardware if you want.

One implication of this is that the platform you develop for is important. C is the first choice for portability of software in the UNIX environment. Hence, solid understanding of Unix is prerequisite to do serious work (*windows.h* and other headers like it make C native on other platforms too). 

Cheers to victory...**at all costs.**

> If you are wondering why I titled this article *Making sense of modern civilization*, it is because of one indisputable fact: *Modern civilization depends on computers and 90% of the software that runs the world is either implemented in C or something closely related to C.*