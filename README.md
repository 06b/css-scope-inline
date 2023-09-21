# 🌘 CSS Scope Inline

![cover](https://github.com/gnat/css-scope-inline/assets/24665/c4935c1b-34e3-4220-9d42-11f064999a57)
(Art by [shahabalizadeh](https://www.artstation.com/artwork/zDgdd))

## Why does this exist?

* You want an easy inline vanilla CSS experience without Tailwind CSS.
* Hate creating unique class names over.. and over.. to use once.
* You want to co-locate your styles for ⚡️ [Locality of Behavior (LoB)](https://htmx.org/essays/locality-of-behaviour/)
* You wish `this` would work in `<style>` tags.
* Use all CSS features: [Nesting](https://caniuse.com/css-nesting), animations. Get scoped [`@keyframes`](https://github.com/gnat/css-scope-inline/blob/main/example.html#L86)!
* Only 18 lines. No build step. No dependencies.
* Pairs well with [htmx](https://htmx.org) and [Surreal](https://github.com/gnat/surreal)
* Want fewer layers, less complexity. Are aware of the cargo cult. ✈️

✨ Want to also scope your `<script>` tags? See our companion project [Surreal](https://github.com/gnat/surreal)

## 👁️ How does it look?
```html
<div>
    <style>
        .me { background: red; } /* ✨ .this and .self also work! */
        .me button { background: blue; }
    </style>
    <button>I'm blue</button>
</div>
```
See the [Live Example](https://gnat.github.io/css-scope-inline/example.html)! Then [view source](https://github.com/gnat/css-scope-inline/blob/main/example.html).

## 🌘 How does it work?

This uses `MutationObserver` to monitor the DOM, and the moment a `<style>` tag is seen, it scopes the styles to whatever the parent element is. No flashing or popping. 

This method also leaves your existing styles untouched, allowing you to mix and match at your liesure.

## 🤔 Why consider this over Tailwind CSS?

Use whatever you'd like, but there's a few advantages with this approach over [Tailwind CDN](https://tailwindcss.com/docs/installation/play-cdn), [Twind](https://github.com/tw-in-js/twind), [UnoCSS](https://github.com/unocss/unocss):

* No repeated styles on child elements (no `[&>*]`, no [extracting classes](https://tailwindcss.com/docs/reusing-styles), no groups). It's just CSS!
* No high risk of eventually requiring a build step. It's just CSS!
* Get the ultra-fast "inspect, play with styles, paste" workflow back. It's just CSS!
* No suffering from FOUC (a flash of unstyled content).
* No chance of [deprecations](https://windicss.org/posts/sunsetting.html). 18 lines is infinitely maintainable.
* Zero friction movement of styles between inline and `.css` files. Just replace `.me`
* No special syntax or editor plugins to install- works with the tools you have.
