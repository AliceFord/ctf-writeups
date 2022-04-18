# PieIsMyFav

I downloaded and decompiled with Ghidra, producing this code:

```c
undefined8 main(void)

{
  int local_18;
  int local_14;
  int local_10;
  int local_c;
  
  local_c = 100;
  local_10 = 14;
  local_18 = 0;
  local_14 = 0;
  puts("Welcome to the wonderful world of assembly!");
  printf("Qual o numero magico? ");
  __isoc99_scanf(&DAT_0010204b,&local_18);
  local_14 = (local_10 + local_c * 3) / local_c;
  if (local_14 == local_18) {
    puts("Essa eh a sua flag!");
  }
  else {
    puts("Try harder...");
  }
  return 0;
}
```

With this, we can do a little maths: `(14 + 100 * 3) / 3 = 3`, giving us out flag. *Note: this is due to integer division, as neither side of the division is a float.*
