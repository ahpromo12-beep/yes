# CE 20 Lab Exam 1 – Multiview Notes

**d = 1.646** (SJSU ID 018833646 → last 3 digits 646) · Save as **Exam1-1.dwg**

Pictures in this folder: `features.png` (the 6 parts), `answer_key_d1646.png` (finished drawing), `construction_lines.png` (the 9 construction lines).

---

## 1. Where the points go (checklist)
- [ ] Name + full ID **018833646** in the **upper right** (−5 if missing)
- [ ] Screenshot of the Layer Properties window (−5 if missing)
- [ ] 5 layers: 0 (untouched), Construction white, Object red, Hidden yellow, Center green
- [ ] Construction lines for height, width and depth (draw these FIRST)
- [ ] Top, front and right side views, lined up
- [ ] Hidden lines + center lines everywhere they belong
- [ ] Only 3 dimensions: **3.250, 2.500, 1.646** (precision 0.000)
- [ ] 2 PDFs (one with construction lines, one without) + the DWG
- [ ] Save every 5 minutes (Ctrl+S)

---

## 2. The object (6 parts)
Heights are measured up from the very bottom of the part (the bottom of the rail).

| # | Part | Size / location |
|---|---|---|
| 1 | Base block | 3.25 × 2.50, **0.62** thick, sits from 0.19 up to **0.81** |
| 2 | Rail under the base | 0.75 wide × 0.19 tall, X = 1.25 to 2.00, runs full depth |
| 3 | Upper block | from 0.81 up to 1.646 (0.836 tall). Left wall 0.25 thick at the front. Front face is 40° from the left edge (**50° in AutoCAD**). Ends at X = 2.00 |
| 4 | 30° slope | starts 0.94 from the back (1.56 from the front), drops 0.543, ends at **1.103** at the back |
| 5 | Ø0.50 hole | goes all the way through. Center X = 1.625 (middle of the rail), 0.75 from the front |
| 6 | Triangle pocket | 0.19 deep (floor at **0.62**), 1.00 along the front edge, 50° side, reaches 1.192 back |

**Height stack:** 0 → rail 0.19 → base top 0.19 + 0.62 = **0.81** → top **1.646**. Pocket floor = 0.81 − 0.19 = 0.62.

---

## 3. AutoCAD setup
1. Workspace **Drafting & Annotation**: click the gear ⚙ at the bottom right, or type `WSCURRENT`.
2. `UNITS`: Decimal, **0.000**, inches.
3. `OPTIONS` → Open and Save → Automatic save every 5 min. Still press Ctrl+S.
4. `LA` to create the layers:

| Layer | Color | Linetype |
|---|---|---|
| Construction | White (7) | Continuous |
| Object | Red (1) | Continuous |
| Hidden | Yellow (2) | HIDDEN (Load…) |
| Center | Green (3) | CENTER (Load…) |
| Dimension (optional) | any | Continuous |

5. Take the **layer screenshot** now.
6. `LTSCALE` = 0.5 (try 0.25) if the dashes look solid.
7. **Object Snap tab** (not the 3D one): Object Snap On (F3), Endpoint, Midpoint, Center, Intersection, Perpendicular. Leave **Nearest** off.
8. **Press F12 so Dynamic Input is OFF**. Otherwise typed points are measured from the last point. You can also put `#` before each point.
9. Ortho **F8** on.

---

## 4. Construction lines (Construction layer)
**Formula:** W = 3.25, D = 2.50, H = d = 1.646, G = gap = 1

| Lines | Values | Formula |
|---|---|---|
| Horizontal | 0 · **1.646** · **2.646** · **5.146** | 0 · H · H+G · H+G+D |
| Vertical | 0 · **3.25** · **4.25** · **6.75** | 0 · W · W+G · W+G+D |
| 45° miter | through **(4.25, 2.646)** to (6.75, 5.146) | through (W+G, H+G) |

**OFFSET method (easiest):**
1. `XLINE` H through 0,0 and `XLINE` V through 0,0.
2. OFFSET the horizontal line up: 1.646, then 1, then 2.5.
3. OFFSET the vertical line right: 3.25, then 1, then 2.5.
4. Miter: `LINE` from the 4.25, 2.646 corner to the 6.75, 5.146 corner (snap Intersection both times).

