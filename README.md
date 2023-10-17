# CEI

This will be a Python script that reads a `emojis.csv` definition file from `$PWD`, and it replaces GH-style "emoji references" (that's how I call them) with the corresponding HTML `<img>` tag. The default global sizes of all emojis is `16em` rather than `2em`, because of the way GH markdown-renderer works.

Despite the fact this script is meant for use in GH, it can also be used to generate HTML files with custom emojis, as the script will be fully format-agnostic (this means both the content-format and filename-extension are ignored). The input text-file to be processed can be in any encoding that Python3 supports, however the **emoji-defs must be UTF-8**
