# Cytopath Stamp Architect

A zero-dependency, client-side web application for designing and standardizing clinical cytopathology reporting stamps.

This tool replaces the friction of analog layout drafting by allowing pathology residents and departments to visually build, customize, and export standard reporting templates (e.g., Bethesda, Paris, Milan, Yokohama) as production-ready SVGs. These SVGs can then be forwarded directly to physical stamp vendors.

**Live Demo:** [https://dr-42.github.io/cyto-stamps/](https://dr-42.github.io/cyto-stamps/)

---

## 🎯 Features

- **Standardized Templates:** Pre-loaded with current consensus criteria layouts for Cervical, Urinary, Thyroid, Salivary Gland, Breast, Serous Fluid, Lymph Node, and CSF.
- **Visual Layout Builder:** Drag-and-drop interface to add checkboxes, tier-lists, fill-lines, and headings.
- **True-to-Size Export:** SVGs are mapped directly to physical millimeters, ensuring the digital preview matches the exact physical dimensions of the final rubber stamp.
- **JSON Portability:** Export stamp layouts as JSON files to share with colleagues or archive for future updates.
- **Local Storage:** Your custom stamps and work-in-progress layouts are automatically saved to your browser.
- **No Backend Required:** Runs entirely in the browser. Fully static and hostable on GitHub Pages.

---

## 🏥 Guide for Pathology Residents & Department Handovers

If you are a new postgraduate resident inheriting this tool, you do not need to know how to code to keep these stamps up to date.

When international reporting guidelines change (e.g., a new iteration of the Paris System), you can update the departmental stamps by following these steps:

1. Open the [Live App](https://dr-42.github.io/cyto-stamps/).
2. Select the existing template that needs updating, or click **+ New stamp**.
3. Use the **Layout Builder** to add, delete, or rename the diagnostic categories as required by the new guidelines.
4. Click **↓ SVG** to download the file to send to the stamp maker.
5. Click **↓ JSON** to download a backup of the layout. Save this JSON file in the shared departmental drive so future residents have the updated standard.

---

## 🛠️ Technical Details & Development

The application is built as a single `index.html` file utilizing vanilla HTML, CSS, and JavaScript.

### Modifying Built-in Templates

To permanently add a new default template or update an existing one for all users, edit the `templates` array inside the `<script>` block of `index.html`:

```javascript
{
  id: "new_system",
  name: "New Reporting System",
  group: "Category",
  stamp: {
    w: 80, // Width in mm
    h: 50, // Height in mm
    fs: 10, // Font size in pt
    sp: 5, // Spacing
    style: "rounded", // 'single', 'double', or 'rounded'
    fields: [
      { type: "title", text: "System Title" },
      { type: "tier-list", options: "I - Benign, II - Atypical, III - Malignant" }
    ]
  }
}
```
