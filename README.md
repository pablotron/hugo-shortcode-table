# hugo-shortcode-table

## Introduction

Replacement for the lackluster table syntax in the default [Hugo
Markdown renderer][goldmark].

Features:
* Emits [CSS][] classes for alignment rather than inline `style`
  attributes (no more `unsafe-inline`).
* Table can be defined as [front matter][front matter] or [site data][].
* Column tooltips.
* Cell-specific overrides (alignment, tooltip, etc).
* [HTML][] and [Markdown][] markup support.
* Easy to configure emitted [CSS][] classes for a variety of frameworks,
  including [Bulma][] and [Bootstrap][].

## Example

Below is a simple example.

Front matter:
```yaml
---
# ... other front matter omitted ...
tables:
  fruits:
    # table columns
    cols: 
      - id: "name"
        name: "Name"
        tip: "The name of the fruit."
      - id: "text"
        name: "Text"
        tip: "A brief description of the fruit."
        align: "right" # right-align column

    # table rows
    rows: 
      - name: "apple"
        text: "red"
      - name: "banana"
        text: "**yellow**" # markdown markup
      - name: "grape"
        text: "green"
```

Content:
```markdown
{{/* render fruits table */}}
{{< table "fruits" >}}
```

## Installation

To get started:

1. Copy `table.html` to the `layouts/shortcodes` directory.
2. Add a table definition to your [page front matter][front matter] (see
   below).
3. Add a `table` shortcode to your page content which references the
   table definition from the previous step (see below).

## Documentation

See the [Table Shortcode Examples page][table-shortcode-examples] for
full documentation and examples.

[site data]: https://gohugo.io/templates/data-templates/#the-data-folder
  "Site data directory."
[front matter]: https://gohugo.io/content-management/front-matter/
  "Hugo page metadata."
[css]: https://en.wikipedia.org/wiki/CSS
  "Cascading Style Sheets"
[bulma]: https://bulma.io/
  "Bulma CSS framework."
[bootstrap]: https://getbootstrap.com/
  "Bootstrap CSS framework."
[json]: https://json.org/
  "JavaScript Object Notation"
[yaml]: https://yaml.org/
  "YAML Ain't a Markup Language"
[toml]: https://github.com/toml-lang/toml
  "Tom's Obvious Markup Language"
[hugo]: https://gohugo.io/
  "Hugo static site generator"
[goldmark]: https://github.com/yuin/goldmark/
  "Goldmark Markdown renderer."
[html]: https://en.wikipedia.org/wiki/HTML
  "HyperText Markup Language"
[markdown]: https://en.wikipedia.org/wiki/Markdown
  "Markdown markup language"
[table-shortcode-examples]: https://pablotron.org/articles/table-shortcode-examples/
  "Table shortcode examples."
