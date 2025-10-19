# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Interactive educational platform for statistics, probability, and quantitative finance concepts. Features a comprehensive directory of articles with interactive visualizations, step-by-step calculations, and real-time data manipulation capabilities.

## High-Level Architecture

### Design System
- **Centralized Styling**: All pages use `unified-styles.css` as the single source of truth for design
- **CSS Variables**: Consistent theming through CSS custom properties for colors, spacing, typography
- **Component-Based**: Reusable UI patterns (cards, formulas, scenarios, exercises, highlights)
- **Responsive**: Mobile-first design with breakpoints at 768px

### Interactive Features
- **Plotly.js Integration**: All visualizations use Plotly.js (v2.24.1) loaded via CDN
- **Real-time Calculations**: JavaScript embedded in each HTML file handles user input and updates
- **Educational Flow**: Concepts build on each other with prerequisite links

## Directory Structure

```
therms-index/
├── index.html              # Main directory with alphabetically organized links
├── unified-styles.css      # Central design system (565 lines)
├── CLAUDE.md              # This file
│
├── Statistics Articles     # Core statistical concepts
├── Probability Articles    # Bayes, LOTP, distributions
├── Finance Articles        # Options, derivatives, risk management
└── kurtosis.html          # Example of complex financial/statistical topic
```

## Development Commands

### Local Development
```bash
# Serve the directory locally
python3 -m http.server 8000
# Navigate to http://localhost:8000/index.html

# Or use any static file server
npx serve .
```

### Adding New Articles
1. Copy an existing article as template (e.g., `mean.html`)
2. Update the title and content
3. Add entry to `index.html` in alphabetical order
4. Ensure Plotly.js CDN is included if using visualizations
5. Use `unified-styles.css` classes for consistent styling

## Article Structure Pattern

Each article follows this structure:
1. **Back button** to directory
2. **Title** and main heading
3. **Description card** - What is this concept?
4. **Formula card** - Mathematical definition
5. **Interactive scenario** - User can manipulate data
6. **Visualization** - Plotly.js chart
7. **Statistics/Results** - Calculated values display
8. **Exercises** (optional) - Collapsible practice problems

## CSS Classes Reference

### Layout Components
- `.card` - Primary content container
- `.scenario` - Interactive example section
- `.formula` - Mathematical notation display
- `.highlight` - Important information callout
- `.exercise` - Practice problem container

### Interactive Elements
- `.collapsible` - Expandable section button
- `.content` - Collapsible content area
- `.control` - Form control wrapper

### Typography
- `.category` - Topic badges
- `.letter` - Alphabetical dividers in directory
- `.directory` - Article listing style

## JavaScript Patterns

Articles use inline JavaScript for interactivity:
```javascript
// Data parsing from input
const values = input.value.split(',').map(v => parseFloat(v.trim())).filter(v => !isNaN(v));

// Plotly.js visualization update
Plotly.newPlot('divId', data, layout, {responsive: true});

// Real-time calculation updates
element.textContent = calculatedValue.toFixed(2);
```

## Article Categories

Current coverage includes:
- **Statistics**: Mean, Standard Deviation, Quantiles, Box Plots, Central Limit Theorem
- **Probability**: Bayes' Rule, Law of Total Probability, Expected Value, PDFs
- **Finance**: Options (Greeks, Strategies, Payoffs), Black-Scholes, Risk Management
- **Credit/Fixed Income**: Five Cs of Credit, MBS Securities
- **Portfolio Theory**: Sharpe Ratio, Mean-Variance Criterion, Market Premium

## Notes for Future Development

- All visualizations should be responsive using `{responsive: true}` in Plotly config
- Maintain alphabetical ordering in `index.html` when adding new articles
- Use semantic HTML5 elements where appropriate
- Keep JavaScript simple and educational - avoid complex frameworks
- Each concept should be self-contained but can link to prerequisites