# Learning about unicode and utf-8
---

### Preface
"It does not make sense to have a string without knowing what encoding it uses. 
You can no longer stick your head in the sand and pretend that “plain” text is ASCII.

**There Ain’t No Such Thing As Plain Text.**

If you have a string, in memory, in a file, or in an email message, you have to know 
what encoding it is in or you cannot interpret it or display it to users correctly." 
- Joel Spolsky

### A Little Bit Of History

So in semi-olden times the only characters that were used were unaccented
english letters, and they were called ascii characters. Ascii code from 32 to
127 were printable and readable letters as `<space>: 32` or `A : 65` and so on.
The codes below 32 were unprintable and were used for control characters.(I got
somewhat rough idea of this while fiddling and following how to make your own
text editor.) This was ASCII or as I like to refer it base ascii

**The Problem Arises** 
Since there was room for more characters i.e., from 128-255. Now people thought 
that they can use these spare spaces for their own use and thus they started 
adding their own versions of letter in these remaining spaces. For example IBM-PC 
had some european language characters and characters for drawing like horizontal 
bars, blocks and stuff like that. This was extended ASCII

This addition of characters varied from place to place as people in russia will
have different symbols after 128 and therefore will someother computer have
from different part of nation. Thus this was tackled by unicode

### Unicode

Understanding unicode is hard but here is my attempt to summarize it.

We know that earlier text/letter is mapped to 8-bits

`A -> 0100 0001`

In unicode a letter is mapped to something called code bits (which I need to
read more about that how it is represented on the memory). So we can assume
that every letter exists and that every capital letter is different from the
small letter. But figuring out what a letter is can cause problems for example
letter `eszett i.e ß` can be seen as a fancy way to write `B`.

letter in every alphabet is assigned a magic number by the Unicode consortium
which is written like this: U+0639. This magic number is called a code point.
The U+ means “Unicode” and the numbers are hexadecimal. U+0639 is the Arabic
letter Ain. The English letter A would be U+0041. Also there is no real limit
to number of unicode characters

So then why was utf-8 invented ? (Ehhhmmm Currently I am also trying to
understand that )

Anyway a brilliant concept of utf-8 was invented. This utf-8 was system of
storing unicode code points, in memory using 8-bits. In utf-8 every codepoint
from 0-127 is stored in a single byte. Only code points 128 and above are stored
using 2,3 or even 6 bytes. So now the unaccented english letters will be stored
as they were stored in ASCII and ANSI. And if you want to use accented letter
you'll have to store several bytes to store a single code point.


### Sources

-  "Joel on software" : [article on unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [utf-8-history.txt](https://www.cl.cam.ac.uk/~mgk25/ucs/utf-8-history.txt)
- [official site](utf8.com)
- [UTF-8 and Unicode FAQ by Markus Kuhn](https://www.cl.cam.ac.uk/~mgk25/unicode.html)
- [better-explained blog article](https://betterexplained.com/articles/unicode/)
- [Faqs : unicode.org/faqs](https://home.unicode.org/basic-info/faq/)
- [Basic Info : unicode.org](https://home.unicode.org/basic-info/overview/)
- [Microsoft Docs : unicode byte order marks](https://docs.microsoft.com/en-us/windows/win32/intl/using-byte-order-marks)
- [Microsoft Docs : Internationalization](https://docs.microsoft.com/en-us/windows/win32/intl/international-support)

---
