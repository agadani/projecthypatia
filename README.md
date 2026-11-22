# Project Hypatia website

Source for https://projecthypatia.org/ (moved from the Google Site at https://sites.google.com/view/projecthypatia/home).

GitHub Pages builds the site automatically from this repository. Any change committed to the `main` branch is live about a minute later. You can make every edit below directly on github.com: open the file, click the pencil icon ("Edit this file"), make the change, and click "Commit changes".

## Where things are

| What you want to change | File |
|---|---|
| The list of papers | `_data/papers.yml` |
| The list of reading groups | `_data/groups.yml` |
| Home page text | `index.md` |
| "Start a Hypatia Reading Group" page | `start-a-group.md` |
| FAQ | `faq.md` |
| Top menu | `_data/navigation.yml` |
| Header images | `assets/images/` |
| Colors, fonts, spacing | `assets/css/style.css` |

The `.md` files are plain text in [Markdown](https://www.markdownguide.org/basic-syntax/): `**bold**`, `*italic*`, `[link text](https://example.com)`, `## Heading`, and lines starting with `- ` for bullet lists.

## Adding a paper

Open `_data/papers.yml`, find the subfield, and add an entry under its `papers:` list. Copy an existing entry and change it, keeping the same indentation (spaces, not tabs):

```yaml
    - title: "Title of the paper"
      link: "https://link-to-the-paper.pdf"
      authors:
        - name: "A. Author"
          link: "https://en.wikipedia.org/wiki/A_Author"
          highlight: true
        - "B. Coauthor"
        - "C. Coauthor"
      venue: "Name of the conference or journal, 2024."
      note: "Optional extra sentence, e.g. awards."
```

- Authors with `highlight: true` are shown in bold (used for the women authors). Their `link:` is optional.
- Other authors only need their name in quotes, one per line.
- `link`, `venue`, and `note` are optional; leave out any line you don't need.
- `venue` and `note` may contain Markdown links: `"[AAAI](https://aaai.org), 2006."`
- Put every value in double quotes. If the text itself contains a double quote, write it as `\"`.
- Papers appear in the order they are listed in the file.

### Adding a new subfield

Add a block at the level of the other subfields (no indentation before the `-`):

```yaml
- subfield: "Human-Computer Interaction"
  papers:
    - title: "..."
      ...
```

The subfield is added to the list of links at the top of the papers page automatically.

## Adding a reading group

Open `_data/groups.yml` and add an entry at the end:

```yaml
- name: "Name of the group"
  link: "https://group-website-or-mailing-list"
  description: "Optional: institution, meeting time, contact."
```

`link` and `description` are optional.

## If something breaks

If the site stops updating after an edit, the most likely cause is a YAML indentation or quoting mistake. Check the "Actions" tab on GitHub: a failed "pages build and deployment" run shows the file and line number. The previous version of the site stays online until a build succeeds.

## Previewing locally (optional)

Not required for editing. With Ruby and Jekyll installed:

```sh
jekyll serve --baseurl ""
```

then open http://localhost:4000/.
