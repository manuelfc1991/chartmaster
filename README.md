# ChartMaster.js - Complete Documentation

## Table of Contents
1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Basic Usage](#basic-usage)
4. [Chart Types](#chart-types)
5. [Configuration Options](#configuration-options)
6. [Methods](#methods)
7. [Events](#events)
8. [Advanced Features](#advanced-features)
9. [Working Examples](#working-examples)

---

## Introduction

ChartMaster.js is a professional, lightweight JavaScript charting library built on HTML5 Canvas. It provides beautiful, interactive charts with smooth animations, tooltips, and advanced features like detailed views.

**Key Features:**
- 9 chart types (Line, Bar, Horizontal Bar, Pie, Doughnut, Funnel, Gauge, Waterfall, Conversion Funnel)
- Smooth animations with multiple easing functions
- Interactive tooltips and detailed views
- Responsive design
- Touch support
- Gradient effects and shadows
- Zero dependencies

---

## Installation

### Option 1: Direct Include
```html
<script src="ChartMaster.js"></script>
```

### Option 2: Module Import
```javascript
const ChartMaster = require('./ChartMaster.js');
```

---

## Basic Usage

### HTML Structure
```html
<canvas id="myChart" width="800" height="400"></canvas>
```

### JavaScript Initialization
```javascript
const chart = new ChartMaster('myChart', {
    type: 'line',
    data: {
        labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May'],
        datasets: [{
            data: [12, 19, 3, 5, 2],
            backgroundColor: '#3b82f6',
            borderColor: '#2563eb'
        }]
    },
    options: {
        // Configuration options
    }
});
```

---

## Chart Types

### 1. Line Chart
Displays data as connected points on a line.

**Type:** `'line'`

**Dataset Properties:**
- `data`: Array of numbers
- `borderColor`: Line color (string)
- `backgroundColor`: Fill color (string)
- `borderWidth`: Line thickness (number, default: 3)

### 2. Bar Chart
Displays vertical bars.

**Type:** `'bar'`

**Dataset Properties:**
- `data`: Array of numbers
- `backgroundColor`: Bar colors (string or array)
- `borderColor`: Border color (string)
- `borderWidth`: Border thickness (number)

### 3. Horizontal Bar Chart
Displays horizontal bars.

**Type:** `'horizontalBar'`

**Dataset Properties:**
Same as Bar Chart

### 4. Pie Chart
Displays circular segments.

**Type:** `'pie'`

**Dataset Properties:**
- `data`: Array of numbers
- `backgroundColor`: Array of colors for each segment

### 5. Doughnut Chart
Pie chart with hollow center.

**Type:** `'doughnut'`

**Dataset Properties:**
Same as Pie Chart

### 6. Funnel Chart
Displays descending stages.

**Type:** `'funnel'`

**Dataset Properties:**
- `data`: Array of numbers
- `backgroundColor`: Array of colors

**Special Options:**
- `funnel.width`: Funnel width ratio (0-1, default: 0.7)
- `funnel.gap`: Gap between segments (0-1, default: 0.02)
- `funnel.sort`: Sort order ('desc', 'asc', or 'none')

### 7. Gauge Chart
Displays single value on arc.

**Type:** `'gauge'`

**Dataset Properties:**
- `data`: Array with single number (0-100)

**Special Options:**
- `gauge.startAngle`: Start angle in degrees (default: -135)
- `gauge.endAngle`: End angle in degrees (default: 135)
- `gauge.thickness`: Arc thickness ratio (default: 0.22)
- `gauge.showValue`: Show center value (boolean)
- `gauge.valueFormat`: Function to format value
- `gauge.ranges`: Array of color ranges

### 8. Waterfall Chart
Shows cumulative effect of sequential values.

**Type:** `'waterfall'`

**Dataset Properties:**
- `data`: Array of numbers (positive/negative)
- `isTotal`: Array of booleans marking total bars

**Special Options:**
- `waterfall.positiveColor`: Color for positive values
- `waterfall.negativeColor`: Color for negative values
- `waterfall.totalColor`: Color for total bars
- `waterfall.connectorLine`: Show connector lines (boolean)
- `waterfall.showValues`: Show value labels (boolean)

### 9. Conversion Funnel Chart
Shows conversion rates between stages.

**Type:** `'conversionFunnel'`

**Dataset Properties:**
- `data`: Array of numbers (descending values)

**Special Options:**
- `conversionFunnel.width`: Bar width ratio (default: 0.8)
- `conversionFunnel.showConversionRates`: Show rates (boolean)
- `conversionFunnel.showValues`: Show values on bars (boolean)
- `conversionFunnel.valueFontSize`: Value text size
- `conversionFunnel.labelFontSize`: Label text size

---

## Configuration Options

### Core Options

#### `type` (string)
Chart type: `'line'`, `'bar'`, `'horizontalBar'`, `'pie'`, `'doughnut'`, `'funnel'`, `'gauge'`, `'waterfall'`, `'conversionFunnel'`

#### `data` (object)
```javascript
data: {
    labels: ['Label1', 'Label2', ...],
    datasets: [{
        data: [value1, value2, ...],
        backgroundColor: '#color' or ['#color1', '#color2', ...],
        borderColor: '#color',
        borderWidth: number
    }]
}
```

#### `backgroundColor` (string)
Canvas background color (default: `'#ffffff'`)

---

### Animation Options

```javascript
animation: {
    duration: 900,           // Animation duration in ms
    easing: 'easeOutQuart'   // Easing function
}
```

**Available Easing Functions:**
- `'linear'`
- `'easeInQuad'`
- `'easeOutQuad'`
- `'easeInOutQuad'`
- `'easeOutQuart'` (default)
- `'easeInOutCubic'`
- `'easeOutElastic'`
- `'easeOutBack'`

---

### Plugin Options

#### Title Plugin
```javascript
plugins: {
    title: {
        display: false,
        text: 'Chart Title',
        color: '#1a1a1a',
        font: {
            size: 18,
            weight: 'bold',
            family: 'Arial'
        },
        padding: {
            top: 12,
            bottom: 16
        },
        align: 'center'  // 'start', 'center', 'end'
    }
}
```

#### Legend Plugin
```javascript
plugins: {
    legend: {
        display: true,
        position: 'top',  // 'top', 'bottom', 'left', 'right'
        align: 'center',  // 'start', 'center', 'end'
        labels: {
            color: '#666',
            font: {
                size: 12,
                family: 'Arial',
                weight: '500'
            },
            padding: 14,
            boxWidth: 14,
            usePointStyle: false
        },
        padding: 16
    }
}
```

#### Tooltip Plugin
```javascript
plugins: {
    tooltip: {
        enabled: true,
        mode: 'nearest'  // Interaction mode
    }
}
```

#### Detailed View Plugin
```javascript
plugins: {
    detailedView: {
        enabled: true,
        trigger: 'doubleClick',  // 'doubleClick', 'longPress', 'click'
        position: 'auto',        // 'auto', 'top', 'bottom', 'left', 'right'
        showStats: true,         // Show statistics
        showRawData: false,      // Show all data points
        customFields: [          // Add custom fields
            {
                label: 'Custom Field',
                value: function(data, index, chart) {
                    return 'Custom Value';
                }
            }
        ],
        template: null,          // Custom HTML template function
        style: {}                // Custom CSS properties
    }
}
```

---

### Scale Options

#### X-Axis
```javascript
scales: {
    x: {
        display: true,
        title: {
            display: false,
            text: 'X-Axis Label',
            color: '#666',
            font: {
                size: 12,
                family: 'Arial'
            }
        },
        grid: {
            display: true,
            color: 'rgba(0, 0, 0, 0.06)'
        },
        ticks: {
            padding: 10,
            maxRotation: 0,
            color: '#666'
        }
    }
}
```

#### Y-Axis
```javascript
scales: {
    y: {
        display: true,
        beginAtZero: true,
        title: {
            display: false,
            text: 'Y-Axis Label',
            color: '#666',
            font: {
                size: 12,
                family: 'Arial'
            }
        },
        grid: {
            display: true,
            color: 'rgba(0, 0, 0, 0.06)'
        },
        ticks: {
            padding: 10,
            color: '#666'
        }
    }
}
```

---

### Layout Options

```javascript
layout: {
    padding: {
        top: 20,
        right: 20,
        bottom: 20,
        left: 20
    },
    autoPadding: true
}
```

---

### Element Options

#### Line Elements
```javascript
elements: {
    line: {
        borderWidth: 3,
        tension: 0.4,      // Curve tension (0 = straight)
        fill: false,       // Fill area under line
        gradient: true,    // Use gradient fill
        shadow: true,      // Drop shadow
        glowEffect: false  // Glow effect
    }
}
```

#### Point Elements
```javascript
elements: {
    point: {
        radius: 4,
        hoverRadius: 6,
        hitRadius: 12,     // Click detection radius
        shadow: true
    }
}
```

#### Bar Elements
```javascript
elements: {
    bar: {
        borderWidth: 0,
        borderRadius: 6,
        gradient: true,
        shadow: true,
        hoverScale: 1.03   // Scale on hover
    }
}
```

#### Arc Elements (Pie/Doughnut)
```javascript
elements: {
    arc: {
        borderWidth: 3,
        borderColor: '#fff',
        hoverOffset: 12,
        shadow: true
    }
}
```

---

## Methods

### `render()`
Renders the chart with animation.

```javascript
chart.render();
```

### `redraw()`
Redraws the chart immediately without animation.

```javascript
chart.redraw();
```

### `update(newData)`
Updates chart with new data or options.

```javascript
chart.update({
    data: newDataObject,
    options: newOptionsObject,
    type: 'bar',
    backgroundColor: '#f0f0f0'
});
```

### `setBackgroundColor(color)`
Changes canvas background color.

```javascript
chart.setBackgroundColor('#ffffff');
```

### `destroy()`
Removes event listeners and cleans up.

```javascript
chart.destroy();
```

### `clear()`
Clears the canvas.

```javascript
chart.clear();
```

---

## Events

### `onClick`
Triggered when an element is clicked.

```javascript
options: {
    onClick: function(event, index, data, chart) {
        console.log('Clicked:', data);
    }
}
```

### `onHover`
Triggered when hovering over an element.

```javascript
options: {
    onHover: function(event, index, data, chart) {
        console.log('Hovered:', data);
    }
}
```

### `onDetailedView`
Triggered when detailed view is opened.

```javascript
options: {
    onDetailedView: function(event, index, data, chart) {
        console.log('Detailed view opened:', data);
    }
}
```

---

## Advanced Features

### Custom Detailed View Template

```javascript
plugins: {
    detailedView: {
        enabled: true,
        template: function(data, stats, chart) {
            return `
                <h4>Custom Template</h4>
                <div class="data-point">
                    <span>Value:</span>
                    <span>${data.value}</span>
                </div>
                <div class="data-point">
                    <span>Average:</span>
                    <span>${stats.average.toFixed(2)}</span>
                </div>
            `;
        }
    }
}
```

### Custom Gauge Ranges

```javascript
gauge: {
    ranges: [
        { min: 0, max: 33, color: '#ef4444' },
        { min: 33, max: 66, color: '#f59e0b' },
        { min: 66, max: 100, color: '#10b981' }
    ]
}
```

### Responsive Design

Charts automatically resize when the window is resized if `responsive: true` (default).

---