# Customizing Qlik Sense Dashboards with CSS

Qlik Sense allows visual customization through CSS code embedded within KPI objects. This tutorial walks you through how to apply custom styles across your dashboards to improve layout consistency, visual hierarchy, and overall design polish.

## What You Can Customize

Using CSS in Qlik Sense lets you control:

- Background color  
- Chart container appearance (shadows, padding, rounded corners)  
- Title alignment and typography  
- KPI styling  
- Tab appearance

Note: this method does not modify measure or dimension colors directly. It targets the shared HTML classes that Qlik Sense assigns to layout and chart components, making them reusable across dashboards.

## Step 1: Create the Styling KPI Object

- Create a KPI object  
- Add the CSS code inside the KPI’s Styles section under “Styles (CSS)”, where you can simply paste the code  
- Make the KPI visually hidden:  
  - Set its background color to match the sheet’s background  
  - Resize it into a small square (one tile)  
  - Place it at the top of the sheet for easy access  

Tip: Add this KPI as a master item so changes automatically apply across all sheets that use it.

## Step 2: Add Custom Styling

The CSS code targets HTML classes used by Qlik Sense to style common dashboard elements. Below are examples of classes you can customize and how to modify them.

### Background Style

I like to give my dashboards a soft gradient background to make them look more polished and modern. This style targets the entire sheet and applies a vertical blue gradient:

```css
/* Apply a light blue gradient background to the whole sheet */
.qv-panel-sheet {
    background: linear-gradient(180deg, #addbeb 0%, #46add2 100%);
}
```

This sets the overall tone of the dashboard and helps make other elements like containers and KPIs stand out more cleanly.

### Container & Visualization Styling


#### Container Styling – .qv-object-container

This styles the outer container around each visualization, giving it padding, soft shadows, and rounded corners:

```css
.qv-object-container {
    background-color: rgba(231, 242, 254, 0.8);
    border-radius: 15px;
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.7);
    padding: 0px 2px 5px 2px;
    margin: 0px 2px 10px 2px;
}
```

#### Visualization Styling (Inside Containers)

The visual elements themselves—charts, tables, and combos—inherit a similar background, with less transparency for better visual focus:

```css
.qv-object-container .qv-object,
.qv-object-pivot-table,
.qv-object-barchart,
.qv-object-linechart,
.qv-object-table,
.qv-object-combochart,
.qv-object-piechart {
    background-color: rgba(231, 242, 253, 1);
    border-radius: 15px;
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.7);
    margin: 0px 2px 10px 2px;
}
```

### Tab Styling

```css
.qsc-tab-row .lui-tab {
    color: black !important;
    cursor: pointer !important;
}
```

```css
.qv-object-kpi {
    background-color: rgba(91, 182, 215, 0);
    border-radius: 1px;
    padding: 5px;
    margin: 5px 0;
    color: white;
}
```

## Finding New Classes

Most of the commonly used Qlik Sense classes are already included in the examples above. However, if you add a visualization that isn’t styled yet, you may need to identify its HTML class manually.

To find and identify a new class:

- Press F12 to open your browser’s Developer Tools  
- Use the Inspect Element tool (the arrow icon in the top-left corner of the panel)  
- Click on the visualization or element you want to style  
- Look through the HTML hierarchy around the selected element to find the relevant class names (they often begin with `.qv-object-` or similar)  
- Once identified, you can target that class in your CSS and test styling changes using trial and error  

Finding the exact class using the Inspect Element tool can sometimes be tricky. A useful tip is to click directly on the visualization you want to style, then explore the HTML lines around your selection — the relevant class is often one or two layers above or below what you first click.

For example, a KPI object includes several classes — for the title, value, and container — all of which can be styled independently. I usually experiment with these classes in the CSS and use trial and error to see which one controls the specific part I want to modify.

Tip: If you're struggling to find the correct class, try copying the entire HTML element and pasting it into ChatGPT. This may help guide you to the relevant class more efficiently.

Make sure that the theme is "Sense Classic".

## Possible Enhancements 

- Dark mode theme  
- Project-based themes (different palettes or layouts for different dashboards)  
- Hover effects (test carefully — they sometimes blur visualizations)
