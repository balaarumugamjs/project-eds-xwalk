# GitHub Copilot Instructions for AEM Boilerplate Project

## Project Overview
This is an Adobe Experience Manager (AEM) Edge Delivery Services project using the AEM Boilerplate template. The project follows Adobe's best practices for building performant, edge-first web experiences.

## Technology Stack
- **JavaScript/ES6+**: Core programming language
- **AEM Edge Delivery Services**: Adobe's edge-first content delivery platform
- **Node.js 18.3.x or newer**: Runtime environment
- **ESLint**: JavaScript linting with Airbnb base config
- **Stylelint**: CSS linting

## Code Style Guidelines
- Follow Airbnb JavaScript style guide
- Use ES6+ features and imports
- Always include `.js` extensions in imports
- Use camelCase for function and variable names
- Use async/await for asynchronous operations
- Prefer const over let, avoid var
- Use arrow functions where appropriate

## Project Structure
- `/blocks/`: Contains custom AEM blocks (components)
- `/scripts/`: Core JavaScript including `aem.js` utilities and `scripts.js` main entry
- `/styles/`: CSS stylesheets
- `/models/`: Component models and definitions (JSON files starting with _)
- `/tools/`: Development and build tools

## Key Concepts
### Blocks
Blocks are the building blocks of pages. Each block should:
- Be self-contained and reusable
- Have its own CSS file
- Export a default `decorate` function
- Handle its own loading and error states

### AEM.js Utilities
The `scripts/aem.js` file contains utility functions for:
- Loading blocks, sections, headers, and footers
- Decorating buttons, icons, and links
- Fetching placeholders and metadata
- RUM (Real User Monitoring) integration

## Development Workflow
1. Run `npm install` to install dependencies
2. Use `npm run lint` to check code quality
3. Use `aem up` to start local development server
4. Make changes to blocks, scripts, or styles
5. Test changes locally before committing

## Best Practices
- Keep blocks simple and focused on single functionality
- Minimize JavaScript and CSS bundle sizes
- Use lazy loading for non-critical resources
- Optimize images and assets
- Follow web performance best practices (aim for 100 Lighthouse score)
- Add JSDoc comments for functions
- Handle errors gracefully

## Common Patterns
### Block Decoration
```javascript
export default function decorate(block) {
  // Manipulate the block DOM
  // Add event listeners
  // Load resources as needed
}
```

### Fetching Data
```javascript
const resp = await fetch('/path/to/resource');
if (resp.ok) {
  const data = await resp.json();
  // Process data
}
```

### Using AEM Utilities
```javascript
import { decorateIcons, getMetadata, loadCSS } from './aem.js';

// Decorate icons in a block
decorateIcons(block);

// Get page metadata
const title = getMetadata('title');

// Load CSS
await loadCSS('/styles/custom.css');
```

## Linting and Code Quality
- All JavaScript files must pass ESLint checks
- All CSS files must pass Stylelint checks
- Use `npm run lint:js` and `npm run lint:css` to check
- Fix linting errors before committing

## Git Workflow
- Use Husky pre-commit hooks (automatically set up)
- Component model files trigger automatic build of JSON files
- Keep commits focused and well-described
- Reference GitHub issues in commit messages

## Testing URLs
- Preview: https://main--{repo}--{owner}.aem.page/
- Live: https://main--{repo}--{owner}.aem.live/

## Additional Resources
- [AEM Edge Delivery Documentation](https://www.aem.live/docs/)
- [Getting Started Guide](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/edge-dev-getting-started)
- [Creating Blocks](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/create-block)
