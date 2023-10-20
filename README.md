# CEI

This will be a Python script that reads an `emojis.csv` definition file from working-directory (or parent dirs), and it replaces GH-style "emoji references" (that's how I call them) with the corresponding HTML `<img>` tag. The default global sizes of all emojis is `16em` rather than `2em`, because of the way GH markdown-renderer works.

An [example of the end-product](https://github.com/Rudxain/Rudxain/blob/main/README.md) can be found at my profile.

Despite the fact this script is meant for use in GH, it can also be used to generate HTML files with custom emojis, as the script will be fully format-agnostic (this means both the content-format and filename-extension are ignored). The input text-file to be processed can be in any encoding that Python3 supports, however the **emoji-defs must be UTF-8**.

If you need advanced-management and/or auto-updates for specific file-lists and globs, you'll need `make` and a `makefile`. I won't implement advanced features, as this script is meant to be basic.

## Why?

- It helps you manage/maintain custom emojis for a single file, or an entire directory.
- Reduces bandwith use by ensuring the same exact URL is shared across refs/macros. This has the side-effect of reducing generated cache.
- All inlined `img`s will have the same structure/pattern, which increases compression-ratio.
- Your source text-files can be readable/pretty by using refs, while the macro-expanded files are the only ones with inline-HTML.
- You can change the size of all emojis from a single config field.
- Optionally use a non-default size for specific emojis. **Only do this if you can't resize the origin image** (this is the case if the URL points to a server you don't own)
- Optional `alt` attribute support for accesibility
