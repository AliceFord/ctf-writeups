# Sh4ll2

First, I downlodade the file and unziped it with password 'crackmes.one'. Then, I decompiled with Ghidra, showing the main function:

```c
undefined8 main(void)

{
  int local_1c;
  int local_18;
  float local_14;
  float local_10;
  float local_c;
  
  local_14 = 3.564;
  __isoc99_scanf(&DAT_00100894,&local_1c);
  local_18 = (int)((float)local_1c + local_14);
  for (local_10 = 0.0; local_10 < (float)local_18; local_10 = local_10 + 0.8) {
    local_c = (float)local_18 + local_10 + local_c;
  }
  printf("%f");
  if (local_c == 4550.8) {
    printf("Good pasword");
  }
  else {
    printf("Bad password");
  }
  return 0;
}


```

I then refactored this for readability:

```c
int main()
{
  int inp;
  int encodedInp;
  float KEY_VAL;
  float i;
  float enc;
  
  KEY_VAL = 3.564;
  scanf("%d",&inp);
  encodedInp = (int)((float)inp + KEY_VAL);
  for (i = 0.0; i < (float)encodedInp; i += 0.8) {
    enc += (float)encodedInp + i;
  }
  printf("%f");
  if (enc == 4550.8) {
    printf("Good pasword");
  }
  else {
    printf("Bad password");
  }
  return 0;
}


```

Now, I can see the algorithm used. I realised that it would probably take me a while to decode manually, so I wrote a quick python script to brute force it, as I guessed that the answer would be a low number, and the `int` cast at the start shows that the input has to be an integer.

```python
import numpy as np

KEY_VAL = 3.564
for inp in range(1, 101):
    enc = 0
    encodedInp = int(float(inp) + KEY_VAL)
    for i in np.arange(0, float(encodedInp), 0.8):
        enc += float(encodedInp) + i

    print(enc, enc == 4550.8, inp)

```

And this exposes the solution as 46, which works in the original binary.
