# PowerFlow User Manual

## Table of Contents
- [Quick Start](#quick-start)
- [Installation](#installation)
- [Data Preparation](#data-preparation)
- [Visual Configuration](#visual-configuration)
- [Using the Org Chart](#using-the-org-chart)
- [Customization Options](#customization-options)
- [Troubleshooting](#troubleshooting)
- [Best Practices](#best-practices)
- [FAQ](#faq)

---

## Quick Start

### 1. Install the Visual
1. Download `PowerFlow-OrgChart-Visual.pbiviz` from [GitHub Releases](https://github.com/TALASSX/PowerFlow/releases)
2. Open Power BI Desktop
3. Go to **File** → **Import** → **"Import a custom visual from a file"**
4. Select the downloaded `.pbiviz` file
5. The PowerFlow visual will appear in your visualizations pane

### 2. Prepare Your Data
Download the sample data file `sample-org-data.csv` from the repository and import it into Power BI, or prepare your own data with the required fields.

### 3. Create Your First Org Chart
1. Click the PowerFlow visual icon in the visualizations pane
2. Drag these fields to the visual:
   - **Employee ID**: Your unique employee identifier
   - **Employee Name**: Employee full names
   - **Manager ID**: Manager's employee ID (leave empty for top-level employees)
3. Your org chart will render automatically!

---

## Installation

### System Requirements
- **Power BI Desktop**: Version 2021 or later recommended
- **Power BI Service**: Fully compatible for published reports
- **Browser Support**: Modern browsers with SVG support (Chrome, Edge, Firefox, Safari)
- **Data Size**: Tested with up to 1000 employees

### Installation Steps

#### Method 1: Direct Download
```bash
# Download the latest release
wget https://github.com/TALASSX/PowerFlow/releases/latest/download/PowerFlow-OrgChart-Visual.pbiviz
```

#### Method 2: From GitHub
1. Visit https://github.com/TALASSX/PowerFlow
2. Go to **Releases** tab
3. Download `PowerFlow-OrgChart-Visual.pbiviz`

#### Method 3: Power BI Marketplace (Future)
Once published to AppSource, you can install directly from Power BI's "Get more visuals" option.

### Post-Installation
After importing, the visual will be available in your visualizations pane with the PowerFlow icon. If you don't see it, try restarting Power BI Desktop.

---

## Data Preparation

### Required Fields

| Field Name | Data Type | Required | Description |
|------------|-----------|----------|-------------|
| `employeeId` | Text/Number | ✅ | Unique identifier for each employee |
| `employeeName` | Text | ✅ | Full name of the employee |
| `managerId` | Text/Number | ✅ | Employee ID of the manager (null/empty for top level) |

### Optional Fields

| Field Name | Data Type | Description |
|------------|-----------|-------------|
| `title` | Text | Job title or position |
| `department` | Text | Department or business unit |
| `imageUrl` | Text | URL to employee profile picture |
| `status` | Text | Employment status (Active/Inactive/On Leave) |
| `salesData` | Text | Comma-separated performance metrics |
| `salesDates` | Text | Comma-separated date strings for sparklines |

### Data Format Examples

#### Basic Hierarchical Data
```csv
employeeId,employeeName,managerId,title,department
1,John Smith,,CEO,Executive
2,Jane Doe,1,CFO,Finance
3,Bob Johnson,1,CTO,Technology
4,Alice Brown,2,VP Finance,Finance
5,Charlie Wilson,3,VP Engineering,Technology
```

#### With Images and Status
```csv
employeeId,employeeName,managerId,title,department,imageUrl,status
1,Sarah Johnson,,CEO,Executive,https://example.com/photos/sarah.jpg,Active
2,Michael Chen,1,CTO,Technology,https://example.com/photos/michael.jpg,Active
3,Emily Davis,1,CFO,Finance,https://example.com/photos/emily.jpg,Active
```

#### With Performance Data
```csv
employeeId,employeeName,managerId,salesData,salesDates
1,John Smith,,"120,135,142,158,165","2024-01-01,2024-02-01,2024-03-01,2024-04-01,2024-05-01"
2,Jane Doe,1,"110,118,125,132,140","2024-01-15,2024-02-15,2024-03-15,2024-04-15,2024-05-15"
```

### Data Validation

#### Common Issues and Solutions

**❌ Issue**: "No data to display"
- **Cause**: Missing required fields or incorrect field mapping
- **Solution**: Ensure `employeeId`, `employeeName`, and `managerId` are properly mapped

**❌ Issue**: "Circular reference detected"
- **Cause**: An employee is listed as their own manager or creates a loop
- **Solution**: Check that no `employeeId` appears in the `managerId` column for its own record

**❌ Issue**: "Orphaned employees"
- **Cause**: Employees with invalid manager IDs
- **Solution**: Ensure all `managerId` values exist as `employeeId` values, or leave empty for top-level

**❌ Issue**: Visual shows as empty
- **Cause**: Data type mismatches or null values in required fields
- **Solution**: Check data types and ensure required fields have valid values

### Sample Data
Download `sample-org-data.csv` from the repository to see a complete example with 50 employees across multiple departments with performance data.

---

## Visual Configuration

### Adding the Visual to Your Report

1. **Open Power BI Desktop**
2. **Load your data** (CSV, database, etc.)
3. **Click the PowerFlow icon** in the visualizations pane
4. **Drag fields** from your data to the visual fields:
   - **Employee ID** → `employeeId`
   - **Employee Name** → `employeeName`
   - **Manager ID** → `managerId`
   - **Title** → `title` (optional)
   - **Department** → `department` (optional)
   - **Image URL** → `imageUrl` (optional)
   - **Status** → `status` (optional)
   - **Sales Data** → `salesData` (optional)
   - **Sales Dates** → `salesDates` (optional)

### Field Mapping

#### Required Fields (Must be mapped)
- **Employee ID**: Unique identifier
- **Employee Name**: Display name
- **Manager ID**: Hierarchical relationship

#### Optional Fields (Enhance functionality)
- **Title**: Shows under employee name
- **Department**: Used for color coding
- **Image URL**: Profile pictures
- **Status**: Active/Inactive indicators
- **Sales Data**: Performance sparklines
- **Sales Dates**: Timeline for sparklines

---

## Using the Org Chart

### Navigation

#### Zoom Controls
- **Mouse Wheel**: Zoom in/out
- **Zoom Buttons**: Use +/- buttons in the visual header
- **Fit to Screen**: Auto-adjust zoom to show entire org chart
- **Reset Zoom**: Return to default zoom level

#### Pan Controls
- **Click and Drag**: Move around the org chart
- **Pan Buttons**: Arrow buttons for precise movement
- **Center View**: Return to center of the hierarchy

### Interactivity

#### Node Interaction
- **Click**: Select employee (highlights node)
- **Double-click**: Expand/collapse subtree
- **Hover**: Show detailed tooltip
- **Right-click**: Context menu (if enabled)

#### Selection
- **Single Select**: Click any employee node
- **Multi-select**: Hold Ctrl and click multiple nodes
- **Cross-filtering**: Selected employees filter other visuals

### Tooltips

When you hover over an employee node, you'll see:
- **Employee Name** and **Title**
- **Department** and **Status**
- **Manager Name** (if applicable)
- **Performance Metrics** (if sales data provided)
- **Sparkline Chart** showing trends

### Expand/Collapse

- **Individual Nodes**: Double-click to expand/collapse
- **Expand All**: Show entire organization
- **Collapse All**: Show only top level
- **Level Control**: Expand to specific levels

---

## Customization Options

### Layout Settings

#### Layout Type
- **Tree**: Traditional hierarchical layout
- **Compact Tree**: Space-efficient layout
- **Linear**: Horizontal or vertical line layout

#### Orientation
- **Top to Bottom**: Standard org chart
- **Bottom to Top**: Inverted hierarchy
- **Left to Right**: Horizontal layout
- **Right to Left**: Right-to-left languages

#### Node Spacing
- **Horizontal Spacing**: Distance between nodes (50-200px)
- **Vertical Spacing**: Distance between levels (50-200px)

### Visual Styling

#### Node Appearance
- **Node Width**: 60-200 pixels
- **Node Height**: 40-150 pixels
- **Border Width**: 1-5 pixels
- **Border Radius**: 0-20 pixels (rounded corners)

#### Colors
- **Department Colors**: Automatic color assignment
- **Custom Color Palette**: Define your own colors
- **Status Colors**: Different colors for Active/Inactive/On Leave
- **Background Color**: Visual background
- **Connection Lines**: Color and thickness

#### Typography
- **Font Family**: System fonts or custom
- **Font Size**: 8-24pt for names and titles
- **Font Color**: Text color
- **Font Weight**: Normal or bold

### Interactive Features

#### Navigation
- **Enable Zoom**: Mouse wheel zooming
- **Enable Pan**: Click and drag navigation
- **Show Controls**: Zoom/pan buttons
- **Auto-fit**: Automatically adjust to content

#### Tooltips
- **Enable Tooltips**: Show on hover
- **Tooltip Style**: Compact or detailed
- **Show Images**: Include profile pictures in tooltips
- **Show Metrics**: Display performance data

#### Selection
- **Enable Selection**: Allow node selection
- **Multi-select**: Allow multiple selections
- **Cross-filtering**: Filter other visuals
- **Highlight Selection**: Visual feedback

### Sparklines Configuration

#### Data Display
- **Enable Sparklines**: Show trend charts
- **Sparkline Height**: 20-50 pixels
- **Color Coding**: Positive/negative trends
- **Animation**: Smooth transitions

#### Trend Indicators
- **Positive Color**: Green for increasing trends
- **Negative Color**: Red for decreasing trends
- **Neutral Color**: Gray for stable trends
- **Threshold**: Define trend sensitivity

---

## Troubleshooting

### Common Issues

#### Visual Not Loading
**Symptoms**: Visual appears empty or shows error
**Solutions**:
1. Check that required fields are mapped
2. Verify data types are correct
3. Ensure no circular references in hierarchy
4. Try refreshing the visual

#### Performance Issues
**Symptoms**: Slow loading or unresponsive
**Solutions**:
1. Limit dataset to <500 employees for optimal performance
2. Remove unnecessary columns
3. Use efficient data types
4. Disable animations if needed

#### Layout Problems
**Symptoms**: Nodes overlapping or misaligned
**Solutions**:
1. Adjust node spacing in formatting options
2. Change layout type (Tree vs Compact Tree)
3. Modify node sizes
4. Check for very long names

#### Images Not Showing
**Symptoms**: Profile pictures don't appear
**Solutions**:
1. Verify image URLs are accessible
2. Check URL format (must be http/https)
3. Ensure images are reasonable size (<100KB)
4. Use placeholder images if needed

#### Sparklines Not Working
**Symptoms**: No trend charts visible
**Solutions**:
1. Check that sales data is comma-separated numbers
2. Verify sales dates are in correct format
3. Ensure both fields are mapped
4. Check data consistency

### Error Messages

#### "No data to display"
- Required fields not mapped
- Data source is empty
- Visual filters hiding all data

#### "Circular reference detected"
- Employee listed as their own manager
- Hierarchy contains loops
- Invalid manager IDs

#### "Invalid data format"
- Wrong data types in fields
- Malformed URLs or dates
- Inconsistent data structure

### Getting Help

1. **Check this manual** for common solutions
2. **Review sample data** format
3. **Test with sample data** first
4. **Report issues** on GitHub with:
   - Power BI version
   - Data sample (anonymized)
   - Screenshot of error
   - Steps to reproduce

---

## Best Practices

### Data Management

#### Data Quality
- Use consistent naming conventions
- Validate hierarchy relationships
- Clean up inactive employees
- Regular data updates

#### Performance Optimization
- Limit to 500 employees for best performance
- Use efficient data types
- Minimize text field lengths
- Compress images before hosting

#### Hierarchy Design
- Keep hierarchy depth reasonable (<8 levels)
- Balance branch sizes
- Use clear naming conventions
- Regular structure validation

### Visual Design

#### Layout Choices
- Choose layout based on organization size
- Consider screen real estate
- Test different orientations
- Use compact layout for large orgs

#### Color Strategy
- Use department-based coloring
- Maintain color consistency
- Consider color-blind users
- Use meaningful color associations

#### Information Hierarchy
- Prioritize important information
- Use appropriate font sizes
- Balance text and visuals
- Consider mobile users

### User Experience

#### Navigation
- Enable zoom and pan for large orgs
- Provide clear navigation controls
- Use tooltips for additional info
- Consider user familiarity

#### Interactivity
- Enable appropriate selection modes
- Use cross-filtering strategically
- Provide clear visual feedback
- Test on target devices

---

## FAQ

### General Questions

**Q: Is PowerFlow free to use?**
A: Yes, PowerFlow is completely free for personal and commercial use.

**Q: Does it work with Power BI Service?**
A: Yes, fully compatible with Power BI Service, including mobile apps.

**Q: What's the maximum number of employees supported?**
A: Tested with up to 1000 employees. For best performance, limit to 500.

**Q: Can I use it with live data connections?**
A: Yes, works with all Power BI data sources including DirectQuery.

### Technical Questions

**Q: Why are my images not showing?**
A: Ensure image URLs are publicly accessible and use HTTPS. Images should be <100KB.

**Q: How do I fix layout issues?**
A: Adjust node spacing and size in the formatting pane. Try different layout types.

**Q: Can I customize the color scheme?**
A: Yes, use the formatting options to define custom colors for departments and statuses.

**Q: Why is the visual slow with my data?**
A: Large datasets (>500 employees) can impact performance. Consider filtering or summarizing data.

### Data Questions

**Q: What if I don't have manager IDs?**
A: You can create a flat structure by leaving manager IDs empty, or use a separate hierarchy field.

**Q: Can I have multiple top-level executives?**
A: Yes, simply leave manager ID empty for all top-level positions.

**Q: How do I handle matrix organizations?**
A: For complex reporting structures, consider using the primary reporting relationship.

**Q: Can I include contractors or external staff?**
A: Yes, treat them like regular employees with appropriate status indicators.

### Feature Questions

**Q: Can I export the org chart?**
A: Power BI's export features work with PowerFlow for PDF and PowerPoint.

**Q: Does it support mobile devices?**
A: Yes, responsive design works on tablets and phones.

**Q: Can I embed it in other applications?**
A: Yes, published Power BI reports with PowerFlow can be embedded.

**Q: Are there keyboard shortcuts?**
A: Standard Power BI navigation works. Visual-specific shortcuts may be added in future updates.

---

## Support

- **Documentation**: https://github.com/TALASSX/PowerFlow
- **Issues & Bug Reports**: https://github.com/TALASSX/PowerFlow/issues
- **Feature Requests**: https://github.com/TALASSX/PowerFlow/issues
- **Sample Data**: https://github.com/TALASSX/PowerFlow/raw/main/sample-org-data.csv

For additional support, please provide:
- Power BI Desktop version
- Data structure sample (anonymized)
- Screenshot of the issue
- Steps to reproduce the problem

---

*Last updated: October 2025*
*PowerFlow Version: 1.0.0*</content>
<parameter name="filePath">C:\Users\rocks\OneDrive\Desktop\OrgChartVisual\docs-repo\USER_MANUAL.md