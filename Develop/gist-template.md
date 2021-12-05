# Regex Lesson: Matching a URL

Welcome to this week's lesson on Regular Expressions, Regex for short. Regex will allow you to identify and search for patterns utilizing a variety of special characters. This makes sifting and scanning through material or code much quicker as you will be able to essnetially search the characters that make-up and identify components of an email, URL, and Hex Values, just to name a few. Being able to search through and quickly find what you're looking for is crutial, and you probably already do it in your everyday computer use such as search engines and finding a specific word in your word document.

## Summary

This lesson will specifically cover Regex in relation to Matching a URL. Below is a code snippet of a URL identifier utilizing Regex:

```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```

Using the code snippet above, we will take you through what each component means and what it does in this case. This will allow you to then utilize the Regex expression of URL matching in your own work. Within a URL there are 3 main components that make-up the link:

1. The `http` & the `://`, which is mandatory to commence all URL links
   1. The `s` that follows the `http` is optional, and not all URL links have them
2. The `www.` followed by the `domain name`
3. The `.com`
   1. The `/` following the `.com` is optional, and not all URL links have them

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

The two principal anchors in this regex expression are the `^` at the beginning and the `$` at the end which constitute an exact string match with the components included within the two anchors. When used alone, the `^` anchor matches any string that _begins_ with the characters that follow the anchor. The `$` matches any string that _ends_ with the characters that precede it. By enclosing the regex between these two anchors, we are asking the search function to match exactly is included between them (what it begins AND ends with).

### Quantifiers

Notice that some of the 4 parentheses groups include "?" and "\*" characters. In Regular Expressions, these characters are known as quantifiers. Group 1 (https?:\/\/) begins by matching the characters "http". The "http" characters are case sensitive (lowercase). The ? after the
"s" character is actually a quantifier that makes a single instance of the character preceding the quantifier optional. Thus, this expression will accept either "http://" OR "https://" (the "s" is optional).
You can also see that the entire first parentheses group is followed by a ? and as such, "https://" or "http://" is entirely optional. A valid URL may begin with http(s) or it may not begin with it at all.

Additionally, in Group 3, we can see the {} quantifier, which defines a range of possible matches. In evaluating the expression within this third parentheses group, Top level domain, this section of the inputted URL only allows for anywhere between 2-6 characters.

### Grouping Constructs

I have now pointed out and described the two anchors in our URL Matching Regex Expression. Now, let's examine what is between the two anchors:
With anchors: /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?$/
Without anchors: (https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?
Within our two anchors, we can now see that there are a number of components separated by parentheses (). Parentheses are used in Regular Expressions to denote different groups.
Within each of these parentheses groups, there is a smaller expression that is being evaluated:

1. (https?:\/\/)
2. ([\da-z\.-]+)
3. ([a-z\.]{2,6}), checks for the top-level domain (com, org. net, .gov, etc)
4. ([\/\w \.-]\*)

The first group is the optional http portion.
The second group is looking for any characters that would represent a domain name, followed by a ".".
The third group is most commonly seen as a ".com" (top-level domain) and is limited to 2-6 characters.
The final group is the filepath or directory location name.

### Bracket Expressions

Bracket expressions are those patterns within `[]`. This simply looks to see if the letters are found at all in a string.
An example is `[a-z]` which is found throughout our regex. This checks that the string being checked contains a character between "a" and "z". The "-" is used to indicate that the pattern should check from the left variable to the right variable.
It should be noted that bracket expressions are case sensitive, so `[a-z]` will NOT match something that has a capital letter, or a number.
When the "-" is at the beginning or end of a pattern, however, this indicates that the hyphen should be included as a regular character to be included in the pattern.
An example is `[\da-z\.-]` where the "-" indicates that the string may have a hyphen to match the pattern.

### Character Classes

A character class is a defined set of characters in regular expressions. They are useful as a kind of shorthand.
An example from our URL regex is `\d` from `([\da-z\.-]+)`.
`\d` is a character class for all Arabic numerals, so it is the equivalent of `[0-9]`.

- \d - all Arabic numerals
- . - any single character except the newline `\n`
- \w - Matches any alphanumeric character from the basic Latin alphabet, including the underscore. This means it is equivalent to the bracket expression of `[A-Za-z0-9_]`

### The OR Operator

The OR operator is `:` and allows for strings to be matched that match one pattern or another.
`https?:\/\/` shows that the start of the string can match:
"https" OR "//"
It should however be noted that the `?` for the "https" pattern allows for there to be no pattern to be there.
This means that the URL could begin with:

1. "https"
2. "//"
3. "" - nothing, and goes straight to the domain name of the URL, such as `gist.github.com`

### Flags

Flags can be used to make your search even more specific. Using optional flags can allow you to search globally, multi-line,
case insensitive and more. These flags can be used separately or together.

In our example we do not have any added flags but if we wanted to add a flag to look at the global scale
it would look like this:

/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_, 'g')_\/?$/

### Character Escapes

A character escape comes in the form of a backslash. The backslash (\) in a regex precedes a character and "escapes" them
as to not be taken literally. It can change the meaning of the character. You can escape literal or common character classes.

For \w in our example, having the backslash would be shorthand for looking up a word character [a-zA-Z0-9_].
\. would be a period (special character: so it needs to be escaped by a \). Without the escape the . could mean any
character except for a line break.

## Author

Author: Shem Baijoo

Github Profile: (https://github.com/spb71)
