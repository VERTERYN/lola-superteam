# LOLA Superteam Host Picker

Random & fair host selection for monthly Superteam meetings.

## Setup

### 1. Push files to the repo

Copy `index.html` and `data.json` to the repo root and push:

```bash
cd /path/to/lola-superteam
# copy index.html and data.json here
git add index.html data.json README.md
git commit -m "Initial setup"
git push
```

### 2. Enable GitHub Pages

1. Go to https://github.com/VERTERYN/lola-superteam/settings/pages
2. Under **Source**, select **Deploy from a branch**
3. Branch: `main`, folder: `/ (root)`
4. Click **Save**
5. Wait ~1 minute, your site will be live at: `https://verteryn.github.io/lola-superteam/`

### 3. Create a Personal Access Token (PAT)

1. Go to https://github.com/settings/personal-access-tokens/new
2. Token name: `superteam-picker`
3. Expiration: pick a long duration (or no expiration)
4. **Repository access**: select "Only select repositories" → pick `lola-superteam`
5. **Permissions**: Repository permissions → **Contents**: Read and write
6. Click **Generate token** and copy it

### 4. Configure the app

1. Open the site (https://verteryn.github.io/lola-superteam/)
2. Click **Setup GitHub Connection**
3. Enter:
   - Owner: `VERTERYN`
   - Repo: `lola-superteam`
   - Token: paste your PAT
   - Branch: `main`
4. Click **Save**

The token is stored in your browser's localStorage. Each person who needs to randomize/override must enter the token on their machine once.

## How it works

- **Randomize**: picks a random person from those who haven't hosted yet in the current cycle
- **Override**: swap an assigned host if they're unavailable — the original person returns to the pool
- When everyone has hosted once, a new cycle starts
- All changes are saved as commits to `data.json` in this repo
- Anyone opening the page sees the latest state

## Adding future dates

Edit `data.json` and add entries to the `"upcoming"` array:

```json
{ "date": "2027-01-06", "name": null }
```
