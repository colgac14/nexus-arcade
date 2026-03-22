# 🎮 NEXUS ARCADE — 2000 Games Website

A full-featured browser gaming hub with **2000 games**, built entirely with HTML, CSS, and vanilla JavaScript. Deploy it for free on **GitHub Pages** in minutes.

---

## 🚀 Features

- ✅ **2000 games** generated with rich metadata (title, genre, rating, dev, year, etc.)
- ✅ **Search** — filter by name, genre, or developer in real-time
- ✅ **Genre filters** — Action, Puzzle, RPG, Racing, Sports, Strategy, Shooter, Horror, Arcade, Simulation, Fighting + more
- ✅ **Sort** — by Rating, Newest, Oldest, A–Z, Z–A, or Random
- ✅ **Pagination** — 60 games per page, smooth navigation
- ✅ **Game modal** — click any card for full details + play button
- ✅ **Retro neon aesthetic** — scanlines, animated grid, Orbitron font
- ✅ **Zero dependencies** — pure HTML/CSS/JS, no frameworks
- ✅ **Mobile responsive**

---

## 📁 File Structure

```
nexus-arcade/
├── index.html          ← Entire website (single file)
└── README.md
```

---

## 🌐 Deploy to GitHub Pages (Free)

### Step 1 — Create a GitHub repo

1. Go to [github.com](https://github.com) → **New repository**
2. Name it `nexus-arcade` (or anything you like)
3. Set it to **Public**
4. Click **Create repository**

### Step 2 — Upload the files

**Option A — via GitHub web UI:**
1. Click **Add file → Upload files**
2. Drag `index.html` (and `README.md`) into the box
3. Click **Commit changes**

**Option B — via Git CLI:**
```bash
git init
git add index.html README.md
git commit -m "🎮 Launch NEXUS ARCADE"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/nexus-arcade.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. Go to your repo → **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Choose **main** branch and **/ (root)**
4. Click **Save**
5. Your site will be live at: `https://YOUR_USERNAME.github.io/nexus-arcade/`

---

## 🎮 Adding Real Games

Each game card has a **PLAY** button. To link real JavaScript games:

1. Add your game files to the repo (e.g., `games/snake/index.html`)
2. In `index.html`, find the `openModal` function and update the play button `onclick`:

```js
document.getElementById('modalPlay').onclick = () => {
  window.open(`games/${game.slug}/index.html`, '_blank');
};
```

3. Add a `slug` property to each game in the `generateGames()` function.

### Free HTML5 Games to Host
- [OpenGameArt.org](https://opengameart.org)
- [itch.io](https://itch.io) (many free/open source)
- [GitHub search: html5 game](https://github.com/search?q=html5+game&type=repositories)

---

## 🛠️ Customization

### Change the site name
Search for `NEXUS ARCADE` and replace with your brand name.

### Change colors
Edit the CSS variables at the top of `index.html`:
```css
:root {
  --accent:  #00f5ff;   /* Cyan — primary color */
  --accent2: #ff006e;   /* Pink — secondary color */
  --accent3: #a855f7;   /* Purple — genre tags */
  --gold:    #ffd700;   /* Gold — star ratings */
}
```

### Modify game count
Change the `generateGames(2000)` call to any number you want.

### Add real game data
Replace `generateGames()` with a fetch from a JSON file:
```js
const response = await fetch('games.json');
allGames = await response.json();
```

---

## 📄 License

MIT — free to use, modify, and distribute.

---

*Built with ❤️ and JavaScript. No frameworks. No build tools. Just code.*
