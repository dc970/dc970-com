# DC970 Site Usage Guide

## Adding a post

Create a new file in `_posts/` named `YYYY-MM-DD-your-title.md`. The date in the filename controls the order posts appear on the home page.

**Front matter** (the block between the `---` lines at the top):

```yaml
---
title: "Your Post Title"
date: 2026-06-01
category: announcement
---

Your content here in Markdown.
```

### Categories

| Category       | Badge color | Use for |
|----------------|-------------|---------|
| `announcement` | Cyan        | Upcoming meeting details, venue, agenda |
| `news`         | Green       | Security news roundups, CVE highlights, research links |
| `meeting`      | Purple      | Recaps and notes from a past meeting |
| `ctf`          | Yellow      | CTF writeups and challenge walkthroughs |

Each category renders as a neon-outlined badge on the home page and post header.

### Content formatting

Posts are written in standard Markdown:

```markdown
## Section heading

Regular paragraph text. **Bold**, _italic_, `inline code`.

- Bullet list item
- Another item

[Link text](https://example.com)
```

Code blocks with syntax highlighting:

````markdown
```python
print("hello")
```
````

---

## Publishing

Once your post file is committed and pushed to `main`, GitHub Actions automatically builds and deploys the site. No other steps are needed.

If you are not pushing directly to `main`, open a pull request — the site deploys once the PR is merged.

**Typical workflow:**

```bash
# 1. Create your post file
# 2. Stage and commit
git add _posts/2026-06-01-your-title.md
git commit -m "Add June meeting announcement"

# 3. Push
git push origin main
```

The site is usually live within a couple of minutes of pushing.

---

## Updating an existing post

Edit the file in `_posts/` and push. The deploy triggers automatically, same as adding a new post.

Do not change the filename — the filename slug becomes part of the post's URL. Changing it will break any existing links to that post.

---

## Local preview

Requires Docker Desktop running.

```powershell
# Start the local dev server
docker compose up -d

# Open http://localhost:4000 in a browser
# The site auto-refreshes when you save a file

# Stop when done
docker compose down
```

Logs (useful if something looks wrong):

```powershell
docker compose logs -f jekyll
```
