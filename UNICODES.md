# Personal Notes Of All the good blogs that I read

---

# Aboslute minimum all the programmers should know about unicode

Source : "Joel on software"  
Link : https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/  
Date of article/blog/paper : 2003/10/08

Understanding unicode is hard but here is my attempt to summarize it.  
We know that earlier text/letter is mapped to 8-bits

A -> 0100 0001

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

---
