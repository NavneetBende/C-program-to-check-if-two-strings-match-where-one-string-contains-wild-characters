Checking if two strings match where one String contains wild characters
Wild Card characters are characters like ‘ * ‘ and ‘ ? ‘. In this C program we will be checking that if two strings match where one string contains wildcard characters. We will be using the concept of ternary operator and pointers in this program, to increase the efficiency and reduce the complexity of the program. For better understanding of this program, you should atleast be having a good knowledge of ternary operator and pointers

String contains wild characters
Algorithm
Start
Accept the inputs
check if both the strings are of same length
comparing each character of both the strings, along with the wild characters
printing the output
yes, if both the strings are same
no, if both the strings are different
 
While loop in C
C program (String contains wild characters)
Run
#include <stdio.h>
#include <stdbool.h>
#include <string.h>


bool check(char *str1, char * str2) ;// declaration of the check() function
int main() 
{ 
    char str1[100] = "prep***ta",str2[100] = "prepinsta";
    printf("First  string with wild characters : ");
    puts(str1);
    printf("Second string without wild characters : ");
    puts(str2);
    check(str1,str2);
    return 0; 
}
bool check(char *str1, char * str2) 
{ 
    // checking end of both the strings 
    if (*str1 == '\0' && *str2 == '\0') 
         return true; 
  
    // comparing the characters of both the strings and wild characters(*)
    if (*str1 == '*' && *(str1+1) != '\0' && *str2 == '\0') 
         return false;
  
    // checking wild characters(?)
    if (*str1 == '?' || *str1 == *str2) 
         return check(str1+1, str2+1); 
    
    if (*str1 == '*') 
         return check(str1+1, str2) || check(str1, str2+1); 
     return false; 
} 

void test(char *str1, char *str2) 
{ 
    check(str1, str2)? puts(" Yes "): puts(" No "); 
}
