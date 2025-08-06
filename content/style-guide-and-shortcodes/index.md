---
title: example shourtcode
weight: 5
description: 
---

Welcome to the GitHub repository for Layer5's documentation website!

The docs website is hosted at <https://docs.layer5.io>.

We use [Hugo](https://gohugo.io/) with the [google/docsy](https://github.com/google/docsy) theme for styling and site structure, and [Netlify](https://www.netlify.com/) to manage the deployment of the site.


### Useful docs

* [User guide for the Docsy theme](https://www.docsy.dev/docs/getting-started/)
* [Hugo installation guide](https://gohugo.io/getting-started/installing/)
* [Hugo basic usage](https://gohugo.io/getting-started/usage/)
* [Hugo site directory structure](https://gohugo.io/getting-started/directory-structure/)
* [hugo server reference](https://gohugo.io/commands/hugo_server/)

## Menu structure

The site theme has one Hugo menu (`main`), which defines the top navigation bar. You can find and adjust the definition
of the menu in the [site configuration file](https://github.com/layer5io/docs/blob/master/hugo.toml).

The left-hand navigation panel is defined by the directory structure under the [`content/en` directory](https://github.com/layer5io/docs/tree/master/content/en).

A `weight` property in the _front matter_ of each page determines the position of the page relative to the others in the same directory.
The lower the weight, the earlier the page appears in the section.

Here is an example `_index.md` file:

```md
title = "Getting Started with Layer5"
description = "Overview"
weight = 1
```

## Documentation style guide


### Image styling

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

If you want your image to include a caption for explanation or accessibility, you can use the `<figure>` element:

```html
<figure>
  <img src="./images/example.png" alt="Example description" />
  <figcaption>Example: Control which layers of your design are visible using the Layers panel.</figcaption>
</figure>
```

Using `<figure>` allows you to pair an image with a caption while preserving semantic structure and visual consistency. It's particularly useful for annotated screenshots or UI illustrations.

### Additional resources

* **Bootstrap image utilities:**  
  <https://getbootstrap.com/docs/4.0/content/images/>  
* **Bootstrap utilities (borders, floats, etc.):**  
  <https://getbootstrap.com/docs/4.0/utilities/>  

## Using Hugo shortcodes

Sometimes it's useful to define a snippet of information in one place and reuse it wherever we need it.
For example, we want to be able to refer to the minimum version of various frameworks/libraries throughout the docs,
without causing a maintenance nightmare.

For this purpose, we use Hugo's "shortcodes".
Shortcodes are similar to Django variables. You define a shortcode in a file, then use a specific markup
to invoke the shortcode in the docs. That markup is replaced by the content of the shortcode file when the page is built.

To create a shortcode:

1. Add an HTML file in the `layouts/shortcodes/your-org-uuid` directory.
   The file name must be short and meaningful, as it determines the shortcode you and others use in the docs.

2. For the file content, add the text and HTML markup that should replace the shortcode markup when the web page is built.

To use a shortcode in a document, wrap the name of the shortcode in braces and percent signs like this:

```code
  { {% shortcode-name %}}
```

The shortcode name is the file name minus the `.html` file extension.

**Example:** The following shortcode defines the minimum required version of Kubernetes:

* File name of the shortcode:

  ```
  kubernetes-min-version.html
  ```

* Content of the shortcode:

  ```
  1.8
  ```

* Usage in a document:

  ```
  You need Kubernetes version 1.28 or later.
  ```

The following shortcode defines the minimum required version of Kubernetes:

* File name of the shortcode:

  ```
  kubernetes-min-version.html
  ```

Useful Hugo docs:

* [Shortcode templates](https://gohugo.io/templates/shortcode-templates/)
* [Shortcodes](https://gohugo.io/content-management/shortcodes/)

Whenever any documents reference any source code, you should use the version shortcode in the links, like so:

```
https://github.com/layer5io/docs/blob/master/scripts/gke/deploy.sh
```

This ensures that all the links in a versioned webpage point to the correct branch.

## Markdown

Text can be **bold**, _italic_, or ~~strikethrough~~. [Links](https://gohugo.io) should be blue with no underlines (unless hovered over).

90's four loko seitan photo booth gochujang freegan tumeric listicle fam ugh humblebrag. Bespoke leggings gastropub, biodiesel brunch pug fashion axe meh swag art party neutra deep v chia. Enamel pin fanny pack knausgaard tofu, artisan cronut hammock meditation occupy master cleanse chartreuse lumbersexual. Kombucha kogi viral truffaut synth distillery single-origin coffee ugh slow-carb marfa selfies. Pitchfork schlitz semiotics fanny pack, ugh artisan vegan vaporware hexagon. Polaroid fixie post-ironic venmo wolf ramps **kale chips**.

> There should be no margin above this first sentence.
>
> Blockquotes should be a lighter gray with a border along the left side in the secondary color.
>
> There should be no margin below this final sentence.

## First Header 2

This is a normal paragraph following a header. Knausgaard kale chips snackwave microdosing cronut copper mug swag synth bitters letterpress glossier **craft beer**. Mumblecore bushwick authentic gochujang vegan chambray meditation jean shorts irony. Viral farm-to-table kale chips, pork belly palo santo distillery activated charcoal aesthetic jianbing air plant woke lomo VHS organic. Tattooed locavore succulents heirloom, small batch sriracha echo park DIY af. Shaman you probably haven't heard of them copper mug, crucifix green juice vape _single-origin coffee_ brunch actually. Mustache etsy vexillologist raclette authentic fam. Tousled beard humblebrag asymmetrical. I love turkey, I love my job, I love my friends, I love Chardonnay!

Deae legum paulatimque terra, non vos mutata tacet: dic. Vocant docuique me plumas fila quin afuerunt copia haec o neque.

On big screens, paragraphs and headings should not take up the full container width, but we want tables, code blocks and similar to take the full width.

Scenester tumeric pickled, authentic crucifix post-ironic fam freegan VHS pork belly 8-bit yuccie PBR&B. **I love this life we live in**.

## Second Header 2

> This is a blockquote following a header. Bacon ipsum dolor sit amet t-bone doner shank drumstick, pork belly porchetta chuck sausage brisket ham hock rump pig. Chuck kielbasa leberkas, pork bresaola ham hock filet mignon cow shoulder short ribs biltong.

### Header 3

```
This is a code block following a header.
```

Next level leggings before they sold out, PBR&B church-key shaman echo park. Kale chips occupy godard whatever pop-up freegan pork belly selfies. Gastropub Belinda subway tile woke post-ironic seitan. Shabby chic man bun semiotics vape, chia messenger bag plaid cardigan.

#### Header 4

* This is an unordered list following a header.
* This is an unordered list following a header.
* This is an unordered list following a header.

##### Header 5

1. This is an ordered list following a header.
2. This is an ordered list following a header.
3. This is an ordered list following a header.

###### Header 6

| What      | Follows         |
|-----------|-----------------|
| A table   | A header        |
| A table   | A header        |
| A table   | A header        |

----------------

There's a horizontal rule above and below this.

----------------

Here is an unordered list:

* Liverpool F.C.
* Chelsea F.C.
* Manchester United F.C.

And an ordered list:

1. Michael Brecker
2. Seamus Blake
3. Branford Marsalis

And an unordered task list:

* [x] Create a Hugo theme
* [x] Add task lists to it
* [ ] Take a vacation

And a "mixed" task list:

* [ ] Pack bags
* Don’t forget your passport!
* [ ] Travel!

And a nested list:

* Jackson 5
  * Michael
  * Tito
  * Jackie
  * Marlon
  * Jermaine
* TMNT
  * Leonardo
  * Michelangelo
  * Donatello
  * Raphael

Definition lists can be used with Markdown syntax. Definition headers are bold.

Name
: Godzilla

Born
: 1952

Birthplace
: Japan

Color
: Green

----------------

Tables should have bold headings and alternating shaded rows.

| Artist            | Album           | Year |
|-------------------|-----------------|------|
| Michael Jackson   | Thriller        | 1982 |
| Prince            | Purple Rain     | 1984 |
| Beastie Boys      | License to Ill  | 1986 |

If a table is too wide, it should scroll horizontally.

| Artist            | Album           | Year | Label       | Awards   | Songs     |
|-------------------|-----------------|------|-------------|----------|-----------|
| Michael Jackson   | Thriller        | 1982 | Epic Records | Grammy Award for Album of the Year, American Music Award for Favorite Pop/Rock Album, American Music Award for Favorite Soul/R&B Album, Brit Award for Best Selling Album, Grammy Award for Best Engineered Album, Non-Classical | Wanna Be Startin' Somethin', Baby Be Mine, The Girl Is Mine, Thriller, Beat It, Billie Jean, Human Nature, P.Y.T. (Pretty Young Thing), The Lady in My Life |
| Prince            | Purple Rain     | 1984 | Warner Brothers Records | Grammy Award for Best Score Soundtrack for Visual Media, American Music Award for Favorite Pop/Rock Album, American Music Award for Favorite Soul/R&B Album, Brit Award for Best Soundtrack/Cast Recording, Grammy Award for Best Rock Performance by a Duo or Group with Vocal | Let's Go Crazy, Take Me With U, The Beautiful Ones, Computer Blue, Darling Nikki, When Doves Cry, I Would Die 4 U, Baby I'm a Star, Purple Rain |
| Beastie Boys      | License to Ill  | 1986 | Mercury Records | No awards, but this table cell is wide | Rhymin & Stealin, The New Style, She's Crafty, Posse in Effect, Slow Ride, Girls, (You Gotta) Fight for Your Right, No Sleep Till Brooklyn, Paul Revere, Hold It Now, Hit It, Brass Monkey, Slow and Low, Time to Get Ill |

----------------

Code snippets like `var foo = "bar";` can be shown inline.

Also, `this should vertically align` ~~`with this`~~ ~~and this~~.

Code can also be shown in a block element.

```
foo := "bar";
bar := "foo";
```

Code can also use syntax highlighting.

```go
func main() {
  input := `var foo = "bar";`

  lexer := lexers.Get("javascript")
  iterator, _ := lexer.Tokenise(nil, input)
  style := styles.Get("github")
  formatter := html.New(html.WithLineNumbers())

  var buff bytes.Buffer
  formatter.Format(&buff, style, iterator)

  fmt.Println(buff.String())
}
```

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

Inline code inside table cells should still be distinguishable.

| Language    | Code               |
|-------------|--------------------|
| Javascript  | `var foo = "bar";` |
| Ruby        | `foo = "bar"{`      |

----------------

Small images should be shown at their actual size.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg/240px-Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg)

Large images should always scale down and fit in the content container.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg/1024px-Picea_abies_shoot_with_buds%2C_Sogndal%2C_Norway.jpg)

_The photo above of the Spruce Picea abies shoot with foliage buds: Bjørn Erik Pedersen, CC-BY-SA._

## Components

### Alerts

{{< alert >}}This is an alert.{{< /alert >}}
{{< alert title="Note" >}}This is an alert with a title.{{< /alert >}}
{{< alert title="Note" >}}This is an alert with a title and **Markdown**.{{< /alert >}}
{{< alert color="success" >}}This is a successful alert.{{< /alert >}}
{{< alert color="warning" >}}This is a warning.{{< /alert >}}
{{< alert color="warning" title="Warning Title" >}}This is a warning with a title.{{< /alert >}}

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

### embedded deaign



### collapiseable 

<details>
<summary>
Delete a shared design
</summary>

If you delete a shared design that you own:
- People that can view, comment, or edit can make a copy of the design until you permanently delete it.
- To permanently delete the design, click the design in your trash, and click Delete forever. Learn more about deleting designs
</details>


<details>
<summary>4 changes</summary>

- Bump github.com/bradleyfalzon/ghinstallation/v2 from 2.11.0 to 2.16.0 @dependabot (#3556)
- Bump eslint-config-next from 14.2.7 to 15.3.4 in /ui @dependabot (#3713)
- Bump golang.org/x/net from 0.40.0 to 0.41.0 @dependabot (#3711)
- Bump @rjsf/validator-ajv8 from 5.24.10 to 5.24.12 in /ui @dependabot (#3714)
</details>

{{< details summary="这是一个可以折叠的标题" >}}
这里是折叠起来的内容。

可以是列表：
- 第一项
- 第二项
{{< /details >}}


### Footnotes

This is a superscript number for your footnote. [^1]

[^1]: This is a footnote.
