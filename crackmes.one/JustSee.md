# JustSee

After downloading and unzipping the two files (first with password 'crackmes.one'), I decompiled the binary file with Ghidra:

```c

undefined8 main(void)

{
  int iVar1;
  long in_FS_OFFSET;
  char local_48 [32];
  undefined8 local_28;
  undefined8 local_20;
  undefined4 local_18;
  long local_10;
  
  local_10 = *(long *)(in_FS_OFFSET + 0x28);
  puts("Hello ! ");
  puts("Give Me Your Flag");
  printf("Check Flag: ");
  __isoc99_scanf(&DAT_004007fc,local_48);
  local_28 = 0x7334457b67616c46;
  local_20 = 0x7d6c6c3468635f79;
  local_18 = 0;
  iVar1 = strcmp(local_48,(char *)&local_28);
  if (iVar1 == 0) {
    puts("G00d ");
  }
  else {
    puts("Bad ");
  }
  if (local_10 != *(long *)(in_FS_OFFSET + 0x28)) {
                    /* WARNING: Subroutine does not return */
    __stack_chk_fail();
  }
  return 0;
}

```

From this it can be seen that the password starts at local_28 (and actually continues until local_18, which is a `\0` byte). By decoding this hex, we can get the password as `Flag{E4sy_ch4ll}`, which is accepted.
