// This program is a brief study about the possible text formatting throught printf
// just run the program and see the results in terminal

#include <stdio.h>

int main(void)
{
    int x = 8, y = 915, z = 17;
    float f = 0.123456789;
    char word[] = "abcdefghijklmnopqrstuvwxyz";

    printf("\nWithout field width definition %%i:\n");
    printf("----------------------\n");
    printf("|%i|%i|%i|\n", x, y, z);
    printf("----------------------\n\n");

    printf("With field width definition %%6i:\n");
    printf("----------------------\n");
    printf("|%6i|%6i|%6i|\n", x, y, z);
    printf("----------------------\n\n");

    printf("With field width and the - flag %%-6i\n(to invert padding to right side):\n");
    printf("----------------------\n");
    printf("|%-6i|%-6i|%-6i|\n", x, y, z);
    printf("----------------------\n\n");

    // You can also define the field width with *, this way you can specify an signed int
    // or variable (of a signed int) in the argument list to define the field width
    printf("Field width with *, via a signed int %%*d --> |%*d|\n\n", 6, x);

    printf("Field width with *, via a signed int var %%*d --> |%*d|\n\n", x-2, x);

    printf("field width + 0 as padding character %%06d --> %06d\n\n", x);
    // Obs, 0 as padding char only works with format specifiers of numbers
    // and is ignored when used with the flag - as it could cause confusion ex: 25000

    // Precision . can be used mainly with 3 classes of format specifiers: those for
    // floating-point numbers --> defines the number of precision digits
    // integers --> defines (minimum) field width and fill with 0s the unused fields
    // strings --> defines the maximum field width (not printing the rest of the string after that)
    printf("About precision, all the following have %%.5 precison:\n");
    printf("for floating point numbers %%.5f --> %.5f\n", f);
    printf("for integers %%.5d --> %.5d (same as %%05d)\n", x);
    printf("for strings %%.5s --> %.5s\n\n", word);

    return 0;
}
