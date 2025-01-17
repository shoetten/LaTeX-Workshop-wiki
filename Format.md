# Formatting

If you want to format a file on save, you have to set `"editor.formatOnSave": true`. See an [official document](https://code.visualstudio.com/docs/getstarted/settings).

## LaTeX files

Install [latexindent.pl](https://github.com/cmhughes/latexindent.pl) for formatting support if it is not provided by your LaTeX distribution.

### Relevant settings

#### latex-workshop.latexindent.path

Define the path of the `latexindent` executable. If `latexindent` is in the `PATH`, setting this variable to the executable name is fine.

| type     | default value   |
| -------- | --------------- |
| _string_ | `"latexindent"` |

#### latex-workshop.latexindent.args

Define the command line arguments for latexindent. In the addition to the placeholders defined for [recipes](Compile#placeholders), the following placeholders are accepted

- `%TMPFILE%`: The full path of the raw TeX file to be formatted. At this moment you need to use it as an input file of `latexindent`.
- `%INDENT%`: The indent character of the file, typically `\t`, `' '`, `' '`.

**Note**: For the moment the `-c` option requires trailing slash."

| type                 | default value                                                     |
| -------------------- | ----------------------------------------------------------------- |
| _Array_ of _strings_ | `[ "-c", "%DIR%/", "%TMPFILE%", "-y=defaultIndent: '%INDENT%'" ]` |

## Bibtex files

BibTeX files can be formatted either by using the VSCode _Format Document_ or _Format Selection_ commands or by calling one of the following three commands

- `latex-workshop.bibsort`: to sort the file,
- `latex-workshop.bibalign`: to align fields,
- `latex-workshop.bibalignsort`: to perform both at once.

These commands can be accessed through Visual Studio Code's **Command Palette** (default <kbd>ctrl</kbd>+<kbd>shift</kbd>+<kbd>p</kbd> or <kbd>⌘</kbd>+<kbd>shift</kbd>+<kbd>p</kbd>).

Whether to sort the file when calling VSCode formatting commands is set by [`latex-workshop.bibtex-format.sort.enabled`](latex-workshopbibtex-formatsortenabled). When formatting bibtex entries, you can decide to keep the trailing comma of the last field in each entry by setting [`latex-workshop.bibtex-format.trailingComma`](#latex-workshopbibtex-formattrailingComma) to `true`

### Sorting

#### latex-workshop.bibtex-format.sortby

The commands `latex-workshop.bibsort` and `latex-workshop.bibalignsort` will sort a `.bib` file according to an array of sorting keys specified in `latex-workshop.bibtex-format.sortby`. Valid keys are either a bibtex field name (title, author, year, etc.), or `\"year-desc\"` to sort by year in descending order, or `\"key\"` for the entry key, or `\"type\"` for the entry type (article, book, misc, etc.). E.g. `[\"author\", \"year-desc\", \"title\"]`.". For example, set this to `["author", "year-desc", "title"]` to sort by `author`, then `year` in descending order, then `title`

|        Type        | Default Value |
| ------------------ | ------------- |
| _array of strings_ | `[ "key" ]`   |

#### latex-workshop.bibtex-format.handleDuplicates

When sorting BibTeX files, how to handle duplicates that appear. Duplicates are decided by `latex-workshop.bibtex-format.sortby`.

|        Type       |      Default Value       | Possible Values                                                         |
| ----------------- | ------------------------ | ----------------------------------------------------------------------- |
| _enum of string_  | `"Highlight Duplicates"` | `"Ignore Duplicates"`, `"Highlight Duplicates"`, `"Comment Duplicates"` |

#### latex-workshop.bibtex-format.sort.enabled

Sort content when calling VSCode formatter on a .bib file.

|        Type        | Default Value |
| ------------------ | ------------- |
| _boolean_          | `false`       |

### Aligning

The commands `latex-workshop.bibalign` and `latex-workshop.bibalignsort` provide basic alignment of bibliography entries. This action can be configured through the following options.

#### latex-workshop.bibtex-format.tab

What kind of indentation to use before each field.

|       Type       | Default Value |          Possible Values            |
| ---------------- | ------------- | ----------------------------------- |
| _enum of string_ | `"2 spaces"`  | `"2 spaces"`, `"4 spaces"`, `"tab"` |

#### latex-workshop.bibtex-format.surround

Whether to surround each field value in quotation marks or curly braces.

|       Type       |   Default Value  |           Possible Values             |
| ---------------- | ---------------- | ------------------------------------- |
| _enum of string_ | `"Curly braces"` | `"Curly braces"`, `"Quotation marks"` |

#### latex-workshop.bibtex-format.case

Whether to use upper- or lowercase field names. (E.g. `AUTHOR = ...` vs `author = ...`).

|       Type       | Default Value |       Possible Values        |
| ---------------- | ------------- | ---------------------------- |
| _enum of string_ | `"lowercase"` | `"UPPERCASE"`, `"lowercase"` |

### latex-workshop.bibtex-format.trailingComma

Keep the trailing comma of the last field item.

|        Type        | Default Value |
| ------------------ | ------------- |
| _boolean_          | `false`       |
