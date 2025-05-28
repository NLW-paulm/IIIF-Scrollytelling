# IIIF Scrollytelling: Interactive Digital Storytelling

An interactive scrollytelling framework that brings digital archives to life using the International Image Interoperability Framework (IIIF). Create engaging narratives that seamlessly combine high-resolution historical documents with smooth scroll-triggered animations and deep-zoom capabilities.

## 🌟 Live Demo

**View the Story**: [https://nlw-paulm.github.io/IIIF-Scrollytelling/](https://nlw-paulm.github.io/IIIF-Scrollytelling/)

**Debug Mode**: [https://nlw-paulm.github.io/IIIF-Scrollytelling/?debug=true](https://nlw-paulm.github.io/IIIF-Scrollytelling/?debug=true)

## ✨ Features

- **IIIF Integration**: Direct integration with IIIF-compliant digital collections
- **Deep Zoom**: Smooth zoom transitions to reveal document details
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Scroll-Triggered Animations**: Story unfolds as users scroll through content
- **High-Resolution Images**: Leverages IIIF's tiled image delivery for fast loading
- **Developer Tools**: Built-in debugging mode for development and troubleshooting
- **No Backend Required**: Pure HTML/CSS/JavaScript - perfect for static hosting

## 🚀 Quick Start

### For Viewers

Simply visit the live demo link above to experience the interactive story. Scroll through the left panel to see the narrative unfold while images on the right zoom and pan to highlight relevant details.

### For Developers

1. **Clone or download** this repository
2. **Open `index.html`** in a web browser
3. **Enable debug mode** by adding `?debug=true` to the URL
4. **Customize the content** following the guide below

## 📖 How to Create Your Own Story

### 1. Prepare Your IIIF Resources

Ensure you have:
- IIIF canvas JSON URLs for your images
- Access to a IIIF-compliant digital collection
- High-resolution digitized documents or images

**Example IIIF Canvas URL:**
```
https://damsssl.llgc.org.uk/iiif/2.0/4627942/canvas/4628013.json
```

### 2. Configure Your Story Data

Edit the `storyData` object in the JavaScript section:

```javascript
const storyData = {
    sections: [
        {
            id: 1,
            canvasJson: "https://your-iiif-server.org/canvas/12345.json",
            initialView: { zoom: 1, x: 0.5, y: 0.5 },
            animation: { zoom: 1.5, x: 0.3, y: 0.7, duration: 2000 },
            description: "Opening scene description"
        },
        // Add more sections...
    ]
};
```

**Configuration Options:**

- `id`: Must match the `data-step` attribute in your HTML
- `canvasJson`: Direct URL to IIIF canvas JSON
- `initialView`: Starting zoom and position (x, y coordinates from 0-1)
- `animation`: Target zoom/pan animation (optional)
- `description`: Internal description for documentation

### 3. Add Your Story Content

Create corresponding HTML sections in the story panel:

```html
<div class="step" data-step="1">
    <div class="step-content">
        <h2>Your Story Title</h2>
        <p>Your narrative content here...</p>
        <div class="highlight-box">
            <p><strong>Key Detail:</strong> Important information to highlight</p>
        </div>
    </div>
</div>
```

### 4. Coordinate Views and Animations

**Zoom and Pan Coordinates:**
- `x: 0.0` = far left, `x: 1.0` = far right
- `y: 0.0` = top, `y: 1.0` = bottom  
- `x: 0.5, y: 0.5` = center
- `zoom: 1` = full image, `zoom: 2` = 2x magnification

**Animation Options:**
- `duration`: Animation length in milliseconds
- Smooth transitions between `initialView` and `animation` states
- Leave `animation` undefined for static views

### 5. Advanced Techniques

**Same Image, Different Views:**
```javascript
// Use the same canvasJson with different zoom/pan settings
{ canvasJson: "same-image.json", initialView: { zoom: 1, x: 0.5, y: 0.5 } },
{ canvasJson: "same-image.json", animation: { zoom: 2, x: 0.3, y: 0.2 } }
```

**No Image Sections:**
```javascript
// For text-only sections or transitions
{ canvasJson: null, specialEffect: "fade" }
```

**Multiple Documents:**
```javascript
// Switch between different IIIF resources
{ canvasJson: "document-1.json", initialView: { zoom: 1.2, x: 0.6, y: 0.4 } },
{ canvasJson: "document-2.json", initialView: { zoom: 1, x: 0.5, y: 0.5 } }
```

## 🛠️ Development Tools

### Debug Mode

Add `?debug=true` to your URL to enable:

- **Console Logging**: Detailed information about step activation and image loading
- **Visual Borders**: Colored borders around each story step
- **Position Debugging**: Real-time step position information
- **Debug Button**: Manual trigger for position analysis

### Troubleshooting

**Common Issues:**

1. **Story starts on wrong step**: Check CSS positioning in `.story-panel` and `.scrolly-content`
2. **Images not loading**: Verify IIIF canvas URLs are accessible and properly formatted
3. **Animations not smooth**: Adjust `threshold` and `rootMargin` in Intersection Observer
4. **Mobile responsiveness**: Test and adjust the CSS media queries

**Debug Console Commands:**
```javascript
debugStepPositions()  // Check step positioning
debugLog('test')      // Conditional logging
```

## 🏗️ Technical Architecture

### Built With
- **OpenSeadragon**: Deep zoom image viewer
- **IIIF Presentation API**: Standardized access to digital collections
- **Intersection Observer**: Efficient scroll event detection
- **CSS Grid & Flexbox**: Responsive layout system

### Browser Support
- Modern browsers with Intersection Observer support
- Mobile and desktop responsive
- HTTPS required for IIIF API access

### Performance Features
- **Lazy Loading**: Images load only when needed
- **Tiled Delivery**: IIIF's efficient image serving
- **Smooth Animations**: Hardware-accelerated CSS transitions
- **Minimal Dependencies**: Only essential libraries included

## 📁 File Structure

```
iiif-scrollytelling/
├── index.html              # Main story file
├── README.md              # This documentation
└── examples/              # Additional story examples (optional)
    ├── story-2.html
    └── story-3.html
```

## 🤝 Contributing

Contributions welcome! Areas for improvement:

- Additional IIIF Presentation API version support
- More animation types and transitions
- Mobile gesture controls
- Accessibility enhancements
- Template generators for common story types

## 📝 License

MIT License - feel free to use this for your own digital storytelling projects.

## 🔗 Resources

- [IIIF Consortium](https://iiif.io/) - Learn about the International Image Interoperability Framework
- [OpenSeadragon](https://openseadragon.github.io/) - Deep zoom viewer documentation
- [IIIF Awesome List](https://github.com/IIIF/awesome-iiif) - Curated IIIF resources and tools

## 💡 Inspiration & Use Cases

Perfect for:
- **Digital Humanities Projects**: Bring historical documents to life
- **Museum Exhibitions**: Create engaging online exhibits
- **Educational Resources**: Interactive learning experiences
- **Archive Presentations**: Showcase institutional collections
- **Research Storytelling**: Present findings with visual evidence

---

**Questions?** Open an issue or contribute improvements to help others create compelling digital stories with IIIF resources.
