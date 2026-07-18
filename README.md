# PrepFusion TITANS Batch Guidance

**A publication-quality student onboarding & preparation strategy PDF**

---

## 📋 Project Overview

This is a professional, modern LaTeX document designed for the PrepFusion TITANS Batch. It covers:

- ✅ Preparation strategy (Network Theory, Digital Electronics, Signals & Systems)
- ✅ Essential YouTube video resources (structured table)
- ✅ App setup guides (iOS MyAppx, Windows PC, external monitor troubleshooting)
- ✅ Test series & AIMT information
- ✅ Offline video download guidelines
- ✅ Direct contact information for instructors

**Design Philosophy:** Clean, modern, scannable, with professional spacing and a carefully curated brand color palette.

---

## 🚀 Quick Start (3 Steps)

### Step 1: Upload & Customize the Logo

**File:** `prepfusion_titans_guide.tex` (lines ~130–145)

Find this block:
```latex
    % ── LOGO PLACEHOLDER ──────────────────────────────────────
    %  Uncomment & place logo.png in the same folder as this file
    % \includegraphics[width=3.2cm]{logo.png}
```

**Action:**
1. Save your logo as `logo.png` (or `.jpg` / `.pdf`)
2. Upload it to **Overleaf in the same folder** as `prepfusion_titans_guide.tex`
3. **Uncomment** the line: remove the `%` at the start
4. Adjust `width=3.2cm` if needed (smaller for compact logo, larger for prominence)

### Step 2: Customize Watermark Opacity

**File:** Lines ~75–88 (TikZ watermark configuration)

Find:
```latex
\node[
  rotate  = 45,
  opacity = 0.05,            % ← ADJUST THIS
  ...
] at (current page.center) {PrepFusion};
```

**Watermark opacity scale:**
- `0.03` → Very faint (barely visible)
- `0.05` → **Recommended** (current default)
- `0.08` → Moderate visibility
- `0.12` → Quite visible
- `0.15+` → Bold, may interfere with text

**Action:** Change `0.05` to your preferred value and recompile.

### Step 3: Swap Watermark (Text → Logo Image)

**Optional:** Replace the "PrepFusion" text watermark with your company logo.

Find the watermark block (lines ~75–88):
```latex
\node[
  rotate  = 45,
  opacity = 0.05,
  font    = \fontsize{72}{72}\selectfont\bfseries,
  color   = pfNavy
] at (current page.center) {PrepFusion};  % ← SWAP THIS LINE
```

**To use logo instead:**
```latex
\node[
  rotate  = 45,
  opacity = 0.05
] at (current page.center) {\includegraphics[width=8cm]{logo.png}};
```

**Adjust `width=8cm`** to fit your logo size appropriately.

---

## 📦 Files & Structure

```
prepfusion_titans_guide.tex    ← Single master .tex file (ready to compile)
logo.png                        ← Your brand logo (upload to Overleaf)
README.md                       ← This file
```

**All content is in one file.** No external dependencies beyond standard LaTeX packages.

---

## 🔧 Compilation

### On Overleaf (Recommended)

