<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Recipe Recommendation System

An AI-powered recipe suggestion app that provides personalized meal recommendations based on your preferences, dietary restrictions, and available ingredients. It also finds nearby grocery stores where you can shop for ingredients!

## Features

✨ **AI-Powered Recipes** - Get personalized recipe suggestions from Google Gemini AI  
🥘 **Dietary Restrictions** - Filter recipes by vegetarian, vegan, gluten-free, and more  
🍽️ **Cuisine Preferences** - Choose your favorite cuisine type  
🛒 **Nearby Stores** - Find grocery stores near your location  
📸 **Visual Recipes** - Beautiful recipe images from Unsplash or AI-generated  
💾 **History** - Keep track of your favorite recipes  
🤖 **Recipe Details** - Get full ingredients and cooking instructions  

## Quick Start

### Prerequisites
- Node.js 16+ installed
- A free Google Gemini API key (get one at: https://aistudio.google.com/apikey)

### Installation

1. **Clone/Download this project**

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up your environment:**
   ```bash
   # Copy the example .env file
   cp .env.local.example .env.local
   
   # Edit .env.local and add your Gemini API key
   # GEMINI_API_KEY=your_key_from_https://aistudio.google.com/apikey
   ```

4. **Start the backend server** (in one terminal):
   ```bash
   npm run server
   # Should show: "Backend proxy server listening on http://localhost:4000"
   ```

5. **Start the frontend** (in another terminal):
   ```bash
   npm run dev
   # Should show: "VITE ready" and "Local: http://localhost:3001"
   ```

6. **Open the app:**
   - Open your browser to: http://localhost:3001
   - Or use the local network URL for devices on your network

## Configuration

### Minimum Setup (Required)
Only the Gemini API key is required. Everything else is optional:

```
GEMINI_API_KEY=your_gemini_key
```

### Full Setup (All Features)
See [.env.local.example](.env.local.example) for all available options:

- **Gemini API** (Required) - For AI recipe generation
- **Unsplash API** (Optional) - For recipe images
- **TomTom API** (Optional) - For finding nearby stores
- **OpenAI API** (Optional) - For DALL-E image generation
- **Edamam API** (Optional) - For recipe images

## Usage

1. **Enter your preferences:**
   - Select a cuisine type (Italian, Mexican, Indian, etc.)
   - Choose dietary restrictions (vegetarian, vegan, etc.)
   - Add ingredients you have available

2. **Get recommendations:**
   - Click "Get Recipe Recommendations"
   - Wait a few seconds for the AI to generate recipes

3. **View details:**
   - Click on a recipe card to see full ingredients and instructions
   - Check for nearby stores to buy missing ingredients

4. **Save favorites:**
   - Your viewed recipes are automatically saved to history
   - View your history anytime from the sidebar

## Troubleshooting

Having issues? Check out the [TROUBLESHOOTING.md](TROUBLESHOOTING.md) guide for:
- 500 errors or recipes not showing
- Nearby stores not working
- No recipe images
- API configuration help
- Performance tips

## Available Commands

```bash
# Start the backend server
npm run server

# Start the frontend dev server with live reload
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## Architecture

```
├── Frontend (React + TypeScript + Vite)
│   ├── pages/          - Main application pages
│   ├── components/     - React components
│   └── services/       - API client services
│
├── Backend (Node.js + Express)
│   └── server/
│       ├── server.js   - Express server & API endpoints
│       └── images/     - Cached recipe images
│
└── Configuration
    ├── .env.local      - Your API keys and settings
    └── .env.local.example - Template with all options
```

## API Endpoints

The backend provides these REST endpoints:

- `POST /api/recommendations` - Get recipe suggestions
- `POST /api/recipe` - Get full recipe details
- `POST /api/nearby-stores` - Find stores near coordinates
- `POST /api/chat` - Chat with the AI assistant
- `POST /api/generate-image` - Generate or cache recipe image
- `POST /api/edamam-image` - Get image from Edamam API

## Performance Notes

- **First request:** Takes 5-10 seconds (AI generation + image download)
- **Cached recipes:** Load instantly from cache
- **Images:** Cached in `server/images/` directory after first load
- **Location:** Prompts once, then cached in browser

## Common Issues

### "API key not found"
→ Make sure you added your Gemini API key to `.env.local`

### "503 Model Unavailable"
→ Gemini API is experiencing high demand. The app will use fallback recipes. Try again in a few minutes.

### "Geolocation permission denied"
→ Allow location access in your browser settings to see nearby stores

### "No images showing"
→ Add UNSPLASH_ACCESS_KEY to `.env.local` or enable FORCE_UNSPLASH=true

See [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for more solutions!

## Browser Compatibility

- Chrome/Chromium (recommended)
- Firefox
- Safari
- Edge
- Mobile browsers (Chrome, Safari, Firefox)

## License

This project is provided as-is for educational and personal use.

## Support

For issues or questions:
1. Check the [TROUBLESHOOTING.md](TROUBLESHOOTING.md) file
2. Review the [.env.local.example](.env.local.example) for configuration options
3. Check the browser console for error messages
4. Verify both backend and frontend servers are running

---

**Enjoy your personalized recipe recommendations!** 🍽️✨
