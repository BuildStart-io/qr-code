# QR Code Generator for WhatsApp Bot

A beautiful, modern Vue 3 + Vite application that fetches and displays QR codes for WhatsApp bot authentication.

## Features

- 🎨 **Modern Design**: Beautiful dark theme with gradients and smooth animations
- 📱 **Responsive**: Works perfectly on all devices
- ⚡ **Fast**: Built with Vite for lightning-fast development and builds
- 🔄 **Real-time**: Fetches QR codes from your API endpoint
- 🎯 **User-friendly**: Clear loading states, success messages, and error handling

## Live Demo

Visit the live demo at: [https://buildstart-io.github.io/qr-code/](https://buildstart-io.github.io/qr-code/)

## Local Development

### Prerequisites

- Node.js 18+ and npm

### Installation

1. Clone the repository:
```bash
git clone https://github.com/BuildStart-io/qr-code.git
cd qr-code
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:5173`

### Building for Production

```bash
npm run build
```

The built files will be in the `dist` directory.

## GitHub Pages Deployment

This project is automatically deployed to GitHub Pages using GitHub Actions.

### Setup Instructions

1. **Enable GitHub Pages in your repository**:
   - Go to your repository on GitHub
   - Click on **Settings** → **Pages**
   - Under **Source**, select **GitHub Actions**

2. **Push to main branch**:
   ```bash
   git add .
   git commit -m "your message"
   git push origin main
   ```

3. The GitHub Action will automatically:
   - Build your project
   - Deploy to GitHub Pages
   - Your site will be available at `https://buildstart-io.github.io/qr-code/`

### Manual Deployment

If you need to manually trigger a deployment:
- Go to the **Actions** tab in your repository
- Select the latest workflow run
- Click **Re-run all jobs**

## API Configuration

The app fetches QR codes from: `http://api.sangeethnipun.cf/qrcode`

To use a different API endpoint:
1. Update the proxy configuration in `vite.config.js`
2. Update the fetch URL in `src/App.vue`

## Technologies Used

- **Vue 3** - Progressive JavaScript framework
- **Vite** - Next-generation frontend tooling
- **QRCode.js** - QR code generation library
- **GitHub Actions** - CI/CD automation
- **GitHub Pages** - Static site hosting

## Project Structure

```
qr-code/
├── .github/
│   └── workflows/
│       └── deploy.yml      # GitHub Actions workflow
├── public/
│   └── .nojekyll           # Disable Jekyll processing
├── src/
│   ├── App.vue             # Main application component
│   ├── main.js             # Application entry point
│   └── style.css           # Global styles
├── index.html              # HTML entry point
├── package.json            # Project dependencies
└── vite.config.js          # Vite configuration
```

## License

MIT

## Author

BuildStart.io
