<table>
<thead><tr><th>Contents</th></tr></thead>
<tbody><tr><td>

1. [DoubleToStringConverter][DoubleToStringConverter]
	1. [DoubleToStringConverter.Flags][DoubleToStringConverter.Flags]
	2. [DoubleToStringConverter.Format][DoubleToStringConverter.Format]
	3. [DoubleToStringConverter.new][DoubleToStringConverter.new]
	4. [DoubleToStringConverter:ToShortest][DoubleToStringConverter:ToShortest]
	5. [DoubleToStringConverter:ToExact][DoubleToStringConverter:ToExact]
2. [DoubleToDecimalConverter][DoubleToDecimalConverter]
	1. [DoubleToDecimalConverter.ToShortest][DoubleToDecimalConverter.ToShortest]
	2. [DoubleToDecimalConverter.ToExact][DoubleToDecimalConverter.ToExact]
3. [DecimalToDoubleConverter][DecimalToDoubleConverter]
	1. [DecimalToDoubleConverter.ToDouble][DecimalToDoubleConverter.ToDouble]

## DoubleToStringConverter
[DoubleToStringConverter]: #user-content-doubletostringconverter
The double to string converter class.

### DoubleToStringConverter.Flags
[DoubleToStringConverter.Flags]: #user-content-doubletostringconverterflags
The possible bit combination of the flags enum:
	NO_FLAGS - No flags
	EMIT_POSITIVE_EXPONENT_SIGN - When the number is in the exponential format,
	it emits the "+" sign for positive exponents.
	EMIT_TRAILING_DECIMAL_POINT - When the number is in the decimal format,
	it emits a trailing decimal point ".".
	EMIT_TRAILING_ZERO_AFTER_POINT - When the number is in the decimal format,
	it emits a trailing "0" after the point, EMIT_TRAILING_DECIMAL_POINT must
	be enabled
	UNIQUE_ZERO - -0.0 does not display the minus sign "-"

### DoubleToStringConverter.Format
[DoubleToStringConverter.Format]: #user-content-doubletostringconverterformat
The format for its string representation:
	AUTO - Print the value in the decimal format if it's in the range of \[10^decimal_in_shortest_low; 10^decimal_in_shortest_high\[
	DECIAML - Print the value in the decimal format
	EXPONENTIAL - Print the value in the exponential format

### DoubleToStringConverter.new
[DoubleToStringConverter.new]: #user-content-doubletostringconverternew

```
function DoubleToStringConverter.new(
	flags: number,
	infinity_symbol: string?,
	nan_symbol: string?,
	exponent_symbol: string,
	decimal_in_shortest_low: number,
	decimal_in_shortest_high: number,
	min_exponent_width: number
): DoubleToStringConverter
```

The flag argument takes [DoubleToStringConverter.Flags][DoubleToStringConverter.Flags] bit combination

infinity_symbol and nan_symbol provide a string representation of these values, if these are nil then if you enter these value, they'll return nil as well

exponent_symbol is the symbol that represents exponents, usually 'e' or 'E'

When the format argument is provided as AUTO, it'll represent the numbers in decimal format if the range \[10^decimal_in_shortest_low; 10^decimal_in_shortest_high\[ and exponential otherwise

min_exponent_width zero fills the exponent integer digit. Basically, adding leading '0's to the exponent until it's at least min_exponent_width long. It only accepts integers from 1 to 5 so the exponent may never have more than 5 digits in total.

### DoubleToStringConverter:ToShortest
[DoubleToStringConverter:ToShortest]: #user-content-doubletostringconvertertoshortest

```
function DoubleToStringConverter:ToShortest(value: number, format: number?)
```

Converts the double to its shortest decimal representation that correctly represents the double.
The format argument takes the [DoubleToStringConverter.Format][DoubleToStringConverter.Format] argument enum as described.

### DoubleToStringConverter:ToExact
[DoubleToStringConverter:ToExact]: #user-content-doubletostringconvertertoexact

```lua
function DoubleToStringConverter:ToExact(value: number, format: number?)
```

Converts the double to its exact decimal representation.
The format argument takes the [DoubleToStringConverter.Format][DoubleToStringConverter.Format] argument enum as described.

## DoubleToDecimalConverter
[DoubleToDecimalConverter]: #user-content-doubletodecimalconverter

### DoubleToDecimalConverter.ToShortest
[DoubleToDecimalConverter.ToShortest]: #user-content-doubletodecimalconvertertoshortest

```lua
function DoubleToDecimalConverter.ToShortest(value: number): ({ number }?, number?, number?)
```

Returns the shortest decimal representation of double converted to decimal in array of table
with the length and scale by the power of ten. Zero, infinity, and NaN will return nil

### DoubleToDecimalConverter.ToExact
[DoubleToDecimalConverter.ToExact]: #user-content-doubletodecimalconvertertoexact

```lua
function DoubleToDecimalConverter.ToExact(value: number): ({ number }?, number?, number?)
```

Returns the exact decimal representation of double converted to decimal in array of table
with the length and scale by the power of ten