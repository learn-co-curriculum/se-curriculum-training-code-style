# Code Style

## Learning Goals

- Use tooling to enforce consistent code style

## Introduction

As with Markdown, we want to ensure as much as possible that any code we present
to students is uniform regardless of who authored it. This is crucial to the
student experience, since encountering inconsistent or unfamiliar syntax from
lesson to lesson can cause students to take their focus away from the learning
objectives.

To that end, we rely as much as possible on tooling to enforce consistency.

Given the number of different languages we teach and the complex rules for code
style, this will always be an area we can improve — if you have suggestions to
bring to the team, this is a great place to contribute!

## Using Prettier

As we saw in the previous lesson, the [Prettier VS Code
extension][prettier extension] is a very helpful tool for automatically
formatting documents based on an opinionated set of rules.

If you use VS Code, and didn't already set this up: Install the Prettier
extension, then include the following configuration in your `settings.json` file
to set it as your editor's default formatter, and (optionally) enable format on
save:

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  // Auto-wrap long lines at 80 characters. https://prettier.io/docs/en/options.html#prose-wrap
  "prettier.proseWrap": "always"
}
```

Prettier is particularly useful because it covers a broad number of languages,
including JavaScript, HTML, CSS, JSON, and Markdown.

It even supports formatting fenced code blocks within Markdown documents, so
long as you identify the language.

We use the default Prettier settings to keep the setup simple. You can read more
about Prettier here:

- [Prettier docs](https://prettier.io/docs/en/index.html)

### Using Prettier with Ruby

There's also a [Prettier plugin for Ruby][prettier ruby]. In general, it works
well, but because Ruby's syntax is much more flexible, it can also introduce
some syntax that our students may not be familiar with. If you use it, make sure
you have a good understanding of the Ruby syntax covered in the curriculum, and
feel free to turn it off when you don't agree with its opinions.

It is also slightly complicated to set up:

- Add `@prettier/plugin-ruby` to the Prettier extension:

```console
# replace x.x.x with the current version number
$ cd ~/.vscode/extensions/esbenp.prettier-vscode-x.x.x
$ npm i -D @prettier/plugin-ruby
```

- Enable the following settings in `settings.json`:

```json
{
  "[ruby]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

## JavaScript Linting with ESLint

[ESLint][eslint] is another tool we can use to identify stylistic issues with
JavaScript code. It's particularly useful for React labs, since we use Create
React App to generate these labs and it comes with some built-in ESLint rules.

As with Prettier, you can use ESLint via a [VS Code extension][eslint extension]
to highlight linting errors.

## Exercise

In this repository, there's a folder `fix-me` with some code from an old React
lesson. Clone this repo, `cd` into the `fix-me` folder, and run `npm install`
(this will install ESLint locally, which is included with the `react-scripts`
library).

Then, check out the `BabyHog.js` file. If you have Prettier configured to format
on save, saving the document will re-format it and fix some style issues. You
also should see the ESLint errors highlighted. Try to fix them before moving to
the next lesson.

## Conclusion

As we expand to support other languages, like Python and Java, it will be
important to identify tools that can enforce consistent style for these
languages as well.

[prettier extension]:
  https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode
[prettier ruby]: https://github.com/prettier/plugin-ruby
[eslint]: https://eslint.org/
[eslint extension]:
  https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint
