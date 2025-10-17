# NextGen Widget AI Training
![Version](https://img.shields.io/badge/version-1.0.0-green.svg)

A comprehensive training repository for building NextGen UGC (User Generated Content) widgets using Nosto's Widget SDK. This repository contains AI training materials, documentation, code examples, and component libraries for developing sophisticated, customizable UGC widgets.

## 📖 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Repository Structure](#repository-structure)
- [Widget Types](#widget-types)
- [Component Library](#component-library)
- [Getting Started](#getting-started)
- [Documentation](#documentation)
- [Development Guides](#development-guides)
- [AI Training Materials](#ai-training-materials)
- [Widget SDK Reference](#widget-sdk-reference)
- [Examples](#examples)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [Support](#support)
- [License](#license)

## 🎯 Overview

The NextGen Widget AI Training repository is designed to train AI assistants and developers on building advanced UGC widgets that seamlessly integrate social media content with e-commerce functionality. This repository serves as a comprehensive knowledge base for:

- **AI Assistant Training**: Structured data for training AI models to assist with widget development
- **Developer Education**: Complete documentation and examples for widget creation
- **Component Reference**: Reusable components and templates for rapid development
- **Best Practices**: Industry-standard approaches to UGC widget development

## ✨ Key Features

### 🎨 Widget Customization
- **Visual Styling**: Complete control over appearance with SCSS/CSS
- **Layout Options**: Grid, Carousel, Masonry, Waterfall, and Story layouts
- **Responsive Design**: Mobile-first approach with breakpoint management
- **Theme Support**: Light/dark themes and custom branding

### 🛒 E-commerce Integration
- **Product Tagging**: Link social content to specific products
- **Add-to-Cart**: Direct purchase integration with Shopify and other platforms
- **Cross-selling**: AI-powered product recommendations
- **Dynamic Filtering**: Content filtering by products, brands, and categories

### 🎯 Advanced Features
- **Shopspots**: Interactive product hotspots on images/videos
- **Expanded Tiles**: Detailed view with product information
- **Social Sharing**: Built-in sharing functionality
- **Analytics Integration**: Google Analytics and custom event tracking
- **Performance Optimization**: Lazy loading and progressive enhancement

## 📁 Repository Structure

```
nextgen-widget-ai-training/
├── components.txt          # Complete component library documentation
├── guides.txt             # Step-by-step development guides
├── handlebars.txt         # Template system documentation
├── libs.txt               # External library integrations
├── placement.sdk.txt      # Widget placement and configuration
├── prompt.txt             # AI assistant behavior guidelines
├── sample-html.txt        # HTML examples and snippets
├── sdk.txt                # Core SDK API reference
├── types.txt              # TypeScript definitions and interfaces
├── widget-loader.txt      # Widget loading and initialization
├── widget-templates.txt   # Pre-built widget templates
├── .gitignore             # Git ignore patterns
└── README.md              # This comprehensive documentation
```

## 🎨 Widget Types

### Grid Widget
- **Purpose**: Display content in a responsive grid layout
- **Best For**: Product showcases, gallery displays
- **Features**: Masonry support, lazy loading, infinite scroll

### Carousel Widget
- **Purpose**: Horizontal scrolling content display
- **Best For**: Featured content, product highlights
- **Features**: Touch/swipe support, navigation arrows, autoplay

### Waterfall Widget
- **Purpose**: Pinterest-style masonry layout
- **Best For**: Mixed content types, dynamic heights
- **Features**: Variable tile sizes, infinite scroll, responsive columns

### Story Widget
- **Purpose**: Instagram Stories-like vertical format
- **Best For**: Mobile-first experiences, video content
- **Features**: Full-screen viewing, auto-progression, interactive elements

### Blank Canvas Widget
- **Purpose**: Completely customizable starting point
- **Best For**: Unique designs, specific requirements
- **Features**: No default styling, maximum flexibility

## 🧩 Component Library

### Core Components

#### `<tile-content>`
Display tile metadata including user info, captions, and timestamps.
```typescript
<tile-content 
  tile-id="123" 
  render-user-info="true"
  render-description="true"
  trim-description="true"
/>
```

#### `<tile-tags>`
Render content tags with optional carousel functionality.
```typescript
<tile-tags 
  tile-id="123" 
  mode="swiper" 
  navigation-arrows="true"
  theme="light"
/>
```

#### `<add-to-cart>`
Shopify integration for direct purchases.
```typescript
<add-to-cart 
  productId="123"
  url="https://store.com/product"
  currency="USD"
  availability="true"
/>
```

#### `<share-menu>`
Social sharing functionality.
```typescript
<share-menu 
  tile-id="123"
  theme="light"
  source-id="custom-id"
/>
```

#### `<shopspot-icon>`
Interactive product hotspots.
```typescript
<shopspot-icon 
  tile-id="123"
  show-tooltip="true"
  mode="expanded"
/>
```

#### `<load-more>`
Pagination and infinite scroll.
```typescript
<load-more 
  button-text="Load More Content"
  auto-load="false"
/>
```

## 🚀 Getting Started

### Prerequisites
- Node.js 18+ (LTS) and npm/yarn
- TypeScript knowledge
- Basic understanding of web components
- Familiarity with SCSS/CSS

### Basic Widget Setup

1. **Choose a Widget Template**
   ```typescript
   import { loadWidget } from '@stackla/widget-utils'
   
   loadWidget({
     config: {
       style: {
         widget_background: '#ffffff',
         margin: '10'
       }
     }
   })
   ```

2. **Customize Layout (layout.hbs)**
   ```handlebars
   <div class="ugc-tiles grid grid-inline">
     {{#tiles}}
       {{>tpl-tile}}
     {{/tiles}}
   </div>
   <load-more />
   ```

3. **Style Components (widget.scss)**
   ```scss
   .grid {
     display: grid;
     gap: var(--margin);
     grid-template-columns: repeat(auto-fit, minmax(var(--tile-size), 1fr));
   }
   ```

4. **Add Interactivity (widget.tsx)**
   ```typescript
   sdk.querySelector('#search-input')?.addEventListener('input', async e => {
     const searchValue = (e.target as HTMLInputElement).value
     await sdk.searchTiles(searchValue, true)
   })
   ```

## 📚 Documentation

### Core Concepts

#### Widget SDK
The Widget SDK provides a comprehensive API for:
- **Tile Management**: CRUD operations for content tiles
- **Event System**: Custom event handling and analytics
- **State Management**: Widget state persistence
- **DOM Manipulation**: Shadow DOM-safe element queries

#### Component Architecture
- **Web Components**: Self-contained, reusable elements
- **Shadow DOM**: Encapsulated styling and behavior
- **Event-driven**: Reactive updates and interactions
- **TypeScript**: Type-safe development experience

#### Handlebars Templates
- **Server-side Rendering**: Initial content generation
- **Dynamic Content**: Data binding and conditionals
- **Partial Support**: Reusable template components
- **Helper Functions**: Custom template logic

### API Reference

#### SDK Methods
```typescript
// Tile Operations
sdk.getTiles(): Tile[]
sdk.getTileById(id: string): Tile | undefined
sdk.searchTiles(query: string): void
sdk.hideTileById(id: string): Promise<void>

// Event Management
sdk.addEventListener(event: string, callback: Function): void
sdk.triggerEvent(event: string, data?: object): void

// DOM Queries (Shadow DOM safe)
sdk.querySelector(selector: string): HTMLElement | null
sdk.querySelectorAll(selector: string): NodeListOf<HTMLElement>

// State Management
sdk.getState(key: string): any
sdk.setState(key: string, value: any): void
```

## 📖 Development Guides

### 1. Creating Custom Components
Learn to build reusable web components with proper lifecycle management and event handling.

### 2. Dynamic Content Filtering
Implement product-based filtering, category filtering, and brand-specific content display.

### 3. E-commerce Integration
Connect widgets to Shopify, WooCommerce, and other platforms for seamless shopping experiences.

### 4. Performance Optimization
Implement lazy loading, image optimization, and efficient DOM manipulation techniques.

### 5. Mobile Responsiveness
Create mobile-first designs with touch gestures and responsive breakpoints.

### 6. Analytics Integration
Set up Google Analytics, custom events, and conversion tracking.

### 7. Accessibility
Ensure WCAG compliance with proper ARIA labels and keyboard navigation.

## 🤖 AI Training Materials

This repository contains specialized training data for AI assistants:

### Training Objectives
- **Code Generation**: Generate widget code based on requirements
- **Problem Solving**: Debug and troubleshoot widget issues
- **Best Practices**: Recommend optimal implementation approaches
- **Documentation**: Provide clear explanations and examples

### AI Assistant Behavior
- Focus on the `blankcanvas` widget template as reference
- Prioritize SDK-based solutions over manual implementations
- Always generate HTML within Handlebars templates when possible
- Provide file-specific code recommendations
- Support both Front-End Engineers and Customer Support Managers

### Context Understanding
- Shadow DOM environment awareness
- Distinguish between inline and expanded tile contexts
- Understand widget lifecycle and event system
- Recognize template modification requirements

## 🎯 Examples

### Simple Grid Widget
```typescript
// widget.tsx
import { loadWidget } from '@stackla/widget-utils'

loadWidget({
  config: {
    style: {
      widget_background: '#f5f5f5',
      margin: '15'
    }
  }
})
```

### Advanced Carousel with Search
```typescript
// widget.tsx
import { loadWidget, ISdk } from '@stackla/widget-utils'

declare const sdk: ISdk

loadWidget({
  extensions: { swiper: true },
  features: { handleLoadMore: false }
})

// Add search functionality
sdk.querySelector('#search-input')?.addEventListener('input', async e => {
  const query = (e.target as HTMLInputElement).value
  await sdk.searchTiles(query, true)
})
```

### Custom Product Integration
```handlebars
<!-- tile.hbs -->
{{#tile class="product-tile"}}
  <div class="tile-content">
    <img src="{{image_thumbnail_url}}" alt="{{name}}" />
    <tile-content tile-id="{{id}}" />
    {{#ifHasProductTags this}}
      <add-to-cart productId="{{getFirstProduct.id}}" />
    {{/ifHasProductTags}}
  </div>
{{/tile}}
```

## ✅ Best Practices

### Code Organization
- ✅ Use TypeScript for type safety
- ✅ Implement proper error handling
- ✅ Follow component lifecycle patterns
- ✅ Use semantic HTML structure

### Performance
- ✅ Implement lazy loading for images and components
- ✅ Use CSS transforms for animations
- ✅ Minimize DOM queries and caching selectors
- ✅ Optimize bundle size with tree shaking

### Accessibility
- ✅ Provide proper ARIA labels
- ✅ Ensure keyboard navigation
- ✅ Use semantic HTML elements
- ✅ Test with screen readers

### Styling
- ✅ Use CSS custom properties for theming
- ✅ Implement mobile-first responsive design
- ✅ Follow BEM or similar naming conventions
- ✅ Avoid global style conflicts

## 🔧 Troubleshooting

### Common Issues

#### Widgets Not Loading
```javascript
// Check for SDK availability
if (window.ugc && window.ugc.widgets) {
  console.log('SDK loaded successfully')
} else {
  console.error('SDK not loaded')
}
```

#### Shadow DOM Issues
```javascript
// Always use SDK methods for DOM queries
const element = sdk.querySelector('.my-element') // ✅ Correct
const element = document.querySelector('.my-element') // ❌ Won't work in Shadow DOM
```

#### Component Not Rendering
```typescript
// Ensure proper component registration
try {
  customElements.define('my-component', MyComponent)
} catch (err) {
  console.warn('Component already defined:', err)
}
```

### Debug Mode
Enable debug logging by setting:
```javascript
window.ugc = { debug: true }
```

## 🤝 Contributing

We welcome contributions to improve the training materials and documentation:

1. **Fork** the repository
2. **Create** a feature branch
3. **Make** your changes with proper documentation
4. **Test** thoroughly
5. **Submit** a pull request

### Guidelines
- Follow existing code style and conventions
- Add comprehensive documentation for new features
- Include examples and use cases
- Update relevant training materials

## 📞 Support

### Resources
- **Documentation**: Comprehensive guides and API reference
- **Examples**: Real-world implementation patterns
- **Community**: Developer forums and discussions
- **Training**: AI assistant knowledge base

### Getting Help
- Check the troubleshooting section
- Review existing examples and guides
- Consult the API documentation
- Contact the development team

---

**Built with ❤️ by the Nosto UGC Team**

> Transform social content into shoppable experiences with NextGen Widgets
