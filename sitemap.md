Tutorial Sitemap NuxtJs:

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

To **automatically generate routes** for your `sitemap.xml` in **Nuxt 2**, you can rely on the default behavior of `@nuxtjs/sitemap`, which **auto-detects all static and dynamic routes**—as long as you're using Nuxt's **file-based routing** and/or properly configured dynamic routes.

Here’s how to do it:

---

### ✅ 1. Minimal Automatic Sitemap Setup (No `routes` needed)

```js
sitemap: {
  hostname: 'https://yourdomain.com',
  gzip: true,
  trailingSlash: false
}
```

> ✅ You don’t need to define `routes` manually if:
> - You use `pages/` directory to define routes
> - You **generate** your site with `nuxt generate` (SSG/static site)
> - Your dynamic routes are defined via `generate.routes` in `nuxt.config.js` (see next)

---

### ⚙️ 2. For Dynamic Routes (e.g., `/blog/:slug`)

If you have dynamic pages (like `/blog/_slug.vue`), you must provide those manually via:

```js
generate: {
  routes: async () => {
    const res = await axios.get('https://api.example.com/posts')
    return res.data.map(post => `/blog/${post.slug}`)
  }
}
```

Then, sitemap will automatically pick it up. No need to specify `routes` in the `sitemap` config.

---

### Example Full `nuxt.config.js`

```js
export default {
  modules: ['@nuxtjs/sitemap'],
  sitemap: {
    hostname: 'https://yourdomain.com',
    gzip: true
  },
  generate: {
    routes: async () => {
      const res = await axios.get('https://api.example.com/posts')
      return res.data.map(post => `/blog/${post.slug}`)
    }
  }
}
```

---

Would you like help writing this for a specific dynamic route in your app (e.g., blog, product pages)?
