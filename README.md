# Portfolio site with a built-in editor

Three files make up the site:

- `index.html` is the public portfolio. It reads everything from `data.json`.
- `data.json` holds your content (name, about, links, projects, skills, accent colour).
- `admin.html` is the editor. It updates `data.json` in your repository through the GitHub API.

## Publish it

1. Create a new **public** repository on GitHub. Name it `your-username.github.io` for a site at the root address, or use any name for `your-username.github.io/name`.
2. Upload `index.html`, `admin.html` and `data.json` to the repository root.
3. Go to **Settings → Pages**. Under *Build and deployment*, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. After a minute, your site is live at the address GitHub shows on that page.

## Set up the editor (once)

1. Open <https://github.com/settings/personal-access-tokens/new>.
2. Under *Repository access*, choose **Only select repositories** and pick your portfolio repository.
3. Under *Repository permissions*, set **Contents** to **Read and write**. Generate the token and copy it.
4. Open `https://your-site-address/admin.html`. Your username and repository are filled in automatically. Paste the token, edit your content and click **Save to GitHub**.

GitHub rebuilds the site about a minute after each save.

## Things to know

- **Why a token?** GitHub Pages only serves static files, so the editor has to commit changes through GitHub's API. Each save creates a normal commit in your history, so you can always roll back.
- **Is `admin.html` safe to leave public?** Yes. It can't change anything without your token. Anyone who finds the page sees only an empty connection form.
- **Token storage.** The token stays in your browser and is sent only to `api.github.com`. It is saved on the device only if you tick *Remember these details*. Use a token limited to this one repository and give it an expiry date.
- **No token?** Use **Download data.json** in the editor, then upload the file to your repository by hand.
- **Preview locally.** Opening `index.html` directly from disk can't load `data.json`. Run `python -m http.server` in the folder and visit <http://localhost:8000>.
