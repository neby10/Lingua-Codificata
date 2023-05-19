# My C Notes

Create > Compile > Execute

Naming Conventions
Struct 			Title Case
Struct Members 		lower_case or lowerCase
Enum 				ETitleCase
Enum Members 		ALL_CAPS or lowerCase
Public functions 		pfx_TitleCase (pfx = two or three letter module prefix) Private functions 		TitleCase
Trivial variables 		i,x,n,f etc... 
Local variables		lower_case or lowerCase
Global variables		g_lowerCase or g_lower_case (searchable by g_ prefix)


Variables
All variables must be declared before they can be used
C is case sensitive (difference between count and Count)
Char is typically 8 bits - e.g. ‘f’
variables based on scope (local and global)
Format specifiers: %d for integers, %c for characters, %f for floating point and doubles (or %.2f for two decimal places etc.), %s for string
Strings end with ‘\n’ which is the null 0, null zero is not technically counted in the length of the string but is counted in terms of memory space needed. Char month[8] = “january” | ‘j’=0, ‘a’=1, ‘n’=2, ‘u’=3, ‘a’=4, ‘r’=5, ‘y’=6, ‘\n’=7
If you have an array of chars and the last element is a ‘\n’, then you can use string.h functions, otherwise you cannot.

5 Basic Data Types
character
integer (typically within range of -32,768 and 32,767)
float
double
Void

Backslash Codes
backspace = \b, newline = \n, horizontal tab = \t, double quote = \”, single quote = \’, null = \0, backslash = \\, vertical tab = \v
form feed = \f, carriage return = \r, bell = \a

When writing your own header files, use the “” format for including other files. When you use quotation marks, C first searches the disk directory in which your program is stored and then searches the built in #include directory. 

The #define preprocessor directive defines constants.
#define CONSTANT constantDefinition

printf(controlString [, data]); actually sends output to the computer’s standard output device. Most operating systems route the standard output to your screen unless you know enough to route the output elsewhere. Can route output to printer, disk drives, etc. 


Do not nest switch statements. Defaults can start to get dicey and program may not run.

Allocating the Heap
	malloc() – if malloc() fails it will point to null 0 so good to check if operation was successful, library is stdlib.h
	free() – free the memory, library is stdlib.h


Structures can be used to group items of different data types. The dot operator (.) is used to access individual data members within a structure variable. The structure pointer operator (->) is used to access individual data members within a structure pointed to by a pointer variable. 
struct myStruct {
	char manuf[25];
	char model[15];
	int diskSpace;
	int memSpace;
	float cost;
	float price;
}

Working with files: 
	#include <stdio.h>
	FILE *fptr;
	int main() {
		fptr = fopen(“filepath”, “w”); // w = write, r = read, a = append
		// rest of program here
		fclose(fptr);
}


stdio.h 
	printf()
	scanf(“%s”, myVar)
	putchar()
	getchar()
	fgets(pointer, acceptableLength, fileStream) - e.g. fgets(myCharArray, 10, stdin);
	puts()

	
math.h
	sqrt()
	pow() - raises a value to the power
	ceil() - returns a float
	floor() - returns a float
	fabs() - absolute value of a number
	cos(x), sin(x), tan(x), acos(x), asin(x), atan(x), log(5)

string.h
strcpy(myVar, “actual string”); 
	> changes variable to the new string
strlen(myVar)
strcat(firstString, lastString) - merges two character arrays, make sure first array can hold both strings
strtok()
strstr()
strcmp()
strncmp()

stdlib.h 
	DO NOT USE gets(), BUFFER OVERFLOW SECURITY ISSUES
	exit(exitCode)
	srand() - used to seed the time of the program to generate truly random values, (MUST USE time.h)
	rand() - generates random number between 0 and 32767

ctype.h
	isalpha(inChar) - checks if character is an alphabetic character (a-z, A-Z)
	isdigit(inChar) - checks if character is a digit from 0-9
	isupper(inChar)
	islower(inChar)
	toupper(inChar)
	tolower(inChar)