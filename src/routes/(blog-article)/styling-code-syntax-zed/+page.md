---
title: Styling code syntax in Zed
slug: styling-code-syntax-zed
coverImage: /images/posts/coding-blog-post.jpg
date: 2024-08-31T13:00:00-06:00
excerpt: How to manage existing blog posts
tags:
    - Zed
keywords:
    - Zed
---

Like VS Code, Zed lets you customize font styling for your code and syntax elements, such as italicizing keywords.

## What does that look like?

Here's an example of a FizzBuzz implementation:

```typescript
function printFizzBuzz(iterations: number) {
  for (let i = 1; i <= iterations; i++) {
    console.log(`${i}: ${getFizzBuzzAnswer(i)}`)
  }
}

// Returns the FizzBuzz string for the input integer.
function getFizzBuzzAnswer(value: number) {
  const isFizz = value % 3 === 0
  const isBuzz = value % 5 === 0
  
  if (isFizz && isBuzz) return "FizzBuzz"
  if (isFizz) return "Fizz"
  if (isBuzz) return "Buzz"
  return value.toString();
}
```

![Zed's default syntax highlighting](/images/posts/zed-default-syntax.png)

The image above shows Zed's default color syntax highlighting for keywords, variables, and types. You can enhance it by applying font weight and italics to specific elements.

## Customizing syntax styles

To customize syntax styles, use the experimental.theme_overrides.syntax setting. Open up Zed's settings (`CMD + ,` or `CTRL + ,`) and add or modify this setting. Let's start by applying a semibold weight to keywords:

```json
{
  "experimental.theme_overrides": {
    "syntax": {
      "keyword": {
        "font_weight": 600
      }
    }
  }
}
```

Once saved, we can immediately see a change in the styling of the keywords:

![Comparing keyword syntax styling in Zed](/images/posts/zed-semibold-keyword.png)

You can also italicize comments and function names, or override the color of elements

```json
{
  "experimental.theme_overrides": {
    "syntax": {
      // ...
      "function": {
        "font_style": "italic"
      },
      "comment": {
        "font_style": "italic",
        "font_weight": 600
      },
      "type": {
        "font_weight": 600
      },
      "punctuation.bracket": {
        "font_weight": 100
      },
      "string": {
        "color": "#ff00b0"
      }
    }
  }
}
```

![alt text](/images/posts/zed-more-examples.png)

## Supported customizations

A list of the tokens supported for highlighting can be found in the [Zed Language extensions documentation](https://github.com/zed-industries/zed/blob/03d8e54fd4e46ba4837bda5b4dcb0e49507c1634/docs/src/extensions/languages.md#syntax-highlighting).

You can customize the following attributes for each of them, although, there appear to be more coming locked behind feature flags currently:

```json
{
  "font_style": "normal" | "italic" | "oblique" | null,
  "font_weight": 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | null,
  "color": "#",
  "background_color": "#"
}
```

It would also be nice to have the ability to customize the font family. [Keep an eye on this GitHub issue](https://github.com/zed-industries/zed/issues/7218) for that feature.
