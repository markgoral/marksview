# marksview.com — static site rebuild

This is a standard, host-agnostic rebuild of marksview.com (previously managed
through Weebly on Network Solutions). It's plain HTML/CSS/JS — no proprietary
formats, no build step — so you can edit it in any text editor and upload it
to any host via FTP.

## File structure

```
marksview/
├── index.html            Home page (TimeVerse app)
├── actiontree.html        ActionTree app page
├── tutorial-videos.html   Tutorial videos page
├── privacy-policy.html    Privacy policy page
├── contact.html           Contact form page
├── css/
│   └── style.css          All site styling
├── js/
│   └── main.js            Mobile nav menu toggle
└── images/
    └── README.txt         List of image files to add (see below)
```

## 1. Add the images

The old site's 7 images couldn't be downloaded automatically. Open
`images/README.txt` for the exact list of filenames and where to grab them
from the old site (or your own copies), then drop them into the `images/`
folder. The HTML already points to the correct filenames, so nothing else
needs to change.

## 2. Set up the contact form (Formspree)

The old Weebly contact form used Weebly's built-in backend, which won't exist
once you move hosts. `contact.html` is wired up to use **Formspree**
(https://formspree.io), a free service that emails you form submissions
without needing your own server:

1. Go to https://formspree.io and sign up for a free account.
2. Create a new form and copy the form ID it gives you (looks like
   `https://formspree.io/f/abcd1234`).
3. Open `contact.html`, find this line near the top of the form:

   ```html
   <form class="contact-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

4. Replace `YOUR_FORM_ID` with your real form ID.
5. Formspree will ask you to confirm your email the first time a message is
   submitted — check your inbox after a test submission.

If you'd rather not use a third-party service, you can instead change the
form to a simple `mailto:` link — just let me know and I can swap it in.

## 3. Preview locally

Just open `index.html` in a browser to check things over. All links between
pages are relative, so it works straight from the folder with no server
needed.

## 4. Upload via FTP

Upload the entire `marksview` folder's contents (not the folder itself) to
your new host's web root (often `public_html` or `www`), keeping the same
folder structure (`css/`, `js/`, `images/` alongside the `.html` files).

## Notes

- Fonts use the system font stack (no external font files or CDN
  dependencies), so the site renders consistently without extra downloads.
- The design keeps all the original text content but uses a refreshed,
  responsive layout (works on mobile via the hamburger menu).
- App Store links point to the same URLs as the original site
  (`appstore.com/TimeVerse`, `appstore.com/ActionTree`) — replace with direct
  App Store IDs if you have them.
