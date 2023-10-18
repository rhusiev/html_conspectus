/*
Insert a 2D coordinate system with the origin at the center of the visible area
```javascript
*/
// Get selected elements and add a 2D coordinate system to the view
const elements = ea.getViewSelectedElements();
const box = ea.getBoundingBox(elements);
const color = ea.getExcalidrawAPI().getAppState().currentItemStrokeColor;

ea.style.strokeColor = color;

// Get the center of the visible
const api = ea.getExcalidrawAPI();

const appState = api.getAppState();
const scrollX = appState.scrollX;
const scrollY = appState.scrollY;
const zoom = appState.zoom.value;
const canvasWidth = appState.width;
const canvasHeight = appState.height;
const visibleWidth = canvasWidth / zoom;
const visibleHeight = canvasHeight / zoom;

let maxVal = 200;
const x = -scrollX + visibleWidth / 2 - length / 2;
const y = -scrollY + visibleHeight / 2 - length / 2;

const arrowXID = ea.addArrow([[x - maxVal, y], [x + maxVal, y]], { startArrowHead: "none", endArrowHead: "triangle" });
const arrowYID = ea.addArrow([[x, y + maxVal], [x, y - maxVal]], { startArrowHead: "none", endArrowHead: "triangle" });
const arrowX = ea.getElement(arrowXID);
const arrowY = ea.getElement(arrowYID);
arrowX.roughness = 0;
arrowY.roughness = 0;

let lineOneID, lineTwoID, lineOne, lineTwo;
const padding = 20;
maxVal -= padding;
for (let i = -maxVal + 2 * padding; i <= maxVal - 2 * padding; i += padding) {
    if (i === 0) continue;
    lineOneID = ea.addLine([[x - maxVal + padding, y + i], [x + maxVal - padding, y + i]]);
    lineTwoID = ea.addLine([[x + i, y - maxVal + padding], [x + i, y + maxVal - padding]]);
    lineOne = ea.getElement(lineOneID);
    lineTwo = ea.getElement(lineTwoID);
    lineOne.strokeWidth = 0.2;
    lineTwo.strokeWidth = 0.2;
    lineOne.roughness = 0;
    lineTwo.roughness = 0;
}

ea.copyViewElementsToEAforEditing(elements);
ea.addElementsToView(false);
