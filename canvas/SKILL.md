# Canvas Skill

Create visual diagrams, flowcharts, mind maps, and drawings using HTML5 Canvas.

## Triggers
- "draw", "diagram", "flowchart", "mindmap", "sketch", "visualize", "chart", "canvas"

## Capabilities

### Diagram Types
- **Flowcharts**: Process flows, decision trees, workflows
- **Mind Maps**: Idea mapping, brainstorming, concept visualization
- **Org Charts**: Team structures, hierarchies
- **Network Diagrams**: System architecture, connections
- **Timelines**: Project schedules, event sequences
- **Simple Drawings**: Shapes, arrows, annotations

## Output

Generate standalone HTML files with embedded Canvas JavaScript that:
- Render immediately in any browser
- Are self-contained (no external dependencies)
- Support responsive sizing
- Include clear labels and colors

## Template

```html
<!DOCTYPE html>
<html>
<head>
  <title>Canvas Diagram</title>
  <style>
    body { margin: 0; display: flex; justify-content: center; align-items: center; min-height: 100vh; background: #f5f5f5; }
    canvas { background: white; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
  </style>
</head>
<body>
  <canvas id="canvas" width="800" height="600"></canvas>
  <script>
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');

    // Helper functions
    function drawBox(x, y, w, h, text, color = '#4A90D9') {
      ctx.fillStyle = color;
      ctx.roundRect(x, y, w, h, 8);
      ctx.fill();
      ctx.fillStyle = 'white';
      ctx.font = 'bold 14px Arial';
      ctx.textAlign = 'center';
      ctx.fillText(text, x + w/2, y + h/2 + 5);
    }

    function drawArrow(fromX, fromY, toX, toY, color = '#333') {
      ctx.strokeStyle = color;
      ctx.lineWidth = 2;
      ctx.beginPath();
      ctx.moveTo(fromX, fromY);
      ctx.lineTo(toX, toY);
      ctx.stroke();
      // Arrowhead
      const angle = Math.atan2(toY - fromY, toX - fromX);
      ctx.beginPath();
      ctx.moveTo(toX, toY);
      ctx.lineTo(toX - 10 * Math.cos(angle - Math.PI/6), toY - 10 * Math.sin(angle - Math.PI/6));
      ctx.lineTo(toX - 10 * Math.cos(angle + Math.PI/6), toY - 10 * Math.sin(angle + Math.PI/6));
      ctx.closePath();
      ctx.fillStyle = color;
      ctx.fill();
    }

    function drawCircle(x, y, r, text, color = '#27AE60') {
      ctx.fillStyle = color;
      ctx.beginPath();
      ctx.arc(x, y, r, 0, Math.PI * 2);
      ctx.fill();
      ctx.fillStyle = 'white';
      ctx.font = 'bold 12px Arial';
      ctx.textAlign = 'center';
      ctx.fillText(text, x, y + 4);
    }

    function drawDiamond(x, y, size, text, color = '#E67E22') {
      ctx.fillStyle = color;
      ctx.beginPath();
      ctx.moveTo(x, y - size);
      ctx.lineTo(x + size, y);
      ctx.lineTo(x, y + size);
      ctx.lineTo(x - size, y);
      ctx.closePath();
      ctx.fill();
      ctx.fillStyle = 'white';
      ctx.font = 'bold 11px Arial';
      ctx.textAlign = 'center';
      ctx.fillText(text, x, y + 4);
    }

    // DRAW YOUR DIAGRAM HERE
    // Example:
    // drawBox(100, 100, 120, 50, 'Start');
    // drawArrow(220, 125, 280, 125);
    // drawDiamond(340, 125, 40, 'Check');

  </script>
</body>
</html>
```

## Colors

| Use | Color |
|-----|-------|
| Primary/Process | #4A90D9 (blue) |
| Success/Start | #27AE60 (green) |
| Warning/Decision | #E67E22 (orange) |
| Error/Stop | #E74C3C (red) |
| Neutral | #95A5A6 (gray) |
| Accent | #9B59B6 (purple) |

## Instructions

1. Understand what the user wants to visualize
2. Choose appropriate diagram type
3. Plan layout (spacing, alignment)
4. Generate complete HTML file
5. Save to workspace and provide path
6. Optionally open in browser for preview

## Save Location

Save diagrams to: `C:\Users\okenw\OneDrive\Documents\claudeclaw\workspace\canvas\`
