# Regex Explained

This tutorial is intended to introduce and explain 'regex' (regular expressions), it's components and uses.

## Summary

Regular expressions, or regex, are patterns used to match and manipulate text. There are several components to regex patterns that allow for powerful and flexible matching. 
Character classes are used to match specific sets of characters, such as digits or letters. 

Metacharacters, such as the period and asterisk, represent any character or any number of characters respectively. Anchors, like the caret and dollar sign, are used to match the beginning or end of a line or string. Quantifiers, such as the plus sign and question mark, control the number of times a character or group of characters can appear. Finally, grouping constructs, such as parentheses and square brackets, allow for complex combinations of patterns to be matched. 

By combining these components, regex patterns can be tailored to match almost any text pattern, making them a powerful tool in data processing and text manipulation.

Here is an example of a regex statment which expresses matching an HTML tag;
` /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/ `

` /^ :` This indicates the start of the string.
` <: ` This matches the opening angle bracket of an HTML tag.
`([a-z]+):` This is a capturing group that matches one or more lowercase letters of the alphabet (a-z). It captures the tag name, which must come immediately after the opening angle bracket.
`([^<]+)*:` This is a non-capturing group that matches zero or more characters that are not an opening angle bracket. It matches any attributes that may be present in the HTML tag.
`(?:>(.*)<\/\1>|\s+\/>)`: This is a non-capturing group that matches either the end of the HTML tag i.e. `>` followed by any characters and then the tag name captured in the first group, followed by `</)`, or a self-closing tag i.e. one or more whitespace characters followed by `/>)`.
`$:` This indicates the end of the string.
So, putting it all together, this regex statement matches any string that represents a valid HTML tag, including any attributes and the content within the tag.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Regex anchors are special characters that allow you to match a specific position in a string, rather than matching a character or set of characters. There are two main types of anchors in regular expressions:

The caret (^): This anchor matches the start of a string. When used at the beginning of a regular expression, it indicates that the following pattern should only match if it appears at the start of the string.

The dollar sign ($) : This anchor matches the end of a string. When used at the end of a regular expression, it indicates that the preceding pattern should only match if it appears at the end of the string.

### Quantifiers

Regex quantifiers are special characters that allow you to match multiple occurrences of a character or group of characters in a regular expression. Here are some common regex quantifiers and what they do:

The asterisk (*): This quantifier matches zero or more occurrences of the preceding character or group. For example, a* would match zero or more occurrences of the letter "a".

The plus sign (+): This quantifier matches one or more occurrences of the preceding character or group. For example, a+ would match one or more occurrences of the letter "a".

The question mark (?): This quantifier matches zero or one occurrence of the preceding character or group. For example, a? would match zero or one occurrence of the letter "a".

The curly braces ({}): This quantifier allows you to specify a specific number of occurrences to match. For example, a{3} would match exactly three occurrences of the letter "a".

The curly braces with a range ({m,n}): This quantifier allows you to specify a range of occurrences to match, where m is the minimum and n is the maximum. For example, a{2,4} would match between two and four occurrences of the letter "a".

The lazy quantifiers (?, *?, +?, {}?): These quantifiers are similar to their greedy counterparts, but they match the smallest possible number of occurrences. For example, a*? would match the smallest possible number of occurrences of the letter "a".

Using quantifiers in your regular expressions can be very useful for matching patterns with variable lengths or repetition, allowing for more flexible and powerful pattern matching.

### OR Operator

Similar although not the same as javaScript, the OR operator in regular expressions (Regex) is represented by the vertical bar symbol "|". It is used to match any one of a set of alternatives.

For example, the regular expression "cat|dog" will match either "cat" or "dog". The OR operator can also be used with groups to specify more complex alternatives. For example, the regular expression "(cat|dog) food" will match "cat food" or "dog food".

In general, the OR operator is used to specify a choice between two or more patterns in a regular expression. It is a powerful tool that allows you to match multiple patterns with a single regular expression.

### Character Classes

Regex character classes are a way to match a set of characters with a single character in a regular expression.

There are several predefined character classes in regular expressions that match common types of characters, such as:

\d - Matches any digit character (0-9).
\w - Matches any word character (alphanumeric characters and underscore).
\s - Matches any whitespace character (space, tab, newline, etc.).
. - Matches any character except newline.
In addition to these predefined character classes, you can create custom character classes using square brackets []. For example, the regular expression [abc] matches any of the characters a, b, or c.

You can also use ranges to specify a range of characters in a character class. For example, the regular expression [a-z] matches any lowercase letter from a to z.

Character classes can also be negated using the caret (^) symbol. For example, the regular expression [^abc] matches any character except a, b, or c.

In summary, character classes in regular expressions provide a powerful way to match a set of characters with a single character in a regular expression, making it easier and more efficient to specify patterns in your regular expressions.

### Flags

Regex flags are optional modifiers that can be added to a regular expression to change its behavior.

Here are some common regex flags and their meanings:

i (case-insensitive): Matches both uppercase and lowercase characters. For example, /hello/i will match "hello", "HELLO", "hElLo", etc.

g (global): Matches all occurrences of the pattern in the input string, not just the first one. For example, /cat/g will match "cat" in "cat and cat and cat".

m (multiline): Changes the behavior of ^ and $ to match the beginning and end of each line, instead of just the beginning and end of the input string.

