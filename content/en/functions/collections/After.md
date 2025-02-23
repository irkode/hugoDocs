---
title: collections.After
description: Slices an array to the items after the Nth item.
categories: []
keywords: []
action:
  aliases: [after]
  related:
    - functions/collections/First
    - functions/collections/Last
  returnType: array
  signatures: [collections.After INDEX COLLECTION]
aliases: [/functions/after]
---

## Usage

Get the element _after_ a given position.

```go-html-template
{{ first 2 (slice "one" "two" "three" "four") }} → [ "three" , "four" ]
```

Returns the complete source array if `N` is `0`.

```go-html-template
{{ collections.After 0 (slice "a" "b") }} → [ "a", "b" ]
```

Returns an empty slice for less than `N + 1` elements in the array.

```go-html-template
{{ collections.After 10 (slice "a" "b") }} → []
```

## Examples

### Use after to `range` over a subset of an array

```go-html-template
{{ $data := slice "one" "two" "three" "four" }}
{{ range after 2 $data }}
  {{ . }}
{{ end }}

→ three
→ four
```

### Use together with `first` to get the values in the middle

```go-html-template
{{ $data := slice "one" "two" "three" "four" }}
{{ range first 2 (after 1 $data) }}
  {{ . }}
{{ end }}

→ two
→ three
```

## Advanced Examples // Use cases // ???

### Limit displayed pages utilizing Hugo's [sorting methods](/quick-reference/page-collections/#sort)

Let's assume you have a `section` page at `example.com/articles`. You have 10 articles, but you want your template to show only two rows:

1. The top row is titled "Featured" and shows only the most recently published article (i.e. by `publishdate` in the content files' front matter).
1. The second row is titled "Recent Articles" and shows only the 2nd- to 4th-most recently published articles.

{{< code file=layouts/section/articles.html >}}
{{ define "main" }}
  <section class="row featured-article">
    <h2>Featured Article</h2>
    {{ range first 1 .Pages.ByPublishDate.Reverse }}
    <header>
      <h3><a href="{{ .RelPermalink }}">{{ .Title }}</a></h3>
    </header>
    <p>{{ .Description }}</p>
  {{ end }}
  </section>
  <div class="row recent-articles">
    <h2>Recent Articles</h2>
    {{ range first 3 (after 1 .Pages.ByPublishDate.Reverse) }}
      <section class="recent-article">
        <header>
          <h3><a href="{{ .RelPermalink }}">{{ .Title }}</a></h3>
        </header>
        <p>{{ .Description }}</p>
      </section>
    {{ end }}
  </div>
{{ end }}
{{< /code >}}

[`first`]: /functions/collections/first/
[`slice`]: /functions/collections/slice/
