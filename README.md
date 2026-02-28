# Snatch Frontend

Fast, lightweight social media video downloader frontend - Built with Astro + React.

## Features

- 🚀 **Fast** - Built on Astro with SSR
- 🎯 **Simple** - Just paste a URL and click download
- 💅 **Modern** - Beautiful UI with Tailwind CSS v4
- 🔒 **Secure** - No data stored, no accounts required

## Supported Platforms

| Platform | Video | Image |
|----------|-------|-------|
| TikTok | ✅ | ✅ |
| X (Twitter) | ✅ | ✅ |
| Instagram | ✅ | ⚠️ |

## Quick Start

### Local Development

```bash
# Install dependencies
bun install

# Copy environment variables
cp .env.example .env
# Edit .env and set RUST_API_URL to your backend URL

# Start development server
bun dev
```

### Deployment

#### Option 1: Cloudflare Pages ⭐ (Recommended)

1. **Configure environment** in `.env.production`:
   ```bash
   RUST_API_URL=https://api.your-domain.com
   ```

2. **Switch to Cloudflare adapter**:
   ```bash
   cp astro.config.cloudflare.mjs astro.config.mjs
   ```

3. **Deploy via Cloudflare Dashboard**:
   - Connect your Git repository
   - Build command: `bun run build`
   - Build output directory: `dist`
   - Environment variable: `RUST_API_URL=https://api.your-domain.com`

4. **Done!** Cloudflare will auto-deploy on every push.

#### Option 2: Docker

```bash
# Build image
docker build -t snatch-frontend .

# Run container
docker run -d -p 4321:4321 -e RUST_API_URL=http://your-api:38701 snatch-frontend
```

#### Option 3: VPS with Node.js

```bash
# Install dependencies
bun install

# Build for production
bun run build

# Run with PM2
npm install -g pm2
pm2 start "node ./dist/server/entry.mjs" --name snatch-frontend
pm2 save
pm2 startup
```

## Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `RUST_API_URL` | Rust API backend URL | `http://localhost:38701` |
| `PORT` | Server port | `4321` |

## Tech Stack

- **Framework**: Astro (SSR)
- **UI**: React + Tailwind CSS v4
- **Package Manager**: Bun
- **Deployment**: Cloudflare Pages / Docker / Node.js

## Scripts

```bash
bun dev          # Start development server
bun build        # Build for production
bun preview      # Preview production build
bun lint         # Lint and fix code
```

## Project Structure

```
snatch-frontend/
├── src/
│   ├── components/     # React components
│   ├── pages/          # Astro pages
│   ├── layouts/        # Layout components
│   └── styles.css      # Global styles
├── public/             # Static assets
├── astro.config.mjs            # Node.js adapter config
├── astro.config.cloudflare.mjs # Cloudflare adapter config
└── package.json
```

## Backend

This frontend requires the [Snatch Backend](https://github.com/youming-ai/snatch-backend) to be running.

## License

MIT
