# LockIn TV Static Website

This is a low-disclosure static website draft for `lockintv.com`.

## Files

- `index.html`: homepage
- `contact.html`: contact page
- `survey.html`: quick product-validation survey with hidden completion timing and optional giveaway follow-up
- `survey_config.js`: survey backend URL config
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

## Survey Storage

The survey page is ready for a Google Sheet backend, but `survey_config.js` needs a Google Apps Script Web App URL before live responses will save to Drive.

Use this script:

```text
C:\Users\friss\Desktop\lockin\business\planning\lockintv_website_survey_sheet_receiver.gs
```

Recommended setup:

1. Sign into the LockIn TV Google account.
2. Go to `https://script.google.com/`.
3. Create a new project.
4. Replace `Code.gs` with `lockintv_website_survey_sheet_receiver.gs`.
5. Run `setupSurveySheet` once and approve permissions.
6. Open logs to get the created spreadsheet URL.
7. Deploy -> New deployment -> Web app.
8. Set `Execute as` to `Me`.
9. Set access to `Anyone`.
10. Copy the Web App URL into `survey_config.js`:

```js
window.LOCKINTV_SURVEY_ENDPOINT = "https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec";
```

The website submits the main survey first. After that, it separately asks whether the user wants to enter the giveaway. The two records are linked by `responseId`.

## GitHub Pages

This folder can be pushed to a GitHub repository and served through GitHub Pages.

## Live Update Checklist

For `lockintv.com`, publish the contents of this `website` folder at the GitHub Pages repository root. The live site needs all of these files/folders:

- `.nojekyll`
- `CNAME`
- `index.html`
- `contact.html`
- `survey.html`
- `survey_config.js`
- `styles.css`
- `assets/lockintv-hero.png`

If the homepage shows the image description text or has no background image, the `assets` folder was not published. If `/survey.html` returns 404, the survey page was not published.

Recommended simple path:

1. Create a new GitHub repository, such as `lockintv-site`.
2. Add these files at the repository root.
3. In GitHub, go to `Settings` -> `Pages`.
4. Set source to the main branch.
5. Point `lockintv.com` DNS to GitHub Pages when ready.
