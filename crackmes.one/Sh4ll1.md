# SH4ll1.md

First, I downloaded the file and used the password 'crackmes.one' to unzip the file.
I then opened it and decompiled it with Ghidra, showing that the main function called two functions:

<img src="https://user-images.githubusercontent.com/48258855/163706785-ca24fa05-9ddf-404d-a364-04e541d33488.png" width="500">

<img src="https://user-images.githubusercontent.com/48258855/163706818-27496257-f4ea-4987-bef9-e93510c00eaf.png" width="500">

The first just initialises some values for us, and the second is the main code. I refactored the code a little to make it more readable:

<img src="https://user-images.githubusercontent.com/48258855/163706847-47a31c76-dbef-4bbb-a147-a3db8a4aa7cf.png" width="300">

Using the initialised values and some basic maths, we can work out that the password should be `(7+5)*45 = 540`, which is correct.
