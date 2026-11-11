# GIS portfolio

A responsive, build-free HTML/CSS portfolio for GitHub Pages, styled around aviation, utility networks, and indoor floorplans. Uses sans-serif typography throughout. Includes three clearly marked GIS examples, a programming/automation/server-hosting showcase, local SVG plan illustrations, expandable project sections, ArcGIS iframe snippets, and a printable résumé template. No JavaScript, API keys, packages, or external fonts are required.

## Preview

Open `index.html` in your browser. For a local web server, run this from the project folder:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000`. Stop the server with `Ctrl+C`.

## Make it yours

1. In `index.html`, replace `Your Name`, `your.name@example.com`, the page description, and the bracketed biography. Search for `PERSONALIZE` to find the main edit points.
2. Replace each example project’s title, summary, tags, detailed description, and map image. Include your role, data sources and dates, methods, findings, and limitations. The included maps are illustrations and represent no real study area or analysis.
3. Keep only the tools you actually use in the toolkit. Rename “Example toolkit” when finished.
4. Add contact links, such as LinkedIn, GitHub, and your public ArcGIS Online profile, inside `.contact-links`. Replace the placeholder email and remove its placeholder note.
5. Fill in `resume.html`, or add your PDF as `assets/resume.pdf` and replace each `href="resume.html"` in `index.html` with `href="assets/resume.pdf"`. The HTML résumé can also be exported using your browser’s **Print → Save as PDF**. Remove its template note and `noindex` meta tag when it is ready.
6. Remove the sample-project labels, introductory template note, and any remaining placeholder copy before using the site on your résumé.

To change colors, edit the variables at the top of `styles.css`.

### Programming, automation, and server hosting

The **Code & infrastructure** section (`id="systems"`) has three editable `.system-card` articles for programming, automation, and server hosting. Replace each example summary and expandable project brief with your own work. Each card includes a commented link for a repository, workflow guide, or architecture document: replace the placeholder URL and remove the surrounding comment markers to enable it.

Show what you built, your role, how it works, and a result you can demonstrate. The workflow strip is explicitly illustrative; edit its steps to fit a real project, or remove it. All technology tags are examples, not statements of experience.

## Embed ArcGIS Online projects

Each project’s expandable section has a commented iframe and full-screen link. Search `index.html` for **EMBED 1** (aviation web app), **EMBED 2** (utility dashboard), or **EMBED 3** (indoor mapping app). StoryMaps can also use the same iframe styling.

1. Publish the ArcGIS content you intend to show. For visitors without an organizational account, share the app, its map, and its underlying layers with **Everyone (public)**. Subscriber or premium layers may need additional app configuration. See [Esri’s app sharing and embedding documentation](https://doc.esri.com/en/arcgis-online/latest/share-maps/share-apps.html).
2. Obtain the iframe embed code from the app’s sharing/embedding interface. For an Instant App or Experience Builder app, use the published app’s embed URL, rather than an editor or item-details page. For a web map, you can create an Instant App and embed that app.
3. Delete that section’s `<div class="embed-placeholder">...</div>`.
4. Remove the `<!-- ... -->` comment markers around the provided iframe and link. Replace the iframe’s `src` with the URL from Esri’s embed code. Replace the link’s `href` with the public app URL. Keep `class="arcgis-embed"`, a meaningful `title`, `loading="lazy"`, and `allowfullscreen`.
5. Test the published app in a private/incognito window while signed out of ArcGIS, and test both the embed and full-screen link on a phone.

For example, replace the placeholder panel in the dashboard project with this code, substituting your real item ID in **both** places:

```html
<iframe
  class="arcgis-embed"
  src="https://www.arcgis.com/apps/dashboards/YOUR_DASHBOARD_ID"
  title="Your project’s dashboard"
  loading="lazy"
  allowfullscreen>
</iframe>
<a class="text-link"
   href="https://www.arcgis.com/apps/dashboards/YOUR_DASHBOARD_ID"
   target="_blank"
   rel="noopener noreferrer">
  Open full-screen dashboard ↗
  <span class="sr-only"> (opens in a new tab)</span>
</a>
```

For StoryMaps, use `https://storymaps.arcgis.com/stories/YOUR_STORY_ID`. The story must be published and shared with everyone. Obtain the embed code from **More → Embed this story**, or the published story’s **Share → Embed** interface. See [Esri’s standard embedding guide](https://doc.esri.com/en/arcgis-storymaps/latest/reference/standard-embedding.html).

The same `.arcgis-embed` class works with iframe-compatible Experience Builder and Instant Apps embeds. Use your app’s generated embed URL. If it contains an `&`, write it as `&amp;` in HTML attributes. No ArcGIS JavaScript SDK is needed for these iframe embeds.

The map frames resize to the available width. Adjust `.arcgis-embed` in `styles.css` to change their height. The two lower cards have narrower frames on desktop; if your dashboard needs more room, move its entire `<article>` outside `.project-grid`, or make it the first project. Always keep the full-screen link so visitors can open complex apps comfortably.

### Add more projects

Copy one entire `<article class="project">...</article>` inside `.project-grid`. Give the copy a unique `id`, update its content and image alt text, and add its embed. No project limit or configuration file is involved.

### Replace the map previews

Export a map or take a screenshot of your published app, save it in `assets/`, and replace the relevant image’s `src`. Update its `alt`, `width`, and `height` attributes for the new image. Include any required data/basemap attribution. The bundled airfield, utility, and floorplan SVG illustrations can be used as temporary previews without an internet connection.

## Publish on GitHub Pages

1. Create a GitHub repository, for example `gis-portfolio`.
2. Upload these files and the complete `assets/` folder to the repository root, keeping `index.html` at the top level. Include `.nojekyll` if uploading through Git; the plain HTML site also works without it.
3. Open the repository’s **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
5. Select **main** and **/ (root)**, then **Save**.
6. Wait for the Pages deployment to complete. GitHub displays your published URL in the Pages settings; normally it is `https://YOUR_USERNAME.github.io/gis-portfolio/` for this repository name. Put that URL on your résumé.

These steps follow [GitHub’s publishing-source documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site). No build command or custom GitHub Actions workflow is needed. All asset and page links are relative, so the site also works in a repository subdirectory URL.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Portfolio content, project details, and ArcGIS embed snippets |
| `styles.css` | Responsive layout, palette, embed sizing, and résumé print styles |
| `resume.html` | Editable résumé template |
| `assets/` | Aviation, utility, and floorplan illustrations and the favicon |
| `.nojekyll` | Serve the static files without Jekyll processing |

Real ArcGIS embeds have not been verified because no project URLs have been supplied yet. Until you replace the commented snippets, the site makes no requests to ArcGIS.
