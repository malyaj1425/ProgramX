# ProgramX
#include <stdlib.h>
#include <stdio.h>
#include <sys/time.h>
#include <time.h>
#define NUM 1000000
#define NUM2 10000000
float time_diff(struct timeval *start, struct timeval *end)
{
    return (end->tv_sec - start->tv_sec) + 1e-6*(end->tv_usec - start->tv_usec);
}
void loopFunc(size_t num)
{
    int tmp = 0;
    for (int i = 0; i < num; ++i) {
        tmp += 1;
    }
}
int main() {
    struct timeval start;
    struct timeval end;
    gettimeofday(&start, NULL);
    loopFunc(NUM);
    gettimeofday(&end, NULL);

    printf("loopFunc(%d)  time spent: %0.8f sec\n",
           NUM, time_diff(&start, &end));
    gettimeofday(&start, NULL);
    loopFunc(NUM2);
    gettimeofday(&end, NULL);
    printf("loopFunc(%d) time spent: %0.8f sec\n",
           NUM2, time_diff(&start, &end));
    exit(EXIT_SUCCESS);
}
Program 2.2 sysinf()
This method is responsible for achieve the information of used software and hardware 
#include<stdio.h>
#include<stdlib.h>
#include<errno.h>
#include<sys/utsname.h>
int main()
{
   struct utsname buf1;
   errno =0;
   if(uname(&buf1)!=0)
   {
      perror("uname doesn't return 0, so there is an error");
      exit(EXIT_FAILURE);
   }
   printf("System Name = %s\n", buf1.sysname);
   printf("Node Name = %s\n", buf1.nodename);
   printf("Version = %s\n", buf1.version);
   printf("Release = %s\n", buf1.release);
   printf("Machine = %s\n", buf1.machine);
}
