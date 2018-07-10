# Mkdocs Meta Bug Example

In the [Custom themes](https://www.mkdocs.org/user-guide/custom-themes/) section of the mkdocs site, there is [a section](https://www.mkdocs.org/user-guide/custom-themes/#pagemeta) that says that page meta data can be accessed a certain way:

```
source: generics.py
      mixins.py

# Page title

Content...
```

and that this should map to the `meta.source` variable in the page template:

```html
{% for filename in page.meta.source %}
  <a class="github" href="https://github.com/.../{{ filename }}">
    <span class="label label-info">{{ filename }}</span>
  </a>
{% endfor %}
```

However, when using this exact example, the behavior is not as expected. When the docs compile, each `filename` in `page.meta.source` is just a letter of the string "generics.py mixins.py":

```html
<a class="github" href="https://github.com/.../g">
  <span class="label label-info">g</span>
</a>

<a class="github" href="https://github.com/.../e">
  <span class="label label-info">e</span>
</a>

<a class="github" href="https://github.com/.../n">
  <span class="label label-info">n</span>
</a>

...
```
