---
title: transform.Highlight
description: Renders code with a syntax highlighter.
categories: []
keywords: []
action:
  aliases: [highlight]
  related:
    - content-management/syntax-highlighting
    - "getting-started/configuration-markup/#highlight"
    - functions/transform/CanHighlight
    - functions/transform/HighlightCodeBlock
  returnType: template.HTML
  signatures: ["transform.Highlight CODE HIGHLIGHTINGLANGUAGE [OPTIONS]"]
aliases: [/functions/highlight]
toc: true
---

## Usage

Highlight a snippet of source CODE (`string`) with athe given higlighting LANGUAGE (`string`)

```go-html-template
{{ $input := `fmt.Println("Hello World!")` }}
{{ transform.Highlight $input "go" }}
```

Use an option string to configure the result.

```go-html-template
{{ $input := `console.log('Hello World!');` }}
{{ $lang := "js" }}
{{ transform.Highlight $input $lang "lineNos=table, style=api" }}
```

Use an option map to configure the result.

```go-html-template
{{ $input := `echo "Hello World!"` }}
{{ $lang := "bash" }}
{{ $opts := dict "lineNos" "table" "style" "dracula" }}
{{ transform.Highlight $input $lang $opts }}
```

## Options

(`map or string`) A map or space-separate key-value pairs wrapped in quotation marks. Set default values for each option
in your [site configuration]. The key names are case-insensitive.

{{% include "functions/_common/highlighting-options" %}}

[site configuration]: getting-started/configuration-markup/#highlight
