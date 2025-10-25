# PowerFlow - Interactive Org Chart Visual for Power BI

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/TALASSX/PowerFlow/blob/main/EULA.md)
[![Power BI](https://img.shields.io/badge/Power%20BI-Visual-orange)](https://powerbi.microsoft.com/)

A powerful and feature-rich organizational chart visual for Power BI featuring D3.js rendering, zoom/pan navigation, employee photos, sparklines, and comprehensive customization options.

![PowerFlow Demo](https://raw.githubusercontent.com/TALASSX/PowerFlow/main/screenshots/PowerFlow-Screenshot-01-MainView.png)

## 📚 Documentation

- **[📖 User Manual](USER_MANUAL.md)** - Complete usage guide with installation, configuration, and troubleshooting
- **[⚡ Features & Capabilities](FEATURES.md)** - Detailed technical specifications and feature overview
- **[📊 Sample Data](sample-org-data.csv)** - Download sample organizational data to test all features

## ✨ Key Features

- **Interactive D3.js Org Charts**: Beautiful hierarchical visualizations with smooth animations
- **Employee Photos**: Display profile pictures for each employee
- **Sparklines**: Performance trend visualization with color-coded indicators
- **Zoom & Pan**: Smooth navigation through large organizations
- **Comprehensive Customization**: Colors, sizes, layouts, and styling options
- **Responsive Design**: Works on desktop and mobile devices
- **Performance Optimized**: Handles large datasets efficiently
- **Tooltip System**: Rich employee information on hover
- **Multiple Layouts**: Tree, compact tree, and custom layouts
- **Status Indicators**: Color-coded employee status (Active/Inactive/On Leave)

## 📥 Installation

### Option 1: Download from Releases
1. Go to [Releases](https://github.com/TALASSX/PowerFlow/releases)
2. Download `PowerFlow-OrgChart-Visual.pbiviz`
3. In Power BI Desktop: File → Import → "Import a custom visual from a file"
4. Select the downloaded .pbiviz file

### Option 2: Direct Download
```bash
# Download the latest release
wget https://github.com/TALASSX/PowerFlow/releases/latest/download/PowerFlow-OrgChart-Visual.pbiviz
```

## 📊 Data Requirements

Your data should include these fields for full functionality:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `employeeId` | Text/Number | ✅ | Unique employee identifier |
| `employeeName` | Text | ✅ | Employee full name |
| `managerId` | Text/Number | ✅ | Manager's employee ID (null for CEO) |
| `title` | Text | ✅ | Job title |
| `department` | Text | ✅ | Department name |
| `imageUrl` | Text | ❌ | Profile picture URL |
| `status` | Text | ❌ | Employment status (Active/Inactive/On Leave) |
| `salesData` | Text | ❌ | Comma-separated sales figures |
| `salesDates` | Text | ❌ | Comma-separated date strings |

### Sample Data Format
```csv
employeeId,employeeName,managerId,title,department,imageUrl,status,salesData,salesDates
1,Sarah Johnson,,CEO,Executive,https://via.placeholder.com/40x40/4A90E2/FFFFFF?text=SJ,Active,"120,135,142,158,165,178,185,192","2024-01-01,2024-02-01,2024-03-01,2024-04-01,2024-05-01,2024-06-01,2024-07-01,2024-08-01"
2,Michael Chen,1,CTO,Technology,https://via.placeholder.com/40x40/7ED321/FFFFFF?text=MC,Active,"110,118,125,132,140,148,155,162","2024-01-15,2024-02-15,2024-03-15,2024-04-15,2024-05-15,2024-06-15,2024-07-15,2024-08-15"
```

## 🚀 Quick Start

1. **Download Sample Data**: Get `sample-org-data.csv` from this repository
2. **Import into Power BI**: Load the CSV file
3. **Add PowerFlow Visual**: Select the visual from your visualizations pane
4. **Map Data Fields**:
   - **Employee ID**: `employeeId`
   - **Employee Name**: `employeeName`
   - **Manager ID**: `managerId`
   - **Title**: `title`
   - **Department**: `department`
   - **Image URL**: `imageUrl` (optional)
   - **Status**: `status` (optional)
   - **Sales Data**: `salesData` (optional)
   - **Sales Dates**: `salesDates` (optional)

5. **Customize**: Use the formatting pane to adjust colors, sizes, and layouts

## 📸 Screenshots

### Main Org Chart View
![Main View](https://raw.githubusercontent.com/TALASSX/PowerFlow/main/screenshots/PowerFlow-Screenshot-01-MainView.png)
Complete organizational hierarchy with employee photos and department color coding.

### Sparklines and Trends
![Sparklines](https://raw.githubusercontent.com/TALASSX/PowerFlow/main/screenshots/PowerFlow-Screenshot-02-Sparklines.png)
Performance data visualization with sales trend sparklines and color-coded indicators.

### Interactive Features
![Interactive](https://raw.githubusercontent.com/TALASSX/PowerFlow/main/screenshots/PowerFlow-Screenshot-03-Interactive.png)
Zoom, pan, and node interaction capabilities with detailed tooltips.

### Formatting Options
![Formatting](https://raw.githubusercontent.com/TALASSX/PowerFlow/main/screenshots/PowerFlow-Screenshot-04-Formatting.png)
Comprehensive customization options for colors, sizes, and layouts.

## 🎨 Customization Options

### Layout Settings
- **Layout Type**: Tree, Compact Tree, Linear
- **Orientation**: Top-Bottom, Left-Right, Bottom-Top, Right-Left
- **Node Spacing**: Adjust horizontal and vertical spacing

### Visual Styling
- **Node Size**: Width and height (60-200px)
- **Colors**: Department-based coloring, custom color palettes
- **Fonts**: Size, family, and color options
- **Borders**: Width, color, and radius

### Interactive Features
- **Zoom & Pan**: Enable/disable navigation
- **Tooltips**: Rich information display
- **Node Expansion**: Click to expand/collapse
- **Sparklines**: Trend visualization toggle

## 📈 Performance

- **Large Datasets**: Optimized for 500+ employees
- **Smooth Animations**: 60fps rendering with D3.js
- **Memory Efficient**: Intelligent caching and debouncing
- **Responsive**: Adapts to container size changes

## 🔧 System Requirements

- **Power BI Desktop**: Latest version recommended
- **Power BI Service**: Fully compatible
- **Browser Support**: Modern browsers with SVG support
- **Data Size**: Tested with datasets up to 1000 employees

## 📞 Support & Documentation

- **[📖 Complete User Manual](USER_MANUAL.md)** - Step-by-step usage guide with installation and troubleshooting
- **[⚡ Technical Features](FEATURES.md)** - Detailed specifications and capabilities
- **[📊 Sample Data](sample-org-data.csv)** - Test data with 50 employees across departments
- **[🐛 Report Issues](https://github.com/TALASSX/PowerFlow/issues)** - Bug reports and feature requests
- **[📧 Get Help](https://github.com/TALASSX/PowerFlow/issues)** - Support and questions

## 📜 Legal

- **Privacy Policy**: [View privacy policy](https://raw.githubusercontent.com/TALASSX/PowerFlow/main/PRIVACY_POLICY.md)
- **End User License Agreement**: [View EULA](https://raw.githubusercontent.com/TALASSX/PowerFlow/main/EULA.md)
- **License**: MIT License

## 🏢 Use Cases

Perfect for:
- **HR Departments**: Organizational structure visualization
- **Executive Dashboards**: Company hierarchy overview
- **Change Management**: Organizational restructuring
- **Headcount Planning**: Department size and distribution
- **Performance Analytics**: Employee trend visualization
- **Business Intelligence**: Hierarchical data presentation

## 🤝 Contributing

While the source code is private, we welcome:
- Bug reports and feature requests via GitHub Issues
- Usage feedback and suggestions
- Sample data contributions

## 📝 Version History

### v1.0.0 (Current)
- Initial public release
- Full feature set with D3.js visualization
- Performance optimizations
- Comprehensive customization options
- Sample data and documentation

## 🙏 Acknowledgments

Built with:
- **D3.js v7**: Powerful SVG manipulation and visualization
- **Power BI Visuals API v5.11.0**: Robust integration framework
- **TypeScript**: Type-safe development
- **Webpack**: Optimized build system

---

**PowerFlow** - Transform your organizational data into beautiful, interactive visualizations.

[Download Now](https://github.com/TALASSX/PowerFlow/releases) • [📖 User Manual](USER_MANUAL.md) • [⚡ Features](FEATURES.md) • [📊 Sample Data](sample-org-data.csv) • [🐛 Report Issues](https://github.com/TALASSX/PowerFlow/issues)</content>
<parameter name="filePath">C:\Users\rocks\OneDrive\Desktop\OrgChartVisual\public-repo\README.md