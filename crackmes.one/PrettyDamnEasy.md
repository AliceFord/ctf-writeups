# PrettyDamnEasy

Download, decompile with Ghidra, and it should produce this code:

```c

undefined8 main(void)

{
  int iVar1;
  undefined8 local_1c;
  undefined2 local_14;
  char local_12 [10];
  
  local_1c = 0x6361726379736165;
  local_14 = 0x6b;
  printf("\nInput the password: ");
  __isoc99_scanf(&DAT_0010201a,local_12);
  iVar1 = strcmp(local_12,(char *)&local_1c);
  if (iVar1 == 0) {
    printf("Correct password");
  }
  else {
    printf("Wrong password, try another");
  }
  putchar(10);
  return 0;
}


```

From this we can see that the password is just local_1c + local_14 (they are on the stack), giving us a value of `easycrack`, after dealing with endianness and stack push order.
