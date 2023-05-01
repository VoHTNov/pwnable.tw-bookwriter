# pwnable.tw-bookwriter
  1. Overwrite "Top Chunk" to Free() "Top Chunk".
  2. Leak Heap with funtion "Author" and Leak Libc Base with funtion "Add" and "View" after Free() "Top Chunk".
  3. Use "Attack Unsorted Bin" to overwrite _IO_list_all pointer to <main_arena+88>. Because, in _IO_FILE, variable "_chain" in offset 104 from start address of _IO_FILE. So, program continue go to strem _IO_FILE in <main_arena+88+104> that is address of smallbin[4] (bin use to save chunk size 0x60 after free).
  4. We can control data in smallbin[4] via overwrite variable "bk" of Chunk in Unsorted Bin and overwite size That Chunk is 0x61.
  5. Use function "add" to add anything will trigger the error and get shell.
  6. In short, it is "House of Orange" (use in <= libc-2.23).
