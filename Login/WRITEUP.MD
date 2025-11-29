# [CTF Name] - [Challenge Name] Writeup
ELF Crack Me 1 - Time to learn x86 ASM & gdb

## 0. What are we gonna learn?
Stack Strings 

## 1. Challenge Information (題目資訊)
* **Category**: Reverse Engineering 
* **Points**: 2
* **Author**: Lazysoup
* **Date**: 2025-11-29

## 2. Description (題目描述)
> "Find the flag"


## 3. Initial Reconnaissance (初步偵察)
在 Windows 直接下載后,unzip -> 丟去 kali 上 -> file 文件 -> 發現是 LSB-32bit 文件
根據題目敘述，應該是要看 ASM 了 -> r2 -A file -> s main ->pdc(print decompile c-code) -> 注意單引號的line

**爲什麽要搜尋單引號?**
因為那就是真正的內容（Data）。
因為在這段程式碼中，駭客（或題目設計者）沒有把 Flag 寫成一個完整的字串放在旁邊，而是像堆積木一樣，一次拿 4 個位元組（4 Bytes），把數字「搬」進記憶體裡。

Radare2 這個逆向工具會自動幫你查表，比如看到 0x47414c46。於是，它在後面幫你加上註釋（Comment），並用單引號包起來給你看 `mov dword [eax], 0x47414c46  ; // 'FLAG'`

 
**Result**
FLAG-4092849uio2jklsj4kl