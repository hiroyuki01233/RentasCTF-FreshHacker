# About
**Category**: Cryptography

**Question**: round and round

**Flag**: RWSC{PIZZINI_CIPHER_IS_EAZY}

**Description**
In this question we were given a text file with the content `2126226{19122929121712_6121911821_26422_842928}`

# How to Solve?
As soon as I received the cipher text, my instinct tells me that it should start with "RWSC" since it's the flag format. A pattern emerged when I solved the first 4 letters, every number represents the alphabet position + 3 (e.g. R = 18 + 3, W = 23 + 3 etc.), therefore I use this method to deduce every letter. To make this process easy you can use online tools to  this ciper named `cachesleuth` (https://www.cachesleuth.com/pizzini.html)

![enter image description here](https://media.discordapp.net/attachments/1009070339684307005/1214964454370975804/image.png?ex=65fb06d2&is=65e891d2&hm=45dfb8896a9d235c6dcf8e8fe42e0af8c64b50a4fa6f851593e23f9fc71797af&=&format=webp&quality=lossless&width=1125&height=601)





