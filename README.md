<p align="center">
  <img src="docs/logo.svg" width="100" alt="TopicMentor Mascot Logo" />
</p>

<h1 align="center">TopicMentor HTML to Figma — Pro Dev Tools</h1>

<p align="center">
  <b>Turn any local HTML/CSS file, web snippet, or AI output into native, pixel-accurate, fully editable Figma layers & components.</b><br />
  Includes dedicated presets for <b>Landscape (16:9)</b> and <b>Portrait (9:16)</b> video screens.<br />
  100% Client-Side · Zero URL tracking · Zero subscriptions · Open Source (MIT)
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License: MIT" /></a>
  <a href="https://www.figma.com/plugin-docs/"><img src="https://img.shields.io/badge/Figma-Plugin_API_v1-F24E1E?logo=figma&logoColor=white" alt="Figma Plugin API" /></a>
  <img src="https://img.shields.io/badge/Privacy-100%25_Client--Side-brightgreen.svg" alt="100% Client-Side" />
  <img src="https://img.shields.io/badge/TypeScript-5.7+-3178C6?logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/PRs-welcome-green.svg" alt="PRs Welcome" />
</p>

<p align="center">
  <a href="#key-features">Key Features</a> ·
  <a href="#quick-start">Quick Start</a> ·
  <a href="#viewport-presets">Viewport Presets</a> ·
  <a href="#how-it-works">How It Works</a> ·
  <a href="#privacy--security">Privacy</a> ·
  <a href="#contributing">Contributing</a>
</p>

---

## ⚡ Key Features

- **Pixel-Accurate DOM Capture:** The browser layout engine does the heavy lifting. The plugin measures the rendered DOM and translates boxes, text runs, SVGs, and images into native Figma frames and layers.
- **Video Screen Creation Workflows:** Dedicated 1-click presets for **Landscape** (`1920 × 1080` for YouTube, TV & Desktop) and **Portrait** (`1080 × 1920` for Shorts, Reels, TikTok & Mobile Stories).
- **GitHub Dark DevTools Design System:** Clean, distraction-free interface built using GitHub Primer dark palette (`#0d1117`, commit green `#238636`, and `#30363d` borders).
- **AI Prompt Assistant:** Built-in "Copy AI prompt" button generates prompt templates for Claude, ChatGPT, and v0 so LLMs output clean, self-contained HTML formatted for your exact viewport.
- **Component & Style Generation:** Converts the root frame into a reusable Figma Component at the flick of a switch. Automatically groups up to 40 primary colors into a linked `TopicMentor/` style palette.
- **Local Assets & Folders Support:** Pick standalone `.html` files or point to entire project directories with local images, stylesheets, and custom web fonts.

---

## 🚀 Quick Start

### 1. Clone & Build

Requirements: [Node.js 18+](https://nodejs.org/) and the [Figma Desktop App](https://www.figma.com/downloads/).

```bash
# Clone the repository
git clone https://github.com/your-username/topicmentor-html-to-figma.git
cd topicmentor-html-to-figma

# Install dependencies and compile TypeScript
npm install
npm run build
```

### 2. Load into Figma Desktop

1. Open the **Figma Desktop App** and open any design draft.
2. Click the Figma menu (☰) in the top-left → **Plugins** → **Development** → **Import plugin from manifest…**
3. Select `manifest.json` from this repository.
4. Run **TopicMentor HTML to Figma — Pro Dev Tools** from your Development plugins menu.

*(Optional)* Run the TypeScript compiler in watch mode during development:
```bash
npm run watch
```

---

## 📐 Viewport Presets

The plugin provides instant segmented viewports optimized for digital design and social video screens:

| Preset | Dimensions | Aspect Ratio | Primary Use Case |
| :--- | :--- | :--- | :--- |
| **Desktop** | `1440 × 1024 px` | ~1.4:1 | Standard Web & Dashboard layouts |
| **Laptop** | `1280 × 832 px` | ~1.5:1 | Compact laptops & MacBook Air displays |
| **Tablet** | `768 × 1024 px` | 3:4 | iPad / Tablet portrait apps |
| **Mobile** | `390 × 844 px` | ~9:19.5 | Modern smartphones (iPhone 14/15/16) |
| **Landscape** | `1920 × 1080 px` | **16:9** | **Full HD Video, YouTube, Presentation Slides** |
| **Portrait** | `1080 × 1920 px` | **9:16** | **Vertical Video, Shorts, Reels, TikTok, Stories** |
| **Letter** | `816 × 1056 px` | Print | US Letter documents (96 DPI) |
| **Custom** | `100` – `4000 px` | Flexible | User-defined custom dimensions |

---

## 🔍 How It Works

```
HTML/CSS Input
   │
   ▼
Sandboxed Browser Render (ui.html iframe)
   │  • Resolves web fonts & remote images
   │  • Executes CSS Grid / Flexbox calculations
   ▼
DOM Measurement Engine
   │  • Walks the DOM tree & computes absolute bounding boxes
   │  • Extracts text runs, line breaks, gradients, shadows & SVGs
   ▼
Figma SceneNode Builder (code.ts)
   │  • Maps boxes to native FrameNodes and ComponentNodes
   │  • Loads local/system fonts & links TopicMentor/ color styles
   ▼
Pixel-Perfect Figma Canvas Layers
```

1. **Sandboxed Render:** The plugin UI ([`ui.html`](ui.html)) renders HTML inside an isolated iframe at your target viewport width and height.
2. **Measurement:** It inspects computed styles, geometry, padding, borders, corner radii, and text line breaks.
3. **Figma Construction:** The main thread ([`code.ts`](code.ts)) maps geometry directly into Figma scene nodes, maintaining absolute positioning for visual parity.

---

## 🔒 Privacy & Security

- **100% Client-Side:** Everything runs locally within your Figma sandbox. No third-party servers, backends, accounts, analytics, or trackers are used.
- **No Data Exfiltration:** Your designs and code never leave your machine.
- **Network Permissions:** `manifest.json` requests wildcard network access exclusively so the browser render engine can load web fonts (like Google Fonts) and CDN images referenced in your HTML.

---

## 📁 Repository Structure

```
├── manifest.json       # Figma plugin manifest schema
├── code.ts             # Figma main thread TypeScript source
├── code.js             # Compiled JavaScript bundle for Figma
├── ui.html             # Plugin user interface, sandboxed DOM parser & CSS
├── tsconfig.json       # TypeScript configuration
├── package.json        # Project metadata & build scripts
├── test/               # Automated test suite (check.html)
├── examples/           # Sample HTML test cases (kitchen-sink, tailwind, etc.)
└── docs/               # Visual assets, branding & documentation media
```

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/amazing-feature`)
3. Commit your Changes (`git commit -m 'Add amazing feature'`)
4. Push to the Branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for more information.

Maintained by **TopicMentor**.
