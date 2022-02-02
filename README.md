# Insert Line Number

This extension is used to insert line numbers to the document which is being edited.

> *Note:*
> This extension inserts actual text-based numbers on each line of the document.
> It is typically used for code samples to easily indicate referenced lines.
> It is not suitable for real code file.

![Screenshot](doc/insert-line-number-1.0.0.gif)

## Features

Line numbers can be inserted into the selected lines, or the whole document if there are no lines selected.

Different formats can be selected among multiple predefined formats, which can be defined in the settings.

## Extension Settings

### `InsertLineNumber.formats`

`InsertLineNumber.formats` is defined in `%APPDATA%\Code\User\settings.json` or File > Preferences > Settings (Ctrl + ,). See below for examples.

`InsertLineNumber.formats` is an array of `InsertLineNumberConfig.Format` objects, which have the following properties:

----
#### Property: `start`
Line number of the first line.
##### Default value: `1`
##### Type: `"current" | number`
- `"current"`: Starts from the real current line number.
For example, user selects lines 10-15 in the editor, line numbers 10-15 will be inserted to these lines.
- `number`: Starts from the given number.
For example, when `start` is set to 1, and user selects lines 10-15 in the editor, line numbers 1-6 will be inserted into these lines.

----
#### Property: `align`
Alignment of the line number.
> *Note:*
> The alignment only apply to the formatted number, no matter the prefix and suffix.
> For example, when prefix is `'C_'` and suffix is `':'`, the result may be `'C_1  :'` or `'C_12 :'`.

##### Default value: `"left"`
##### Type: `"left" | "right"`
- `"left"`: Align to the left.
- `"right"`: Align to the right.

----
#### Property: `padding`
Padding *char* to satisfy padding to the width.
##### Default value: `"space"`
##### Type: `"space" | "zero"`
- `"space"`: Pad line numbers with whitespaces.
- `"zero"`: Pad line numbers with 0.

----
#### Property: `width`
Width of each line number.
> *Note:*
> If a line number is longer than the specified width, it won't be truncated.

##### Default value: `"normal"`
##### Type: `"normal" | "alignToLast" | number`
`"normal"`: No padding; keep the line numbers as-is.
`"alignToLast"`: Pad the line numbers to the last (longest) one.
`number`: Pad the line numbers to the given width.

----
#### Property: `prefix`
Prefix would be inserted before the formatted line number.
##### Default value: `""`
##### Type: `string`

----
#### Property: `suffix`
Suffix would be inserted after the formatted line number.
##### Default value: `":  "`
##### Type: `string`

------------


## Example settings
```json
   "InsertLineNumber.formats": [
        {
            "start": 1,
            "align": "right",
            "padding": "space",
            "width": "alignToLast",
            "prefix": "",
            "suffix": ": "
        },
        {
            "start": 1,
            "align": "left",
            "padding": "space",
            "width": "alignToLast",
            "prefix": "",
            "suffix": ": "
        },
        {
            "start": 1,
            "align": "left",
            "padding": "space",
            "width": "normal",
            "prefix": "",
            "suffix": ": "
        },
        {
            "start": "current",
            "align": "right",
            "padding": "zero",
            "width": 6,
            "prefix": "",
            "suffix": ": "
        },
        {
            "start": "current",
            "align": "left",
            "padding": "space",
            "width": 5,
            "prefix": "",
            "suffix": " |     "
        }
    ],
```

**Enjoy!**
