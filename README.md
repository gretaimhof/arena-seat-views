# Project: “Tank Tour” — Akins Ford Arena  
**Delivered To:** Athens Rock Lobsters  

---

## 1. Overview
The **Rock Lobsters Arena Seat Views** website provides an interactive, visual experience for exploring panoramic seat views from *The Tank* at Akins Ford Arena.  

Visitors can:
- View the full seating chart of the arena  
- Hover over sections and rows to highlight seating areas  
- Click directly on sections/rows to open 360° seat views  
- View premium areas such as party suites  
- Seamlessly switch between the arena map and viewer  

All project files are contained in this folder.  
You can also view the **live hosted version** online here:  
> https://gretaimhof.github.io/arena-seat-views/

---

## 2. How to Open the Website Locally

### Option A — Local (Quick View)
1. Locate `index.html` in the main project folder.  
2. Double-click to open it in your web browser (Google Chrome recommended).  

> Important: Some browsers may block local file loading. If images do not appear, use Option B.

### Option B — Local Web Server (Recommended)
1. Open the project folder in VS Code.  
2. Install the **Live Server** extension.  
3. Right-click `index.html` → **Open with Live Server**.  

---

## 3. Folder Structure
```
arena-seat-views/
│
├── index.html
├── /images/
│   ├── seating_chart.png
│   ├── map_overlay.svg
│   ├── /119/
│   │   ├── 119_A-C.jpg
│   ├── /120/
│   ├── /WhiteClawSuite/
│   └── /MagnoliasSuite/
```

---

## 4. How Seat Views Are Loaded

The site uses an **SVG overlay** to define clickable seating areas.

Each area has a unique ID:
```
<path id="119_A-C" />
```

This directly maps to:
```
images/119/119_A-C.jpg
```

### Naming Format
```
[Section]_[Row(s)].jpg
```

### Examples
```
119_A.jpg
119_A-C.jpg
120_Q.jpg
```

> File names and SVG IDs must match exactly.

---

## 5. Updating Seat Photos

### To Add or Replace Photos
1. Navigate to the correct section folder inside `/images/`.  
2. Add or replace the panoramic image.  
3. Ensure the file name matches the SVG ID format.  

No code changes are required if naming is consistent.

---

## 6. Adding or Updating Sections/Rows

Sections and rows are controlled by:
```
/images/map_overlay.svg
```

### To Update:
1. Edit the overlay in Figma.  
2. Export as SVG.  
3. Ensure each clickable shape:
   - Is a `<path>`
   - Has an ID like:
     ```
     119_A-C
     ```
4. Replace `map_overlay.svg`.

---

## 7. Updating the Map Overlay

### File Location
```
/images/map_overlay.svg
```

### Steps:
1. Open overlay in Figma  
2. Select only clickable shapes  
3. Flatten (Cmd/Ctrl + E)  
4. Export as SVG  
5. Replace file  
6. Refresh site  

### Requirements
Each shape must:
- Be a `<path>`
- Have an `id`

#### Section Example
```
<path id="119_A-C" />
```

#### Suite Example
```
<path id="MagnoliasSuite" data-label="Magnolia's Party Suite" />
```

### If it doesn’t update
- Hard refresh:
  ```
  Cmd + Shift + R
  ```
- Or rename:
  ```
  map_overlay_v2.svg
  ```

---

## 8. Adding Premium Areas (Suites)

### SVG
```
<path id="MagnoliasSuite" data-label="Magnolia's Party Suite" />
```

### Image
```
images/MagnoliasSuite/MagnoliasSuite.jpg
```

### Behavior
- Click → opens panorama  
- Displays custom label  
- No section/row formatting  

---

## 9. Updating the Arena Map

File:
```
/images/seating_chart.png
```

### Steps
1. Replace image  
2. Keep proportions similar  
3. Update overlay if layout changes  

---

## 10. How the Viewer Works

- Built with **Pannellum**
- Loads panoramas dynamically
- Displays:
  - Section + rows
  - OR suite labels  

---

## 11. Maintenance Guidelines
- Use `.jpg` images  
- Keep naming consistent  
- Do not rename `index.html`  
- Update overlay when needed  

---

## 12. Viewing the Live Version

Live site:
https://gretaimhof.github.io/arena-seat-views/

### To update
```
git add .
git commit -m "update"
git push
```

---

## 13. Contact
**Developer:** Greta Imhof  
**Email:** gretaimhof@gmail.com  
