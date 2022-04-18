# easy_reverse

I downloaded and unzipped the file, and imported into Ghidra, and then refactored the code:

```c
void main(int argc,char *argv[])
{
  size_t argLength;
  
  if (argc == 2) {
    argLength = strlen(argv[1]);
    if (argLength == 10) {
      if (argv[1][4] == '@') {
        puts("Nice Job!!");
        printf("flag{%s}\n",argv[1]);
      }
      else {
        usage(*argv);
      }
    }
    else {
      usage(*argv);
    }
  }
  else {
    usage(*argv);
  }
  return 0;
}
```

By this point, the code is quite evident in meaning, and shows that any string that has an `@` in the 5th character and that is 10 characters long is valid.
