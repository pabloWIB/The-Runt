[![902shots-so.png](https://i.postimg.cc/3RCbHRYx/902shots-so.png)](https://postimg.cc/XGqgfnrR)
# The Runt

A modern, responsive real estate advisory platform offering free online guidance for families looking to find their perfect home. Built as a static website with clean design and user-focused experience.

## Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Styling**: Custom CSS with responsive design
- **Deployment**: Static hosting compatible
- **Dependencies**: None (pure static implementation)

## Features

- **Free Real Estate Advisory**: Complete $0/month online real estate guidance service
- **Family-Focused Approach**: Specialized assistance for families seeking new homes
- **Responsive Design**: Optimized for all devices and screen sizes
- **User Testimonials**: Client feedback and success stories section
- **Contact Integration**: Multiple communication channels including email and phone
- **Goal-Oriented Guidance**: Structured approach to help users reach their housing objectives
- **Information Hub**: Comprehensive resources for home buying decisions
- **Social Media Integration**: Connected Instagram presence for community building

## Project Structure

```
the-runt/
├── index.html              # Main landing page
├── css/
│   ├── styles.css         # Main stylesheet
│   ├── responsive.css     # Mobile responsiveness
│   └── components.css     # Component-specific styles
├── js/
│   ├── main.js           # Core functionality
│   ├── contact.js        # Contact form handling
│   └── navigation.js     # Navigation interactions
├── images/
│   ├── hero/             # Hero section images
│   ├── testimonials/     # Client photos
│   └── icons/            # UI icons and graphics
├── pages/
│   ├── how-it-works.html # Service explanation
│   ├── features.html     # Feature details
│   ├── pricing.html      # Pricing information
│   └── contact.html      # Contact page
└── README.md
```

## Quick Start

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/pabloWIB/The-Runt.git
   cd The-Runt
   ```

2. **Open locally**
   - Simply open `index.html` in your preferred web browser
   - Or use a local server for better development experience:
   ```bash
   # Using Node.js http-server
   npx http-server . -p 3000
   
   # Using PHP built-in server
   php -S localhost:3000
   
   # Using any other static file server
   ```

3. **Start developing**
   - Edit HTML files for content changes
   - Modify CSS files for styling updates
   - Update JavaScript files for functionality enhancements

### File Serving

For optimal development experience, serve files through a local server rather than opening HTML files directly to avoid CORS issues with any future AJAX requests or resource loading.

## Deployment

### Static Hosting Platforms

**Netlify** (Recommended)
1. Connect your GitHub repository
2. Set build command: `# none required`
3. Set publish directory: `./`
4. Deploy automatically on git push

**Vercel**
1. Import project from GitHub
2. Framework preset: Other
3. Build command: Leave empty
4. Output directory: `./`

**GitHub Pages**
1. Go to repository Settings
2. Navigate to Pages section
3. Select source: Deploy from branch
4. Choose main branch and root folder

**Other Options**
- Firebase Hosting
- AWS S3 + CloudFront
- Surge.sh
- Cloudflare Pages

## Customization

### Content Updates

**Contact Information**
- Update email in `contact.html` and footer sections
- Modify phone number in contact components
- Update social media links (Instagram, etc.)

**Service Information**
- Edit pricing details in `pricing.html`
- Modify feature descriptions in `features.html`
- Update "How it Works" content in respective page

**Branding**
- Replace logo images in `images/` directory
- Update color scheme in `css/styles.css`
- Modify fonts and typography in CSS files

### Styling Modifications

**Colors**: Update CSS custom properties for consistent theming
```css
:root {
  --primary-color: #your-color;
  --secondary-color: #your-color;
  --accent-color: #your-color;
}
```

**Typography**: Modify font families and sizes in `css/styles.css`

**Layout**: Adjust grid layouts and component spacing in respective CSS files

### Functionality Extensions

**Contact Forms**: Add form handling with services like Formspree, Netlify Forms, or EmailJS

**Analytics**: Integrate Google Analytics or alternative tracking solutions

**Performance**: Optimize images and implement lazy loading for better performance

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Internet Explorer 11+ (with potential minor styling differences)

## Performance Considerations

- Optimize images for web (WebP format recommended)
- Minify CSS and JavaScript for production
- Implement proper caching headers via hosting platform
- Consider implementing lazy loading for images
- Use responsive images with appropriate sizing

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

### Development Guidelines

- Maintain responsive design principles
- Follow semantic HTML structure
- Keep CSS organized and modular
- Ensure cross-browser compatibility
- Test on multiple devices and screen sizes
- Maintain clean, readable code structure

## License

Copyright (c) 2022 THERUNT. All rights reserved.

This project is proprietary software. Unauthorized copying, modification, distribution, or use of this software is strictly prohibited without explicit written permission from the copyright holder.

---

For questions, support, or business inquiries, contact: Infor@therunt.com
