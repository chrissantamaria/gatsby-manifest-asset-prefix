# gatsby-plugin-manifest asset prefix bug

This repo displays a bug with gatsby-plugin-manifest not properly prefixing the manifest `<link>` when an asset prefix is set.

## Reproduction Steps

1. Clone the repo
2. Install dependencies:

```bash
yarn
```

3. Create a production build:

```bash
yarn build
```

4. Check the resolved `href` of a normal static asset (ex: `app-data.json`) and notice that it's correctly prefixed:

```bash
$ npx prettier public/index.html | grep "app-data.json"
      href="https://cdn.example.com/page-data/app-data.json"
```

5. Check the href of the generated manifest and notice that it's not prefixed:

```bash
$ npx prettier public/index.html | grep "manifest.webmanifest"
    <link rel="manifest" href="/manifest.webmanifest" crossorigin="anonymous" />
```