s (dot-all): Allows the dot (.) to match any character, including newline characters.

u (unicode): Enables full Unicode support, including matching Unicode characters and properties.

y (sticky): Matches only at the index indicated by the lastIndex property of the regular expression.

To use a flag in a regular expression, you add it after the final delimiter, for example, /pattern/flags.

Using flags can help you refine your regular expressions to better match specific patterns in your input text.


### Grouping and Capturing

Regex grouping and capturing allow you to match and extract specific parts of a regular expression. Grouping is achieved by enclosing part of the regular expression in parentheses, which creates a sub-expression or a group. This allows you to apply quantifiers and other modifiers to the entire group. Capturing is the process of extracting the text matched by a group and making it available for use in the replacement text or for further processing. This is done by assigning a number to the group, starting from 1 for the first group, and using the backslash followed by the group number in the replacement text or in subsequent regular expressions. Grouping and capturing are useful for complex regular expressions that need to match and manipulate specific parts of the input text.

### Bracket Expressions

A regex bracket expression, also known as a character class, is a set of characters enclosed in square brackets [] that matches any single character from that set. Bracket expressions allow you to specify a range of characters or character classes that you want to match, for example, [abc] matches a, b, or c, while [0-9] matches any digit from 0 to 9. You can also use the caret (^) symbol at the beginning of a bracket expression to negate it, matching any character that is not in the set, for example, [^abc] matches any character that is not a, b, or c. Bracket expressions are a powerful tool for matching specific sets of characters in a regular expression.

### Greedy and Lazy Match

Greedy and lazy matches are two types of quantifiers in regex that determine how many times a character or group can be repeated in a match.

A greedy quantifier matches as much text as possible while still allowing the overall pattern to match. For example, the pattern ".*" will match the longest possible string of characters, while still allowing the overall pattern to match. This behavior is called greedy matching.

In contrast, a lazy quantifier matches as little text as possible while still allowing the overall pattern to match. The lazy quantifier is denoted by adding a question mark (?) to the quantifier. For example, the pattern ".*?" will match the shortest possible string of characters, while still allowing the overall pattern to match.

Greedy matching is the default behavior in regex, but sometimes it can cause performance issues or produce unexpected results. In these cases, using a lazy quantifier can help to produce more predictable and efficient matches.

### Boundaries

Regex boundaries are special characters that match the start or end of a word, line, or string in a regular expression. They allow you to match patterns that occur at specific positions within the input text.

Here are some common regex boundaries and their meanings:

`^ (caret):` Matches the start of a line or string. For example, the pattern "^hello" matches any line or string that starts with "hello".

`$ (dollar):` Matches the end of a line or string. For example, the pattern "world$" matches any line or string that ends with "world".

`\b (word boundary):` Matches the position between a word character (letter, digit, or underscore) and a non-word character (such as a space or punctuation mark). For example, the pattern `"\bcat\b"` matches the word "cat" but not "catalog".

`\B (non-word boundary):` Matches the position between two word characters or two non-word characters. For example, the pattern "l\B" matches "l" in "hello" but not in "cool".

Regex boundaries are useful for specifying precise patterns that occur at specific positions in the input text. They can help you avoid matching unintended patterns and make your regular expressions more precise and efficient.

### Back-references

Regex back-references allow you to refer to previously matched text within a regular expression. They are created by capturing a group of text using parentheses and then referring to that group later in the expression using a backslash followed by the group number. 

For example, the pattern "(cat) \1" matches the string "cat cat" because the first group matches "cat" and the back-reference \1 refers to that same text. Back-references are useful for matching patterns that repeat, such as duplicate words, tags, or parentheses, and can help to make your regular expressions more concise and readable.

### Look-ahead and Look-behind

Regex look-ahead and look-behind are two types of non-capturing groups that allow you to match a pattern only if it is followed or preceded by another pattern, without actually including the look-ahead or look-behind pattern in the match.

Look-ahead is denoted by (?=) and matches a pattern only if it is followed by another pattern. For example, the pattern "foo(?=bar)" matches "foo" only if it is followed by "bar". The look-ahead assertion is a zero-width assertion, meaning that it doesn't consume any characters in the input text.

Look-behind is denoted by (?<=) and matches a pattern only if it is preceded by another pattern. For example, the pattern "(?<=foo)bar" matches "bar" only if it is preceded by "foo". The look-behind assertion is also a zero-width assertion.

Look-ahead and look-behind are powerful tools for matching complex patterns that depend on the context of the input text. They allow you to match patterns that are not directly adjacent to the pattern you are looking for, without including the intervening text in the match. However, they can be less efficient than other regex techniques, and some regex engines do not support all types of look-ahead and look-behind assertions.

## Author

This tutorial was created and written by T.Parker.

 [skwidHubz (GitHub)](https://github.com/skwidhubz)

As a junior developer, I have a strong foundation in programming languages such as HTML, CSS, JavaScript, Node.js, and React. I am passionate about web development and are eager to learn new technologies and tools to build high-quality web applications. I have experience working on both front-end and back-end projects and are comfortable with creating responsive designs and implementing functionality using JavaScript frameworks. I am a team player and enjoy collaborating with other developers to solve complex problems and deliver projects on time. I am always seeking to improve your skills and stay up-to-date with the latest industry trends and best practices in web development.
