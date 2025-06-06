# Frontend Architecture Overview

This document summarizes the frontend architecture, based on an analysis of the provided codebase structure and file contents.

## 1. Overall Layout Philosophy

Pages generally adhere to a standard three-part structure:

*   **Header:** Contains the main navigation, branding (logo), and potentially call-to-action buttons or utility links. It is often sticky and transforms into an offcanvas menu on mobile devices.
*   **Main Content:** This is the primary section of the page and varies greatly depending on the page's purpose. It is typically built by assembling various content blocks or sections.
*   **Footer:** Located at the bottom of the page, it usually includes copyright information, navigation links (privacy policy, terms of service), contact details, social media icons, and a theme switcher (light/dark mode).

## 2. Core Technologies

The frontend stack is built upon the following core technologies:

*   **Bootstrap 5:** Serves as the foundational CSS framework, providing a responsive grid system, pre-styled components, and utility classes.
*   **Sass:** Used for customizing and extending Bootstrap. While the source `.scss` files were not directly analyzed, the class naming conventions (e.g., `bg-soft-primary`, `text-purple`) and the overall structure of `theme.min.css` strongly suggest its use for more maintainable and modular styling.

## 3. Key Reusable Components

Several components are designed for reuse across different pages:

*   **Header/Navigation:**
    *   **Navbar:** A responsive navigation bar, typically at the top of the page.
    *   **Offcanvas Mobile Version:** On smaller screens, the main navigation often collapses into an offcanvas menu that slides in from the side.
    *   **Dropdowns:** Used within the navigation for sub-menus.
    *   **Sticky Behavior:** The header often remains fixed at the top of the viewport as the user scrolls (`sticky-top` or JavaScript-driven via Headhesive).

*   **Footer:**
    *   **Content:** Typically includes:
        *   Navigation links (e.g., About Us, Contact, FAQ, Privacy Policy, Terms of Use).
        *   Contact information (address, phone, email).
        *   Copyright statement.
        *   Social media links/icons.
        *   A theme switcher for toggling between light and dark modes.

## 4. Styling and Theming

*   **`assets/css/theme.min.css`:** This is the primary compiled and minified stylesheet. It contains all custom styles, Bootstrap overrides, and theme-specific rules. It's the result of processing Sass files and any other CSS sources.
*   **Light/Dark Mode Functionality:**
    *   The application supports both light and dark color schemes.
    *   CSS selectors like `[data-bs-theme="dark"]` and `[data-bs-theme="light"]` are used to apply different styles based on the active theme.
    *   A JavaScript-based theme switcher is typically present, often in the footer, to allow users to toggle modes. This likely manipulates the `data-bs-theme` attribute on the `<html>` or `<body>` tag.
*   **Utility Classes:**
    *   Extensive use of Bootstrap utility classes (e.g., `mb-3`, `p-5`, `text-center`, `d-flex`).
    *   Custom utility classes (e.g., `bg-soft-primary`, `text-ash`) are also defined, likely in Sass, to provide consistent styling options that extend Bootstrap's defaults.

## 5. JavaScript Functionality

*   **`assets/js/theme.min.js`:** This is the primary compiled and minified JavaScript file. It bundles vendor scripts and custom JavaScript code for the theme.
*   **Key Functionalities Handled:**
    *   **Bootstrap Component Initialization:** Activates Bootstrap JavaScript components (e.g., carousels, modals, dropdowns, tooltips, popovers).
    *   **Sticky Header:** Manages the behavior of the sticky/fixed header (potentially using libraries like Headhesive.js).
    *   **Scroll-to-Top Button:** Shows/hides a button that allows users to quickly return to the top of the page.
    *   **Active Navigation Link Highlighting:** Dynamically updates the visual state of navigation links to indicate the current page or section.
    *   **Form Validations and Interactions:** Custom scripts for handling form submissions, input validations, or specific interactive form elements.
    *   **Animations and Effects:** Implements custom animations or visual effects (e.g., on scroll animations via ScrollCue).
*   **Vendor Libraries Used:** The theme integrates several third-party JavaScript libraries for specific features:
    *   **Swiper:** For creating touch-enabled sliders and carousels.
    *   **ScrollCue.js:** For revealing elements on scroll (scroll animations).
    *   **GLightbox:** For creating responsive lightboxes for images and videos.
    *   **Parallax.js (or similar):** For creating parallax scrolling effects (though `rellax.min.js` is also listed, which is a specific parallax library).
    *   **Rellax.js:** A lightweight, vanilla JavaScript parallax library.
    *   **Plyr:** A simple, accessible, and customizable HTML5 media player.
    *   **Headhesive.js:** For creating sticky headers that appear on scroll.
    *   **intl-tel-input:** For international telephone number input formatting and validation.

## 6. Modularity

*   **`blocks` Directory:** The presence of a `blocks` or `partials` directory (inferred, common practice) suggests that the UI is constructed from reusable HTML snippets or components. These blocks might represent individual sections like "hero," "testimonials," "pricing," "contact-form," etc.
*   **Sections:** Pages are built by combining these reusable blocks/sections. This approach promotes consistency and makes it easier to create new pages or modify existing layouts. Each HTML page likely includes these blocks to form the complete page structure.

## 7. Asset Management

*   **`assets/` Directory:** This directory serves as the central repository for all static frontend resources. It is typically organized into subdirectories:
    *   `css/`: For stylesheets (`theme.min.css` and potentially others).
    *   `js/`: For JavaScript files (`theme.min.js` and potentially others).
    *   `img/` or `images/`: For image assets.
    *   `fonts/`: For custom web fonts.
    *   `scss/` (if source maps or direct linking is used, though typically compiled into `css/`): For Sass source files.
    *   `node_modules/` or `vendor/` (sometimes within `assets/` or at the root): For third-party libraries, though `theme.min.js` implies these are bundled.

This structure allows for a clear separation of concerns and organized management of frontend resources.