1. Create a **new blank project** on [Overleaf](https://overleaf.com)
2. Copy the contents of `prepfusion_titans_guide.tex` into `main.tex`
3. Upload `logo.png` to the project
4. Ensure compiler is set to **pdfLaTeX** (Menu → Settings → Compiler)
5. **Compile twice** (first pass generates TOC, second pass resolves page references)
6. Download the PDF

### Locally (Terminal)

```bash
pdflatex prepfusion_titans_guide.tex
pdflatex prepfusion_titans_guide.tex    # Run twice for footer page count
```

Output: `prepfusion_titans_guide.pdf`

### Why Compile Twice?

The footer displays "Page X of Y" using `\pageref{LastPage}`. LaTeX needs two passes:
1. **Pass 1:** Collects page labels
2. **Pass 2:** Resolves all `\ref` and `\pageref` commands

---

## 🎨 Customization Guide

### Color Palette

Edit lines 28–33 in the preamble to change the entire document's color scheme:

```latex
\definecolor{pfNavy}    {HTML}{1A2F5A}   % Headers, rules, navy boxes
\definecolor{pfTeal}    {HTML}{0E7C7B}   % Section accents, teal boxes
\definecolor{pfOrange}  {HTML}{E8602C}   % Alert/action boxes (IMPORTANT)
\definecolor{pfCharcoal}{HTML}{2D2D2D}   % Body text
\definecolor{pfLightBg} {HTML}{F4F6FA}   % Light backgrounds, alt rows
\definecolor{pfMid}     {HTML}{D0D7E8}   % Subtle borders, light rules
```

**Example:** To use a corporate blue instead of navy:
```latex
\definecolor{pfNavy}{HTML}{003D82}  % Your corporate blue
```

All headings, section backgrounds, and rules will automatically update.

### Font

Currently: **Helvetica (sans-serif)**, applied globally.

To change globally, edit line 37:
```latex
\renewcommand{\familydefault}{\sfdefault}  % ← Change this
```

Options:
- `\sfdefault` → Sans-serif (current)
- `\rmdefault` → Serif (e.g., Computer Modern, Times)
- `\ttdefault` → Monospace (not recommended for body)

### Margins & Page Size

Edit line 20 (geometry package):
```latex
\usepackage[
  top    = 1in,      % ← Adjust
  bottom = 1in,
  left   = 0.75in,
  right  = 0.75in,
]{geometry}
```

### Header & Footer Text

Edit lines 54–62 (fancyhdr configuration):
```latex
\fancyhead[L]{
  \small\color{pfNavy}\textbf{PrepFusion}\ \textcolor{pfMid}{|}\ TITANS Batch Guidance
}
```

Change "PrepFusion" to your organization name or remove entirely.

---

## 📦 Custom Environments (Boxes)

Five styled callout boxes are pre-configured. Use them throughout the document:

### 1. Alert Box (Orange) — For Critical Action Items

```latex
\begin{alertbox}[Icon & Title]
  \small
  Content goes here. Use for:
  — MOST IMPORTANT sections
  — Action required items
  — Warnings / cautions
\end{alertbox}
```

**Example:**
```latex
\begin{alertbox}[\faExclamationTriangle\enspace Action Required]
  Start with Network Theory through Chapter 3.
\end{alertbox}
```

### 2. Info Box (Navy) — For General Information

```latex
\begin{infobox}[Title]
  Use for:
  — Welcome messages
  — Contact details
  — General guidance
\end{infobox}
```

### 3. Step Box (Teal) — For How-To Instructions

```latex
\begin{stepbox}[Title]
  \small
  \begin{enumerate}
    \item First step
    \item Second step
  \end{enumerate}
\end{stepbox}
```

### 4. Note Box (Subtle Grey) — For Inline Notes

```latex
\begin{notebox}
  \small\faInfoCircle\enspace Quick side note or tip.
\end{notebox}
```

### 5. Title Box (Full Navy) — Header Section

Used automatically at document top. Edit the parameters around line ~192 if customizing.

---

## 🎯 Content Structure

| Section | Lines | Content |
|---|---|---|
| Preamble & Setup | 1–180 | Packages, colors, fonts, watermark |
| Welcome Box | ~192–210 | Intro & instructor contacts |
| Preparation Strategy | ~220–250 | Subject recommendations & table |
| Video Resources | ~260–310 | Table of 9 essential YouTube links |
| App Support | ~320–380 | iOS, Windows, external monitor, troubleshooting |
| Test Series | ~390–420 | Fusion Test Series & AIMT guides |
| Offline Downloads | ~430–460 | Video download rules & limitations |
| Footer Contact | ~470–480 | Final contact section |

---

## 🔗 Hyperlinks

All YouTube links and website URLs are styled with the `\pflink{}{}` macro:

```latex
\pflink{https://youtu.be/6Wp2MuZTROw}{youtu.be/6Wp2MuZTROw}
```

This creates a **teal, underlined link** that is clickable in the PDF and easy to scan.

**To add a new link:**
```latex
\pflink{https://example.com/page}{example.com/page}
```

---

## 📱 Icons & Special Characters

The document includes **FontAwesome 5** icons for visual interest:

| Icon Macro | Symbol | Use |
|---|---|---|
| `\faHandshake` | 🤝 | Welcome |
| `\faWhatsapp` | 💬 | Contact |
| `\faExclamationTriangle` | ⚠️ | Warning |
| `\faStar` | ⭐ | Important |
| `\faApple` | 🍎 | iOS |
| `\faWindows` | ⊞ | Windows |
| `\faDesktop` | 🖥️ | Monitor |
| `\faBug` | 🐛 | Troubleshooting |
| `\faCheckCircle` | ✓ | Completed |
| `\faTimes` | ✕ | Cannot do |
| `\faClipboardList` | 📋 | Test series |
| `\faTrophy` | 🏆 | AIMT |
| `\faPlayCircle` | ▶️ | Video |
| `\faGlobe` | 🌐 | Website |
| `\faYoutube` | ▶️ | YouTube |
| `\faInfoCircle` | ℹ️ | Info |
| `\faCalendar` | 📅 | Date |
| `\faUsers` | 👥 | People |

---

## 🐛 Troubleshooting

### Compilation Error: "Illegal parameter number"

**Cause:** Special characters or nested macros in section formatting.

**Solution:** Already fixed in this version. If you add custom `\titleformat` commands, avoid nesting `\parbox` inside section arguments. Use `\makebox` instead.

### Logo Not Appearing

1. Check that `logo.png` is **in the same Overleaf folder** as the `.tex` file
2. Verify the `\includegraphics{logo.png}` line is **uncommented**
3. Try a different image format: `.jpg`, `.pdf`, or `.eps`
4. Ensure file is not corrupted (test in another document first)

### Watermark Too Faint / Too Visible

Adjust the `opacity` parameter (lines ~75–88):
- **Faint:** `0.03` – `0.05`
- **Moderate:** `0.06` – `0.10`
- **Bold:** `0.11` – `0.15`

### Links Not Clickable in PDF

Ensure `hyperref` is loaded **after** all color definitions. The current file loads it at line ~150, which is correct.

### Footer "Page X of Y" Shows Question Marks

**Cause:** You only compiled once.

**Solution:** Compile twice with `pdflatex` (or click "Recompile" twice on Overleaf).

### Table Not Fitting on Page

Use the `tabularx` environment (already in the video resources section). Adjust `X` column widths:
```latex
\begin{tabularx}{\linewidth}{@{} p{0.5cm} X X @{}}
  % narrower first column, flexible middle & right columns
\end{tabularx}
```

---

## 📝 Content Editing Tips

### Keeping Formatting Consistent

1. **Headings:** Use `\section{}` and `\subsection{}`
2. **Important notes:** Wrap in `\begin{alertbox}[Title]...\end{alertbox}`
3. **Steps/instructions:** Use `\begin{stepbox}[Title]...\end{stepbox}`
4. **Contact/general info:** Use `\begin{infobox}[Title]...\end{infobox}`
5. **External links:** Always use `\pflink{url}{display text}`

### Adding a New Section

```latex
\section{My New Section}

\subsection{A subsection}

Your paragraph text here.

\begin{alertbox}[Key Point]
  Important information.
\end{alertbox}
```

The colors and formatting will apply automatically.

---

## 📄 Document Metadata

Edit lines ~164–167 to update PDF properties:

```latex
\usepackage[
  colorlinks = true,
  pdftitle   = {PrepFusion TITANS Batch Guidance},  % ← Change title
  pdfauthor  = {PrepFusion},                        % ← Change author
]{hyperref}
```

This metadata appears in PDF viewers (File Info).

---

## 🎓 Example Customizations

### Change Body Text to Serif (Palatino)

Replace line 37:
```latex
\usepackage{mathpazo}          % Palatino font
\renewcommand{\familydefault}{\rmdefault}  % Use serif (Roman)
```

### Increase All Margins

Edit geometry (line ~20):
```latex
\usepackage[
  top    = 1.25in,
  bottom = 1.25in,
  left   = 1in,
  right  = 1in,
]{geometry}
```

### Remove Watermark Entirely

Comment out the watermark block (lines ~75–88):
```latex
% \AddToShipoutPictureBG{%
%  ... watermark code ...
% }
```

### Darker Navy Sections

Edit `pfNavy` (line ~28):
```latex
\definecolor{pfNavy}{HTML}{0A1930}  % Darker navy
```

---

## 📞 Support

For questions or issues:

- **Anish Sir:** +91-79804 52273
- **Himanshu Sir:** +91-90791 08591
- **Website:** [prepfusion.in](https://prepfusion.in)
- **YouTube:** [@PrepFusion-GATE](https://youtube.com/@PrepFusion-GATE)

---

## 📜 License & Credit

**Created by:** PrepFusion Engineering  
**For:** TITANS Batch Students  
**Design:** Modern, scannable, professional LaTeX  
**Fonts:** Helvetica (sans-serif) + FontAwesome 5 icons  
**Compile Engine:** pdfLaTeX

---

## ✅ Checklist Before Sharing

- [ ] Logo uploaded and uncommented in line ~130
- [ ] Watermark opacity set to desired level (lines ~75–88)
- [ ] Document compiled **twice** (for page references)
- [ ] PDF downloaded and tested in Adobe Reader / web viewer
- [ ] All hyperlinks clickable
- [ ] Color scheme matches brand (edit lines 28–33 if needed)
- [ ] Header/footer text updated if using for another organization

---

**Happy documenting! 🚀**
