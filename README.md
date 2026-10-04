# Mathematics papers

A simple website for Madhup's mathematical papers and notes. Readers click a paper to open its PDF in a new tab. Responsive layout, no packages, and no build step.

## Publish with GitHub and Vercel

1. Extract `mathematics-papers-vercel.zip`.
2. Create a new GitHub repository, for example `mathematics-papers`.
3. Upload the **contents** of the extracted `mathematics-papers` folder to the repository. `index.html`, `papers.json`, `vercel.json`, and `README.md` must be at the top level. Upload the `papers` folder too. Do not upload the ZIP itself or an extra outer folder.
4. Commit the files to `main`.
5. On Vercel, choose **Add New → Project**, connect GitHub if necessary, and import this repository.
6. Use these settings:

| Setting | Value |
| --- | --- |
| Framework Preset | Other |
| Root Directory | Repository root (leave the default) |
| Build Command | Empty (no command) |
| Output Directory | `.` |

The included `vercel.json` configures the static output and empty build command.

7. Click **Deploy**. Open your Vercel link after deployment succeeds.

## Add your first PDF

1. Rename the PDF to a simple filename, such as `my-first-paper.pdf`.
2. In GitHub, open the `papers` folder, choose **Add file → Upload files**, and upload the PDF. Commit the change.
3. Open `papers.json` in the repository root and click the pencil icon to edit it.
4. Replace the initial `[]` with the following, using your actual title and filename:

```json
[
  {
    "title": "My first mathematics paper",
    "pdf": "./papers/my-first-paper.pdf"
  }
]
```

5. Commit the edit to `main`. Vercel automatically redeploys the website. Your paper appears after deployment finishes.

Uploading the PDF alone does not add a paper entry; add its entry in `papers.json` too. File paths are case-sensitive, so the name in `pdf` must exactly match the uploaded filename.

## More papers and optional details

Each paper is one object inside the same square brackets. Separate objects with commas. Do not put a comma after the last object. Entries appear in the order you list them.

```json
[
  {
    "title": "Your first paper's title",
    "subject": "Number theory",
    "date": "October 2026",
    "pages": 5,
    "description": "A short description of what this paper explores.",
    "pdf": "./papers/first-paper.pdf"
  },
  {
    "title": "Your second paper's title",
    "subject": "Geometry",
    "pdf": "./papers/second-paper.pdf"
  }
]
```

Only `title` and `pdf` are required. You can omit subject, date, pages, and description. These are examples for editing, not included papers.

## Change the site text

Edit `index.html` to change the name, heading, introduction, or footer. Styles and the paper list logic are in that same file. Commit your changes to update the Vercel site.

## Local preview

Opening `index.html` by double-clicking can prevent `papers.json` from loading. Use a local web server instead, or test the deployed Vercel site.

If Python 3 is installed, run this from the website folder:

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Troubleshooting

- **No paper appears:** check that you edited `papers.json`, that it is valid JSON, and that Vercel finished the latest deployment.
- **PDF gives a 404:** check the folder, filename, capitalization, and `.pdf` extension against the `pdf` path.
- **Homepage gives a 404:** ensure `index.html` is at the repository root and Vercel's root directory points there.
