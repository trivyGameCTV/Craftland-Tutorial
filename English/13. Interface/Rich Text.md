# Rich Text

# Introduction

Rich Text is a form of text that can contain information in various formats. Rich text syntax allows you to define text formatting more flexibly. It can be used in in-game displays, such as text objects, UI text widgets, or floating text.

# Rich Text Formatting

| Rich Text Format | Tag Syntax   | Example                           | Visual Example                                               |
| ---------------- | ------------ | --------------------------------- | ------------------------------------------------------------ |
| Bold             | \[b][/b]     | text<br />\[b]text[/b]            | ![image](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/13-UI/image-20241125151515596.png) |
| Italic           | \[i][/i]     | text<br />\[i]text[/i]            | ![image](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/13-UI/image-20241125151549707.png) |
| Underline        | \[u][/u]     | text<br />\[u]text[/u]            | ![image](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/13-UI/image-20241125151838860.png) |
| Strikethrough    | \[s][/s]     | text<br />\[s]text[/s]            | ![image](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/13-UI/image-20241125151936095.png) |
| Color            | \[color][-]  | text<br />\[FF0000FF]text[-]      | ![image](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/13-UI/image-20241125152041177.png) |
| Superscript      | \[sup][/sup] | text<br />text\[sup]textsup[/sup] | ![image](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/13-UI/image-20241125152311740.png) |
| Subscript        | \[sub][/sub] | text<br />text\[sub]textsub[/sub] | ![image](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/41-RichText/image-20241125152243395.png) |

Rich text supports nesting. For example, if you want to make a piece of text both bold and italicized, you can write it as \[b][i]text\[/i][/b].

# Color Values

When specifying a text color in rich text, you can use one of the following formats:

1. **Hexadecimal RGBA format**: 8 characters long, where each pair represents a channel (red, green, blue, alpha) as a hexadecimal number from 00 to FF (0 to 255). Example: \[FF0000FF] — red is at maximum intensity, green and blue are 0, and the alpha is also at maximum (fully opaque red).

2. **Hexadecimal RGB format**: Similar to RGBA, but only 6 characters (without alpha). The transparency (alpha) is assumed to be FF (fully opaque). Example: \[00FF00] — green is at maximum intensity, red and blue are 0, resulting in fully opaque green.

3. **INT32 format**: An integer between -2147483648 and 2147483647, representing a color value converted from the RGBA format. You can use a script to convert a given color value to its corresponding INT32 representation.
