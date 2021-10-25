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

## Installation

To get started:

1. Copy `table.html` to the `layouts/shortcodes` directory.
2. Add a table definition to your [page front matter][front matter] (see
   example).
3. Add a `table` shortcode to your page content which references the
   table definition from the previous step (see example).

## Example

Below is a simple example.

Front matter:
```yaml
---
# ... other front matter omitted ...
tables:
  fruits:
    # table name (optional)
    name: "Fruits"

    # table columns (required)
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

Generated [HTML][], with whitespace added:
```html
<table class='table' title='Fruits' aria-label='Fruits'>
  <thead>
    <tr>
      <th title='The name of the fruit.' aria-label='The name of the fruit.'>
        Name
      </th>

      <th class='has-text-right' title='A brief description of the fruit.' aria-label='A brief description of the fruit.'>
        Text
      </th>
    </tr>
  </thead>

  <tbody>
    <tr data-tr_y='0'>
      <td data-td_x='0' data-td_id='name' title='The name of the fruit.' aria-label='The name of the fruit.'>
        apple
      </td>

      <td data-td_x='1' data-td_id='text' class='has-text-right' title='A brief description of the fruit.' aria-label='A brief description of the fruit.'>
        red
      </td>
    </tr>

    <tr data-tr_y='1'>
      <td data-td_x='0' data-td_id='name' title='The name of the fruit.' aria-label='The name of the fruit.'>
        banana
      </td>

      <td data-td_x='1' data-td_id='text' class='has-text-right' title='A brief description of the fruit.' aria-label='A brief description of the fruit.'>
        <strong>yellow</strong>
      </td>
    </tr>

    <tr data-tr_y='2'>
      <td data-td_x='0' data-td_id='name' title='The name of the fruit.' aria-label='The name of the fruit.'>
        grape
      </td>

      <td data-td_x='1' data-td_id='text' class='has-text-right' title='A brief description of the fruit.' aria-label='A brief description of the fruit.'>
        green
      </td>
    </tr>
  </tbody>
</table>
```

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
