# hhf

A simple, phone-friendly page listing Waterbear Field School projects at
Hannan Healthy Foods Farm: one card per project, each with a short blurb and
a list of tasks.

`index.html` reads `wfs_projects_edit.md` (a Markdown download of the shared Google
Doc) and builds the cards from it. There's no build step.

The empty `.nojekyll` file matters: it stops GitHub Pages from turning the
`.md` file into an HTML page, which would leave the page with nothing to read.

## Updating the projects

1. In the Google Doc: **File → Download → Markdown (.md)**.
2. Save it here as `wfs_projects_edit.md`, replacing the old one.
3. Commit and push.

How the doc maps to the page:

- **First heading**: the doc's own title. The page ignores it; the page title
  ("WFS Projects at HHF") is set in `index.html`.
- **A heading followed by bullet points**: a project card.
- **A heading with no bullet points under it**: an area (Fields, Hoop Houses,
  …) that groups the cards after it.
- **A paragraph under a project heading**: that card's blurb.
- **Task status**: put `[WORKING]` or `[DONE]` anywhere in a bullet, or use
  Google Docs checklists (checked items show as done). A bullet starting with
  `(Optional)` gets an "Optional" tag.

Headings can be bold lines or real Google Docs headings; both work.

## Adding photos

Put a JPG in `photos/` named after the card, e.g. `photos/structures-coolbot.jpg`.
To see every card's expected filename, open the page with `?photos` on the
end of the URL (`…/index.html?photos`). Filenames turn green once the photo is
found.

Phone photos are large, so shrink them first:

    convert IMG_1234.jpg -auto-orient -resize 1600x1600\> -quality 80 photos/structures-coolbot.jpg

## Previewing locally

Browsers won't let the page read `wfs_projects_edit.md` from a file opened
directly, so use a tiny local server:

    python3 -m http.server
    # then open http://localhost:8000
