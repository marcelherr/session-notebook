# HTML and the web

## Learning Objectives

- understanding client/server communication
- writing HTML code
- knowing about the importance of semantic HTML

---

## How the web works

The world wide web is a network of computers that can exchange information with each other. There
are many different protocols that define the rules on how machines communicate. Browsers use HTTP
(Hypertext Transfer Protocol) to communicate with web servers.

- The URL (Uniform Resource Locator) is the unique address of a resource on the web contains a human
  readable domain name, that needs to be resolved to the technical IP (Internet Protocol) address of
  the web server via a DNS (Domain Name Server)
- The browser sends a **GET** (that's an HTTP method) **request** to load a HTML (Hyper Text Markup
  Language) document from a web server
- The web server sends a **response** containing the document
- Often the HTML code contains references to additional resources (CSS (Cascading Style Sheet)
  files, images, etc.), which the browser then also requests from the server
- The browser **renders** the received content to the screen and makes it interactive
- Browsers might also request additional data from servers later via subsequent **GET** or **POST**
  requests

<img src="./assets/request-response.png" width=600 />

---

## HTML basics

HTML (Hyper Text Markup Language) is used to express text in a structured way. HTML tags indicate
what kind of element is displayed on the website. For example, a headline is written like this:

```html
<h1>I am a headline!</h1>
```

The content considered as headline is wrapped within an **opening tag** and a **closing tag**. The
whole thing is called an **element**.

Elements are nested into each other to create structure and hierarchy.

```html
<h1>I am a <em>headline!</em></h1>
```

