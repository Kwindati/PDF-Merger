# 📎 PDF Merger

A simple Jupyter notebook that merges all the PDFs in a folder into one file. You choose the order with file name prefixes: `A_`, `B_`, `C_` …

---

## Table of Contents

- [Features](#features)
- [How the Ordering Works](#how-the-ordering-works)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Example](#example)
- [Troubleshooting](#troubleshooting)
- [Tips](#tips)

---

## Features

- Merges every PDF in a folder with one cell run
- Control the order with simple prefixes: `A_`, `B_`, `C_` …
- Natural number sorting (`A_file2.pdf` comes before `A_file10.pdf`)
- Files without a prefix are added at the end
- Adds a bookmark for each source file in the merged PDF
- Saves `merged.pdf` in the same folder and never re-merges an old output file

## How the Ordering Works

Files are sorted by the prefix letter first, then by name.

| File name | Merge position |
|---|---|
| `A_first.pdf` | 1 |
| `B_second.pdf` | 2 |
| `C_third.pdf` | 3 |
| `notes.pdf` (no prefix) | last |

The prefix is one letter followed by an underscore, and it is not case sensitive.

## Project Structure

```
pdf-merger/
├── pdf_merger.ipynb     # The notebook with the merge code
├── examples/            # Sample PDFs (A_first.pdf, B_second.pdf, C_third.pdf)
├── requirements.txt
└── README.md
```

## Getting Started

**Requirements:** Python 3.8 or newer and Jupyter.

```bash
git clone https://github.com/<your-username>/pdf-merger.git
cd pdf-merger
jupyter notebook
```

Then open `pdf_merger.ipynb`.

## Usage

1. Run the first code cell once to install the dependency:
   ```python
   %pip install pypdf
   ```
2. In the next cell, set the folder that contains your PDFs:
   ```python
   FOLDER = r"C:\Users\you\Documents\my_pdfs"
   ```
3. Run the cell. It prints the merge order and saves `merged.pdf` in that folder.

By default `FOLDER = r"examples"`, so you can run the notebook right away on the sample files.

## Example

Input files in the `examples` folder:

```
A_first.pdf
B_second.pdf
C_third.pdf
```

Output:

```
Merge order:
  1. A_first.pdf
  2. B_second.pdf
  3. C_third.pdf

Saved: examples/merged.pdf
```

## Troubleshooting

| Problem | Fix |
|---|---|
| `ModuleNotFoundError: No module named 'pypdf'` | Run `%pip install pypdf`, then restart the kernel |
| `Folder not found` | Use the folder that contains the PDFs, not a single file |
| `No PDF files found` | Check that the PDFs are directly inside the folder, not in a subfolder |
| `PermissionError` | Close `merged.pdf` if it is open in a PDF viewer |
| Read errors with OneDrive files | Set the folder to "Always keep on this device" so the files are downloaded |

## Tips

- To remove pages, merge first, then print the merged PDF and select the pages you want.
- On Windows you can paste the path with or without quotes.
- To change the order, rename the files and run again.

## Built With

- [pypdf](https://pypi.org/project/pypdf/) for reading and writing PDFs
