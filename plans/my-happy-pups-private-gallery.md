# My Happy Pups — private coloring book gallery (approved plan)

Status: PLANNED — not deployed or secured yet. Owner approved a separate Cloudflare-protected gallery linked from the public Pups Journal on November 7, 2026.

## Architecture
- Keep Pups Journal and its GitHub Pages publication public and unchanged.
- Add a journal link to the private gallery **only after** its working Cloudflare URL is confirmed.
- Host the gallery and its image endpoints behind Cloudflare Access; reuse the existing two-email tester allowlist for owner and mother, without copying emails or credentials into this public repository.
- Do not commit family photos, original portraits, approved coloring pages, Access tokens, email addresses, or secrets to this public repository. Use private object storage and authorize every image request server-side; verify direct-image URLs are denied to unauthorized users.
- Keep the original artwork unchanged. Do not regenerate approved images.

## Gallery behavior
- Mobile-first, swipeable chapters, large previous/next controls and accessible tap targets.
- Each spread: full-color portrait alongside its matching black-and-white coloring page; tap to enlarge, with a one-page-at-a-time option for narrow screens.
- Clearly distinguish APPROVED from DRAFT; no automatic publication of drafts.
- Chapters: Jasper (Scruffybutt), Brutus, Butterscotch, with other dogs added only after confirmation.
- No user download workflow required for viewing.

## Artwork and approval inventory (not a claim of file storage)
- Brutus & Me: final two-panel spread approved November 7, 2026. Preserve exact approved likenesses of both owner and Brutus. **Original image bytes have not been uploaded to permanent protected storage.**
- Jasper: previously discussed shade tree, blue-harness digging, purple plush under blanket, car bandana, indoor toys, forest creek; verify which exact files were approved before publishing.
- Butterscotch: verify approved portrait pairs and names before publishing.
- Brutis and Joey: distinguish names and chapters; do not assume any unverified artwork is approved.

## Outstanding before launch
1. Confirm the actual Cloudflare account/application and how the existing Access tester allowlist is configured. Do not request passwords, one-time codes, or tokens.
2. Create Cloudflare-protected gallery deployment and private storage.
3. Locate exact approved original images, preserve copies, and verify integrity before upload.
4. Test authorized and unauthorized access to gallery HTML, APIs, and individual images.
5. Add the verified gallery URL to Pups Journal and publish through its normal GitHub Pages workflow.
