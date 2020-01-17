# Stringzz Pico 2019

[Info Ref for Format Strings vuln](http://www.cis.syr.edu/~wedu/Teaching/cis643/LectureNotes_New/Format_String.pdf)

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define FLAG_BUFFER 128
#define LINE_BUFFER_SIZE 2000

void printMessage3(char *in)
{
  puts("will be printed:\n");
  printf(in);
}
void printMessage2(char *in)
{
  puts("your input ");
  printMessage3(in);
}

void printMessage1(char *in)
{
  puts("Now ");
  printMessage2(in);
}

int main (int argc, char **argv)
{
    puts("input whatever string you want; then it will be printed back:\n");
    int read;
    unsigned int len;
    char *input = NULL;
    getline(&input, &len, stdin);
    //There is no win function, but the flag is wandering in the memory!
    char * buf = malloc(sizeof(char)*FLAG_BUFFER);
    FILE *f = fopen("flag.txt","r");
    fgets(buf,FLAG_BUFFER,f);
    printMessage1(input);
    fflush(stdout);
 
}
```

So after some reading a playing I noticed on this problem you could cause it to print out as much memory as you wanted as long as the first thing you passed it was a %x. Which try's to print a pointer, after that you can use %s as many times as you want to look for string data hiding up the memory. 

After I learned this I found the short hand `%[#]$s` where `[#]` can be w/e number location you want so you can pass say `%15$s` to the program and it will give you the 15th spot in memory. 

I continued to play till I found the flag with `%37$s`; 

Flag: `picoCTF{str1nG_CH3353_159c98a8}`