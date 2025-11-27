# ChartMaster.js

A lightweight, feature-rich JavaScript charting library with no dependencies. Create beautiful, interactive charts with smooth animations and modern design.

## Features

### Chart Types
- **Line Chart** - Smooth curves with optional fill
- **Bar Chart** - Vertical bars with rounded corners
- **Pie Chart** - Classic circular segments
- **Doughnut Chart** - Pie chart with hollow center
- **Funnel Chart** - Conversion/process visualization
- **Gauge Chart** - Speedometer-style metric display

### Interactive Features
- **Hover Effects** - Interactive tooltips and highlights
- **Click Events** - Custom click handlers
- **Detailed View** - Double-click for in-depth data analysis
- **Touch Support** - Full mobile and tablet compatibility
- **Responsive** - Auto-resize on window changes

### Animation
- **Smooth Animations** - Multiple easing functions
- **Configurable Duration** - Control animation speed
- **Progressive Rendering** - Staggered element appearance

### Customization
- **Custom Colors** - Full color control for all elements
- **Flexible Layout** - Adjustable padding and spacing
- **Legend** - Show/hide with positioning options
- **Grid & Axes** - Configurable display options
- **Background Color** - Set canvas background

## Installation

Include the script in your HTML:

```html
<script src="ChartMaster.js"></script>
```

## Quick Start

```html
<canvas id="myChart" width="600" height="400"></canvas>

<script>
  const chart = new ChartMaster('myChart', {
    type: 'line',
    data: {
      labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May'],
      datasets: [{
        data: [12, 19, 3, 5, 2],
        borderColor: '#3b82f6',
        backgroundColor: '#3b82f6'
      }]
    }
  });
</script>
```

## Chart Types

### Line Chart

```javascript
new ChartMaster('canvas', {
  type: 'line',
  data: {
    labels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri'],
    datasets: [{
      data: [12, 19, 3, 5, 15],
      borderColor: '#3b82f6',
      backgroundColor: '#3b82f6'
    }]
  },
  options: {
    elements: {
      line: {
        tension: 0.4,  // Curve smoothness
        fill: true     // Fill under line
      }
    }
  }
});
```

### Bar Chart

```javascript
new ChartMaster('canvas', {
  type: 'bar',
  data: {
    labels: ['Q1', 'Q2', 'Q3', 'Q4'],
    datasets: [{
      data: [45, 67, 89, 72],
      backgroundColor: ['#ef4444', '#f59e0b', '#10b981', '#3b82f6']
    }]
  }
});
```

### Pie Chart

```javascript
new ChartMaster('canvas', {
  type: 'pie',
  data: {
    labels: ['Red', 'Blue', 'Yellow'],
    datasets: [{
      data: [300, 50, 100],
      backgroundColor: ['#ef4444', '#3b82f6', '#f59e0b']
    }]
  }
});
```

### Doughnut Chart

```javascript
new ChartMaster('canvas', {
  type: 'doughnut',
  data: {
    labels: ['Desktop', 'Mobile', 'Tablet'],
    datasets: [{
      data: [60, 30, 10],
      backgroundColor: ['#3b82f6', '#10b981', '#f59e0b']
    }]
  }
});
```

### Funnel Chart

```javascript
new ChartMaster('canvas', {
  type: 'funnel',
  data: {
    labels: ['Visitors', 'Signups', 'Active', 'Paid'],
    datasets: [{
      data: [1000, 500, 250, 100],
      backgroundColor: ['#3b82f6', '#10b981', '#f59e0b', '#ef4444']
    }]
  },
  options: {
    funnel: {
      width: 0.7,      // Funnel width (70% of chart area)
      gap: 0.02,       // Gap between segments
      sort: 'desc'     // Sort: 'desc', 'asc', 'none'
    }
  }
});
```

### Gauge Chart

```javascript
new ChartMaster('canvas', {
  type: 'gauge',
  data: {
    labels: ['Performance'],
    datasets: [{
      data: [75]  // Value between 0-100
    }]
  },
  options: {
    gauge: {
      startAngle: -135,
      endAngle: 135,
      thickness: 0.25,
      showValue: true,
      valueFormat: (value) => value.toFixed(1) + '%',
      ranges: [
        { min: 0, max: 33, color: '#ef4444' },   // Red
        { min: 33, max: 66, color: '#f59e0b' },  // Orange
        { min: 66, max: 100, color: '#10b981' }  // Green
      ]
    }
  }
});
```

## Configuration Options

### Global Options

```javascript
{
  responsive: true,              // Auto-resize on window resize
  maintainAspectRatio: true,     // Maintain aspect ratio
  backgroundColor: '#ffffff',    // Canvas background color
  
  animation: {
    duration: 800,               // Animation duration in ms
    easing: 'easeOutQuart'       // Easing function
  },
  
  layout: {
    padding: {
      top: 20,
      right: 20,
      bottom: 20,
      left: 20
    }
  }
}
```

### Plugins

