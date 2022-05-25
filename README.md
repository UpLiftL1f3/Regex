# Email Regex

In this ReadMe we will be going over the different properties that make up a regular expression otherwise known as Regex. As we go through each property we will be referring to the email regex: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Summary

The regex above is a simple regular expression to match email addresses. Note all regular expressions are wrapped in /'s. Firstly we'll breakdown the different properties of Regular Expressions and them breakdown the email regex at the end.

## Table of Contents

- [Anchors](#anchors)
- [Bracket Expressions](#bracket-expressions)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

^ and $ are two characters that are considered to be **anchors** .
The **^** anchor signifies a string that **begins** with one of the characters that follow it. **Important** note to keep in mind is that regex are **case-sensitive**. This means if you write "^Hi" the following string must follow with "Hi" or "Hi Tom" NOT "hi" or "hi Tom", because the first letter of H was uppercase so the string that follows the anchor has to also start with an uppercase H.

The **$** anchor signifies a string that **ends** with the character that proceeds it.

### Bracket Expressions

Anything inside of the "**[ ]**" represents a range of characters that we want to use. Bracket Expressions are also known as **positive character group**, because they outline the characters we want to include.

- whenever you use **[abc]** you are essentially looking for a string that contains a or b or c, regardless of the length of the string. So al of the following examples would match: "aaa", "bin" "court", "abracadabra", and "bca".
- you will more commonly see a hyphen (**-**) used between alphanumeric or alphabetic characters to express anything between. For example [abc] and [a-c] will look for the exact same thing.
- Whenever you use a ^ symbol inside of a bracket ([^0-9]) you are saying that the following string can contain anything EXCEPT any integers between 0 through 9.

so to conclude this section lets give the example [a-z0-9_-], this will match any string that includes any combination of lowercase letters between a and z, any number between 0 and 9, and the special characters of an underscore or a hyphen. The following examples fulfill the requirements of this regex:

- "lernantino"
- "lernantino1"
- "l3rnantino_1"
- "lern-antino"
- "21452"
- "_-_-"

What about the string "Helper"? This would not match our pattern because it includes an uppercase character, H. If bracket expression was [a-zA-Z0-9_-] then the string "Helper" would have matched as well.

### Quantifiers

The Quantifiers are essentially the conditions to the string we are looking for for example {3,16} means that the string has to be at least 3 characters long and can **NOT** exceed 16 characters while still only containing the characters expressed in the bracket expression.

Let's return to our entire regex:
/^[a-z0-9_-]{3,16}$/

This regex is looking for any string between 3 and 16 characters that starts and ends with a combination of lowercase characters, the numbers 0–9, and the special characters of an underscore and a hyphen.

The following examples match:

- 123
- l3rn-antin0_1

The following examples **DO NOT** match:

- 25
- L3RN-antino0_1 ()
- l3rn-antin0_am1k0
- l3rn\*antin0?1
  (these strings do not match because the special characters \* and ? aren't allowed in this regex.)

### Grouping Constructs

The primary way a regex is grouped is by using parentheses (**()**). Each section within parentheses is known as a **subexpression**.

The following example contains two grouping constructs or subexpressions:

(def):(mno)

The first section is looking for a string that matches "def" exactly. While the second subsection is looking for an exact string of "mno".
The subexpressions are split by a colon (**:**). Thus the string "def:mno" would match whereas the string "fed:mno" would NOT.

### The OR Operator

The **OR OPERATOR** simply adds flexibility to any constructs or subexpressions. For Example: given our earlier example of (def):(mno) if we were to write it as (d|e|f):(m|n|o) then the previously failed string og "def:mno" would NOW MATCH the constraints given although the order still maters so "mno:def" would NOT MATCH.

### Character Escapes

The backslash "\" in a regex **escapes** or allows the following character to ignore its original functionality and to simply include it. For example, the open curly brace ({) is used to begin a quantifier, but adding a backslash before the open curly brace (\{) means that the regex should look for the open curly brace character instead of beginning to define a quantifier.

### Character Classes

when pertaining to a dot (.)

- matches any single character except line terminators: \n, \r, \u2028 or \u2029
- For example, /.y/ matches "my" and "ay", but not "yes", in "yes make my day".
- inside a character class the dot loses it's functionality and becomes a literal dot(.)

\d = Matches any digit (Arabic numeral). Equivalent to [0-9]

### Flags

First I want to reiterate that a regex must be wrapped in slash characters "/.../". Flags are placed at the end of a regex, after the second slash, and they define additional functionality or limits for the regex. There are 6 different flags that can be used, but i will only explain the 3 that you're most likely to encounter.

- g— which stands for **Global search**: the regex should be tested against all possible matches in a string.

* i— which stands for **Case-insensitive** search: case should be ignored while attempting a match in a string
* m—which stands for **Multi-line** search: a multi-line input string should be treated as multiple lines

## Email Regex Breakdown

Email Regex: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

The regex provided above is an example of an email regex. stating that the properties between the /.../ are the properties of the regex. The ^ anchor is stating that it must start with any of the following characters [a-z0-9_\.]. The character escape (\) is allowing the . withing the Bracket Expression to be represented as an actual dot and not any character in that placement. The Quantifier (+) is stating that it needs to be followed by a @. Later the [\da-z\.-] followed by the Bracket Expression which starts with a character class of \b which represents arabic numeric characters "0-9" or a-z and the character dot(.) as explained earlier. Lastly the bracket expression a-z with a dot followed by a quantifier of {2,6} which expresses a limit of at least 2 characters and a max length of 6 characters.

## Author

Gil Benvenitz [UpLiftL1f3](https://github.com/UpLiftL1f3?tab=repositories)
