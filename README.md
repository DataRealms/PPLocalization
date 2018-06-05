# Foreword

Firstly, thank you for your interest in localising Planetoid Pioneers!

This file should help you understand how to undergo providing translations for
the game. If any instruction is unclear, please get in touch with someone from Data
Realms before undergoing any translation - this will save wasted time and work!

# File Setup

Each locale is represented with a json file. The list of locales to be loaded
is included in the file `index.json`. You will need to add a new locale here
for it to become present in the game.

Each locale filename is of the form `XX.json`, where `XX` is the 2 character
ISO 639-1 id of the language. This is the same id used in `index.json` to
specify the locale, and is used by the game to identify the locale as well,
for saving the selected locale and swapping locales at runtime.

Each locale file contains an info section, and a translation section.

The info section contains an ID, an english name, and a localised name.

	"info" : {
		"id": "en",
		"english_name": "English",
		"localised_name": "English"
	}

- `id` is the ISO 639-1 id of the language (again).
- `english_name` is the english language version of the language name.
	This is to help developers see at a glance what the file contains if
	they are unfamiliar with the ISO 639-1 codes.
- `localised_name` is the own-language version of the language name.
	This is displayed in the menu to the user.

The translations section contains a map of english strings and locale-agnostic
string IDs, to their localised content.

More information on the precise specification of these can be found below in
the section **Sourcing Translation Strings**.

# File Format and Encoding

Comments (both `//` and `/* */` form) and trailing commas are allowed in the json files.

UTF8 encoding is used for all files.

# Sourcing Translation Strings

`en.json` is the master list for translations. Other translations should be based
on this file, and any new strings to be translated should be put here first.

Translators should add a translation for each entry found in `en.json`

If the english file has empty content for an entry, the translation should be
based on the entry ID itself (ID is content).

If the english file _does_ have content (for example, see the modal section),
translation should be based on the english file content, as the entry ID is
only an ID, and is not displayed to the user.

Any content {IN BRACKETS} should be preserved verbatim - it is used
to position replacements. The replacements themselves may be
localised separately, or may be something like a number or username.
This allows each translation to be adapted to the native grammar
without too much effort.

Note: this only applies to brackets in _content_ - entry IDs as
described above are also in brackets, but should not be preserved.

# Language Difference Considerations

If you encounter trouble translating a certain phrase or formulation to
your language, let us know. Changes can be made before to accomodate
differences between languages - we can either provide a special ID,
or rework how the string is formed altogether.

# Representation Considerations

If you need to use quotations or line breaks within translations,
these must be "escaped" with a backslash. Failure to do so will
result in an error loading the locale file.

	\" for quotes
	\n for line breaks

HTML entities such as <, > and & must also be escaped or they will
disrupt UI layout. They should be replaced with their html escaped
form.

	&lt; for <
	&gt; for >
	&amp; for &.

Avoid using any "creative" unicode space or layout characters, such as
zero width spaces or similar.

Any other characters should work fine. If you encounter issues, please
get in touch.
