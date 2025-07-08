# 🖼️ MENG E-Commerce Platform - PNG Diagram Extractor

A powerful JavaScript tool for extracting diagrams from documentation as high-quality PNG images, with an interactive HTML gallery viewer.

## 🚀 Features

### **High-Quality PNG Export**
- ✅ **PNG Export** - Ultra high-quality images (3x scale, 300 DPI equivalent)
- ✅ **Batch Processing** - Extract all diagrams at once
- ✅ **HTML Gallery** - Interactive image viewer with zoom
- ✅ **Index Generation** - CSV index of all generated images

### **Supported Diagram Types**
- 🏗️ **Class Diagrams** - UML class structures with relationships
- 🔄 **Flowcharts** - Process flows and decision trees
- 📋 **Sequence Diagrams** - Interaction timelines
- 🗃️ **ER Diagrams** - Database entity relationships
- 📊 **All Mermaid Types** - Gantt, Pie, Git graphs, and more

### **Advanced Features**
- 🔍 **Auto-Detection** - Automatically identifies diagram types
- 📦 **Bulk Operations** - Extract all diagrams at once
- 🎯 **High Quality** - 3x scale rendering for crisp images
- 📱 **Responsive Gallery** - Mobile-friendly HTML image viewer
- 🔄 **Real-time Preview** - Full-size image preview in gallery

## 📁 File Structure

```
📂 diagrams/
├── 📄 diagram-extractor.js      # Main extraction engine
├── 📄 html-template.js          # HTML template generator
├── 📄 usage-example.html        # Demo page with sample diagrams
├── 📄 README.md                 # This documentation
└── 📂 output/                   # Generated files (after extraction)
    ├── 📊 diagram-1.csv         # Individual diagram CSV files
    ├── 🖼️ diagram-1.png         # Individual diagram images
    ├── 📋 diagram-index.csv     # Master index file
    └── 🌐 diagram-viewer.html   # Interactive viewer
```

## 🛠️ Installation & Setup

### **1. Include Required Libraries**
Add these scripts to your HTML page:

```html
<!-- Mermaid for diagram rendering -->
<script src="https://cdn.jsdelivr.net/npm/mermaid/dist/mermaid.min.js"></script>

<!-- html2canvas for image generation -->
<script src="https://html2canvas.herokuapp.com/dist/html2canvas.min.js"></script>

<!-- Diagram extractor -->
<script src="diagram-extractor.js"></script>
```

### **2. Initialize Mermaid**
```javascript
mermaid.initialize({
    startOnLoad: true,
    theme: 'default',
    themeVariables: {
        fontSize: '16px',
        fontFamily: 'Arial, sans-serif'
    }
});
```

### **3. Add Diagrams to Your Page**
Use standard Mermaid syntax:

```html
<div class="mermaid">
    graph TD
        A[Start] --> B[Process]
        B --> C[End]
</div>
```

## 🎯 Usage

### **Method 1: Automatic Button (Recommended)**
The extractor automatically adds an extraction button to your page:

1. Load the page with `diagram-extractor.js`
2. Click the "📊 Extract All Diagrams" button
3. Wait for processing
4. Check your Downloads folder

### **Method 2: Manual Trigger**
Call the extraction function programmatically:

```javascript
// Extract all diagrams
extractAllDiagrams();

// Or create an instance for more control
const extractor = new DiagramExtractor();
await extractor.init();
```

### **Method 3: Individual Extraction**
Extract specific diagrams:

```javascript
const extractor = new DiagramExtractor();
await extractor.scanDiagrams();

// Extract specific diagram
const diagram = extractor.diagrams[0];
const csvContent = await extractor.extractDiagramToCSV(diagram);
const imageData = await extractor.generateDiagramImage(diagram);
```

## 📊 CSV Output Format

### **Class Diagrams**
```csv
Diagram Title,Class Name,Element Type,Element Name,Element Details,Relationship Target,Relationship Type,Visibility,Line Number
"User Management","User","Class","User","Class Definition","","","","1"
"User Management","User","Attribute","id","String","","","Private","2"
"User Management","User","Method","login()","void","","","Public","3"
```

### **Flowcharts**
```csv
Diagram Title,Node ID,Node Type,Node Label,Connection Target,Connection Type,Connection Label,Line Number
"Process Flow","A","Rectangle","Start Process","","","","1"
"Process Flow","A","Connection","","B","Solid Arrow","","2"
```

### **Sequence Diagrams**
```csv
Diagram Title,Participant,Action Type,Target,Message,Note,Line Number
"Order Process","User","Participant","","","","1"
"Order Process","User","Sync Message","API","Place Order","","2"
```

## 🌐 HTML Viewer Features

The generated `diagram-viewer.html` includes:

- 📊 **Interactive Dashboard** - Statistics and overview
- 🔍 **Filter by Type** - View specific diagram types
- 👁️ **CSV Preview** - View data without downloading
- 📥 **Download Options** - Individual CSV and image downloads
- 📱 **Responsive Design** - Works on all devices
- 🎨 **Modern UI** - Beautiful gradient design

## 🔧 Configuration Options

### **Customize Image Quality**
```javascript
// In diagram-extractor.js, modify the html2canvas options:
const canvas = await html2canvas(diagram.element, {
    backgroundColor: '#ffffff',
    scale: 3,              // Increase for higher quality
    useCORS: true,
    logging: false
});
```

### **Customize CSV Headers**
Modify the CSV headers in the parsing functions:
```javascript
let csvContent = 'Custom,Headers,Here\n';
```

### **Add Custom Diagram Types**
Extend the `detectDiagramType` function:
```javascript
detectDiagramType(code) {
    // Add your custom detection logic
    if (code.includes('myCustomDiagram')) return 'customType';
    // ... existing logic
}
```

## 🎯 Example Usage

See `usage-example.html` for a complete working example with:
- System Architecture Diagram
- Class Diagram
- Sequence Diagram
- ER Diagram
- Flowchart

## 🐛 Troubleshooting

### **Common Issues**

1. **No diagrams found**
   - Ensure diagrams have the `mermaid` class
   - Check that Mermaid is properly initialized

2. **Images not generating**
   - Verify html2canvas is loaded
   - Check browser console for errors

3. **CSV data incomplete**
   - Ensure diagram syntax is valid
   - Check for unsupported diagram features

4. **Downloads not working**
   - Check browser download permissions
   - Ensure popup blockers aren't interfering

### **Browser Compatibility**
- ✅ Chrome 80+
- ✅ Firefox 75+
- ✅ Safari 13+
- ✅ Edge 80+

## 📈 Performance Tips

1. **Large Documents**: Process diagrams in batches
2. **High-Quality Images**: Reduce scale factor for faster processing
3. **Memory Usage**: Clear processed data after download
4. **Network**: Use local copies of libraries for better performance

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add your improvements
4. Test with various diagram types
5. Submit a pull request

## 📄 License

This project is part of the MENG E-Commerce Platform documentation system.

## 🆘 Support

For issues or questions:
1. Check the troubleshooting section
2. Review the example files
3. Check browser console for errors
4. Ensure all dependencies are loaded

---

**Happy Diagramming! 📊✨**
