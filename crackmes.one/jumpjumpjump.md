# jumpjumpjump

First I downloaded and decompiled with Ghira, and then refactored the code:

```c
int main(void)
{
  size_t inpLen;
  ulong counter;
  char inp [112];
  long local_28;
  int i;
  int total;
  
  total = 0;
  puts("enter the magic string");
  fgets(inp,100,stdin);
  inpLen = strlen(inp);
  if (inpLen < 12) {
    i = 0;
    while( true ) {
      counter = (ulong)i;
      inpLen = strlen(inp);
      if (inpLen <= counter) break;
      total += inp[i];
      i++;
    }
    if (total == 1000) {
      local_28 = strcat_str();
      printf("flag is flag{");
      for (i = 0; i < 10; i++) {
        putchar((int)*(char *)(local_28 + i));
      }
      puts("}");
    }
    else {
      puts("wrong string\nNo flag for you.");
    }
  }
  else {
    puts("too long...sorry no flag for you!!!");
  }
  return 0;
}
```

With this, we can see a rather over-complicated loop, which just sums the ascii values of each character in our input string. As we see that the target value is 1000 and the max length is 11, I submitted 10 `d`'s, with an ascii value of 100, but this didn't work! I then tried it with `python3 -c "print('d'*10+'\x00')" | ./rev03`, which did fortunately work, as the issue must have been the string not being properly terminated. This outputs the flag as `flag{!#&*/5<DMW}`.
