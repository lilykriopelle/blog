---
layout: post
title:  "Ruby [OPERATOR]="
date:   2015-12-02 10:47:53 -0500
categories: ruby
---

I was recently preparing a lecture on the `||=` idiom in Ruby, when I realized: I wasn't totally certain which other operators could be combined with assignment in this shorthand.  No amount of googling led me to the information I wanted - probably because this is kind of a tough thing to search for - what exactly are you supposed to type?

After a few fruitless google searches, I decided to go straight to the source, and spent a little quality time with Ruby's [grammar][grammar] to find the answer to my question.  Line 883 of the linked code (a `.y` file that gets fed to YACC, resulting in `parse.c`) reads `%token <id> tOP_ASGN	/* +=, -=  etc. */`.  To find where these operate/assign rules are defined, I did a simple search through the rest of the file for `tOP_ASGN`.  Reading backwards from each return statement, it was easy enough to reconstruct the token sequences that ruby parses as `[op]=`.

I wasn't necessarily surprised by what I found (a useful assortment of numerical, boolean, and bitwise operations, many of which I had already been using), but I am happy to have an answer.  Without further ado, here's a list of `[op]=` statements in Ruby.  If you find one I've missed, please let me know, and I'll happily include it!

tl; dr - `[+=, -=, /=, *=, **=, %=, &&=, ||=, <<=, >>=, &=, |=, ^=]`

{% highlight ruby %}

# += PLUS equals
x = 2
x += 1
x         # => 3

# -= MINUS equals
x = 2
x -= 1
x         # => 1

# /= DIVIDE equals
x = 8
x /= 2
x         # => 4

# *= TIMES equals
x = 4
x *= 2
x         # => 8

# **= POWER equals
x = 2
x **= 3
x         # => 8

# %= MOD EQUALS
x = 5
x %= 4
x         # => 1

# &&= AND equals
x = true
x &&= 3
x         # => 3

x = false
x &&= 3
x         # => false

# ||= OR equals
x = false
x ||= 3
x         # => 3

x = true
x ||= 3
x         # => true

# <<= BIT SHIFT LEFT equals
x = 1
x <<= 1
x         # => 2

# >>= BIT SHIFT RIGHT equals
x = 2
x >>= 1
x         # => 1

# &= BITWISE AND equals
x = 3
x &= 2
x         # =>2

# |= BITWISE OR equals
x = 6
x |= 5
x         # => 7

^= XOR equals
x = 7
x ^= 5
x         # => 2


{% endhighlight %}

[grammar]: https://github.com/ruby/ruby/blob/trunk/parse.y
