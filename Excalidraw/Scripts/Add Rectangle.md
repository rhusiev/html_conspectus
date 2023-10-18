/*
Insert a rectangle
```javascript
*/
// Get script settings
const settings = ea.getScriptSettings();
let padding = settings["Default padding"]?.value || 10;

// Prompt for padding if enabled in settings
if (settings["Prompt for padding?"]) {
  const inputPadding = parseInt(await utils.inputPrompt("Padding?", "number", padding.toString()));
  if (isNaN(inputPadding)) {
    new Notice("The padding value provided is not a number");
    return;
  }
  padding = inputPadding;
}

// Get selected elements and add a rectangle with rounded edges around them
const elements = ea.getViewSelectedElements();
const box = ea.getBoundingBox(elements);
const color = ea.getExcalidrawAPI().getAppState().currentItemStrokeColor;

ea.style.strokeColor = color;

const strokeSharpness = "round";
const strokeWidth = 2;
const strokeColor = "#eceff4";
const strokeStyle = "solid";
const roughness = 0;
const fillStyle = "solid";
const backgroundColor = "#3b4252";
const roundness = { type: 3 };
const width = 180;
const height = 60;

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

const rectangleX = -scrollX + visibleWidth / 2 - width / 2;
const rectangleY = -scrollY + visibleHeight / 2 - height / 2;

const rectangleId = ea.addRect(rectangleX, rectangleY, width, height);
const rectangle = ea.getElement(rectangleId);
rectangle.strokeSharpness = strokeSharpness;
rectangle.strokeWidth = strokeWidth;
rectangle.strokeColor = strokeColor;
rectangle.strokeStyle = strokeStyle;
rectangle.roughness = roughness;
rectangle.fillStyle = fillStyle;
rectangle.backgroundColor = backgroundColor;
rectangle.roundness = roundness;
rectangle.width = width;
rectangle.height = height;

ea.copyViewElementsToEAforEditing(elements);
ea.addElementsToView(false);
