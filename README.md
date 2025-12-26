# Mighty Beanz Image Generator

A React-based web application that transforms any uploaded image into a stylized "Mighty Beanz" capsule/pill design using OpenAI's GPT-4.1 image generation API. The app creates a vertical pill-shaped capsule with the user's image on the top 80% and a realistic metallic silver base on the bottom 20%.

**Live Site:** [mightymemesgenerator.vercel.app](https://mightymemesgenerator.vercel.app)

---

## 🎯 Project Purpose

Mighty Beanz Image Generator is an AI-powered image transformation tool that creates artistic pill-shaped capsules from user-uploaded images. The application serves as a meme generator and creative tool, allowing users to:

- Upload any image via drag-and-drop or file selection
- Transform images into stylized "Mighty Beanz" capsule designs
- Download the generated capsule images
- Share and use the generated images for memes and creative content

The project is associated with the Mighty Beanz community (Solana CA: `S4kYvBGEP2AcpC2Nw4BjwhK9oXq7iXrHupwkgmQU7f5`) and provides a fun, interactive way to create branded capsule artwork.

---

## 🛠️ Technology Stack

### Frontend Framework & Core
- **React 19.1.0** - Modern React library for building user interfaces
- **React DOM 19.1.0** - React rendering library for the web
- **React Scripts 5.0.1** - Build tooling and configuration (Create React App)

### AI & Image Processing
- **OpenAI SDK 4.103.0** - JavaScript client for OpenAI API
  - Uses GPT-4.1 model with image generation capabilities
  - Implements `responses.create()` API for multimodal image generation
  - Processes base64-encoded images for API communication

### Development & Testing
- **@testing-library/react 16.3.0** - React component testing utilities
- **@testing-library/jest-dom 6.6.3** - Custom Jest matchers for DOM testing
- **@testing-library/user-event 13.5.0** - User interaction simulation for tests
- **@testing-library/dom 10.4.0** - DOM testing utilities

### Performance Monitoring
- **web-vitals 2.1.4** - Web performance metrics library
  - Tracks Core Web Vitals (CLS, FID, FCP, LCP, TTFB)
  - Integrated via `reportWebVitals.js`

### Build Tools & Configuration
- **Create React App** - Project scaffolding and build configuration
- **Webpack** (via react-scripts) - Module bundler
- **Babel** (via react-scripts) - JavaScript compiler/transpiler
- **ESLint** - Code linting (react-app config)

### Styling
- **CSS3** - Custom stylesheets for all components
- **CSS Gradients** - Background and button styling
- **Flexbox** - Layout system
- **CSS Transitions** - Smooth animations and hover effects

### Browser APIs Used
- **FileReader API** - Reading and converting image files to base64
- **Blob API** - Handling binary image data
- **URL.createObjectURL()** - Creating preview URLs for uploaded images
- **URL.revokeObjectURL()** - Memory management for object URLs
- **crypto.randomUUID()** - Generating unique IDs for image objects
- **Canvas API** (implicit via image rendering) - Image display

### Environment & Configuration
- **Environment Variables** - `REACT_APP_API_KEY` for OpenAI API authentication
- **PWA Manifest** - Progressive Web App configuration
- **Favicon & Icons** - Custom branding assets

### Deployment
- **Vercel** - Hosting platform (based on live URL)

---

## 🔌 APIs & External Services

### OpenAI API
- **Service:** OpenAI GPT-4.1 Image Generation
- **Endpoint:** `openai.responses.create()`
- **Model:** `gpt-4.1`
- **Authentication:** API key via `REACT_APP_API_KEY` environment variable
- **Features Used:**
  - Multimodal input (text prompt + image)
  - Image generation tool
  - Base64 image encoding/decoding
- **Request Format:**
  - Text prompt describing the desired output
  - Base64-encoded input image
  - Image generation tool specification
- **Response Format:**
  - Base64-encoded generated image
  - Filtered from `image_generation_call` output type

### Web Vitals API
- **Service:** Browser Performance Metrics
- **Metrics Tracked:**
  - CLS (Cumulative Layout Shift)
  - FID (First Input Delay)
  - FCP (First Contentful Paint)
  - LCP (Largest Contentful Paint)
  - TTFB (Time to First Byte)

---

## ✨ Unique Features

### 1. **Drag-and-Drop Image Upload**
- Intuitive drag-and-drop interface for image uploads
- Click-to-select fallback option
- Visual feedback during drag operations (border color change, scale transform)
- Supports multiple image formats: JPG, PNG, GIF, WebP, SVG

### 2. **Image Preview System**
- Real-time preview of uploaded images before generation
- Individual image removal with X button
- Proper memory management with URL cleanup on unmount
- UUID-based image tracking system

### 3. **AI-Powered Image Transformation**
- Sophisticated prompt engineering for consistent capsule design:
  - Top 80%: User's uploaded image content
  - Bottom 20%: Realistic metallic silver surface with specular highlights
  - Professional lighting, shadows, and reflections
  - Soft drop shadow for depth
- Base64 encoding/decoding pipeline for API communication
- Error handling and user feedback

### 4. **Loading States & UX**
- Loading indicator during image generation ("Generating..." button state)
- Disabled button state during processing
- Conditional rendering based on generation status
- User-friendly error messages

### 5. **Download Functionality**
- Direct download of generated capsule images
- Automatic filename: `pill-capsule.png`
- Base64 data URL to download link conversion

### 6. **Responsive Design**
- Centered layout with flexbox
- Max-width constraints for optimal viewing
- Responsive image scaling (50% max-width)
- Mobile-friendly touch interactions

### 7. **Custom Styling & Theming**
- Dark theme with gradient overlays
- Custom background image support (`bg.png`)
- Sophisticated button styling with hover effects
- Smooth CSS transitions and animations
- Professional color palette (#cad3e7 text, dark backgrounds)

### 8. **Memory Management**
- Automatic cleanup of object URLs on component unmount
- URL registry tracking system
- Prevents memory leaks from blob URLs

### 9. **Progressive Web App (PWA) Support**
- Web app manifest configuration
- Custom favicon and icons
- Standalone display mode support
- Theme color customization

### 10. **Error Handling**
- File type validation
- Image extraction error handling
- API error catching and user alerts
- Graceful degradation

---

## 📁 Project Structure

```
beanz/
├── public/
│   ├── bg.png              # Background image
│   ├── favicon.png         # Custom favicon
│   ├── index.html          # HTML template
│   ├── logo192.png         # PWA icon (192x192)
│   ├── logo512.png         # PWA icon (512x512)
│   ├── manifest.json       # PWA manifest
│   └── robots.txt          # SEO robots file
├── src/
│   ├── components/
│   │   ├── GenerateButton.jsx    # AI image generation component
│   │   ├── ImageDropZone.jsx     # Drag-and-drop upload component
│   │   └── styles.css            # Component-specific styles
│   ├── App.js              # Main application component
│   ├── App.css             # Application styles
│   ├── App.test.js         # Component tests
│   ├── index.js            # React entry point
│   ├── index.css           # Global styles
│   ├── logo.svg            # React logo (unused)
│   ├── reportWebVitals.js  # Performance monitoring
│   └── setupTests.js       # Test configuration
├── .gitignore              # Git ignore rules
├── package.json            # Dependencies and scripts
├── package-lock.json       # Locked dependency versions
└── README.md               # This file
```

---

## 📝 Complete Commit History & Effects

### Initial Setup & Foundation

**Commit: `1dbbe08` - "Initialize project using Create React App"**
- **Date:** May 27, 2025, 11:19 AM
- **Author:** Arthur Wu
- **Effect:** Created the base React application structure with Create React App, including all default configuration files, build scripts, and initial project scaffolding.

**Commit: `2141533` - "added react app"**
- **Date:** May 27, 2025, 1:52 PM
- **Author:** Arthur Wu
- **Effect:** Confirmed React app initialization and prepared the foundation for custom development.

### Background & Color Styling

**Commit: `600cdd1` - "background"**
- **Date:** May 27, 2025, 3:25 PM
- **Effect:** Initial background styling implementation.

**Commit: `cc518a0` - "background color"**
- **Date:** May 27, 2025, 3:28 PM
- **Effect:** Added background color styling to the application.

**Commit: `1ecf6af` - "background black"**
- **Date:** May 27, 2025, 3:35 PM
- **Effect:** Changed background to black color scheme.

**Commit: `8cbbc0e` - "made the black softer"**
- **Date:** May 27, 2025, 3:36 PM
- **Effect:** Softened the black background for better visual appeal.

**Commit: `8bab4b7` - "color done"**
- **Date:** May 27, 2025, 3:38 PM
- **Effect:** Completed color scheme adjustments.

**Commit: `479f22d` - "color done"**
- **Date:** May 27, 2025, 3:40 PM
- **Effect:** Finalized color scheme implementation.

**Commit: `559dfe0` - "Color update test"**
- **Date:** May 27, 2025, 3:40 PM
- **Effect:** Tested color updates and refinements.

### Layout & Structure

**Commit: `f8106ae` - "added header"**
- **Date:** May 27, 2025, 3:42 PM
- **Effect:** Added the main header element ("Mighty Beanz Image Generator") to the application.

**Commit: `fe9b4a9` - "added padding"**
- **Date:** May 27, 2025, 3:43 PM
- **Effect:** Initial padding implementation for layout spacing.

**Commit: `58d82d4` - "adjusted padding"**
- **Date:** May 27, 2025, 3:44 PM
- **Effect:** Refined padding values for better spacing.

**Commit: `f496964` - "padding adjusted"**
- **Date:** May 27, 2025, 3:53 PM
- **Effect:** Further padding adjustments for optimal layout.

**Commit: `dd4026c` - "adjusted button"**
- **Date:** May 27, 2025, 3:54 PM
- **Effect:** Button styling and positioning adjustments.

**Commit: `f934442` - "testing padding"**
- **Date:** May 27, 2025, 3:56 PM
- **Effect:** Tested various padding configurations.

**Commit: `0564a96` - "margin added to button"**
- **Date:** May 27, 2025, 3:58 PM
- **Effect:** Added margin spacing to the generate button.

**Commit: `6d81ef7` - "added h3"**
- **Date:** May 27, 2025, 4:04 PM
- **Effect:** Added h3 subtitle element with instructions and CA/Twitter links.

**Commit: `857a849` - "made header larger and changed button color"**
- **Date:** May 27, 2025, 4:07 PM
- **Effect:** Increased header font size and updated button color scheme for better visibility.

**Commit: `c7dd23a` - "added background"**
- **Date:** May 27, 2025, 4:13 PM
- **Effect:** Added background image (`bg.png`) with gradient overlay for visual depth.

**Commit: `53d8d55` - "yur"**
- **Date:** May 27, 2025, 4:15 PM
- **Effect:** Minor adjustments or testing commit.

### Image Display & Generation

**Commit: `1dd5899` - "center"**
- **Date:** May 27, 2025, 4:16 PM
- **Effect:** Centered image display in the layout.

**Commit: `505a224` - "height ajusted"**
- **Date:** May 27, 2025, 4:17 PM
- **Effect:** Adjusted image height for proper display.

**Commit: `476ee09` - "changed size"**
- **Date:** May 27, 2025, 4:18 PM
- **Effect:** Modified image size dimensions.

**Commit: `e2a5a8f` - "testing"**
- **Date:** May 27, 2025, 4:19 PM
- **Effect:** Testing image display and sizing.

**Commit: `50d6b46` - "ajusted size"**
- **Date:** May 27, 2025, 4:19 PM
- **Effect:** Final size adjustments for generated images.

**Commit: `1029f08` - "added gradient"**
- **Date:** May 27, 2025, 4:23 PM
- **Effect:** Added gradient overlay to background for enhanced visual appeal.

**Commit: `20406a5` - "made text brighter"**
- **Date:** May 27, 2025, 4:41 PM
- **Effect:** Increased text brightness/contrast for better readability.

**Commit: `b17c43e` - "Edited text"**
- **Date:** May 27, 2025, 4:43 PM
- **Effect:** Updated text content and messaging.

**Commit: `ca5a193` - "made image darker"**
- **Date:** May 27, 2025, 4:44 PM
- **Effect:** Adjusted image brightness/darkness for better contrast.

**Commit: `460ba3a` - "margin bottom h1"**
- **Date:** May 27, 2025, 4:44 PM
- **Effect:** Added bottom margin to h1 header for spacing.

### Download & Favicon Features

**Commit: `fa6635f` - "added download button and updated the tab headder"**
- **Date:** May 27, 2025, 4:52 PM
- **Effect:** Implemented download functionality for generated images and updated HTML title tag.

**Commit: `b9599ab` - "updated favicon"**
- **Date:** May 27, 2025, 4:54 PM
- **Effect:** Updated favicon icon.

**Commit: `9b268f6` - "updated manifest"**
- **Date:** May 27, 2025, 4:54 PM
- **Effect:** Updated PWA manifest with new icon references.

**Commit: `224deb1` - "added favicon.png"**
- **Date:** May 27, 2025, 4:57 PM
- **Effect:** Added custom favicon.png file to public directory.

### Image Generation Refinements

**Commit: `97b1272` - "updated title and the images scaling for the genation and centering"**
- **Date:** May 27, 2025, 5:01 PM
- **Effect:** Updated page title and improved image scaling/centering for generated capsules.

**Commit: `d2ca8f9` - "made the generated image centered and smaller"**
- **Date:** May 27, 2025, 5:19 PM
- **Effect:** Centered generated images and reduced their size (50% max-width) for better display.

**Commit: `9245fad` - "reverted changes"**
- **Date:** May 27, 2025, 5:22 PM
- **Effect:** Reverted some previous changes, likely to fix issues.

**Commit: `2672600` - "made fixes to generate button & image display"**
- **Date:** May 27, 2025, 5:41 PM
- **Author:** Arthur Wu
- **Effect:** Fixed issues with the generate button functionality and image display logic.

**Commit: `2b2a84a` - "pusgh"**
- **Date:** May 27, 2025, 6:29 PM
- **Effect:** Push commit (likely deployment or final adjustments).

**Commit: `62b950b` - "adjusted maxwidth"**
- **Date:** May 27, 2025, 6:33 PM
- **Effect:** Adjusted maximum width constraints for responsive design.

**Commit: `ddfa0e6` - "removed favicon.ico references"**
- **Date:** May 27, 2025, 6:43 PM
- **Effect:** Removed old favicon.ico references, using favicon.png instead.

### Text & Preview Features

**Commit: `1173e99` - "added text"**
- **Date:** May 27, 2025, 6:50 PM
- **Effect:** Added instructional text ("Refresh if there are any issues").

**Commit: `8cd1c3d` - "made p text larger"**
- **Date:** May 27, 2025, 6:52 PM
- **Effect:** Increased paragraph text size for better readability.

**Commit: `9cbbb1a` - "added preview"**
- **Date:** May 27, 2025, 8:28 PM
- **Effect:** Added image preview functionality for uploaded images before generation.

### Final Naming & Polish

**Commit: `8cf7e81` - "Change name"**
- **Date:** May 27, 2025, 8:31 PM
- **Effect:** Changed project/application name.

**Commit: `d4ffb71` - "CA"**
- **Date:** May 27, 2025, 8:44 PM
- **Effect:** Added or updated Solana contract address (CA) information.

**Commit: `179fe96` - "beanz"**
- **Date:** May 27, 2025, 8:49 PM
- **Effect:** Final naming commit, establishing "beanz" as the project identifier.

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher recommended)
- npm or yarn package manager
- OpenAI API key

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/shrayg/beanz.git
   cd beanz
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment variables:**
   Create a `.env` file in the root directory:
   ```
   REACT_APP_API_KEY=your_openai_api_key_here
   ```

4. **Start the development server:**
   ```bash
   npm start
   ```
   The app will open at [http://localhost:3000](http://localhost:3000)

### Building for Production

```bash
npm run build
```

This creates an optimized production build in the `build` folder.

### Running Tests

```bash
npm test
```

---

## 🔧 Configuration

### Environment Variables
- `REACT_APP_API_KEY` - Required OpenAI API key for image generation

### Customization
- **Background Image:** Replace `public/bg.png` with your custom background
- **Favicon:** Update `public/favicon.png` for custom branding
- **Colors:** Modify CSS variables in `src/App.css` and `src/components/styles.css`
- **Prompt:** Edit the AI prompt in `src/components/GenerateButton.jsx` (line 26)

---

## 📊 Performance

The application uses Web Vitals to monitor:
- **CLS (Cumulative Layout Shift):** Measures visual stability
- **FID (First Input Delay):** Measures interactivity
- **FCP (First Contentful Paint):** Measures loading performance
- **LCP (Largest Contentful Paint):** Measures loading performance
- **TTFB (Time to First Byte):** Measures server response time

---

## 🔒 Security Notes

- API keys are stored in environment variables (never commit `.env` files)
- Image data is processed client-side before API transmission
- Base64 encoding ensures safe image data transmission
- Object URLs are properly cleaned up to prevent memory leaks

---

## 📄 License

This project is private and proprietary.

---

## 👥 Contributors

- **shrayg** (indoshray@gmail.com) - Primary developer, UI/UX design, styling
- **Arthur Wu** (arthur.kainan.wu@gmail.com) - Initial setup, core functionality, bug fixes

---

## 🔗 Links

- **Live Site:** [mightymemesgenerator.vercel.app](https://mightymemesgenerator.vercel.app)
- **GitHub Repository:** [https://github.com/shrayg/beanz](https://github.com/shrayg/beanz)
- **Solana CA:** `S4kYvBGEP2AcpC2Nw4BjwhK9oXq7iXrHupwkgmQU7f5`
- **Twitter Community:** [https://x.com/i/communities/1927305352602640601](https://x.com/i/communities/1927305352602640601)

---

## 🎨 Design Philosophy

The Mighty Beanz Image Generator emphasizes:
- **Simplicity:** Clean, intuitive interface with minimal friction
- **Visual Appeal:** Dark theme with gradient overlays and professional styling
- **User Experience:** Drag-and-drop, instant previews, clear feedback
- **Performance:** Efficient image processing and memory management
- **Accessibility:** Clear typography, proper contrast, responsive design

---

*Last Updated: May 27, 2025*
