# Svelte + TS + Vite + PWA + tailwind

npm create vite@latest
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
npx tailwindcss init tailwind.config.cjs -p
npm install -D vite-plugin-pwa


upload tailwind config

```ts
/** @type {import('tailwindcss').Config} */
export default {
  content: ['./src/**/*.{html,js,svelte,ts}'],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Vite config 
```ts
import { defineConfig } from 'vite'
import { svelte } from '@sveltejs/vite-plugin-svelte'
import { VitePWA } from 'vite-plugin-pwa'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    svelte(),
     VitePWA(
      {
        workbox: {
          globPatterns: ['**/*.{js,css,html,svg,png,woff2}'],
        },
        registerType: "autoUpdate",
        manifest: {
          "background_color": "#ffffff",
          "theme_color": "#7E1F86",
          "name": "appname",
          "short_name": "appname",
          "start_url": "/",
          "display": "standalone",
          "icons": [
            {
              "src": "pic.png",
              "sizes": "1000x1000",
              "type": "image/png",
              "purpose": "maskable any"
            }
          ]
        }
      })],
})
```