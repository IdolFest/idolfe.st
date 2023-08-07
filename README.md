# idolfe.st

A link shortener based on a slightly modified version of [Suri](https://github.com/jstayton/suri).

## Editing

### How to Edit

You can [edit `src/links.json`](https://github.com/NWIdolFest/idolfe.st/edit/main/src/links.json) in your browser.

Each shortlink looks like this:

`"tw": "https://twitter.com/nwidolfest"`

That translates to: "If a user visits `idolfe.st/tw`, redirect them to `https://twitter.com/nwidolfest`.

You'll see curly braces `{}` at the start and end of the file. Don't touch them! All of your edits will happen inside those braces. 

To add a new shortlink:

1. Add a comma `,` to the second-to-last line of the file, which should contain the current last redirect. This indicates that you're about to add a new redirect.
   1. The last redirect should now look something like: `"tw": "https://twitter.com/nwidolfest",`.
   1. The comma goes outside the quotation marks, and before the `}` on the last line.
1. Then, add a new line with the `"shortlink": "redirect"` you want. 
   1. Make sure to use quotes around both the shortlink and the redirect. 
   1. Do *NOT* end the line with a comma. THIS IS SUPER IMPORTANT.
   1. The last redirect should now look something like: `"insta": "https://instagram.com/NWIdolFest"` (note the lack of comma!).
1. Click the green "Commit changes" button. You don't have to change anything about commit message.
1. Wait about 5 minutes for the site to rebuild. On the home screen of the repository, you'll see a little orange dot when it's buiding that will change to a green check mark once it's complete. Then, your link should work.

<img width="893" alt="Finished build" src="https://github.com/IdolFest/idolfe.st/assets/3937986/c4d8b6dc-45d9-4b54-bc71-30bc12549fb2">

*If you see the green check, your shortlink is ready.*

That's it!

### Misc Details

Shortlinks can be as short or as long as you want, using whatever mixture of characters you want. `/` is a special entry for redirecting the root path.

For the redirect URL, you can provide either a full URL (like `http://google.com` or `https://twitter.com/foo`), or a path (like `register` or `hotel`). If you only provide a path, the link shortener will prepend https://nwidolfest.com/ to the path. That means you can type `"reg": "register"` and Suri will create a shortlink to https://nwidolfest.com/register. (You can do `"reg": "https://nwidolfest.com/register"` too, but this way saves you some typing.)

## Development

### Config

Environment variables are used to set config options. There is only one at this
point:

| Variable  | Description                                                        | Values   | Default |
| --------- | ------------------------------------------------------------------ | -------- | ------- |
| `SURI_JS` | Whether to redirect with JavaScript instead of a `<meta>` refresh. | `1`, `0` | `0`     |

### Install Manually

To install Suri somewhere else, or just on your own machine:

1. Fork this repository to create your own copy and clone to your machine.

1. Make sure you have a compatible version of [Node.js](https://nodejs.org/)
   (see `engines.node` in [`package.json`](package.json)).
   [nvm](https://github.com/nvm-sh/nvm) is the recommended installation method
   on your own machine:

   ```bash
   $ nvm install
   ```

1. Install dependencies with npm:

   ```bash
   $ npm install
   ```

1. Build the static site:

   ```bash
   $ npm run build
   ```

1. Deploy the generated `_site` directory to its final destination.

## Development

The following includes a few instructions for developing on Suri. For
11ty-specific details – the static site generator that powers Suri – see their
[docs](https://www.11ty.dev/docs/).

### Install

Follow the "Install Manually" section above to setup on your own machine.

### Start

Start the development server:

```bash
$ npm run dev
```

### Code Style

[Prettier](https://prettier.com/) is setup to enforce a consistent code style.
It's highly recommended to
[add an integration to your editor](https://prettier.io/docs/en/editors.html)
that automatically formats on save.

To run via the command line:

```bash
$ npm run lint
```

## Releasing

After development is done in the `development` branch and is ready for release,
it should be merged into the `master` branch, where the latest release code
lives. [Release It!](https://github.com/release-it/release-it) is then used to
interactively orchestrate the release process:

```bash
$ npm run release
```

![piratepx](https://app.piratepx.com/ship?p=e91ddd1b-31ad-4c36-b03e-be4a1e9a7678&i=suri)
