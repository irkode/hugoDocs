---
title: logical path
---

{{< new-in 0.123.0 >}}

A page or page resource identifier derived from the file path, excluding its extension and language identifier. This value is neither a file path nor a URL. Starting with a file path relative to the `content` directory, Hugo determines the logical path by stripping the file extension and language identifier, converting to lower case, then replacing spaces with hyphens. {{% comment %}}<!-- You may also set this value using the `path` front matter field. -->{{% /comment %}} See [examples](/methods/page/path/#examples).

{{% include "/getting-started/glossary/_link-reference-definitions" %}}