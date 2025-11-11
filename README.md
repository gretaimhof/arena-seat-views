**Project:** “Tank Tour” — Akins Ford Arena  
**Delivered To:** Athens Rock Lobsters  

---

## 1. Overview
The **Rock Lobsters Arena Seat Views** website provides an interactive, visual experience for exploring panoramic seat views from *The Tank* at Akins Ford Arena.  

Visitors can:
- View the full seating chart of the arena  
- Hover over glowing seat markers (pins)  
- Click pins or dropdown options to open 360° seat views  
- Seamlessly switch between the arena map and viewer  

All project files are contained in this folder.  
You can also view the **live hosted version** online here:  
> **[https://gretaimhof.github.io/arena-seat-views/](https://gretaimhof.github.io/arena-seat-views/)**

---

## 2. How to Open the Website Locally
You can open the site on any computer without an internet connection.

### Option A — Local (Quick View)
1. Locate **`index.html`** in the main project folder.  
2. Double-click to open it in your web browser (Google Chrome recommended).  

> **Important:**  
> When opened locally (`file:///` path), some browsers may block image loading or interactive features for security reasons.  
> If the map or images do not appear:
> - Try a different browser such as Firefox or Safari.  
> - Or use **Option B** below to open the site through a lightweight local web server.

---

### Option B — Local Web Server (Recommended for Full Functionality)
If you want to view or test the site exactly as it appears online:
1. Open the project folder in **Visual Studio Code (VS Code)**.  
2. Install the extension **“Live Server”** (if not already installed).  
3. Right-click `index.html` → choose **“Open with Live Server.”**  
4. The site will open in your browser and all images will load correctly.  

This avoids browser security restrictions that prevent local image access.

---

## 3. Folder Structure
```
arena-seat-views/
│
├── index.html               ← Main website file
├── /images/                 ← All images used by the site
│   ├── seating_chart_small.jpg   ← Arena background map
│   ├── /100/                      ← Section 100 seat photos
│   ├── /119/                      ← Section 119 seat photos
│   ├── /120/                      ← Section 120 seat photos
│   └── ...                        ← Add new sections as needed
```

---

## 4. Updating Seat Photos
Each section has its own folder inside `/images/`, containing panoramic seat images for that section.

Example:
```
images/100/100 E-2.jpg
images/100/100 H-2.jpg
images/100/100 M-2.jpg
```

### To Add or Replace Seat Photos
1. Open the correct section folder (e.g., `/images/120/`).  
2. Add or replace your 360° seat photos.  
3. Use the exact file naming format:
   ```
   [Section number] [Row letter]-2.jpg
   ```
   Example:
   ```
   120 Q-2.jpg
   ```
4. Save and reopen `index.html` in your browser to see the update.

> The site automatically loads images by their file names — they must match this format exactly.

---

## 5. Updating the Arena Map
The main background seating chart image is stored here:
```
/images/seating_chart_small.jpg
```

### To Replace the Map
1. Save your new seating chart as a `.jpg`.  
2. Use approximately the same proportions (wide rectangle).  
3. Replace the existing `seating_chart_small.jpg` file.  
4. Open `index.html` to confirm that the new map appears correctly.  

If the proportions or layout change significantly, you will need to adjust pin positions (see Section 7).

---

## 6. Managing the Dropdown Menu
Sections and rows are defined at the top of `index.html` inside this code block:
```js
const scenes = {
  "100": { seats: ["E","H","M","Q"] },
  "119": { seats: ["B","E","H","M","Q"] },
  "120": { seats: ["H","M","Q"] },
};
```

### To Add a New Section
1. Open `index.html` in a text editor.  
2. Locate the `const scenes = { ... }` section.  
3. Add your new section using the same format:  
   ```js
   "130": { seats: ["B","E","H","M","Q","R"] },
   ```
4. Save and reload the page — the new section will appear automatically in the dropdown list.

---

## 7. Adding or Moving Seat Pins
Each seat pin is a clickable marker that opens a 360° seat view.  
Pins are defined in `index.html` under the `pinMarkers` array and use **percentage-based coordinates** to stay positioned correctly no matter the screen size.

### Example Pin Definition
```js
const pinMarkers = [
  { section:"119", seat:"B", x:69.0, y:68.5, title:"Sec 119 — Row B" },
  { section:"119", seat:"E", x:69.0, y:69.8, title:"Sec 119 — Row E" },
];
```

| Field | Description |
|--------|-------------|
| **section** | The section number (e.g., `"119"`) |
| **seat** | The row letter (e.g., `"E"`) |
| **x** | Horizontal position (0 = left, 100 = right) |
| **y** | Vertical position (0 = top, 100 = bottom) |
| **title** | Label displayed on hover |

---

### To Add a New Pin
1. Open `index.html` and find the line that starts with `const pinMarkers = [`.  
2. Add a new entry like this:
   ```js
   { section:"120", seat:"M", x:77.0, y:34.2, title:"Sec 120 — Row M" },
   ```
3. Save and reload the site in your browser — the pin will appear.

### To Move an Existing Pin
1. Adjust the `x` (horizontal) and `y` (vertical) values.  
   - Increase `x` → move right  
   - Decrease `x` → move left  
   - Increase `y` → move down  
   - Decrease `y` → move up  
2. Save the file and refresh the page to test new placement.  

Because the coordinates are percentage-based, pins automatically scale with the map image.

---

## 8. Developer Mode (`?dev`)
Developer Mode is a **built-in helper tool** that lets you precisely record pin coordinates for new or updated seat views.  
It provides an interface with input fields for section and row, and buttons to start or stop capturing coordinates.

### How to Enable Developer Mode
1. Open `index.html` in your browser.  
2. In the address bar, add `?dev` to the end of the file URL.  
   Example:
   ```
   file:///Users/YourName/Desktop/arena-seat-views/index.html?dev
   ```
3. Press **Enter**.  
   Developer Mode will activate.

---

### How to Use Developer Mode
1. You’ll see a small control panel appear in the top corner of the page.  
2. Enter the **Section number** (e.g., `119`) and **Row letter** (e.g., `M`).  
3. Click **Start Capturing**.  
4. Click on the map to record seat locations — each click logs coordinates for the section and row entered.  
5. When finished, click **Stop Capturing.**  
6. The tool will output the formatted coordinates, such as:
   ```js
   { section:"119", seat:"M", x:68.9, y:72.4, title:"Sec 119 — Row M" },
   ```
7. Copy these entries into the `pinMarkers` array inside `index.html`.  
8. Save and reload the site (without `?dev`) to view the pins in place.

> Developer Mode is only visible when opened locally and does not appear on the public version of the website.

---

## 9. Maintenance Guidelines
- Keep all images in `.jpg` format.  
- Maintain consistent folder and file naming.  
- Avoid renaming or deleting `index.html`.  

---

## 10. Viewing the Live Version
A live version of the site is hosted on GitHub Pages:  
> **[https://gretaimhof.github.io/arena-seat-views/](https://gretaimhof.github.io/arena-seat-views/)**  

This hosted version matches the local files and can be used to preview or share the interactive map.

---

## 11. Contact
For questions, updates, or additional assistance:  
**Developer:** Greta Imhof  
**Email:** gretaimhof@gmail.com 

If the Rock Lobsters team would like to be **added as a GitHub collaborator** or have the **repository ownership transferred** for long-term maintenance, please reach out via email.

