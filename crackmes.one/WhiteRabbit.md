# WhiteRabbit

I downloaded and decompiled with Ghidra, but the main function only contained this:

```c

undefined8 main(void)
{
  puts("The only way out is inward\n\n\n\n\n");
  printf("...");
  puts("Voce consegue achar a funcao escondida?");
  return 0;
}

```

So I had a quick look through the symbols in the code, and found one labelled `secret`, which contained this code:

```c
void secret(void)

{
  printf("flag{%d%c%c%dn%c%d%c%d_%dh_M%d%ds_G%d%ct%dS%d}\n",3,0x73,99,0,100,1,100,0,3,4,1,0,0x73, 0,0
        );
  return;
}
```

Which, after execution, yielded the flag as `flag{3sc0nd1d0_3h_M41s_G0st0S0}`.
