# s21_decimal
## Implementation of the decimal.h library functions

### Example:
```
typedef struct {
  int bits[4];
} s21_decimal;
```
### Arithmetic Operators
|	Operator name	|	Operators	|	Function	|
|------------|------------|------------|
|	Addition	|	+	|	int s21_add(s21_decimal value_1, s21_decimal value_2, s21_decimal *result)	|
|	Subtraction	|	-	|	int s21_sub(s21_decimal value_1, s21_decimal value_2, s21_decimal *result)	|
|	Multiplication	|	*	|	int s21_mul(s21_decimal value_1, s21_decimal value_2, s21_decimal *result)	|
|	Division	|	/	|	int s21_div(s21_decimal value_1, s21_decimal value_2, s21_decimal *result)	|

The functions return the error code:

* 0 - OK
* 1 - the number is too large or equal to infinity
* 2 - the number is too small or equal to negative infinity
* 3 - division by 0

### Comparison Operators					
|	Operator name	|	Operators	|	Function	|
|------------|------------|------------|
|	Less than	|	<	|	int s21_is_less(s21_decimal, s21_decimal)	|
|	Less than or equal to	|	<=	|	int s21_is_less_or_equal(s21_decimal, s21_decimal)	|
|	Greater than	|	>	|	int s21_is_greater(s21_decimal, s21_decimal)	|
|	Greater than or equal to	|	>=	|	int s21_is_greater_or_equal(s21_decimal, s21_decimal)	|
|	Equal to	|	==	|	int s21_is_equal(s21_decimal, s21_decimal)	|
|	Not equal to	|	!=	|	int s21_is_not_equal(s21_decimal, s21_decimal)	|

Return value:

* 0 - FALSE
* 1 - TRUE

### Convertors and parsers			
|	Convertor/parser	|	Function	|
|------------|------------|
|	From int	|	int s21_from_int_to_decimal(int src, s21_decimal *dst)	|
|	From float	|	int s21_from_float_to_decimal(float src, s21_decimal *dst)	|
|	To int	|	int s21_from_decimal_to_int(s21_decimal src, int *dst)	|
|	To float	|	int s21_from_decimal_to_float(s21_decimal src, float *dst)	|

Return value - code error:

* 0 - OK
* 1 - convertation error

### Another functions			
|	Description	|	Function	|
|------------|------------|
|	Rounds a specified Decimal number to the closest integer toward negative infinity.	|	int s21_floor(s21_decimal value, s21_decimal *result)	|
|	Rounds a decimal value to the nearest integer.	|	int s21_round(s21_decimal value, s21_decimal *result)	|
|	Returns the integral digits of the specified Decimal; any fractional digits are discarded, including trailing zeroes.	|	int s21_truncate(s21_decimal value, s21_decimal *result)	|
|	Returns the result of multiplying the specified Decimal value by negative one.	|	int s21_negate(s21_decimal value, s21_decimal *result)	|

Return value - code error:

* 0 - OK
* 1 - calculation error

### Requirements:
The functions of the decimal.h library described above must be implemented:

* The library must be developed in C language of C11 standard using gcc compiler;
* The library code must be located in the src folder on the develop branch;
* Do not use outdated and legacy language constructions and library functions. Pay attention to the legacy and obsolete marks in the official documentation on the language and the libraries used. Use the POSIX.1-2017 standard;
* When writing code it is necessary to follow the Google style;
* Make it as a static library named s21_decimal (with the s21_decimal.h header file);
* The library must be developed according to the principles of structured programming;
* Use prefix s21_ before each function;
* Prepare full coverage of library functions code with unit-tests using the Check library;
* Unit tests must cover at least 80% of each function (checked using gcov);
* Provide a Makefile for building the library and tests (with targets all, clean, test, s21_decimal.a, gcov_report);
* The gcov_report target should generate a gcov report in the form of an html page. Unit tests must be run with gcov flags to do this;
* When implementing decimal, stick to the binary representation with the integer bits array as specified in the example above. Observe the position of the digits of a number in the bits array;
* It is forbidden to use the __int128 type;
* Trailing zeros can be as preserved as deleted (except for the s21_truncate function);
* The defined type must support numbers from -79,228,162,514,264,337,593,543,950,335 to +79,228,162,514,264,337,593,543,950,335.
