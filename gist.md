# Matching a URL with Regular Expression

The following tutorial will introduce a regex pattern for validating a
URL.

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`
[Source](https://code.tutsplus.com/tutorials/8-regular-expressions-you-should-know--net-6149)

# Summary

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

This pattern is composed of four main segments: an optional
protocol, the domain name, extension, and an optional directory or file
path.

- `^` Is an Anchor used to assert the start of the string
- `(https?:\/\/)?` Is an optional Group, matching a protocol either
'http://' or 'https://'
- `([\da-z\.-]+)` Is a Group that matches a domain name containing 
one or more lowercase letters, digits, periods, or hyphens
- `\.` Matches a period
- `([a-z\.]{2,6})` Is a Group that matches two to six lowercase letters
or periods for the purpose of validating the domain extension
- `([\/\w \.-]*)*` A Group that matches zero or more occurrences of forward
slashes, words, spaces, periods, or hyphens. The last `*` Quantifier 
matches zero or more instances of this Group, to validate an optional
file or directory path
- `\/?` An optional forward slash, used to match a URL's trailing slash
- `$` The Anchor used to assert the end of the string.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
Anchors are Regular Expression tokens used to match a position within
a string. This unique property allows for anchors to be commonly used
in matching the boundaries of a given string.

Within our pattern, we have the following two anchors:

Beginning - denoted as `^`
: This anchor simply matches the beginning of a given string

End - denoted as `$`
: The last anchor in our regular expression, in our case matches the
end of a given string

### Quantifiers
Quantifiers are a useful tool in regular expression for specifying how
many times a preceding token must be matched. Aside from matching
quantity, Quantifiers can also be used to express optionality.

Within our pattern, we have the following 4 types of quantifiers:

Optional - denoted as `?`
: The first type of quantifier used in this pattern, used to match
either a single or no instance of the preceding token. In our pattern, 
Optional is used three separate times:
: `s?` defines 's' as an optional character, in order to match both
'https' and 'http'
: `(https?:\/\/)?` defines the inclusion of a protocol as optional.
Allows a given string without 'https://' or 'http://' to match
: `\/?` denotes a trailing slash at the end of a given string to be
optional

Plus - denoted as `+`
: Plus is used to match one or more instances of the preceding token.
Plus is included in this pattern once:
: `[\da-z\.-]+` matches one or more instances of this character set.
Used in this pattern to match a domain name with letters, hyphens,
periods

Star - denoted as `*`
: Finally, Star is the last type of Quantifier used in this pattern.
Star matches zero or more instances of the preceding token. This
Quantifier is used twice in our pattern, both within and for the
same token:
: `([\/\w \.-]*)*` matches any number of `\/` forward slashes,
`\w` word characters, ` ` spaces, `\.` periods, and `-` hyphens.
The last star succeeding this group denotes a directory or file path
at the end of a given string to be optional

### Grouping Constructs
Groups are used in regular expressions to combine multiple tokens
together. This allows us to evaluate the entire sequence of
tokens together. Our pattern contains 4 Groups:

- `(https?:\/\/)?` the protocol of our URL; the `?` Quantifier
defines this Group as optional
- `([\da-z\.-]+)` the domain name
- `([a-z\.]{2,6})` the domain suffix; matches strings such as
'.com'
- `([\/\w \.-]*)*` a file or directory path; the `*` Quantifier
matches zero or more instances of this Group

### Bracket Expressions
Bracket Expressions match any character in the set, enclosed by
brackets. Our pattern contains the following Bracket Expressions:

- `[\da-z\.-]+` matches at least one or more instances of `\d` digits,
`a-z` lowercase letters, `\.` periods, or `-` hyphens
- `[a-z\.]{2,6}` matches between two and six instances of `a-z`
lowercase letters, or `\.` periods
- `[\/\w \.-]*` matches any number of `\/` forward slashes, ` ` spaces,
`\.` periods, or `-` hyphens

### Character Classes
Regular Expression contains a variety of predefined Character Classes,
used to match a character from a specific set. Our pattern makes use
of the following Character Classes:

Digit - denoted as `\d`
: The Digit Character Class matches any digit from 0 to 9

Range - denoted as `-`
: Range Character Classes match any character at or within the
specified list. In order to define a Range, the `-` operator must be
placed between two characters. Range then matches any character with 
a valid character code. Our pattern uses the `a-z` for any lowercase
letter

Word - denoted as `\w`
: Word Character Classes match any word character. It is used once
in the pattern, `([\/\w \.-]*)*`

### Character Escapes
As Regular Expression contains many characters with special meanings,
Character Escapes can be used to account for situations in which
patterns must use them as character literals. This is simply done by
the use of a `&#92;` backslash to prefix the character with which to use
literally. The following Character Escapes are used in our pattern:

- Escaped Forward Slash `\/`
- Escaped Period `\.`

## Author
[GitHub - agcontr1](https://github.com/agcontr1)