**Trim an xline:** `TRIM` → `O` → Standard → pick the cutting lines → Enter → click the pieces to remove.

**Lines hidden behind construction lines?** Lock the Construction layer (padlock) so it fades, or `DRAWORDER` → Back.

**Converting depth:** top view y = 2.646 + depth · side view x = 4.25 + depth.

---

## 5. FRONT VIEW
**Object outline (one LINE):**
`0,.19 → 1.25,.19 → 1.25,0 → 2,0 → 2,.19 → 3.25,.19 → 3.25,.81 → 2,.81 → 2,1.343 → 1.559,1.646 → 0,1.646 → C`

| Line | Type | What it is |
|---|---|---|
| .25,.81 → .25,1.646 | Object | left wall meets the 40° wall |
| .25,.81 → 2,.81 | Object | top edge of the base |
| 2.25,.62 → 3.25,.62 | Object | pocket floor |
| 2.25,.62 → 2.25,.81 | Object | pocket left end |
| 0,1.103 → 2,1.103 | **Hidden** | bottom of the 30° slope at the back (behind the block) |
| 1.375,0 → 1.375,.81 and 1.875,0 → 1.875,.81 | **Hidden** | hole sides |
| 1.625,−.15 → 1.625,.96 | **Center** | hole center line |

## 6. TOP VIEW
| Line | Type | What it is |
|---|---|---|
| RECTANG 0,2.646 → 3.25,5.146 | Object | outline |
| 0,4.206 → 1.559,4.206 | Object | where the flat top meets the slope |
| .25,2.646 → @2.7225<50 (ends 2,4.732) | Object | 40° wall |
| 2,4.732 → 2,5.146 | Object | block's right end |
| 2.25,2.646 → @1.5557<50 (ends 3.25,3.838) | Object | pocket's slanted side |
| CIRCLE 1.625,3.396, D .5 | Object | hole |
| 1.25,2.646 → 1.25,5.146 | **Hidden** | rail's left side |
| 2,2.646 → 2,4.732 | **Hidden** | rail's right side (stops where the red line takes over) |
| 1.225,3.396 → 2.025,3.396 and 1.625,2.996 → 1.625,3.796 | **Center** | crossing center lines |

## 7. RIGHT SIDE VIEW
**Object outline:** `4.25,0 → 6.75,0 → 6.75,1.103 → 5.81,1.646 → 4.25,1.646 → C` (the slope is `5.81,1.646 → @1.0854<-30`)

| Line | Type | What it is |
|---|---|---|
| 4.25,.19 → 6.75,.19 | Object | rail meets the base bottom |
| 4.25,.81 → 6.75,.81 | Object | top of the base |
| 4.25,.62 → 5.442,.62 → 5.442,.81 | Object | pocket step |
| 6.336,.81 → 6.336,1.343 | Object | 40° wall meets the end face (easy to miss!) |
| 4.75,0 → 4.75,.81 and 5.25,0 → 5.25,.81 | **Hidden** | hole sides |
| 5,−.15 → 5,.96 | **Center** | hole center line |

**Quick check:** the slanted lines must land exactly on 1.559,1.646 → 2,1.343 (front) and 5.81,1.646 → 6.75,1.103 (side).

---

## 8. Where the odd numbers come from (trig)
Any slanted line is the long side of an imaginary right triangle. **tan(angle) = opposite ÷ adjacent**, where the adjacent side is the edge the angle is measured from. Use **DEG** mode.

| Number | Math | Meaning |
|---|---|---|
| 1.559 | 0.25 + 1.56 × tan 40° | 40° wall meets the start of the slope |
| 2.086 | 1.75 ÷ tan 40° | 40° wall reaches X = 2.00 |
| 0.543 → 1.103 | 0.94 × tan 30°, then 1.646 − 0.543 | how far the slope drops; where it ends |
| 0.303 → 1.343 | (2.086 − 1.56) × tan 30° | slope height at the 40° wall |
| 1.192 | 1.00 × tan 50° | how far back the pocket goes |
| 0.81 | 0.19 + 0.62 | top of the base |
| 1.625 | 1.25 + 0.75 ÷ 2 | hole center = middle of the rail |
| 1.56 | 2.50 − 0.94 | where the slope starts |