```javascript
plugins: {
  title: {
    display: true,
    text: 'My Chart',
    color: '#333',
    font: {
      size: 16,
      weight: 'bold',
      family: 'Arial'
    },
    padding: 20
  },
  
  legend: {
    display: true,
    position: 'top',  // 'top' or 'bottom'
    labels: {
      color: '#666',
      font: {
        size: 12,
        family: 'Arial'
      },
      padding: 10
    }
  },
  
  tooltip: {
    enabled: true,
    mode: 'nearest'
  }
}
```

### Scales (Line & Bar Charts)

```javascript
scales: {
  x: {
    display: true,
    grid: {
      display: true,
      color: 'rgba(0, 0, 0, 0.08)'
    },
    ticks: {
      color: '#666',
      font: { size: 11 }
    }
  },
  y: {
    display: true,
    beginAtZero: true,
    grid: {
      display: true,
      color: 'rgba(0, 0, 0, 0.08)'
    },
    ticks: {
      color: '#666',
      font: { size: 11 }
    }
  }
}
```

### Elements

```javascript
elements: {
  line: {
    borderWidth: 2,
    tension: 0.4,      // 0 = straight, 1 = very curved
    fill: false
  },
  
  point: {
    radius: 3,
    hoverRadius: 5,
    hitRadius: 10      // Hit detection area
  },
  
  bar: {
    borderWidth: 0,
    borderRadius: 4
  },
  
  arc: {
    borderWidth: 2,
    borderColor: '#fff',
    hoverOffset: 10    // Offset on hover for pie/doughnut
  }
}
```

### Detailed View

```javascript
detailedView: {
  enabled: true,
  trigger: 'doubleClick',  // 'doubleClick' or 'longPress'
  showStats: true,         // Show statistics (avg, median, etc.)
  showRawData: false       // Show all data points
}
```

## Events

### onClick

```javascript
onClick: function(event, index, data, chart) {
  console.log('Clicked:', data.label, data.value);
}
```

### onHover

```javascript
onHover: function(event, index, data, chart) {
  if (data) {
    console.log('Hovering:', data.label);
  }
}
```

### onDetailedView

```javascript
onDetailedView: function(event, index, data, chart) {
  console.log('Detailed view opened for:', data.label);
}
```

## Methods

### update()

Update chart data or options:

```javascript
chart.update({
  data: {
    labels: ['A', 'B', 'C'],
    datasets: [{
      data: [10, 20, 30]
    }]
  }
});
```

### setBackgroundColor()

Change background color:

```javascript
chart.setBackgroundColor('#f0f0f0');
```

### render()

Re-render chart with animation:

```javascript
chart.render();
```

### redraw()

Redraw chart without animation:

```javascript
chart.redraw();
```

### destroy()

Clean up and remove chart:

```javascript
chart.destroy();
```

## Animation Easing Functions

Available easing functions:
- `linear`
- `easeInQuad`
- `easeOutQuad`
- `easeInOutQuad`
- `easeOutQuart` (default)
- `easeInOutCubic`
- `easeOutElastic`

```javascript
options: {
  animation: {
    duration: 1000,
    easing: 'easeOutElastic'
  }
}
```

## Color Formats

ChartMaster supports multiple color formats:

```javascript
// Hex
backgroundColor: '#3b82f6'

// RGB
backgroundColor: 'rgb(59, 130, 246)'

// Color arrays (for multiple elements)
backgroundColor: ['#ef4444', '#10b981', '#3b82f6']
```

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile browsers (iOS Safari, Chrome Mobile)

## Performance Tips

1. **Use appropriate canvas size** - Larger canvases require more processing
2. **Limit data points** - For line charts, consider data sampling for large datasets
3. **Disable animations** - Set `animation.duration: 0` for instant rendering
4. **Cache instances** - Reuse chart instances with `update()` instead of recreating

## Examples

### Multi-Color Bar Chart

```javascript
new ChartMaster('canvas', {
  type: 'bar',
  data: {
    labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple'],
    datasets: [{
      data: [12, 19, 3, 5, 2],
      backgroundColor: [
        '#ef4444',
        '#3b82f6',
        '#f59e0b',
        '#10b981',
        '#8b5cf6'
      ]
    }]
  }
});
```

### Filled Line Chart

```javascript
new ChartMaster('canvas', {
  type: 'line',
  data: {
    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
    datasets: [{
      data: [0, 10, 5, 15, 10, 20],
      borderColor: '#3b82f6',
      backgroundColor: '#3b82f6'
    }]
  },
  options: {
    elements: {
      line: {
        fill: true,
        tension: 0.4
      }
    }
  }
});
```

### Custom Gauge with Click Handler

```javascript
new ChartMaster('canvas', {
  type: 'gauge',
  data: {
    labels: ['CPU Usage'],
    datasets: [{ data: [67] }]
  },
  options: {
    gauge: {
      valueFormat: (value) => value.toFixed(0) + '%',
      ranges: [
        { min: 0, max: 50, color: '#10b981' },
        { min: 50, max: 80, color: '#f59e0b' },
        { min: 80, max: 100, color: '#ef4444' }
      ]
    },
    onClick: function(e, index, data) {
      alert('CPU Usage: ' + data.value + '%');
    }
  }
});
```

## License

MIT License - Feel free to use in personal and commercial projects.

## Version

Current version: 3.0.0

## Support

For issues and feature requests, please refer to the project repository.