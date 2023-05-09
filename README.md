<div align="center">
  <h1>The Cairo Programming Language Book</h1>
  <h3> Alexandria </h3>
  <img src="assets/alexandria.jpg" height="400" width="400">
</div>

## Description

This repository contains the source of "The Cairo Programming Language" book, a comprehensive documentation of the Cairo 1 programming language. This documentation is your go-to resource for mastering Cairo, created and maintained by the Starknet community. You can read the book [online](https://cairo-book.github.io/).

<div align="center">
  <h3> Created by builders, for builders 📜</h3>
</div>

## Contribute

### Setup

1. Rust related packages:
   - Install toolchain providing `cargo` using [rustup](https://rustup.rs/).
   - Install [mdBook](https://rust-lang.github.io/mdBook/guide/installation.html) and the translation extension:  
   ```
   cargo install mdbook mdbook-i18n-helpers
   ```
2. Host machine packages:
   - Install [gettext](https://www.gnu.org/software/gettext/) for translations, usually available with regular package manager:  
   `sudo apt install gettext`.
   
3. Clone this repository.

### Work locally (english, main language)

All the Markdown files **MUST** be edited in english. To work locally in english:

   - Start a local server with `mdbook server` and visit [localhost:3000](http://localhost:3000) to view the book.
   You can use the `--open` flag to open the browser automatically: `mdbook serve --open`.
    
   - Make changes to the book and refresh the browser to see the changes.
    
   - Open a PR with your changes.

### Work locally (translations)

This book is targetting international audience, and aims at being gradually translated in several languages.

Translations can be found in `.po` files where the translators only have to translate chunk of texts called `msg`. A message is always identified by a `msgid`, which **MUST NOT** be changed. Only the `msgstr`.

**All files in the `src` directory MUST be written in english**. This ensures that all the translation files can be
auto-generated and updated by translators.

When english text is changed or if you want to work on a translation, those are the step to update the translated content:

   - Run `bash translations_build.sh` to ensure the translations messaged are up to date with the english version.

   - Open the translation file you are interested in `po/fr.po` for instance. You can also use editors like [poedit](https://poedit.net/) to help you on this task.

   - In this process, *unchanged messages* are intact, *deleted messages* are marked as old and can be removed from the po file, and the *updated messages* are marked as fuzzy and must be updated before removing the marker (deleting the line). More information can be found [here](https://en.wikipedia.org/wiki/Gettext) and [here](https://github.com/google/mdbook-i18n-helpers).

   A fuzzy marker looks like this:
   ```
   #: src/page1.md:3
   #, fuzzy   <<<<< HERE. Remove this line when the text is correctly updated or with UI of po editor.
   msgid "A blob of test being translated."
   msgstr "Un bout de text à traduire."
   ```

   - When you are done, you should only have changes into the `po/xx.po` file. Commit them and open a PR.
   The PR must stars with `i18n` to let the maintainers know that the PR is only changing translation.
