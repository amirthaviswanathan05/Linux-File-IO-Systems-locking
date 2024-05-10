# Linux-File-IO-Systems-locking
Ex07-Linux File-IO Systems-locking
# AIM:
To Write a C program that illustrates files copying and locking

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux IO Systems locking

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## 1.To Write a C program that illustrates files copying 
```
include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>
int main()
{
char block[1024];
int in, out;
int nread;
in = open("filecopy.c", O_RDONLY);
out = open("file.out", O_WRONLY|O_CREAT, S_IRUSR|S_IWUSR);
while((nread = read(in,block,sizeof(block))) > 0)
write(out,block,nread);
exit(0);}
```


## 2.To Write a C program that illustrates files locking
```
#include <fcntl.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <sys/file.h>
int main (int argc, char* argv[])
{ char* file = argv[1];
 int fd;
 struct flock lock;
 printf ("opening %s\n", file);
 /* Open a file descriptor to the file. */
 fd = open (file, O_WRONLY);
// acquire shared lock
if (flock(fd, LOCK_SH) == -1) {
    printf("error");
}else
{printf("Acquiring shared lock using flock");
}
getchar();
// non-atomically upgrade to exclusive lock
// do it in non-blocking mode, i.e. fail if can't upgrade immediately
if (flock(fd, LOCK_EX | LOCK_NB) == -1) {
    printf("error");
}else
{printf("Acquiring exclusive lock using flock");}
getchar();
// release lock
// lock is also released automatically when close() is called or process exits
if (flock(fd, LOCK_UN) == -1) {
    printf("error");
}else{
printf("unlocking");
}
getchar();
close (fd);
return 0;
}
```
NAME: AMIRTHAVARSHINI V
REG NO: 212223040014

## OUTPUT
C program that illustrates files copying

![327921334-c8cecbba-ba1f-4a9f-8176-0b1cee85f960](https://github.com/amirthaviswanathan05/Linux-File-IO-Systems-locking/assets/149035397/df06fc8c-2410-486c-8950-3334458fd555)

C program that illustrates files locking
![327921400-f1780296-e1eb-4caa-817f-93455fadc979](https://github.com/amirthaviswanathan05/Linux-File-IO-Systems-locking/assets/149035397/7a6be4de-4e81-449a-8fb5-f98343f63c68)


# RESULT:
The programs are executed successfully.
