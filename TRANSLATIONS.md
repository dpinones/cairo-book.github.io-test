   - In this process, *unchanged messages* are intact, *deleted messages* are marked as old and can be removed from the po file, and the *updated messages* are marked as fuzzy and must be updated before removing the marker (deleting the line). More information can be found [here](https://en.wikipedia.org/wiki/Gettext) and [here](https://github.com/google/mdbook-i18n-helpers).

Translations can be found in `.po` files where the translators only have to translate chunk of texts called `msg`. A message is always identified by a `msgid`, which **MUST NOT** be changed. Only the `msgstr`.
