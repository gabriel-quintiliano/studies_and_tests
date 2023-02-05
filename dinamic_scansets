// This program is to show an example of how to dinamically define a scanset to used with
// functions such as scanf, sscanf and fscanf. For that we just need to edit a format_string
// (via sprintf) which will be passed to one of these functions as their second argument
// (instead of the most commonly used string literal format).
//
// TIP: For the % to be include into the final string instead of being perceived as a
// format specifier place holder, use %%. Ex: %%d wil yield "%d" in the final string

#include <stdio.h>

int main(void)
{
    char format_string[100]; // buffer to store the format string delivered from sprintf
    char r_begin = 'a', r_end = 'd'; // definition of the range's begin and end

    // Here I format a string to be later used as a format string in sscanf
    sprintf(format_string, "%%*[^%c-%c]%%[%c-%c]", r_begin, r_end, r_begin, r_end);
    
    // printf("format_string = %s\n", format_string); // just if you want to check the format_string

    char in_sentence[] = "   shji k kkn xxxxxxxbcadbacaadbcdbdddddddddd23hh123 456 785 famoso";
    char out_sentence[40];
    
    sscanf(in_sentence, format_string, out_sentence); // format_string == "%*[^a-d]%[a-d]"
    // According to the scansets, sscanf will read and discard everything except for matches from 'a' to 'd'
    // (in other sentences, it will stop reading when it bumps into either an 'a', 'b', 'c' or 'd'), and then
    // throught the second scanset will read only chars from 'a' to 'd' and finally store the recovered data
    // in the out_sentence buffer

    printf("\nin_sentence after parsing it via sscanf:\n%s\n\n", out_sentence); // prints "bcadbacaadbcdbdddddddddd"

    return 0;
}
