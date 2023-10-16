# CEI - :B: => <🅱️>
> [!note]
> This is unimplemented

This will be a program that parses a "definitions-file" from working-directory (or parent dirs), and it replaces GH/Discord-style "emoji references" (AKA ["short-codes"](https://emojipedia.org/shortcodes)) with the corresponding HTML `<img>` element.

> [!warning]
> Beware of [hot-linking](https://en.wikipedia.org/wiki/Inline_linking)!
>
> It's not just rude and [unstable](https://en.wikipedia.org/wiki/Link_rot), it can be a security risk!
> Also [SVGs can contain scripts](https://github.com/Rudxain/custom-emoji-inliner/issues/3)

The default global sizes of all emojis is `16em` rather than `2em`, because of how GH's markdown-renderer works. An [example end-product can be found at my profile](https://github.com/Rudxain/Rudxain/blob/main/README.md).

For convenience, the program will provide [its own (built-in) emoji pool/name-space/library](cei-def.tsv), which contains commonly used emojis such as lang-logos and mascots. 3rd-party defs have precedence over built-in, so you can easily override any def with your preferred URI.

It's designed for MarkDown, but it can be used to generate HTML files with custom emojis (although this might **completely break** your HTML if you aren't careful), as it'll be fully format-agnostic (content-format and filename-extension are irrelevant). However, the input text-file to be processed and the emoji-defs must be UTF-8.

If you need advanced-management and/or auto-updates/hot-reloading for specific file-lists and globs, you'll need `make` and a make-file. I won't implement advanced features, as this program is meant to be "basic".

## Name
- "custom": Because it supports anything that can be considered an emoji, regardless if it's "officially-Unicode" or made-up.
- "emoji": Actually 🤓, it supports any *graphical icon*, not just emojis. But because of how they look when rendered, they [are indeed "emojis" according to WP](https://en.wikipedia.org/wiki/Emoji).
- "inliner": This one packs 2 meanings in 1!
  - it does "variable-inlining" similarly to compilers
  - it literally replaces the "variable" by its value, within a line of text, rather than inserting the `<img>` element on its own line (as usual in HTML).

## Why?
- It helps manage/maintain custom emojis for a single file, or an entire directory. So (similarly to Discord servers) you can have **entire repos** with custom-emojis, and users can copy your defs/macros file to easily post comments with your emojis! (yes! this includes Issues, PRs, and Discussions!)
- Reduces bandwidth use by ensuring the same exact URL is shared across refs/macros. This has the side-effect of reducing generated cache.
- All inlined `img`s will have the same structure/pattern, which can increase compression-ratio.
- Your source text-files can be readable/pretty by using refs, while the macro-expanded files are the only ones with inline-HTML.
- You can change the size of all emojis from a single config field.
- Optionally use a non-default size for specific emojis. **Only do this if you can't resize the origin image** (this is the case if the URL points to a server you don't own)
- Optional `alt` & `title` attributes for accessibility