Some elements can't contain any other elements and therefore don't have a closing tag. They are
self-closing and called
[_empty elements_](https://developer.mozilla.org/en-US/docs/Glossary/Empty_element).

```html
<hr />
or
<br />
```

### HTML tag attributes

Some elements require some more information in order to work properly. This information is
specified via attributes, for example:

- the source of an image
  ```html
  <img src="logo.png" alt="The logo of the company." />
  ```
- the destination of an anchor element
  ```html
  <a href="https://example.com"> click me </a>
  ```
- the type of an input element
  ```html
  <input type="date" />
  ```

> 💡 The [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes) contain
> detailed information about elements and corresponding attributes.

### Layout of an HTML file

Every HTML document starts with a
[doctype](https://developer.mozilla.org/en-US/docs/Glossary/Doctype) followed by the `<html>`
element, which consists of two main parts:

- The `<head>` contains important meta information for the browser like
  - the charset (utf-8)
  - the favicon displayed in the tab
  - the title of the website
  - CSS and JavaScript files needed for the website
- The `<body>` contains the visible content of the website structured by html elements

```html
<!DOCTYPE html>
<html>
  <head>
    … meta information, additional links to CSS / JavaScript files …
  </head>
  <body>
    … elements displayed on the web page …
  </body>
</html>
```

### List of common HTML elements

| element             | meaning                                                      |
| ------------------- | ------------------------------------------------------------ |
| `<head></head>`     | only once per website, includes meta data and linked files   |
| `<body></body>`     | only once per website, includes the html website content     |
| `<h1></h1>`         | only once per website, a level one heading                   |
| `<h2></h2>`         | a level two heading                                          |
| `<p></p>`           | a paragraph                                                  |
| `<a></a>`           | an anchor (link)                                             |
| `<img>`             | an image (self-closing / empty)                              |
| `<form></form>`     | a form element                                               |
| `<input>`           | an input field (self-closing / empty)                        |
| `<button></button>` | a clickable element equipped with some kind of functionality |

> 💡 A comprehensive [list of all html elements can be found at the MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#inline_text_semantics).

---

## Structuring a Website

Developers have two main tools to express a meaningful structure in a website:

1.  Using semantic HTML elements
2.  Nesting / grouping of HTML elements

### Semantic HTML

Semantic HTML elements not only divide the content of the web page into distinct parts, but also
describe the function or purpose of the elements. This has two major benefits:

- The HTML becomes more understandable for other developers
- Accessibility tools and search engines can interpret the website

Therefore, one should use semantic HTML elements whenever possible.

### List of Semantic HTML elements

| element                 | meaning                                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------- |
| `<main></main>`         | only once per website, includes the main content of the page                                                        |
| `<section></section>`   | a generic standalone section of a document                                                                          |
| `<ul></ul>`/`<ol></ol>` | a list of elements with the same structure, only has `<li>` elements as direct children                             |
| `<nav></nav>`           | a navigation bar                                                                                                    |
| `<aside></aside>`       | element representing a portion of a document whose content is only indirectly related to the main content           |
| `<article></article>`   | representing a self-containing part of the website, which is intended to be independently distributable or reusable |
| `<header></header>`     | representing introductory content, typically a group of introductory or navigational aids                           |
| `<footer></footer>`     | typically contains information about the author of the section, copyright data or links to related documents        |

> 💡 You can find a comprehensive [list of semantic html elements in the MDN web docs](https://developer.mozilla.org/en-US/docs/Glossary/Semantics).

### Nesting HTML elements

Nesting groups elements together in a meaningful way. The element containing the other elements is
called the **parent element**, which contains one or more **child elements**.

The following cases are typical examples of nested elements:

- ```html
  <ul>
    <li>first item</li>
    <li>second item</li>
    <li>third item</li>
  </ul>
  ```
- ```html
  <article>
    <h2>Some headline</h2>
    <p>I am a paragraph…</p>
    <a href="https://www.github.com">a link to another website</a>
  </article>
  ```
- ```html
  <button>
    <img src="arrow.svg" />
    <span> submit </span>
  </button>
  ```

Below is a sketch of how semantic elements can be nested in a web page.<br><br>
<img src="./assets/sectioning-elements.png" width=700 />

## Emmet

Visual Studio Code has a useful tool called Emmet which lets you autocomplete a lot of code by just
typing certain snippets and pressing the <kbd>Tab</kbd> key afterwards. Try these snippets inside an
HTML file and see what happens:

- `!`
- `.highlight`
- `button#red`
- `ul>li.card\*10`

> 💡 You can learn about more Emmet commands in
> [this cheat-sheet](https://docs.emmet.io/cheat-sheet/)

---

## Resources

- [MDN: Introduction to HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)
- [MDN: Getting started with HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)
- [MDN: HTML Elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
- [MDN: Semantic elements: Glossary](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)
- [MDN: HTML attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes)

# Accessibility

## Learning Objectives

In this session you will learn:

- [ ] what accessibility is and why it is important for web developers
- [ ] what the benefits of semantic HTML are
- [ ] how to make code accessible

---

## Accessibility

In Web Development it is important for us to enable as many people as possible to use our Web sites,
even people with disabilities (auditory, visual, neurological, physical, etc.). There is a strong
business case for adapting accessible design:

- We can reach a wider audience (older people, people with disabilities, people with slow internet
  connection).
- Accessible design is important for SEO.
- Accessible design makes websites more usable and improves overall user experience.
- It is required by law in many countries to make your Web sites accessible.

---

## Semantic HTML

Semantic HTML helps screen readers and other assistive technology get useful information on the
structure of a Web site. It is also important for SEO and improves readability of our HTML.

- Use elements like `header`, `nav`, `main`, `article`, `aside`, `footer` to structure every page.
- Use only one `h1` heading per page.
- Do not skip heading levels (use `h1` once, then for the next level of headings use `h2`, for the
  structurally next level of headings use `h3`).

---

## ARIA

ARIA is short for Accessible Rich Internet Applications. It is a set of attributes and roles that
help make Web sites more accessible to people with disabilities.

### ARIA Roles

An ARIA Role is an attribute that can be added to an HTML element. They give semantic meaning to
elements. There are six different categories of roles. Let us briefly look at two categories:

- Document structure Roles like `note` or `tooltip` describe the structure of a section of content.
- Widget Roles like `slider` or `menu` describe the type of element presented on a Web site.

> 💡 A comprehensive list of Roles and their categories can be found in the
> [mdn ARIA Roles docs](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Roles).

### ARIA States and Properties

ARIA states and properties refer to similar features. They provide specific information on elements,
their state and relationship to other elements. Assistive technology like screen readers use them to
present content to users.

> 💡 You can find a list of ARIA states and properties in the
> [mdn ARIA Attributes docs](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes).

Two important ARIA attributes are:

- `aria-label`: Defines a label for an interactive element. Use it when the accessible name of an
  element is missing, for example when a button contains no text but only an icon:

  ```
  <button aria-label="Close" onclick="...">
    <svg ...><path .../></svg>
  </button>
  ```

- `aria-labelledby`: Identifies which element labels the element it is applied to. Some elements
  have a native way of referencing another element with its label (for example input elements and
  label elements which we will come to at a later point in time). If there is no native way to
  reference a labelling element use the aria-labelledby attribute:

  ```
  <nav aria-labelledby="title">
    <h2 id="title">Products</h2>
    ...
  </nav>
  ```

### Accessibility Quick Wins

- Use alt attributes on your images:

```
<img src="..." alt="funny looking cat with hat">
```

- Use high contrast colors so your content is shown clearly on all devices.
- Make sure all your interactive elements have an accessible name
- Use plain and simple language

---

## Resources

- [MDN: Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
- [The A11y Project: Checklist ](https://www.a11yproject.com/checklist/)
- [Web Accessibility Initiative: Introduction to Web Accessibility](https://www.w3.org/WAI/fundamentals/accessibility-intro/)
- [Web Accessibility for Designers](https://webaim.org/resources/designers/)

# HTML Forms

## Learning Objectives

- Understanding the purpose and structure of forms
- Knowing most common types of form fields
- Building useable and accessible forms
- Understanding the different types of buttons
- Understanding client-side form validation
- Understanding the default behavior of form submit

---

## Basic form setup

### `<form>` tag

The `<form>` tag must be wrapped around the complete form with all elements, that are presented as
form controls to the user.

```html
<form>
  <!-- All form elements inside -->
</form>
```

### Form field names

Forms are created to request information from the user. Each fragment of information (each form
field) requires a unique name. It can be set with the `name` attribute and pairs up with the entered
data, when submitting the form.

```html
<input name="first-name" />
```

### Labels

The `<label>` always goes together with a form field. It provides a caption to let users understand,
what kind of data they are asked to enter.

It is required to define, which label and form field belong together. Use the `for` attribute on the
`<label>` and the `id` attribute on the form field. Their values needs to match.

```html
<label for="first-name">First name</label>
<input name="first-name" id="first-name" />
```

> ❗️ Always add a label to a form field. Otherwise users won't understand the purpose of a field,
> which makes it unusable.

> ❗️ Never use the `placeholder` attribute instead of a label.

---

## Different types of form fields

### Text

The default `type` for `<input>` elements is `text`. Choose the `type` based on the kind of data the
user is requested to enter. Use `type="text"` when none of the other types is a better fit.

```html
<label for="first-name">First name</label>
<input type="text" name="first-name" id="first-name" />
```

### Email

Use `type="email"` to let the user enter an email address. The browser can check automatically,
whether the entered text is a valid email address. .

```html
<label for="email-address">Email address</label>
<input type="email" name="email-address" id="email-address" />
```

### Number

Use `type="number"` to let the user enter a number.

```html
<label for="age">Age</label> <input type="number" name="age" id="age" />
```

### Date

Use `type="date"` to let the user enter a date with the help of a date picker (calendar) provided by
the browser.

```html
<label for="date-of-birth">Date of birth</label>
<input type="date" name="date-of-birth" id="date-of-birth" />
```

### Color

Use `type="color"` to let the user enter a color with the help of a color picker tool provided by
the browser.

```html
<label for="favorite-color">Favorite color</label>
<input type="color" name="favorite-color" id="favorite-color" />
```

### Multi-line text

Use the tag `<textarea>` to let the user enter longer text with multiple lines.

```html
<label for="personal-message">Personal Message</label>
<textarea name="personal-message" id="personal-message"></textarea>
```

> ❗️ Please be aware that the `<textarea>` tag is not a self-closing tag like `<input>`.

### Select / dropdown menu

The `<select>` field lets the user choose between different options wrapped into `<option>` tags
that are nested into their parent `<select>` tag - this renders a dropdown menu. Each `<option>` has
a `value` attribute defining the data to be submitted. The option's text presented to the user is
defined between the opening and closing tag.

```html
<label for="billing-plan">Billing plan</label>
<select name="billing-plan" id="billing-plan">
  <option value="weekly">Weekly billing</option>
  <option value="monthly">Monthly billing</option>
  <option value="yearly">Monthly billing</option>
</select>
```

### Radio elements

The `<input type="radio" />` element is another way of presenting a choice with different options to
the user. In many situations it can be used as an alternative to `<select>`.

```html
<input
  type="radio"
  name="billing-plan"
  id="billing-plan-weekly"
  value="weekly"
/>
<label for="billing-plan-weekly">Weekly billing</label>

<input
  type="radio"
  name="billing-plan"
  id="billing-plan-monthly"
  value="monthly"
/>
<label for="billing-plan-monthly">Monthly billing</label>

<input
  type="radio"
  name="billing-plan"
  id="billing-plan-yearly"
  value="yearly"
/>
<label for="billing-plan-yearly">Yearly billing</label>
```

> ❗️ The `name` attribute must be equal among all radio elements that refer to the same choice. The
> browser groups them together and ensures only one radio element can be selected at the same time.

### Checkboxes

In contrast to the radio element, `<input type="checkbox" />` presents individual choices, that are
not related to each other. Each choice can either be "on" ("true") or "off" ("false").

```html
<input type="checkbox" name="accept-data-privacy" id="accept-data-privacy" />
<label for="accept-data-privacy">I accept the data privacy agreement</label>

<input
  type="checkbox"
  name="accept-terms-conditions"
  id="accept-terms-conditions"
/>
<label for="accept-terms-conditions">I accept the terms and conditions </label>
```

> ❗️ The `name` attribute must not be equal among the checkbox elements. They are used to represent
> individual choices.

### More form field types

The different types of `<input>` elements described above is just a small selection. Please refer to
the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input) to see a
complete list of all types with examples.

---

### HTML Form Validation

Before submitting a form, it is important to ensure all required form fields are filled out, in the
correct format. This is called **client-side form validation**.

HTML provides several form field attributes to enable validation features build into the browser.

| Attribute                 | Description                                                                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `required`                | if present, a form field needs to be filled in before the form can be submitted                                                                    |
| `minlength` / `maxlength` | minimum and maximum length of textual data (strings)                                                                                               |
| `min` / `max`             | minimum and maximum values of numerical input types                                                                                                |
| `type`                    | each input type has its own prefigured validation (like `email`)                                                                                   |
| `pattern`                 | [a regular expression pattern](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) the entered data needs to follow |

Example: The following input field is valid if its value exists and it is a string between 3 and 30
characters:

```html
<input
  id="input-name"
  type="text"
  name="name"
  minlength="3"
  maxlength="30"
  required
/>
```

---

### Default Behavior of Form Submit

If you click the submit button of a form, it triggers the following default behavior (which we will change in the future using JavaScript):

- The form sends a GET request with names and their values as prop inside an URL like
  `/?firstName=value1&lastName=value2&...`.
- The page is reloaded and thus the data is lost for us.

---

## Buttons

### Submit button

The default `type` for a `<button>` element is `submit`. It is used to let users submit the form's
data after they filled out all fields.

```html
<button type="submit">Send</button>
```

> 💡 Since it's the default, it would work the same without the type attribute:
> `<button>Send</button>`.

### Reset button

A button with `type="reset"` lets the user reset all form fields to the their default value on
click.

```html
<button type="reset">Reset all fields</button>
```

### Other buttons

Since `type="submit"` is the default for `<button>` elements, buttons outside of a `form` element
should always be defined with `type="button"` to be semantically correct.

```html
<button type="button">Click here for more information</button>
```

This also applies to buttons with diverging functionality within a form.

---

## Form structure and a11y

### Fieldset and Legend

The `<fieldset>` element is used to group multiple fields together. Use the `<legend>` element to
provide a caption for such a group.

```html
<fieldset>
  <legend>Personal information</legend>

  <label for="first-name">First name</label>
  <input type="text" name="first-name" id="first-name" />

  <label for="email">Email address</label>
  <input type="email" name="email" id="email" />
</fieldset>
```

### `aria` labels

#### aria-label

The `aria-label` attribute defines a label for an interactive element. Use it when the accessible
name is missing and there is no content visible in the DOM that can be referenced via the
`aria-labelledby` attribute, e.g. a button with no text but only an icon:

```html
<button aria-label="Close form" onClick="...">
  <svg ...><path ... /></svg>
</button>
```

#### aria-labelledby

The `aria-labelledby` attribute identifies which element labels the element it is applied to. Use
the `id` attribute to create the connection:

```html
<h2 id="title">Personal Information Form</h2>
<form aria-labelledby="title">...</form>
```

#### aria-describedby

The `aria-describedby` attribute allows more verbose information than a label. Use the `id`
attribute to create the connection:

```html
<p id="description">
  We need some personal information about you in order to proceed. Please fill
  in this form so that we can help you.
</p>
<fieldset aria-describedby="description">...</fieldset>
```

---

## Resources

- [`<form>`: The Form element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)
- [`<input>`: The Input (Form Input) element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
- [Forms Tutorial W3C](https://www.w3.org/WAI/tutorials/forms/)
- [Forms (Web Accessibility Guidelines)](http://web-accessibility.carnegiemuseums.org/code/forms/)
