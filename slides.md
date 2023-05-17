---
theme: ./
author: 'Ania Karoń'
position: 'Web Accessibility Specialist'
position2: 'and Senior Frontend Developer'
email: 'anna.karon@snow.dog'
profilePicture: 'anna-karon-photo.jpg'
linkedin: 'https://www.linkedin.com/in/anna-karon/'

---

# Accessibility space on frontend

Workshops

---
layout: aboutme
---

---

# Workshops plan


12:00 - 12:15 Introduction

12:15 - 12:35 Testing tools, project installation

12:35 - 13:00 Fixing accessibility: structure and semantic

13:00 - 13:15 Break

13:15 - 14:00 Fixing accessibility: components

14:00 - 14:15 Break

14:15 - 14:45 Testing

14:45 - 15:00 Summary


---
layout: center
class: "text-center"
---

# Accessibility space

## How we work?

Repo: [https://github.com/anqaka/a11y-space](https://github.com/anqaka/a11y-space)

Website: [A11y space](https://a11y-space.vercel.app/)

<div>&nbsp;</div>

### Tech stack:

[Astro.build](https://astro.build/)

HTML, [Tailwindcss](https://tailwindcss.com/), JS/TS

Deployment: Vercel (SSG)


---

# Testing accessibility
<div>&nbsp;</div>

## Automatic tests
* [Axe - browser extension](https://www.deque.com/axe/browser-extensions/)
* [Wave - browser extension](https://wave.webaim.org/extension/)
* [Lighthouse](https://developer.chrome.com/docs/lighthouse/accessibility/)
<div>&nbsp;</div>

## Manual tests
* code review
* [ANDI](https://www.ssa.gov/accessibility/andi/help/install.html)
* Screen readers - VoiceOver (macOS), Narrator or NDVA (Windows), [ChromeVox (browser extension)](https://chrome.google.com/webstore/detail/screen-reader/kgejglhpjiefppelpmljglcjbhoiplfn)


---

# Structure and semantic
<div>&nbsp;</div>

* HTML Doc - RWD, lang, title
* Landmarks: `header`, `main`, `footer`, `section`, `nav`, `aside`
* Semantic HTML: `<p>`, `<ul><li>...</li></ul>`, `<button>`, `<a href="/">`, `<article>`, `<address>`, `<time>` etc...
* Headings - `<h1>` - `<h6>`

---


# Structure and semantic

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Page title</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
  </head>
  <body>
    <header>
      ...
    </header>
    <main>
      <h1>Heading</h1>
      ...
    </main>
    <aside>
      ...
    </aside>
    <footer>
      ...
    </footer>
  </body>
</html>
```

---

# Images and alternative texts
<div>&nbsp;</div>

## Informative images

Informative images convey a simple concept or information that can be expressed in a short phrase or sentence. The text alternative should convey the meaning or content that is displayed visually, which typically isn’t a literal description of the image.

labeling information, supplementing information, conveying an impression or emotion

```xml
<img src="informative-image" alt="alternative text" />
```

---

# Images and alternative texts
<div>&nbsp;</div>

## Functional images

Functional images are used to initiate actions rather than to convey information, ex. in buttons and links

```xml
<a href="/">
  <img src="logo-image" alt="Company logo" />
</a>

<a href="/" aria-label="Homepage">
  <img src="logo-image" alt="Company logo" />
</a>
```

---

# Images and alternative texts
<div>&nbsp;</div>

## Decorative images
Decorative images don’t add information to the content of a page.

```xml
<img src="decorative-image" alt="" aria-hidden="true" />
```

[An alt Decision Tree on WAI Tutorials](https://www.w3.org/WAI/tutorials/images/decision-tree/)

---
layout: two-cols-header
---

# Alternative content

All graphic interactive elements without visible label, should have alternative text

::left::


## aria-label

Add directly on element

```xml
<button type="button" aria-label="Add to cart">
  <svg>Add to cart icon</svg>
</button>
```

[aria-label docs](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label)

::right::

## aria-labelledby

Bind element which serves as a label (ex. heading), using its `id`

```xml
<section type="button" aria-labelledby="section-heading">
  <h2 id="section-heading">Heading section</h2>
</section>
```

[aria-labelledby docs](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-labelledby)

---

# Alternative content

## aria-describedby

For adding additional description (ex. form field, button),Bind element which serves as a description (ex. heading), using its `id`

```xml
<form>
  <label for="fname">First name</label>
  <input aria-describedby="int2" autocomplete="given-name" id="fname" type="text">
  <p id="int2">Your first name is sometimes called your "given name".</p>
</form>
```

[aria-describedby docs](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-describedby)

---
layout: two-cols-header
---

# How to hide elements?

**Pozor!** Hide with care and caution. Don't hide crucial elements, like headings, SEO doesn't like it.

::left::

**For everyone**

```css
.element {
  display: none;
  visibility: hidden;
}
```

**For assistive technologies**

`aria-hidden="true"`

```xml
<span class="aria-hidden">Decorative element</span>
```


::right::

**Only visually**

```css
/* Hiding class, making content visible only to screen readers but not visually */
/* "sr" meaning "screen-reader" */

.sr-only:not(:focus):not(:active) {
  clip: rect(0 0 0 0);
  clip-path: inset(50%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}
```

Tailwindcss - `sr-only`


---

# Focus

**`focus` state should be well visible**

* css `outline`, browser provide `focus` state by default, if you don't style focus state, don't remove `outline: none`
* order focusable elements, focus management
* `:focus` i `:focus-visible`

---
layout: image
image: '/photo-snowdog.jpeg'
---


---
layout: two-cols-header
---

# Tabs

<style>
li {
  font-size: 0.875rem;
}
</style>

::left::

**Aria - roles and attributes**

* role=tablist
* role=tab
* role=tabpanel
* aria-selected
* aria-labelledby
* aria-controls


**Keyboard navigation**

* `Tab` - focus active tab
* `Left arrow`, `Right arrow` - move focus between tabs
* `Space` i `Enter` - activate tab
* `Home` (optional) - move focus to the first tab
* `End` (optional) - move focus to the last tab


::right::

```xml
<div>
  <h2 id="heading">Heading</h2>
  <div role="tablist" aria-labelledby="heading">
    <button id="tab-1" type="button" role="tab" aria-selected="true" aria-controls="tabpanel-1">
      <span>Tab 1</span>
    </button>
    <button id="tab-2" type="button" role="tab" aria-selected="false" aria-controls="tabpanel-2" tabindex="-1">
      <span>Tab 1</span>
    </button>
  </div>
  <div id="tabpanel-1" role="tabpanel" aria-labelledby="tab-1">
    <p>
      Content tab 1
    </p>
  </div>
  <div id="tabpanel-2" role="tabpanel" aria-labelledby="tab-3" aria-hidden="true">
    <p>
      Content tab 2
    </p>
  </div>
</div>
```

---
layout: two-cols-header
---

# Dialog

<style>
li {
  font-size: 0.875rem;
}
</style>

::left::

**Aria - roles and attributes**

* role=dialog
* aria-modal
* aria-labelledby
* aria-hidden
* aria-haspopup (trigger)
* aria-expanded (trigger)


**Keyboard navigation**

* `Tab` - focus next focusable element inside a dialogs
* `Shift + Tab` - focus previous focusable element inside a dialogs
* `Escape` - close dialog and move focus back to the page (on trigger if exist)


::right::

```xml
<div
  role="dialog"
  aria-modal="true"
  aria-hidden="true"
  class="dialog"
  aria-labelledby="heading"
>
  <div class="dialog-content" autofocus tabindex="0">
    <h2 id="heading">Heading</h2>
    dialog content
    <button type="button">Close</button>
  </div>
</div>
```

---

# Live regions

* `aria-live` - announces dynamically changed content (set on container)
* `polite` value - informs about changes when AT finish current task
* `assertive` value - informs about changes immediately
* `aria-atomic` - informs about how elements inside live region (container with `aria-live` attr) should be annoounced - only changes: `false` value, all: `true` value



---
layout: thankyou

---