**AutoCAD angles:** 0° points right and angles go counterclockwise. 40° from the left edge → 90 − 40 = **50°**. Slope going down to the right → **−30°**.

**Exam shortcut, no math:** draw the line too long (`@3<50`), then `TRIM` it at a construction line.

**Projection, no math:** width goes up and down (front ↔ top), height goes across (front ↔ side), depth goes through the 45° line (top ↔ side).

---

## 9. Line rules
- **Object** (red, solid): edges you can see.
- **Hidden** (yellow, dashed): real edges behind material, even ones at the very back.
- **Center** (green): a cross on circles, one line down the middle of a hole seen from the side. Extend it about 0.15 past the hole, in all 3 views.
- **Priority:** object > hidden > center. If a hidden edge lands on a solid line, don't draw it. That's why the rail's far side has no dashed line in the side view.
- An edge you look straight down shows up as a single point, so it needs no line.

---

## 10. Dimensions
- `DIMSTYLE` → Modify → Primary Units → **Precision 0.000**
- `DIMLINEAR`, snapping to the object's corners: **3.250** under the front view, **1.646** overall height (rail bottom to top), **2.500** under the side view
- Nothing else: no hole size, no angles
- `MTEXT` with name + **018833646**, upper right, not on layer 0

---

## 11. Submitting
1. Ctrl+P → **DWG To PDF.pc3**, ANSI A or Letter, landscape. **Window** around everything, Center the plot, **1:1**. Plot style None or acad.ctb (**not monochrome.ctb**). Save as PDF #1.
2. Turn the Construction layer **off** (lightbulb) → plot again for PDF #2.
3. Turn it back on, save **Exam1-1.dwg**, then submit both PDFs, the DWG and the screenshot.

---

## 12. Real exam routine (any object)
1. Split the object into parts. Write down W, D, H (= 1.XYZ) and G = 1.
2. Work out the 4 heights and 4 widths, plus the miter point (W+G, H+G).
3. Chain the isometric dimensions to get every feature position.
4. Layers → screenshot → F12 off → construction lines → lock them.
5. Front, top, then side view. Project between them.
6. Hidden lines, center lines, 3 dimensions, name and ID, 2 PDFs.

---

## 13. Q&A log (added as we go)
- **Horizontal hidden line in the front view?** It's the bottom edge of the 30° slope at the back face (height 1.103). The upper block is in front of it, so it's hidden.
- **3D Object Snap tab?** Ignore it and leave it off. Use the **Object Snap** tab instead.
- **Toolbar shows Box/Extrude (3D)?** Switch the workspace to **Drafting & Annotation**. A [Top][2D Wireframe] view is already fine.
- **Can't see the red line under a construction line?** Lock the Construction layer, or `DRAWORDER` → Back. If the line vanishes when the Construction layer is off, it's on the wrong layer.
- **Miter starts at (3.25, 1.646) instead of (4.25, 2.646)?** It's still correct (same 45° line). Trimming the extra piece is optional.
- **Why no hidden line for the rail's far side in the side view?** Its hidden edges land exactly on the solid 0 and 0.19 lines. Visible beats hidden.
- **Why 0.81?** Rail 0.19 + base 0.62.
- **Pocket "rectangle" in the front view?** Corners (2.25,.62), (3.25,.62), (3.25,.81), (2.25,.81). X: 3.25 − 1.00 = 2.25 to 3.25. Height: 0.81 − 0.19 = 0.62 to 0.81. The outline already covers the top (.81) and right (3.25) sides, so draw only `2.25,.62 → 3.25,.62` and `2.25,.62 → 2.25,.81`. The outline goes up to .81 at X = 3.25, not .62, because the back part of the base behind the pocket is full height.
- **Why tan 40° when the top view isn't a triangle?** The 40° wall plus a vertical and a horizontal leg make an imaginary right triangle. tan 40° = sideways ÷ back.
