# Documentation
|Type|description|
|---|---|
|[StringIndex](#StringIndex)||
|[StringView](#StringView)| |
|[View](#View)||
|[String](#String)||

|Value|description|
|---|---|
|[concat](#concat)||
|[contains](#contains)||
|[contains\_char](#contains_char)||
|[default](#default)||
|[ends\_with](#ends_with)||
|[fold](#fold)||
|[from\_array](#from_array)| same as \`String::from\_array\`|
|[from\_iter](#from_iter)||
|[index\_at](#index_at)||
|[index\_at\_rev](#index_at_rev)||
|[index\_of](#index_of)||
|[is\_blank](#is_blank)||
|[is\_empty](#is_empty)||
|[iter](#iter)||
|[iter2](#iter2)||
|[last\_index\_of](#last_index_of)||
|[length\_eq](#length_eq)||
|[length\_ge](#length_ge)||
|[pad\_end](#pad_end)||
|[pad\_start](#pad_start)||
|[repeat](#repeat)||
|[replace](#replace)||
|[replace\_all](#replace_all)||
|[rev](#rev)||
|[rev\_fold](#rev_fold)||
|[rev\_get](#rev_get)||
|[rev\_iter](#rev_iter)||
|[split](#split)||
|[starts\_with](#starts_with)||
|[to\_array](#to_array)||
|[to\_bytes](#to_bytes)||
|[to\_lower](#to_lower)||
|[to\_upper](#to_upper)||
|[trim](#trim)||
|[trim\_end](#trim_end)||
|[trim\_space](#trim_space)||
|[trim\_start](#trim_start)||

## StringIndex

```moonbit
:::source,moonbitlang/core/string/deprecated.mbt,22:::type StringIndex
```


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,22:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/string#StringIndex">StringIndex</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/string/deprecated.mbt,22:::fn op_equal(<a href="moonbitlang/core/string#StringIndex">StringIndex</a>, <a href="moonbitlang/core/string#StringIndex">StringIndex</a>) -> Bool
    ```
    > automatically derived
- ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,22:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/string#StringIndex">StringIndex</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/string/deprecated.mbt,22:::fn output(<a href="moonbitlang/core/string#StringIndex">StringIndex</a>, <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > automatically derived

## StringView

```moonbit
:::source,moonbitlang/core/string/view.mbt,20:::type StringView
```
 
 A `StringView` represents a view of a String that maintains proper Unicode
character boundaries. It allows safe access to a substring while handling
multi-byte characters correctly.
alert deprecated "use @string.View instead"

#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/string/view.mbt,218:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for <a href="moonbitlang/core/string#StringView">StringView</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/string/view.mbt,218:::fn compare(self : <a href="moonbitlang/core/string#StringView">StringView</a>, other : <a href="moonbitlang/core/string#StringView">StringView</a>) -> Int
    ```
    > 
    >  Views are ordered lexicographically by their charcodes(code unit). This
    > orders Unicode characters based on their positions in the code charts. This is
    > not necessarily the same as "alphabetical" order, which varies by language
    > and locale.
- ```moonbit
  :::source,moonbitlang/core/string/view.mbt,197:::impl <a href="moonbitlang/core/builtin#Eq">Eq</a> for <a href="moonbitlang/core/string#StringView">StringView</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/string/view.mbt,197:::fn op_equal(self : <a href="moonbitlang/core/string#StringView">StringView</a>, other : <a href="moonbitlang/core/string#StringView">StringView</a>) -> Bool
    ```
    > 
    >  Compares two views for equality. Returns true only if both views
    > have the same length and contain identical characters in the same order.
- ```moonbit
  :::source,moonbitlang/core/string/view.mbt,131:::impl <a href="moonbitlang/core/builtin#Show">Show</a> for <a href="moonbitlang/core/string#StringView">StringView</a>
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/string/view.mbt,131:::fn output(self : <a href="moonbitlang/core/string#StringView">StringView</a>, logger : <a href="moonbitlang/core/builtin#Logger">Logger</a>) -> Unit
    ```
    > 
  * ```moonbit
    :::source,moonbitlang/core/string/view.mbt,146:::fn to_string(self : <a href="moonbitlang/core/string#StringView">StringView</a>) -> String
    ```
    > 
    >  Returns a new String containing a copy of the characters in this view.
    >  
    >  #### Examples
    >  
    >  ```
    >  let str = "Hello World"
    >  let view = str[0:5]  // "Hello"
    >  inspect!(view.to_string(), content="Hello")
    >  ```

#### mooncakes-io-method-mark-Methods
- #### char\_at
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,94:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::char_at(self : <a href="moonbitlang/core/string#StringView">StringView</a>, index : Int) -> Char
  ```
  > 
- #### char\_length
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,110:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::char_length(self : <a href="moonbitlang/core/string#StringView">StringView</a>) -> Int
  ```
  >  
  >  Returns the number of Unicode characters in this view.
  >  
  >  Note this has O(n) complexity where n is the length of the code points in
  > the view.
- #### char\_length\_eq
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,118:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::char_length_eq(self : <a href="moonbitlang/core/string#StringView">StringView</a>, len : Int) -> Bool
  ```
  > 
  >  Test if the length of the view is equal to the given length.
  >  
  >  This has O(n) complexity where n is the length in the parameter.
- #### char\_length\_ge
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,126:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::char_length_ge(self : <a href="moonbitlang/core/string#StringView">StringView</a>, len : Int) -> Bool
  ```
  > 
  >  Test if the length of the view is greater than or equal to the given length.
  >  
  >  This has O(n) complexity where n is the length in the parameter.
- #### charcode\_at
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,100:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::charcode_at(self : <a href="moonbitlang/core/string#StringView">StringView</a>, index : Int) -> Int
  ```
  > 
- #### iter
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,152:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::iter(self : <a href="moonbitlang/core/string#StringView">StringView</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]
  ```
  > 
  >  Returns an iterator over the Unicode characters in the string view.
- #### length
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,139:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::length(self : <a href="moonbitlang/core/string#StringView">StringView</a>) -> Int
  ```
  > 
- #### length\_eq
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,145:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::length_eq(self : <a href="moonbitlang/core/string#StringView">StringView</a>, len : Int) -> Bool
  ```
  > 
- #### length\_ge
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,151:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::length_ge(self : <a href="moonbitlang/core/string#StringView">StringView</a>, len : Int) -> Bool
  ```
  > 
- #### offset\_of\_nth\_char
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,80:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::offset_of_nth_char(self : <a href="moonbitlang/core/string#StringView">StringView</a>, i : Int) -> Int?
  ```
  > 
  >  Returns the UTF-16 index of the i-th (zero-indexed) Unicode character of
  > the view. If i is negative, it returns the index of the (n + i)-th character
  > where n is the total number of Unicode characters in the view.
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,112:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::op_as_view(self : <a href="moonbitlang/core/string#StringView">StringView</a>, start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/string#StringView">StringView</a>
  ```
  > 
- #### op\_get
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,208:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::op_get(self : <a href="moonbitlang/core/string#StringView">StringView</a>, index : Int) -> Char
  ```
  > 
  >  Return the character at the given index.
  >  
  >  The time complexity is O(n) where n is the given index, as it needs to scan
  > through the UTF-16 code units to find the nth Unicode character.
  >  
  >  #### Example
  >  
  >  ```
  >  let str = "Hello🤣🤣🤣"
  >  let view = str[1:6]
  >  inspect!(view[0], content="e")
  >  inspect!(view[4], content="🤣")
  >  ```
- #### rev\_get
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,228:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::rev_get(self : <a href="moonbitlang/core/string#StringView">StringView</a>, index : Int) -> Char
  ```
  > 
  >  Returns the character at the given index from the end of the view.
  >  
  >  The time complexity is O(n) where n is the given index, as it needs to scan
  > through the UTF-16 code units to find the nth Unicode character.
  >  
  >  #### Example
  >  
  >  ```
  >  let str = "Hello🤣🤣🤣"
  >  let view = str[1:6]
  >  inspect!(view.rev_get(0), content="🤣")
  >  inspect!(view.rev_get(4), content="e")
  >  ```
- #### rev\_iter
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,174:::fn <a href="moonbitlang/core/string#StringView">StringView</a>::rev_iter(self : <a href="moonbitlang/core/string#StringView">StringView</a>) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]
  ```
  > 
  >  Returns an iterator over the Unicode characters in the string view in reverse order.

## View

```moonbit
:::source,moonbitlang/core/string/view.mbt,38:::type View = <a href="moonbitlang/core/string#StringView">StringView</a>
```

 A `@string.View` represents a view of a String that maintains proper Unicode
character boundaries. It allows safe access to a substring while handling
multi-byte characters correctly.

## concat

```moonbit
:::source,moonbitlang/core/string/string.mbt,63:::fn concat(strings : <a href="moonbitlang/core/array#Array">Array</a>[String], separator~ : String = ..) -> String
```

 Concatenate strings.

 ```
 let s = @string.concat(["Hello", ", ", "world!"])
 assert_eq!(s, "Hello, world!")
 let s = @string.concat(["a", "b", "c"], separator=",")
 assert_eq!(s, "a,b,c")
 ```

## contains

```moonbit
:::source,moonbitlang/core/string/string.mbt,452:::fn contains(self : String, str : String) -> Bool
```

 Returns true if this string contains given sub string.

## contains\_char

```moonbit
:::source,moonbitlang/core/string/string.mbt,282:::fn contains_char(self : String, c : Char) -> Bool
```


## default

```moonbit
:::source,moonbitlang/core/string/string.mbt,120:::fn default() -> String
```

 same as `String::default`

## ends\_with

```moonbit
:::source,moonbitlang/core/string/string.mbt,468:::fn ends_with(self : String, str : String) -> Bool
```

 Returns true if this string ends with a sub string.

## fold

```moonbit
:::source,moonbitlang/core/string/string.mbt,200:::fn fold[A](self : String, init~ : A, f : (A, Char) -> A) -> A
```

 Note: This method operates on Unicode characters, not Utf16 code units.
As a result, the count of characters passed to the folding function may not be equal to the length of the string.

## from\_array

```moonbit
:::source,moonbitlang/core/string/string.mbt,35:::fn from_array(chars : <a href="moonbitlang/core/array#Array">Array</a>[Char]) -> String
```
 same as `String::from_array`

## from\_iter

```moonbit
:::source,moonbitlang/core/string/string.mbt,49:::fn from_iter(iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]) -> String
```

 same as `String::from_iter`

## index\_at

```moonbit
:::source,moonbitlang/core/string/deprecated.mbt,26:::fn index_at(self : String, offset_by : Int, start~ : <a href="moonbitlang/core/string#StringIndex">StringIndex</a> = ..) -> <a href="moonbitlang/core/string#StringIndex">StringIndex</a>?
```


## index\_at\_rev

```moonbit
:::source,moonbitlang/core/string/deprecated.mbt,36:::fn index_at_rev(self : String, offset_by : Int, end? : <a href="moonbitlang/core/string#StringIndex">StringIndex</a>) -> <a href="moonbitlang/core/string#StringIndex">StringIndex</a>?
```


## index\_of

```moonbit
:::source,moonbitlang/core/string/string.mbt,352:::fn index_of(self : String, str : String, from~ : Int = ..) -> Int
```

 Returns the first index of the sub string.

## is\_blank

```moonbit
:::source,moonbitlang/core/string/string.mbt,346:::fn is_blank(self : String) -> Bool
```

 Returns true if this string is blank.

## is\_empty

```moonbit
:::source,moonbitlang/core/string/string.mbt,340:::fn is_empty(self : String) -> Bool
```

 Returns true if this string is empty.

## iter

```moonbit
:::source,moonbitlang/core/string/string.mbt,152:::fn iter(self : String) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]
```

 Returns an iterator over the Unicode characters in the string.

 Note: This iterator yields Unicode characters, not Utf16 code units.
As a result, the count of characters returned by `iter().count()` may not be equal to the length of the string returned by `length()`.

 ```
 let s = "Hello, World!🤣";
 assert_eq!(s.iter().count(), 14); // Unicode characters
 assert_eq!(s.length(), 15); // Utf16 code units
 ```

## iter2

```moonbit
:::source,moonbitlang/core/string/string.mbt,175:::fn iter2(self : String) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, Char]
```


## last\_index\_of

```moonbit
:::source,moonbitlang/core/string/string.mbt,399:::fn last_index_of(self : String, str : String, from~ : Int = ..) -> Int
```

 Returns the last index of the sub string.

## length\_eq

```moonbit
:::source,moonbitlang/core/string/deprecated.mbt,145:::fn length_eq(self : <a href="moonbitlang/core/string#StringView">StringView</a>, len : Int) -> Bool
```


## length\_ge

```moonbit
:::source,moonbitlang/core/string/deprecated.mbt,151:::fn length_ge(self : <a href="moonbitlang/core/string#StringView">StringView</a>, len : Int) -> Bool
```


## pad\_end

```moonbit
:::source,moonbitlang/core/string/string.mbt,668:::fn pad_end(self : String, total_width : Int, padding_char : Char) -> String
```

 `pad_end` is a new String with `padding_char`s suffixed to `self` if `self.length() < total_width`. The length of the
returned string is `total_width`.

 Example:

 ```
 assert_eq!("2".pad_end(3, 'x'), "2xx")
 ```

## pad\_start

```moonbit
:::source,moonbitlang/core/string/string.mbt,641:::fn pad_start(self : String, total_width : Int, padding_char : Char) -> String
```

 `pad_start` is a new string with `padding_char`s prefixed to `self` if `self.length() < total_width`. The length of the
returned string is `total_width`.

 Example:

 ```
 assert_eq!("2".pad_start(3, '0'), "002")
 ```

## repeat

```moonbit
:::source,moonbitlang/core/string/string.mbt,617:::fn repeat(self : String, n : Int) -> String
```

 Repeats the string `n` times.

## replace

```moonbit
:::source,moonbitlang/core/string/string.mbt,532:::fn replace(self : String, old~ : String, new~ : String) -> String
```

 Replace the first old string in this string to new string.

## replace\_all

```moonbit
:::source,moonbitlang/core/string/string.mbt,545:::fn replace_all(self : String, old~ : String, new~ : String) -> String
```

 Replace all old string in this string to new string.

## rev

```moonbit
:::source,moonbitlang/core/string/string.mbt,607:::fn rev(self : String) -> String
```

 Reverse string
It respects Unicode characters and surrogate pairs but not grapheme clusters.
TODO: make it an intrinsic function

## rev\_fold

```moonbit
:::source,moonbitlang/core/string/string.mbt,209:::fn rev_fold[A](self : String, init~ : A, f : (A, Char) -> A) -> A
```


## rev\_get

```moonbit
:::source,moonbitlang/core/string/deprecated.mbt,228:::fn rev_get(self : <a href="moonbitlang/core/string#StringView">StringView</a>, index : Int) -> Char
```

 Returns the character at the given index from the end of the view.
 
 The time complexity is O(n) where n is the given index, as it needs to scan
through the UTF-16 code units to find the nth Unicode character.
 
 #### Example
 
 ```
 let str = "Hello🤣🤣🤣"
 let view = str[1:6]
 inspect!(view.rev_get(0), content="🤣")
 inspect!(view.rev_get(4), content="e")
 ```

## rev\_iter

```moonbit
:::source,moonbitlang/core/string/string.mbt,243:::fn rev_iter(self : String) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]
```

 Returns an iterator that yields characters from the end to the start of the string. This function handles
Unicode surrogate pairs correctly, ensuring that characters are not split across surrogate pairs.

 #### Parameters

 - `self` : The input `String` to be iterated in reverse.

 #### Returns

 - An `Iter[Char]` that yields characters from the end to the start of the string.

 #### Behavior

 - The function iterates over the string in reverse order.
 - If a trailing surrogate is encountered, it checks for a preceding leading surrogate to form a complete Unicode code point.
 - Yields each character or combined code point to the iterator.
 - Stops iteration if the `yield_` function returns `IterEnd`.

 #### Examples

 ```
 let input = "Hello, World!"
 let reversed = input.rev_iter().collect()
 assert_eq!(reversed, ['!', 'd', 'l', 'r', 'o', 'W', ' ', ',', 'o', 'l', 'l', 'e', 'H'])
 ```

## split

```moonbit
:::source,moonbitlang/core/string/string.mbt,504:::fn split(self : String, separator : String) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[String]
```

 Splits the input `String` into an `Iter` of `String` using the specified `separator`.

 #### Parameters

 - `self` : The input `String` to be split.
 - `separator` : The `String` used as the delimiter for splitting.

 #### Returns

 - An `Iter` of `String` where each element is a substring of the original string, separated by the `separator`.

 #### Behavior

 - If the `separator` is an empty string (`""`), the function returns an `Iter` where each element is a single character from the input string converted to a `String`.
 - If the `separator` is not empty, the function searches for occurrences of the `separator` in the input string and yields substrings between these occurrences.
 - If no more occurrences of the `separator` are found, the remaining part of the string is yielded as the last element of the `Iter`.

 #### Examples

 ```
 let input = "a,b,c,d"
 let separator = ","
 let result = input.split(separator).collect()
 assert_eq!(result, ["a", "b", "c", "d"])
 ```

## starts\_with

```moonbit
:::source,moonbitlang/core/string/string.mbt,458:::fn starts_with(self : String, str : String) -> Bool
```

 Returns true if this string starts with a sub string.

## to\_array

```moonbit
:::source,moonbitlang/core/string/string.mbt,132:::fn to_array(self : String) -> <a href="moonbitlang/core/array#Array">Array</a>[Char]
```

 Converts the String into an array of Chars.

## to\_bytes

```moonbit
:::source,moonbitlang/core/string/string.mbt,126:::fn to_bytes(self : String) -> Bytes
```

 `String` holds a sequence of UTF-16 code units encoded in little endian format

## to\_lower

```moonbit
:::source,moonbitlang/core/string/string.mbt,575:::fn to_lower(self : String) -> String
```

 Converts this string to lowercase.

## to\_upper

```moonbit
:::source,moonbitlang/core/string/string.mbt,590:::fn to_upper(self : String) -> String
```

 Converts this string to uppercase.

## trim

```moonbit
:::source,moonbitlang/core/string/string.mbt,273:::fn trim(self : String, trim_set : String) -> String
```

 Removes all leading and trailing chars contained in the given string.

## trim\_end

```moonbit
:::source,moonbitlang/core/string/string.mbt,314:::fn trim_end(self : String, trim_set : String) -> String
```

 Removes all trailing chars contained in the given string.

## trim\_space

```moonbit
:::source,moonbitlang/core/string/string.mbt,267:::fn trim_space(self : String) -> String
```

 Removes all leading and trailing spaces.

## trim\_start

```moonbit
:::source,moonbitlang/core/string/string.mbt,288:::fn trim_start(self : String, trim_set : String) -> String
```

 Removes all leading chars contained in the given string.

## String


#### mooncakes-io-implementation-mark-Implementations
- ```moonbit
  :::source,moonbitlang/core/string/string.mbt,94:::impl <a href="moonbitlang/core/builtin#Compare">Compare</a> for String
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/string/string.mbt,94:::fn compare(self : String, other : String) -> Int
    ```
    > 
    >  Strings are ordered lexicographically by their charcodes(code unit). This
    > orders Unicode characters based on their positions in the code charts. This is
    > not necessarily the same as "alphabetical" order, which varies by language
    > and locale.
- ```moonbit
  :::source,moonbitlang/core/string/string.mbt,114:::impl <a href="moonbitlang/core/builtin#Default">Default</a> for String
  ```
  > 
  * ```moonbit
    :::source,moonbitlang/core/string/string.mbt,114:::fn default() -> String
    ```
    > 
    >  The empty string

#### mooncakes-io-method-mark-Methods
- #### char\_at
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,769:::fn <a href="moonbitlang/core/string#String">String</a>::char_at(self : String, index : Int) -> Char
  ```
  > 
  >  Returns the Unicode character at the given index.
- #### char\_length\_eq
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,780:::fn <a href="moonbitlang/core/string#String">String</a>::char_length_eq(self : String, len : Int, start_offset~ : Int = .., end_offset~ : Int = ..) -> Bool
  ```
  > 
  >  Test if the length of the string is equal to the given length.
  > 
  >  This has O(n) complexity where n is the length in the parameter.
- #### char\_length\_ge
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,807:::fn <a href="moonbitlang/core/string#String">String</a>::char_length_ge(self : String, len : Int, start_offset~ : Int = .., end_offset~ : Int = ..) -> Bool
  ```
  > 
  >  Test if the length of the string is greater than or equal to the given length.
  > 
  >  This has O(n) complexity where n is the length in the parameter.
- #### concat
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,17:::fn <a href="moonbitlang/core/string#String">String</a>::concat(self : <a href="moonbitlang/core/array#Array">Array</a>[String], separator~ : String = ..) -> String
  ```
  > 
- #### contains
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,452:::fn <a href="moonbitlang/core/string#String">String</a>::contains(self : String, str : String) -> Bool
  ```
  > 
  >  Returns true if this string contains given sub string.
- #### contains\_char
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,282:::fn <a href="moonbitlang/core/string#String">String</a>::contains_char(self : String, c : Char) -> Bool
  ```
  > 
- #### ends\_with
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,468:::fn <a href="moonbitlang/core/string#String">String</a>::ends_with(self : String, str : String) -> Bool
  ```
  > 
  >  Returns true if this string ends with a sub string.
- #### fold
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,200:::fn <a href="moonbitlang/core/string#String">String</a>::fold[A](self : String, init~ : A, f : (A, Char) -> A) -> A
  ```
  > 
  >  Note: This method operates on Unicode characters, not Utf16 code units.
  > As a result, the count of characters passed to the folding function may not be equal to the length of the string.
- #### from\_array
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,26:::fn <a href="moonbitlang/core/string#String">String</a>::from_array(chars : <a href="moonbitlang/core/array#Array">Array</a>[Char]) -> String
  ```
  > 
  >  Convert char array to string.
  > 
  >  ```
  >  let s = @string.from_array(['H', 'e', 'l', 'l', 'o'])
  >  assert_eq!(s, "Hello")
  >  ```
  > 
  >  Do not convert large datas to `Array[Char]` and build a string with `String::from_array`.
  > 
  >  For efficiency considerations, it's recommended to use `Buffer` instead.
- #### from\_iter
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,42:::fn <a href="moonbitlang/core/string#String">String</a>::from_iter(iter : <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]) -> String
  ```
  > 
  >  Convert char iterator to string,
  > a simple wrapper for `from_array`.
- #### index\_at
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,26:::fn <a href="moonbitlang/core/string#String">String</a>::index_at(self : String, offset_by : Int, start~ : <a href="moonbitlang/core/string#StringIndex">StringIndex</a> = ..) -> <a href="moonbitlang/core/string#StringIndex">StringIndex</a>?
  ```
  > 
- #### index\_at\_rev
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,36:::fn <a href="moonbitlang/core/string#String">String</a>::index_at_rev(self : String, offset_by : Int, end? : <a href="moonbitlang/core/string#StringIndex">StringIndex</a>) -> <a href="moonbitlang/core/string#StringIndex">StringIndex</a>?
  ```
  > 
- #### index\_of
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,352:::fn <a href="moonbitlang/core/string#String">String</a>::index_of(self : String, str : String, from~ : Int = ..) -> Int
  ```
  > 
  >  Returns the first index of the sub string.
- #### is\_blank
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,346:::fn <a href="moonbitlang/core/string#String">String</a>::is_blank(self : String) -> Bool
  ```
  > 
  >  Returns true if this string is blank.
- #### is\_empty
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,340:::fn <a href="moonbitlang/core/string#String">String</a>::is_empty(self : String) -> Bool
  ```
  > 
  >  Returns true if this string is empty.
- #### iter
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,152:::fn <a href="moonbitlang/core/string#String">String</a>::iter(self : String) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]
  ```
  > 
  >  Returns an iterator over the Unicode characters in the string.
  > 
  >  Note: This iterator yields Unicode characters, not Utf16 code units.
  > As a result, the count of characters returned by `iter().count()` may not be equal to the length of the string returned by `length()`.
  > 
  >  ```
  >  let s = "Hello, World!🤣";
  >  assert_eq!(s.iter().count(), 14); // Unicode characters
  >  assert_eq!(s.length(), 15); // Utf16 code units
  >  ```
- #### iter2
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,175:::fn <a href="moonbitlang/core/string#String">String</a>::iter2(self : String) -> <a href="moonbitlang/core/builtin#Iter2">Iter2</a>[Int, Char]
  ```
  > 
- #### last\_index\_of
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,399:::fn <a href="moonbitlang/core/string#String">String</a>::last_index_of(self : String, str : String, from~ : Int = ..) -> Int
  ```
  > 
  >  Returns the last index of the sub string.
- #### length\_eq
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,180:::fn <a href="moonbitlang/core/string#String">String</a>::length_eq(self : String, len : Int) -> Bool
  ```
  > 
  >  Test if the length of the string is equal to the given length.
  > 
  >  This has O(n) complexity where n is the length in the parameter.
- #### length\_ge
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,189:::fn <a href="moonbitlang/core/string#String">String</a>::length_ge(self : String, len : Int) -> Bool
  ```
  > 
  >  Test if the length of the string is greater than or equal to the given length.
  > 
  >  This has O(n) complexity where n is the length in the parameter.
- #### offset\_of\_nth\_char
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,752:::fn <a href="moonbitlang/core/string#String">String</a>::offset_of_nth_char(self : String, i : Int, start_offset~ : Int = .., end_offset~ : Int = ..) -> Int?
  ```
  > 
  >  Returns the UTF-16 index of the i-th (zero-indexed) Unicode character
  > within the range \[start, end). If i is negative, it returns the index of
  > the (n + i)-th character where n is the number of Unicode characters
  > in the range \[start, end).
  >  
  >  This functions assumes that the string is valid UTF-16.
- #### op\_as\_view
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,88:::fn <a href="moonbitlang/core/string#String">String</a>::op_as_view(self : String, start~ : Int = .., end? : Int) -> <a href="moonbitlang/core/string#StringView">StringView</a>
  ```
  > 
- #### pad\_end
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,668:::fn <a href="moonbitlang/core/string#String">String</a>::pad_end(self : String, total_width : Int, padding_char : Char) -> String
  ```
  > 
  >  `pad_end` is a new String with `padding_char`s suffixed to `self` if `self.length() < total_width`. The length of the
  > returned string is `total_width`.
  > 
  >  Example:
  > 
  >  ```
  >  assert_eq!("2".pad_end(3, 'x'), "2xx")
  >  ```
- #### pad\_start
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,641:::fn <a href="moonbitlang/core/string#String">String</a>::pad_start(self : String, total_width : Int, padding_char : Char) -> String
  ```
  > 
  >  `pad_start` is a new string with `padding_char`s prefixed to `self` if `self.length() < total_width`. The length of the
  > returned string is `total_width`.
  > 
  >  Example:
  > 
  >  ```
  >  assert_eq!("2".pad_start(3, '0'), "002")
  >  ```
- #### repeat
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,617:::fn <a href="moonbitlang/core/string#String">String</a>::repeat(self : String, n : Int) -> String
  ```
  > 
  >  Repeats the string `n` times.
- #### replace
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,532:::fn <a href="moonbitlang/core/string#String">String</a>::replace(self : String, old~ : String, new~ : String) -> String
  ```
  > 
  >  Replace the first old string in this string to new string.
- #### replace\_all
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,545:::fn <a href="moonbitlang/core/string#String">String</a>::replace_all(self : String, old~ : String, new~ : String) -> String
  ```
  > 
  >  Replace all old string in this string to new string.
- #### rev
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,607:::fn <a href="moonbitlang/core/string#String">String</a>::rev(self : String) -> String
  ```
  > 
  >  Reverse string
  > It respects Unicode characters and surrogate pairs but not grapheme clusters.
  > TODO: make it an intrinsic function
- #### rev\_fold
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,209:::fn <a href="moonbitlang/core/string#String">String</a>::rev_fold[A](self : String, init~ : A, f : (A, Char) -> A) -> A
  ```
  > 
- #### rev\_get
  ```moonbit
  :::source,moonbitlang/core/string/deprecated.mbt,170:::fn <a href="moonbitlang/core/string#String">String</a>::rev_get(self : String, index : Int) -> Char
  ```
  > 
  >  Returns the character at the given index from the end of the string.
  > 
  >  #### Examples
  > 
  >  ```moonbit
  >  let s = "Hello🤣🤣🤣"
  >  inspect!(s.rev_get(0), content="🤣")
  >  inspect!(s.rev_get(4), content="l")
  >  ```
  > 
  >  #### Panics
  > 
  >  @alert unsafe "Panics if the index is out of bounds."
- #### rev\_iter
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,243:::fn <a href="moonbitlang/core/string#String">String</a>::rev_iter(self : String) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[Char]
  ```
  > 
  >  Returns an iterator that yields characters from the end to the start of the string. This function handles
  > Unicode surrogate pairs correctly, ensuring that characters are not split across surrogate pairs.
  > 
  >  #### Parameters
  > 
  >  - `self` : The input `String` to be iterated in reverse.
  > 
  >  #### Returns
  > 
  >  - An `Iter[Char]` that yields characters from the end to the start of the string.
  > 
  >  #### Behavior
  > 
  >  - The function iterates over the string in reverse order.
  >  - If a trailing surrogate is encountered, it checks for a preceding leading surrogate to form a complete Unicode code point.
  >  - Yields each character or combined code point to the iterator.
  >  - Stops iteration if the `yield_` function returns `IterEnd`.
  > 
  >  #### Examples
  > 
  >  ```
  >  let input = "Hello, World!"
  >  let reversed = input.rev_iter().collect()
  >  assert_eq!(reversed, ['!', 'd', 'l', 'r', 'o', 'W', ' ', ',', 'o', 'l', 'l', 'e', 'H'])
  >  ```
- #### split
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,504:::fn <a href="moonbitlang/core/string#String">String</a>::split(self : String, separator : String) -> <a href="moonbitlang/core/builtin#Iter">Iter</a>[String]
  ```
  > 
  >  Splits the input `String` into an `Iter` of `String` using the specified `separator`.
  > 
  >  #### Parameters
  > 
  >  - `self` : The input `String` to be split.
  >  - `separator` : The `String` used as the delimiter for splitting.
  > 
  >  #### Returns
  > 
  >  - An `Iter` of `String` where each element is a substring of the original string, separated by the `separator`.
  > 
  >  #### Behavior
  > 
  >  - If the `separator` is an empty string (`""`), the function returns an `Iter` where each element is a single character from the input string converted to a `String`.
  >  - If the `separator` is not empty, the function searches for occurrences of the `separator` in the input string and yields substrings between these occurrences.
  >  - If no more occurrences of the `separator` are found, the remaining part of the string is yielded as the last element of the `Iter`.
  > 
  >  #### Examples
  > 
  >  ```
  >  let input = "a,b,c,d"
  >  let separator = ","
  >  let result = input.split(separator).collect()
  >  assert_eq!(result, ["a", "b", "c", "d"])
  >  ```
- #### starts\_with
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,458:::fn <a href="moonbitlang/core/string#String">String</a>::starts_with(self : String, str : String) -> Bool
  ```
  > 
  >  Returns true if this string starts with a sub string.
- #### to\_array
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,132:::fn <a href="moonbitlang/core/string#String">String</a>::to_array(self : String) -> <a href="moonbitlang/core/array#Array">Array</a>[Char]
  ```
  > 
  >  Converts the String into an array of Chars.
- #### to\_bytes
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,126:::fn <a href="moonbitlang/core/string#String">String</a>::to_bytes(self : String) -> Bytes
  ```
  > 
  >  `String` holds a sequence of UTF-16 code units encoded in little endian format
- #### to\_lower
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,575:::fn <a href="moonbitlang/core/string#String">String</a>::to_lower(self : String) -> String
  ```
  > 
  >  Converts this string to lowercase.
- #### to\_upper
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,590:::fn <a href="moonbitlang/core/string#String">String</a>::to_upper(self : String) -> String
  ```
  > 
  >  Converts this string to uppercase.
- #### trim
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,273:::fn <a href="moonbitlang/core/string#String">String</a>::trim(self : String, trim_set : String) -> String
  ```
  > 
  >  Removes all leading and trailing chars contained in the given string.
- #### trim\_end
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,314:::fn <a href="moonbitlang/core/string#String">String</a>::trim_end(self : String, trim_set : String) -> String
  ```
  > 
  >  Removes all trailing chars contained in the given string.
- #### trim\_space
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,267:::fn <a href="moonbitlang/core/string#String">String</a>::trim_space(self : String) -> String
  ```
  > 
  >  Removes all leading and trailing spaces.
- #### trim\_start
  ```moonbit
  :::source,moonbitlang/core/string/string.mbt,288:::fn <a href="moonbitlang/core/string#String">String</a>::trim_start(self : String, trim_set : String) -> String
  ```
  > 
  >  Removes all leading chars contained in the given string.
- #### view
  ```moonbit
  :::source,moonbitlang/core/string/view.mbt,63:::fn <a href="moonbitlang/core/string#String">String</a>::view(self : String, start_offset~ : Int = .., end_offset~ : Int = ..) -> <a href="moonbitlang/core/string#StringView">StringView</a>
  ```
  > 
  >  Creates a `View` into a `String`.
  >  
  >  #### Example
  >  
  >  ```
  >  let str = "Hello🤣🤣🤣"
  >  let view1 = str.view()
  >  inspect!(view1, content=
  >   "Hello🤣🤣🤣"
  >  )
  >  let start_offset = str.offset_of_nth_char(1).unwrap()
  >  let end_offset = str.offset_of_nth_char(6).unwrap() // the second emoji
  >  let view2 = str.view(start_offset~, end_offset~)
  >  inspect!(view2, content=
  >   "ello🤣"
  >  )
  >  ```
