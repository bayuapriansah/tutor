Great — since you're using **Nuxt.js**, here's how you can generate a `sitemap.xml` and configure a `robots.txt` file properly:

---

### ✅ 1. Install Sitemap & Robots Modules

If you're using **Nuxt 2**:

```bash
npm install @nuxtjs/sitemap @nuxtjs/robots
```

Then add them to your `nuxt.config.js`:

```js
modules: [
  '@nuxtjs/sitemap',
  '@nuxtjs/robots'
],
```

---

### 📄 2. Configure `sitemap.xml`

In `nuxt.config.js`, add:

```js
sitemap: {
  hostname: 'https://yourdomain.com',
  gzip: true,
  routes: [
    // Optionally define static/dynamic routes manually or use automatic generation
  ]
}
```

This will automatically generate `sitemap.xml` at `https://yourdomain.com/sitemap.xml`

---

### 🤖 3. Configure `robots.txt`

In `nuxt.config.js`, add:

```js
robots: {
  UserAgent: '*',
  Disallow: '',
  Sitemap: 'https://yourdomain.com/sitemap.xml'
}
```

This generates a default `robots.txt` that allows all crawlers and points them to your sitemap.

---

### 📦 4. Build & Deploy

When you run:

```bash
npm run build
npm run generate
```

Nuxt will place `sitemap.xml` and `robots.txt` in the `dist/` folder, ready for deployment.

---

### 📌 Sample robots.txt Output

```
User-Agent: *
Disallow:
Sitemap: https://yourdomain.com/sitemap.xml
```

---
