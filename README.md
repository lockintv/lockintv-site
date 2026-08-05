# LockIn TV Static Website

This is a low-disclosure static website draft for `lockintv.com`.

## Files

- `index.html`: homepage
- `contact.html`: contact page
- `styles.css`: shared styling
- `assets/lockintv-hero.png`: generated hero image

## Local Preview

Open this file in a browser:

```text
C:\Users\friss\Desktop\lockin\website\index.html
```

No build step is required.

## Contact Form Note

The contact page currently uses a `mailto:dan@lockintv.com` form. That means it opens the visitor's email app with the message addressed to Dan.

For a true web form that submits directly from GitHub Pages, create a Formspree, Basin, or similar endpoint and replace this line in `contact.html`:

```html
<form action="mailto:dan@lockintv.com" method="post" enctype="text/plain">
```

with the endpoint they provide, for example:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="post">
```

## GitHub Pages

This folder can be pushed to a GitHub repository and served through GitHub Pages.

Recommended simple path:

1. Create a new GitHub repository, such as `lockintv-site`.
2. Add these files at the repository root.
3. In GitHub, go to `Settings` -> `Pages`.
4. Set source to the main branch.
5. Point `lockintv.com` DNS to GitHub Pages when ready.
