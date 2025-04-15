# Documentation
|Type|description|
|---|---|
|[Char](#Char)||

|Value|description|
|---|---|
|[is\_ascii](#is_ascii)| Checks if the value is within the ASCII range.|
|[is\_ascii\_alphabetic](#is_ascii_alphabetic)| Checks if the value is an ASCII alphabetic character:|
|[is\_ascii\_control](#is_ascii_control)| Checks if the value is an ASCII control character:|
|[is\_ascii\_digit](#is_ascii_digit)| Checks if the value is an ASCII decimal digit:|
|[is\_ascii\_graphic](#is_ascii_graphic)| Checks if the value is an ASCII graphic character:|
|[is\_ascii\_hexdigit](#is_ascii_hexdigit)| Checks if the value is an ASCII hexadecimal digit:|
|[is\_ascii\_lowercase](#is_ascii_lowercase)| Checks if the value is an ASCII lowercase character:|
|[is\_ascii\_octdigit](#is_ascii_octdigit)| Checks if the value is an ASCII octal digit:|
|[is\_ascii\_punctuation](#is_ascii_punctuation)| Checks if the value is an ASCII punctuation character:|
|[is\_ascii\_uppercase](#is_ascii_uppercase)| Checks if the value is an ASCII uppercase character:|
|[is\_ascii\_whitespace](#is_ascii_whitespace)| Checks if the value is an ASCII whitespace character:|
|[is\_control](#is_control)| Returns true if this char has the general category for control codes.|
|[is\_digit](#is_digit)| |
|[is\_numeric](#is_numeric)| Returns true if this char has one of the general categories for numbers.|
|[is\_printable](#is_printable)| Returns true if this character is printable (visible when displayed).|
|[is\_whitespace](#is_whitespace)| Returns true if this char has the White\_Space property.|

## is\_ascii

```moonbit
:::source,moonbitlang/core/char/char.mbt,26:::fn is_ascii(self : Char) -> Bool
```
 Checks if the value is within the ASCII range.

## is\_ascii\_alphabetic

```moonbit
:::source,moonbitlang/core/char/char.mbt,33:::fn is_ascii_alphabetic(self : Char) -> Bool
```
 Checks if the value is an ASCII alphabetic  character:
 - U+0041 'A' ..= U+005A 'Z'
 - U+0061 'a' ..= U+007A 'z'

## is\_ascii\_control

```moonbit
:::source,moonbitlang/core/char/char.mbt,40:::fn is_ascii_control(self : Char) -> Bool
```
 Checks if the value is an ASCII control character:
U+0000 NUL ..= U+001F UNIT SEPARATOR, or U+007F DELETE.
Note that most ASCII whitespace characters are control characters, but SPACE is not.

## is\_ascii\_digit

```moonbit
:::source,moonbitlang/core/char/char.mbt,46:::fn is_ascii_digit(self : Char) -> Bool
```
 Checks if the value is an ASCII decimal digit:
U+0030 '0' ..= U+0039 '9'

## is\_ascii\_graphic

```moonbit
:::source,moonbitlang/core/char/char.mbt,52:::fn is_ascii_graphic(self : Char) -> Bool
```
 Checks if the value is an ASCII graphic character:
U+0021 '!' ..= U+007E '~'

## is\_ascii\_hexdigit

```moonbit
:::source,moonbitlang/core/char/char.mbt,60:::fn is_ascii_hexdigit(self : Char) -> Bool
```
 Checks if the value is an ASCII hexadecimal digit:
 - U+0030 '0' ..= U+0039 '9'
 - U+0041 'A' ..= U+0046 'F'
 - U+0061 'a' ..= U+0066 'f'

## is\_ascii\_lowercase

```moonbit
:::source,moonbitlang/core/char/char.mbt,66:::fn is_ascii_lowercase(self : Char) -> Bool
```
 Checks if the value is an ASCII lowercase character:
U+0061 'a' ..= U+007A 'z'.

## is\_ascii\_octdigit

```moonbit
:::source,moonbitlang/core/char/char.mbt,72:::fn is_ascii_octdigit(self : Char) -> Bool
```
 Checks if the value is an ASCII octal digit:
U+0030 '0' ..= U+0037 '7'

## is\_ascii\_punctuation

```moonbit
:::source,moonbitlang/core/char/char.mbt,81:::fn is_ascii_punctuation(self : Char) -> Bool
```
 Checks if the value is an ASCII punctuation character:
 - U+0021 ..= U+002F ! " \# \$ % & ' ( ) \* + , - . /
 - U+003A ..= U+0040 : ; \< = \> ? @
 - U+005B ..= U+0060 \[ \\ \] ^ \_ \`
 - U+007B ..= U+007E { \| } ~

## is\_ascii\_uppercase

```moonbit
:::source,moonbitlang/core/char/char.mbt,91:::fn is_ascii_uppercase(self : Char) -> Bool
```
 Checks if the value is an ASCII uppercase character:
U+0041 'A' ..= U+005A 'Z'

## is\_ascii\_whitespace

```moonbit
:::source,moonbitlang/core/char/char.mbt,97:::fn is_ascii_whitespace(self : Char) -> Bool
```
 Checks if the value is an ASCII whitespace character:
U+0020 SPACE, U+0009 HORIZONTAL TAB, U+000A LINE FEED, U+000C FORM FEED, or U+000D CARRIAGE RETURN.

## is\_control

```moonbit
:::source,moonbitlang/core/char/char.mbt,102:::fn is_control(self : Char) -> Bool
```
 Returns true if this char has the general category for control codes.

## is\_digit

```moonbit
:::source,moonbitlang/core/char/char.mbt,110:::fn is_digit(self : Char, radix : UInt) -> Bool
```
 
 Checks if a char is a digit in the given radix (range from 2 to 36).
 
 panic if the radix is invalid.

## is\_numeric

```moonbit
:::source,moonbitlang/core/char/char.mbt,139:::fn is_numeric(self : Char) -> Bool
```
 Returns true if this char has one of the general categories for numbers.

## is\_printable

```moonbit
:::source,moonbitlang/core/char/char.mbt,302:::fn is_printable(self : Char) -> Bool
```
 Returns true if this character is printable (visible when displayed).
Aligns with Unicode standard categories for printable characters.
Characters are considered printable if they are:
 - Letters (L\*)
 - Marks (M\*)
 - Numbers (N\*)
 - Punctuation (P\*)
 - Symbols (S\*)
 - Spaces (Zs), with some exceptions
   Characters are considered non-printable if they are:
 - Control characters (Cc)
 - Format characters (Cf)
 - Line/paragraph separators (Zl, Zp)
 - Private use (Co)
 - Unassigned (Cn)
 - Surrogates (Cs)

## is\_whitespace

```moonbit
:::source,moonbitlang/core/char/char.mbt,123:::fn is_whitespace(self : Char) -> Bool
```
 Returns true if this char has the White\_Space property.

## Char


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/char/char.mbt,16:::impl <a href="moonbitlang/core/builtin#Hash">Hash</a> for Char
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/char/char.mbt,16:::fn hash(self : Char) -> Int
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/char/char.mbt,21:::fn hash_combine(self : Char, hasher : <a href="moonbitlang/core/builtin#Hasher">Hasher</a>) -> Unit
    ```
    > 

#### mooncakes-io-method-mark-Methods
- #### is\_ascii
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,26:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii(self : Char) -> Bool
  ```
  >  Checks if the value is within the ASCII range.
- #### is\_ascii\_alphabetic
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,33:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_alphabetic(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII alphabetic  character:
  >  - U+0041 'A' ..= U+005A 'Z'
  >  - U+0061 'a' ..= U+007A 'z'
- #### is\_ascii\_control
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,40:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_control(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII control character:
  > U+0000 NUL ..= U+001F UNIT SEPARATOR, or U+007F DELETE.
  > Note that most ASCII whitespace characters are control characters, but SPACE is not.
- #### is\_ascii\_digit
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,46:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_digit(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII decimal digit:
  > U+0030 '0' ..= U+0039 '9'
- #### is\_ascii\_graphic
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,52:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_graphic(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII graphic character:
  > U+0021 '!' ..= U+007E '~'
- #### is\_ascii\_hexdigit
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,60:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_hexdigit(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII hexadecimal digit:
  >  - U+0030 '0' ..= U+0039 '9'
  >  - U+0041 'A' ..= U+0046 'F'
  >  - U+0061 'a' ..= U+0066 'f'
- #### is\_ascii\_lowercase
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,66:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_lowercase(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII lowercase character:
  > U+0061 'a' ..= U+007A 'z'.
- #### is\_ascii\_octdigit
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,72:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_octdigit(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII octal digit:
  > U+0030 '0' ..= U+0037 '7'
- #### is\_ascii\_punctuation
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,81:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_punctuation(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII punctuation character:
  >  - U+0021 ..= U+002F ! " \# \$ % & ' ( ) \* + , - . /
  >  - U+003A ..= U+0040 : ; \< = \> ? @
  >  - U+005B ..= U+0060 \[ \\ \] ^ \_ \`
  >  - U+007B ..= U+007E { \| } ~
- #### is\_ascii\_uppercase
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,91:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_uppercase(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII uppercase character:
  > U+0041 'A' ..= U+005A 'Z'
- #### is\_ascii\_whitespace
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,97:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_ascii_whitespace(self : Char) -> Bool
  ```
  >  Checks if the value is an ASCII whitespace character:
  > U+0020 SPACE, U+0009 HORIZONTAL TAB, U+000A LINE FEED, U+000C FORM FEED, or U+000D CARRIAGE RETURN.
- #### is\_control
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,102:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_control(self : Char) -> Bool
  ```
  >  Returns true if this char has the general category for control codes.
- #### is\_digit
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,110:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_digit(self : Char, radix : UInt) -> Bool
  ```
  >  
  >  Checks if a char is a digit in the given radix (range from 2 to 36).
  >  
  >  panic if the radix is invalid.
- #### is\_numeric
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,139:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_numeric(self : Char) -> Bool
  ```
  >  Returns true if this char has one of the general categories for numbers.
- #### is\_printable
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,302:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_printable(self : Char) -> Bool
  ```
  >  Returns true if this character is printable (visible when displayed).
  > Aligns with Unicode standard categories for printable characters.
  > Characters are considered printable if they are:
  >  - Letters (L\*)
  >  - Marks (M\*)
  >  - Numbers (N\*)
  >  - Punctuation (P\*)
  >  - Symbols (S\*)
  >  - Spaces (Zs), with some exceptions
  >    Characters are considered non-printable if they are:
  >  - Control characters (Cc)
  >  - Format characters (Cf)
  >  - Line/paragraph separators (Zl, Zp)
  >  - Private use (Co)
  >  - Unassigned (Cn)
  >  - Surrogates (Cs)
- #### is\_whitespace
  ```moonbit
  :::source,moonbitlang/core/char/char.mbt,123:::fn <a href="moonbitlang/core/char#Char">Char</a>::is_whitespace(self : Char) -> Bool
  ```
  >  Returns true if this char has the White\_Space property.
