# Fierce Design System

Fierce brand design system — tokens, components, and reference pages for marketing assets.

---

## Fierce Change® Landing Page

A standalone landing page for the Fierce Change® program launch, built with vanilla HTML/CSS/JS.

### Live Pages

| Page | Path | Purpose |
|------|------|---------|
| Landing Page | `pages/fierce-change/index.html` | Main conversion page with form |
| Thank You | `pages/fierce-change/thank-you.html` | Post-submission confirmation |

---

## File Structure

```
fierce-design-system/
├── README.md                    # This file
├── DESIGN_SYSTEM.md             # Full design system documentation
├── EXTRACTION_NOTES.md          # Design decisions and extraction notes
├── theme.css                    # Consolidated CSS custom properties
│
├── tokens/                      # Design tokens
│   ├── colors.css
│   ├── typography.css
│   └── spacing.css
│
├── components/                  # Reusable component examples
│   ├── button.html
│   ├── card.html
│   ├── form-input.html
│   ├── hero.html
│   ├── navigation.html
│   ├── footer.html
│   ├── stat-callout.html
│   ├── pull-quote.html
│   ├── numbered-list.html
│   ├── outcome-grid.html
│   ├── video-phone-frame.html
│   └── ...
│
├── pages/
│   └── fierce-change/
│       ├── index.html           # Landing page (DEPLOY THIS)
│       ├── thank-you.html       # Thank you page (DEPLOY THIS)
│       └── assets/
│           ├── phone-frame.svg  # iPhone frame for video
│           └── thumbnail-clark.png  # Video thumbnail
│
└── examples/                    # Source reference files
    ├── fierce-learning-series.html
    ├── fierce-learning-onsite.html
    └── ...
```

---

## Form Submission (HubSpot Integration)

The landing page uses a **custom HTML form** that submits directly to HubSpot's Forms API via JavaScript fetch. This approach provides full control over styling and avoids HubSpot's embedded form rendering issues.

### How It Works

1. User fills out the form
2. JavaScript captures form data + UTM parameters from URL
3. Data is POSTed to HubSpot Forms API
4. On success, user is redirected to `thank-you.html`

### HubSpot API Endpoint

```
POST https://api.hsforms.com/submissions/v3/integration/submit/{portalId}/{formGuid}
```

**Current Configuration:**
- Portal ID: `21395487`
- Form GUID: `007823af-d12e-4619-8d30-89a48850d889`

### Form Fields Submitted

| Field | HubSpot Property | Required |
|-------|------------------|----------|
| First name | `firstname` | Yes |
| Last name | `lastname` | Yes |
| Work email | `email` | Yes |
| Company | `company` | Yes |
| Title | `jobtitle` | No |
| Company size | `company_size` | Yes |
| Message | `message` | No |

### UTM Tracking (Hidden Fields)

The form automatically captures URL parameters and submits them as hidden fields:

| Parameter | HubSpot Property |
|-----------|------------------|
| `utm_source` | `utm_source` |
| `utm_campaign` | `utm_campaign` |
| `utm_content` | `utm_content` |
| `utm_medium` | `utm_medium` |
| `gclid` | `gclid` |

**Example URL with tracking:**
```
https://yourdomain.com/fierce-change/?utm_source=linkedin&utm_campaign=change-launch&utm_content=hero-cta
```

---

## Deployment

### Requirements

- **Static file hosting** (no server-side processing required)
- HTTPS enabled
- CORS: HubSpot Forms API allows cross-origin requests from any domain

### Recommended Platforms

- **Vercel** — `vercel deploy`
- **Netlify** — drag-and-drop or Git integration
- **AWS S3 + CloudFront**
- **GitHub Pages**
- **Any static hosting**

### Deploy Steps

1. Clone the repository
2. Deploy the `pages/fierce-change/` directory (or entire repo)
3. Ensure both `index.html` and `thank-you.html` are accessible
4. Test form submission with UTM parameters

### File Paths

The landing page uses relative paths, so both files must be in the same directory:
- `index.html` redirects to `thank-you.html` (relative path)
- Assets are in `./assets/` subdirectory

---

## WordPress Integration (iframe)

If embedding in WordPress via iframe:

### Basic Embed

```html
<iframe
  src="https://yourdomain.com/fierce-change/"
  width="100%"
  height="4000"
  frameborder="0"
  style="border: none; overflow: hidden;"
></iframe>
```

### UTM Passthrough

To pass UTM parameters from WordPress URL into the iframe:

```html
<script>
  // Get UTM params from parent page URL
  const params = new URLSearchParams(window.location.search);
  const utmParams = ['utm_source', 'utm_campaign', 'utm_content', 'utm_medium', 'utm_term', 'gclid'];

  // Build query string for iframe
  const iframeParams = new URLSearchParams();
  utmParams.forEach(param => {
    if (params.has(param)) {
      iframeParams.set(param, params.get(param));
    }
  });

  // Set iframe src with UTM params
  const baseUrl = 'https://yourdomain.com/fierce-change/';
  const iframeSrc = iframeParams.toString() ? `${baseUrl}?${iframeParams.toString()}` : baseUrl;
  document.getElementById('fierce-change-iframe').src = iframeSrc;
</script>

<iframe
  id="fierce-change-iframe"
  src="https://yourdomain.com/fierce-change/"
  width="100%"
  height="4000"
  frameborder="0"
></iframe>
```

### Height Considerations

The landing page is approximately 4000-5000px tall. For better UX, consider:
- Using a library like `iframe-resizer` for dynamic height
- Or setting a fixed height that accommodates the full page

---

## Outstanding Items Before Launch

### Must Confirm

| Item | Status | Notes |
|------|--------|-------|
| HubSpot Form ID | `007823af-d12e-4619-8d30-89a48850d889` | Verify this is the correct production form |
| HubSpot Portal ID | `21395487` | Verify this is the correct portal |
| Vimeo Embed | `https://vimeo.com/1193413116` | Confirm embed permissions for Fierce domains |
| Hosting URL | TBD | Update any absolute URLs once hosting is confirmed |
| Video Thumbnail | Included | `assets/thumbnail-clark.png` — confirm this is final |

### Optional Enhancements

- [ ] Add Google Analytics / GTM tracking
- [ ] Add favicon
- [ ] Add Open Graph image for social sharing
- [ ] Configure redirect from non-www to www (or vice versa)

---

## External Dependencies

### Fonts (Google Fonts CDN)

```html
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=DM+Serif+Display&display=swap" rel="stylesheet">
```

### Video (Vimeo)

```
https://player.vimeo.com/video/1193413116
```

### Form Submission (HubSpot)

```
https://api.hsforms.com/submissions/v3/integration/submit/21395487/007823af-d12e-4619-8d30-89a48850d889
```

---

## No Build Required

This project is **pure HTML/CSS/JS** with no build step, bundler, or package.json dependencies. Simply deploy the static files.

---

## Browser Support

Tested and compatible with:
- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile Safari / Chrome

---

## Contact

For questions about design decisions, see `DESIGN_SYSTEM.md` and `EXTRACTION_NOTES.md`.
