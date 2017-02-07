---
title: compact
description: Liquid filter that removes nil values from an array.
---

Removes any `nil` values from an array.

For this example, assume `site.pages` is an array of content pages for a website, and some of these pages have an attribute called `category` that specifies their content category. If we `map` those categories to an array, some of the array items might be `nil` if any pages do not have a `category` attribute.


<p class="code-label">Input</p>
{{#raw}}
```liquid
{{map (assign "site_categories" site.pages) 'category'}}

{{#each site_categories as |category|}}
  {{ category }}
{{/each}}
```
{{/raw}}

<p class="code-label">Output</p>
```text
  business
  celebrities

  lifestyle
  sports

  technology
```

By using `compact` when we create our `site_categories` array, we can remove all the `nil` values in the array.

<p class="code-label">Input</p>
{{#raw}}
```liquid
{{compact (map (assign "site_categories" site.pages) 'category')}}

{{#each site_categories as |category|}}
  {{ category }}
{{/each}}
```
{{/raw}}

<p class="code-label">Output</p>
```text
  business
  celebrities
  lifestyle
  sports
  technology
```