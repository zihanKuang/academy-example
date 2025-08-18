---
title: Content Formatting Examples
weight: 5
description: A collection of examples for formatting content, from basic Markdown text to advanced custom components and shortcodes.
draft: true
---

Welcome! This page showcases our Hugo shortcodes and images and Markdown.

{{< alert title="Note" title="Example Page: Not for Production" >}}
This page will not be published in the [production version](https://cloud.layer5.io/academy/) of the site. It is only visible for local preview and serves as a reference. You can safely delete this page from your repository at any time.
{{< /alert >}}

## Image styling

By default, Markdown images are written like this:

```markdown
![Alt text](/path/to/image.png)
```

These are rendered with:
* `max-width: 70%` of the viewport
* `max-height: 80vh` of the viewport height
* centered block layout

This default styling works well for most landscape (horizontal) images. However, if an image is very tall, narrow, or otherwise looks awkward, you can override the default by embedding raw HTML and specifying a custom size:

```html
<img src="./images/example.png" alt="Example description" 
style="max-width: 40vw; max-height: 60vh; display: block; margin: 1rem auto;" />
```

## Using Hugo shortcodes

Shortcodes let you define reusable snippets and embed them in content.

Usage:

```code
  { {% shortcode-name %}}
```

The shortcode name is the file name (minus the `.html`) in `layouts/shortcodes/your-org-uuid`.

## Markdown

Text can be **bold**, _italic_, or ~~strikethrough~~. [Links](https://gohugo.io) have no underline (unless hovered).

> Blockquotes are lighter with a left border.

### Code

```
This is a code block.
```

Inline code like `var foo = "bar";` is supported.

### Lists

Unordered:

* Liverpool F.C.
* Chelsea F.C.
* Manchester United F.C.

Ordered:

1. Michael Brecker
2. Seamus Blake
3. Branford Marsalis

Task list:

* [x] Create a Hugo theme
* [x] Add task lists to it
* [ ] Take a vacation

### Tables

| Artist            | Album           | Year |
|-------------------|-----------------|------|
| Michael Jackson   | Thriller        | 1982 |
| Prince            | Purple Rain     | 1984 |
| Beastie Boys      | License to Ill  | 1986 |

Inline code inside table cells:

| Language    | Code               |
|-------------|--------------------|
| Javascript  | `var foo = "bar";` |
| Ruby        | `foo = "bar"{`     |

----------------

Small images should be shown at their actual size.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg/240px-Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg)

Large images should always scale down and fit in the content container.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg/1024px-Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg)

_The photo above of the Spruce Picea abies shoot with foliage buds: Bjørn Erik Pedersen, CC-BY-SA._

## Components

### Embedded design

```
{{</* meshery-design-embed
  id="embedded-design-c811e9f4-2522-4eb6-b775-7475545356d8"
  src="./embedded-design-deploy-meshery-using-meshery.js"
*/>}}
```

效果如下面：

<!-- Learn more at https://docs.layer5.io/kanvas/designer/export-designs/#exporting-as-embedding -->
{{< meshery-design-embed
  id="embedded-design-c811e9f4-2522-4eb6-b775-7475545356d8"
  src="./embedded-design-deploy-meshery-using-meshery.js"
>}}

### Alerts

{{< alert >}}This is an alert.{{< /alert >}}
{{< alert title="Note" >}}This is an alert with a title.{{< /alert >}}
{{< alert title="Note" >}}This is an alert with a title and **Markdown**.{{< /alert >}}
{{< alert type="success" title="Successful Note">}}This is a successful alert.{{< /alert >}}
{{< alert type="warning" >}}This is a warning.{{< /alert >}}
{{< alert type="warning" title="Warning Title" >}}This is a warning with a title.{{< /alert >}}

### TabPane

{{< tabpane text=true >}}

{{% tab header="Full-sized Logo Example" lang="en" active="true" %}}

When users register through the [Open Organization Invitation Link](https://docs.layer5.io/cloud/identity/organizations/org-management/#using-the-open-organization-invitation-link), they will see the full-sized logo.

{{< /tab >}}

{{% tab header="Logo Mark Example" lang="en" %}}

When logging into Layer5 Cloud on mobile devices, the small logo mark will be displayed.

<img src="./images/example.png" alt="Logo Mark" style="width:50%; height:auto;" />

{{< /tab >}}

{{< /tabpane >}}

### Collapsible

{{< details summary="This is a collapsible title" >}}
This is the collapsed content.

It can be a list:
- First item
- Second item
{{< /details >}}

### Footnotes

This is a superscript number for your footnote. [^1]

[^1]: This is a footnote.
