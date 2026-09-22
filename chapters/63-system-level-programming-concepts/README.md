# 63. System-Level Programming Concepts

## Scope
ISO C provides portable language/library facilities, while processes, file descriptors, sockets, signals, threads, mmap, fork, exec, and similar APIs are operating-system-specific extensions.

## POSIX example: process creation
~~~c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main(void) {
    pid_t pid=fork();
    if(pid<0){perror("fork");return 1;}
    if(pid==0){
        puts("child");
        _exit(0);
    }
    int status;
    if(waitpid(pid,&status,0)<0){perror("waitpid");return 1;}
    puts("parent");
    return 0;
}
~~~
This is POSIX, not ISO C. Build and run only on a compatible system.

## Topics
Processes and address spaces, threads, synchronization, system calls, descriptors, signals, IPC, sockets, memory mapping, scheduling, and privilege boundaries.

## Safety
System APIs have platform-specific contracts and failure modes. Check return values and avoid unsafe assumptions about concurrent access.

## Practice
Write POSIX file-descriptor utilities, a producer-consumer program, and a client/server socket example while documenting platform requirements.