# SvelteKit + PixiJS Template

A template for creating web games or interactive applications using SvelteKit and PixiJS, optimized for static site deployment (e.g., GitHub Pages).

# Preview
https://hamgarian.github.io/sveltePixi-template/

## Features

- 🎮 PixiJS v8 integration
- ⚡ SvelteKit for fast, modern web development
- 📦 Static site generation for easy deployment
- 🎨 TailwindCSS for styling
- 🔧 TypeScript support
- 📱 Responsive design

## Getting Started

### Prerequisites

- Node.js (v18 or later recommended)
- npm or yarn

### Installation

1. Clone this repository:
```bash
git clone <your-repo-url>
cd <your-project-name>
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

### Development

The project structure is organized as follows:

```
src/
├── lib/
│   └── components/
│       └── PixiCanvas.svelte  # Main PixiJS canvas component
├── routes/
│   └── +page.svelte          # Main page
└── app.html                  # HTML template
```

### Building for Production

To build the project for production:

```bash
npm run build
```

The built files will be in the `build` directory.

### Deploying to GitHub Pages

1. Update `svelte.config.js` to use the static adapter:
```js
import adapter from '@sveltejs/adapter-static';
```

2. Add a GitHub Actions workflow (`.github/workflows/deploy.yml`):
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: ['main']

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: 18
      - run: npm install
      - run: npm run build
      - uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: build
```

## Usage

1. Create your game components in `src/lib/components/`
2. Import and use the `PixiCanvas` component in your pages
3. Add your game logic and assets

Example:
```svelte
<script>
  import PixiCanvas from '$lib/components/PixiCanvas.svelte';
</script>

<PixiCanvas />
```

## Customization

- Add your game assets to the `static` directory
- Modify the PixiJS setup in `PixiCanvas.svelte`
- Add more components as needed

## License

MIT

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request
