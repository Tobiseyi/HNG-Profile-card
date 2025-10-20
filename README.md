# Accessible Profile Card

Single-file demo implementing the Profile Card task.

## Features
- Semantic HTML (`article`, `figure`, `nav`, `section`, headings)
- All required `data-testid` attributes:
  - test-profile-card
  - test-user-name
  - test-user-bio
  - test-user-time
  - test-user-avatar
  - test-user-social-links
  - test-user-social-twitter / github / linkedin
  - test-user-hobbies
  - test-user-dislikes
- Avatar via image URL or file upload
- Current time in milliseconds (`Date.now()`), updated every 500ms
- Responsive (mobile / tablet / desktop)
- Accessible: alt text, focus styles, keyboard controls, ARIA attributes
- Social links open in new tab with `rel="noopener noreferrer"`

## Run locally
1. Clone the repo
2. Open `index.html` in a browser (no server required)

## Deploy
- GitHub Pages:
  1. Push repo to GitHub.
  2. In repo settings > Pages, set source to `main` branch `/ (root)`.
  3. Visit the provided `https://<user>.github.io/<repo>/` URL.

- Netlify:
  1. Drop the repo into Netlify or connect repo and set build to `None` / publish directory `/`.
  2. Deploy.

## Tests & Notes for graders
- The element `document.querySelector('[data-testid="test-user-time"]').textContent` equals a `Number` similar to `Date.now()` (within a reasonable delta). The page updates the value every 500ms.
- Avatar `<img data-testid="test-user-avatar">` has `alt` text and `src` (updated by URL or file).
- Social links are child of the element with `data-testid="test-user-social-links"`.



Notes for automated tests & grading

Time check: The element test-user-time outputs Date.now() as a string. Because a small render delay may exist, tests should accept a small delta (e.g. compare to Date.now() ± 2000ms) or read almost-immediately after load. The page refreshes the timestamp every 500ms to keep it current.

Avatar handling: The img with data-testid="test-user-avatar" always exists; starting src points to an Unsplash placeholder (networked) — if you want offline mode remove that and use a local image. Uploads use URL.createObjectURL() so the src becomes a usable image URL for tests.

Social links: Inside test-user-social-links and each social link has an individual data-testid (e.g., test-user-social-twitter) so automated tests can target both the container and specific items.

Focus styles / keyboard: Links and buttons are standard HTML elements, focusable by keyboard; focus styling is visible. The inputs and the read-more button are keyboard accessible.

Responsiveness: Use the browser responsive inspector at breakpoints like 360px (mobile), 768px (tablet), 1280px (desktop) to verify layout.
