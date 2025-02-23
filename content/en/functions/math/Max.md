---
title: math.Max
description: Returns the greater of all numbers. Accepts scalars, slices, or both.
categories: []
keywords: []
action:
  aliases: []
  related:
    - functions/math/Min
  returnType: float64
  signatures: [math.Max VALUE...]
---

## Usage

Get the maximum of a list of numbers

```go-html-template
{{ math.Max 2 4 6 }} → 6
{{ math.Max 1 (slice 2 6) 4 }} → 6
```

Returns 0 for an empty slice.

```go-html-template
{{ math.Max slice }} → 0
```

## Examples:

* Use a conditional to handle empty input arrays.

  > ```go-html-template
  > {{ if $slice }}
  >   {{ $max = math.Max $slice }}
  > {{ else }}
  >   {{ errorf "Empty slice as input to math.Max" }}
  > {{ end }}
  > ```
```
