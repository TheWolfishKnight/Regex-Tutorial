# HTML Tag Regex Tutorial

Welcome to this tutorial on the HTML tag regex! The purpose of this tutorial is to help you understand how to use the regex `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/` to match HTML tags in a string.

## Summary

The HTML tag regex `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/` matches a string that starts with `<`, followed by one or more lowercase letters, then optionally followed by one or more characters that are not `<`, then either a `>` with content followed by a closing tag with the same name, or a self-closing tag `/>`.

## Table of Contents

- [HTML Tag Regex Tutorial](#html-tag-regex-tutorial)
- [Summary](#summary)
- [Table of Contents](#table-of-contents)
- [Start of Line](#1-start-of-line)
  - [Usage](#usage)
- [Tag Start](#2-tag-start)
  - [Usage](#usage-1)
- [Tag Name](#3-tag-name)
  - [Usage](#usage-2)
- [Tag Attributes](#4-tag-attributes)
  - [Usage Example:](#usage-example)
- [Tag End](#5-tag-end)
  - [Usage](#usage-3)
- [HTML Tag Regex Breakdown](#html-tag-regex-breakdown)
- [Using the HTML Tag Regex](#using-the-html-tag-regex)
- [About the Author](#about-the-author)

##

## 1. Start of Line

The `^` symbol in the regex is used to indicate the start of a line. This is important in ensuring that the pattern only matches at the start of the string and not just anywhere in the string.

The start of line character is often used to make sure that the pattern only matches at the start of a string and not just anywhere within the string. This can be useful in situations where you only want to match a specific pattern at the start of a string, such as matching the start of an HTML tag.

In the case of the HTML tag regex, the `^` symbol helps to ensure that the pattern only matches an HTML tag if it appears at the start of a line. This is an important consideration in HTML parsing, as it helps to prevent partial matches from being returned.

### Usage

The `^` symbol in the regex is used to indicate the start of a line. This is important in ensuring that the pattern only matches at the start of the string and not just anywhere in the string.

The start of line character is often used to make sure that the pattern only matches at the start of a string and not just anywhere within the string. This can be useful in situations where you only want to match a specific pattern at the start of a string, such as matching the start of an HTML tag.

In the case of the HTML tag regex, the `^` symbol helps to ensure that the pattern only matches an HTML tag if it appears at the start of a line. This is an important consideration in HTML parsing, as it helps to prevent partial matches from being returned.

## 2. Tag Start

The `<` symbol in this regex is used to match the start tag of an HTML element. It specifies that the string being matched should start with an opening angle bracket.

This character is crucial in ensuring that the regex only matches actual HTML tags and not just any string that contains angle brackets. It provides a way to distinguish between a string that represents an HTML tag and a string that represents something else entirely.

In the context of this regex, the `<` symbol is used to specify that the string being matched should start with an opening angle bracket. This is the first step in ensuring that the string being matched is a valid HTML tag.

### Usage

The `<` in the regex is used to match the opening angle bracket of an HTML tag. This is an important part of the syntax of an HTML tag, as it signals the start of the tag and defines the tag's type.

Here is an example of how this part of the regex could be used:

```js
const htmlTagRegex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;
const htmlString = "<div>Hello World</div>";

const match = htmlString.match(htmlTagRegex);
console.log(match);
// Output: [ "<div>Hello World</div>", "div", undefined, "Hello World" ]
```

## 3. Tag Name

The `([a-z]+)` part of the regex matches the tag name of the HTML element. It uses a capturing group to capture the tag name into a separate capture group. This capture group is then used later in the regex to ensure that the closing tag matches the opening tag.

### Usage

Here's an example of using the `([a-z]+)` part of the regex to match the tag name of an HTML element:

```javascript
const html = "<h1>Hello, world!</h1>";
const regex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;
const match = html.match(regex);

console.log(match[1]); // Output: "h1"
```

## 4. Tag Attributes

The `([^<]+)*` section of the regex is responsible for matching any characters that are not `<`. This section is enclosed within a capturing group, denoted by the parentheses, and is followed by the `*` symbol. This symbol means that the preceding capturing group is optional and may occur zero or more times.

This section of the regex is used to match any attributes that may be present within an HTML tag. For example, if an HTML tag has an attribute such as `class`, `id`, or `style`, this section will match it.

#### Usage Example:

```javascript
const regex = /^<([a-z]+)([^<]+)(?:>(.)</\1>|\s+/>)$/;
const str = '<div class="container">Content here</div>';

const result = str.match(regex);
console.log(result);
// Output: [
// '<div class="container">Content here</div>',
// 'div',
// ' class="container"',
// 'Content here',
// undefined
// ]
```

## 5. Explanation of `(?:>(.*)<\/\1>|\s+\/>)`

The `(?:>(.*)<\/\1>|\s+\/>)` part of the regex matches the end of an HTML tag. This section of the regex allows for two different scenarios: a closing tag, or a self-closing tag.

In the first scenario, a closing tag is matched with `>(.*)<\/\1>`. The `>(.*)` matches the contents of the tag, while `<\/\1>` matches the closing tag, with `\1` being a reference to the first capture group, `([a-z]+)`. This way, the tag name in the opening and closing tag must match.

In the second scenario, a self-closing tag is matched with `\s+\/>`. The `\s+` matches one or more whitespace characters, while `\/>` matches the self-closing tag syntax.

This section of the regex allows for the matching of the end of an HTML tag, whether it be a closing tag or a self-closing tag.

### Usage

The `(?:>(.*)<\/\1>|\s+\/>)` part of the regex is used to match the end of an HTML tag, and ensure that the syntax is correct. This allows for the verification of properly formatted HTML tags, and can be used in a program to ensure that the HTML code is well-formed.

```javascript
const regex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;
const str = '<div class="container">Hello World!</div>';

let result = str.match(regex);

console.log(result);
// Output: ["<div class="container">Hello World!</div>", "div", " class="container"", "Hello World!"]
```

In this example, the regex is used to match the HTML tag in the string str. The match method is used to test the string against the regex pattern. If a match is found, an array is returned with the first element being the complete match, followed by any capturing groups in the pattern. In this case, the capturing groups are ([a-z]+), ([^<]+)_, and (?:>(._)<\/\1>|\s+\/>).

## 5. Tag End

The `$` symbol at the end of the regex pattern is used to indicate the end of the string. This ensures that the regex pattern will only match strings that end with the pattern specified by the regex.

In the context of this regex pattern, the `$` symbol is used to ensure that the regex only matches complete HTML tags, and not any partial tags or strings that contain an HTML tag.

### Usage

The `$` symbol can be used in any regex pattern to indicate the end of the string. It is often used in combination with the `^` symbol, which indicates the start of the string, to create a regex pattern that matches a complete string.

```javascript
/^Hello.*world!$/;
```

In the context of this HTML tag regex pattern, the `$` symbol is used to make sure that the regex matches complete HTML tags, including both the opening and closing tags, and not just partial tags or strings that contain an HTML tag.

## HTML Tag Regex Breakdown

Let's break down the HTML tag regex to see how it works:

- `^` - Matches the start of the string
- `<` - Matches the character `<`
- `([a-z]+)` - Matches one or more lowercase letters, and captures the match as a group
- `([^<]+)*` - Matches zero or more characters that are not `<`, and captures the match as a group
- `(?:>(.*)<\/\1>|\s+\/>)` - Matches either a `>` with content followed by a closing tag with the same name captured in group 1, or a self-closing tag `/>`
- `$` - Matches the end of the string

## Using the HTML Tag Regex

Now that we understand the structure of the HTML tag regex, let's see how we can use it in code:

```javascript
const htmlString =
  "<html><head><title>Example Page</title></head><body><h1>Hello World!</h1></body></html>";

const htmlTagRegex = /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/;

const match = htmlString.match(htmlTagRegex);

if (match) {
  console.log("The HTML string is a valid tag.");
} else {
  console.log("The HTML string is not a valid tag.");
}
```

In this example, the $ part of the regex is used to match the end of the string being tested. The htmlString variable contains a string that represents an HTML tag. The htmlTagRegex variable contains the regular expression pattern used to match the tag. The match variable is used to store the result of htmlString.match(htmlTagRegex).

If the match is successful, meaning that the HTML string is a valid tag, the code logs "The HTML string is a valid tag." to the console. If the match is unsuccessful, meaning that the HTML string is not a valid tag, the code logs "The HTML string is not a valid tag." to the console.

The $ character in the regex is used to specify that the pattern should match the end of the string. In this case, the pattern must match the entire HTML string, not just a portion of it. This helps to ensure that the tag is properly formatted and complete, with both an opening and a closing tag.

## About the Author

This tutorial was written by TheWolfishKnight. If you want to learn more about regular expressions and other programming topics, be sure to check out my GitHub profile: [TheWolfishKnight on GitHub](https://github.com/TheWolfishKnight).
