title = "Markdown elements"
excerpt = "Test post that uses every element the site styles."
published = 0
;;
Markdown elements
=================

This draft uses every element that blog posts can produce, so the site's content styles can be
checked in one place. It stays unpublished; view it while signed in to the backend.

## Headings

### Third-level heading

#### Fourth-level heading

##### Fifth-level heading

###### Sixth-level heading

## Text

A paragraph with **strong text**, *emphasised text*, ~~struck-through text~~, `inline code`, a
[link](https://github.com/Sonic-DE) and an autolink <https://sonicde.org>.  
This line follows a hard line break.

Raw inline HTML: <kbd>Ctrl</kbd> + <kbd>C</kbd>, <samp>sample output</samp>, <mark>marked</mark>,
H<sub>2</sub>O, E = mc<sup>2</sup>, <abbr title="Graphical user interface">GUI</abbr>,
<s>struck with s</s>.

---

## Code

```cpp
#include <QTimer>

int main()
{
    QTimer::singleShot(1000, [] { qInfo("A very long line that should scroll horizontally rather than wrap inside the column, so it keeps going and going."); });
}
```

## Quotes

> A quoted paragraph.
>
> > A nested quote.

## Lists

- First item
- Second item
  - Nested item
    - Third-level item
- Third item

3. Ordered list starting at three
4. Next item

- Loose list item one.

- Loose list item two, with its own paragraph.

<dl>
  <dt>Term</dt>
  <dd>Definition of the term.</dd>
</dl>

## Media

![Sample image](images/sample.svg)

<figure>

![Sample image in a figure](images/sample.svg)

<figcaption>A figure with a caption.</figcaption>
</figure>

## Tables

| Left | Centre | Right |
| :--- | :---: | ---: |
| a | b | c |
| A longer cell that makes the table wider | centred | 1.00 |

## Details

<details>
  <summary>Click to expand</summary>

  Hidden content inside a details element.
</details>
