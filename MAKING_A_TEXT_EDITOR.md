# Personal Notes On How to make a text editor 

- Source : [Build Your Own Text Editor ](https://viewsourcecode.org/snaptoken/kilo/index.html)

[Chapter 2](https://viewsourcecode.org/snaptoken/kilo/02.enteringRawMode.html)

- Terminal attributes can be read into a termios struct by tcgetattr(). After 
modifying them, you can then apply them to the terminal using tcsetattr(). The 
TCSAFLUSH argument specifies when to apply the change: in this case, it waits 
for all pending output to be written to the terminal, and also discards any 
input that hasn’t been read.

- ECHO is a bitflag, defined as `00000000000000000000000000001000` in binary. 
 We use the bitwise-NOT operator (~) on this value to get 
 `11111111111111111111111111110111`. We then bitwise-AND this value with the 
 flags field, which forces the fourth bit in the flags field to become 0, and 
 causes every other bit to retain its current value. Flipping bits like this is 
 common in C.


Q. what is the reason to enable raw mode.

A. The input stream generally starts in canonical or cooked mode which is not
desired for a complex terminal application due to :
    1. In application like a text editor we want to input the text so that we 
    can respond to it immediately.
    2. Second reason is that it disables all the keys that ur terminal might be 
    using. Like ctrl-s puts the application to the background, Or ctrl-q quits 
    the application. Which is not desired again.

- iscntrl() tests whether a character is a control character. Control 
 characters are nonprintable characters that we don’t want to print to the 
 screen. ASCII codes 0–31 are all control characters, and 127 is also a 
 control character. ASCII codes 32–126 are all printable. 
 (Check out the [ASCII table](https://www.asciitable.com/) to see all of the characters.)

- IXON comes from <termios.h>. The I stands for “input flag” 
(which it is, unlike the other I flags we’ve seen so far) and XON comes from 
the names of the two control characters that Ctrl-S and Ctrl-Q produce: XOFF 
to pause transmission and XON to resume transmission.
For more see [Software control](https://en.wikipedia.org/wiki/Software_flow_control)

- As far as I can tell:

 - When BRKINT is turned on, a break condition will cause a SIGINT signal 
   to be sent to the program, like pressing Ctrl-C.

 - INPCK enables parity checking, which doesn’t seem to apply to modern 
  terminal emulators.  ISTRIP causes the 8th bit of each input byte to be 
  stripped, meaning it will set it to 0. This is probably already turned off.

 - CS8 is not a flag, it is a bit mask with multiple bits, which we set using 
  the bitwise-OR (|) operator unlike all the flags we are turning off. It sets 
  the character size (CS) to 8 bits per byte. On my system, it’s already set that way.

