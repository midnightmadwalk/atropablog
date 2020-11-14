---
title: Instereing answer with gcc and clang compiler
comments: true
keywords: debug, reversed
tags: [ gcc, clang, compiler, C ]
description: make fun for study
---

# Instereing answer with gcc and clang compiler

> One day, My companion Tsai ask me a question,“do you know (++i)(++i)(++i) equal answer？”, Then i wrote a program for run. 

```C
    #include "stdio.h" 
    int main() {
    	int d=3;
    	printf("%d",(++i)+(++i)+(++i));
    	return 0;;
    }
```

**I GOT TWO VALUE FOR ANSWER!!**

GCC-7.4.0 COMPILER:

> $: gcc 运算符和表达式.c && ./a.out

> $:16


CLANG-8.1.0 COMPILER:
> $: clang 运算符和表达式.c && ./a.out

> $:15


so, I reversed code for analysis.

#reversed assembly(AT&T format) 

`$: objdump -d a.out > gcc.dmp`

```
000000000000064a <main>:
 64a:	55                   	push   %rbp      		  /赋值？/
 64b:	48 89 e5             	mov    %rsp,%rbp  		  /rsp，rbp为堆栈地址？/
 64e:	48 83 ec 10          	sub    $0x10,%rsp  		  /值为16/
 652:	c7 45 fc 03 00 00 00 	movl   $0x3,-0x4(%rbp)    /把i=3长字节放在rbp堆栈/
 659:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)    /i=i+1放入rbp堆栈/
 65d:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)    /i=i+1放入rbp堆栈，此时i=5/
 661:	8b 45 fc             	mov    -0x4(%rbp),%eax    /把rbp短字节(i=5)堆栈值，移动到寄存器ax/
 64a:	55                   	push   %rbp               /赋值？/
 64b:	48 89 e5             	mov    %rsp,%rbp          /rsp，rbp为堆栈地址？/
 64e:	48 83 ec 10          	sub    $0x10,%rsp         /值为16/
 652:	c7 45 fc 03 00 00 00 	movl   $0x3,-0x4(%rbp)    /把i=3长字节放在rbp堆栈/
 659:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)    /i=i+1放入rbp堆栈/
 65d:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)    /i=i+1放入rbp堆栈，此时i=5/
 661:	8b 45 fc             	mov    -0x4(%rbp),%eax    /把rbp短字节(i=5)堆栈值，移动到寄存器ax/
 664:	8d 14 00             	lea    (%rax,%rax,1),%edx /寄存器ax与寄存器ax相加放到寄存器dx/ /dx=10/
 667:	83 45 fc 01          	addl   $0x1,-0x4(%rbp)    /i=i+1=6放入rbp堆栈/
 66b:	8b 45 fc             	mov    -0x4(%rbp),%eax    /把结果i=6移动到寄存器ax/
 66e:	01 d0                	add    %edx,%eax          /把寄存器dx与寄存器ax相加，也就是10+6/
 670:	89 c6                	mov    %eax,%esi          /把16移动到寄存器si/
 672:	48 8d 3d 9b 00 00 00 	lea    0x9b(%rip),%rdi        # 714 <_IO_stdin_used+0x4>   /我也没看懂/   
 679:	b8 00 00 00 00       	mov    $0x0,%eax          /寄存器ax赋值/
 67e:	e8 9d fe ff ff       	callq  520 <printf@plt>   /调用函数printf/
 683:	b8 00 00 00 00       	mov    $0x0,%eax          /寄存器ax赋值/
 688:	c9                   	leaveq 
 689:	c3                   	retq 
 68a:	66 0f 1f 44 00 00    	nopw   0x0(%rax,%rax,1)  
```
> the self-added operator seem not higher priority,it always self-add, and than register and register add.

------------
**Let's see clang compiler**

`$: objdump -d a.out > clang.dmp`

```
0000000000400500 <main>:
  400500:	55                   	push   %rbp         	  /赋值?/
  400500:	55                   	push   %rbp               /赋值?/
  400501:	48 89 e5             	mov    %rsp,%rbp    
  400504:	48 83 ec 10          	sub    $0x10,%rsp
  400508:	48 bf e4 05 40 00 00 	movabs $0x4005e4,%rdi     
  40050f:	00 00 00 
  400512:	c7 45 fc 00 00 00 00 	movl   $0x0,-0x4(%rbp)     
  400519:	c7 45 f8 03 00 00 00 	movl   $0x3,-0x8(%rbp)
  400520:	8b 45 f8             	mov    -0x8(%rbp),%eax 
  400523:	83 c0 01             	add    $0x1,%eax          /寄存器ax +1，此时寄存器ax的i=4/
  400526:	89 45 f8             	mov    %eax,-0x8(%rbp)    /把i=i+1结果给rbp堆栈/
  400529:	8b 4d f8             	mov    -0x8(%rbp),%ecx    /把rbp堆栈赋值给寄存器cx，rbp堆栈的值为4/
  40052c:	83 c1 01             	add    $0x1,%ecx          /寄存器cx +1，此时寄存器cx的i=5/
  40052f:	89 4d f8             	mov    %ecx,-0x8(%rbp)    /寄存器cx值给rbp堆栈，rbp堆栈的值为5/
  400532:	01 c8                	add    %ecx,%eax          /寄存器ax与寄存器cx相加，4+5=9，寄存器ax为9/
  400534:	8b 4d f8             	mov    -0x8(%rbp),%ecx    /把rbp堆栈的值给寄存器cx，此时寄存器cx的值i=5/
  400537:	83 c1 01             	add    $0x1,%ecx          /寄存器cx +1，此时i=6/
  40053a:	89 4d f8             	mov    %ecx,-0x8(%rbp)    /寄存器cx值给rbp堆栈，rbp堆栈的值为6/
  40053d:	01 c8                	add    %ecx,%eax          /寄存器cx与寄存器ax相加，6+9=15/
  40053f:	89 c6                	mov    %eax,%esi          /寄存器ax值赋值到寄存器si/
  400541:	b0 00                	mov    $0x0,%al           /移动到寄存器al/
  400543:	e8 b8 fe ff ff       	callq  400400 <printf@plt>/调用fun函数printf/
  400548:	31 c9                	xor    %ecx,%ecx          /异或运算，cx与cx的值相同，结果为0/
  40054a:	89 45 f4             	mov    %eax,-0xc(%rbp)    /寄存器ax/
  40054d:	89 c8                	mov    %ecx,%eax          /寄存器cx的值给寄存器ax，结果是15/
  40054f:	48 83 c4 10          	add    $0x10,%rsp         /rsp堆栈为什么要填入10？/
  400553:	5d                   	pop    %rbp
  400554:	c3                   	retq   
  400555:	66 2e 0f 1f 84 00 00 	nopw   %cs:0x0(%rax,%rax,1)
  40055c:	00 00 00 
  40055f:	90                   	nop
```

> The answer seems also correct, But I confuse what different from gcc and clang compiler...
---------

#Conclusion

Seem gcc build less asm code than clang.