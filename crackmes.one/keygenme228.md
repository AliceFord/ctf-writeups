# keygenme228

First, I download the file and open with Ghidra. In the Ghidra menu, I select the main function and then copy and paste it to a blank notepad++ file:

<img src="https://user-images.githubusercontent.com/48258855/163683672-40f6db58-766c-483c-aff7-5896573a079b.png" width="500">

After this, I clean up the code a little, adding sensible variable names:

<img src="https://user-images.githubusercontent.com/48258855/163683849-a8f79bc4-7896-45ce-9b85-1ffc9f99355f.png" width="500">

From the first block, we can see that two characters next to each other must be **either** equal to one another, or the first one must be larger. *Note: this only seems to affect characters excluding the last two*

From the second block, we can see that it now wants the characters in the other order: for each block of two, if the first subtract the second is smaller than 0 then valid is false, the opposite of before. Luckily for us though, this is only triggered if the first is invalid, which it isn't here.
