# Salaam Japan - Cloudflare Pages

This is a static web prototype. Japanese OCR is still experimental and must not be used as a definitive halal verdict.

## Cloudflare Pages GitHub deployment
1. Create a new GitHub repository (e.g. `salaam-japan`).
2. Upload `index.html` at the repository root.
3. In Cloudflare dashboard, Workers & Pages > Create > Pages > Connect to Git.
4. Authorize the repository and select it.
5. Set production branch to `main`, framework preset to None, build command empty, output directory `/` (repository root).
6. Deploy and open the generated `.pages.dev` URL.
7. Subsequent commits to `main` deploy automatically.

Do not choose Direct Upload if you want built-in Git integration for this project.

## Safety
- Never store Cloudflare API tokens or OCR service keys in frontend JavaScript.
- Future cloud OCR should use a server-side Cloudflare Worker or Pages Function.
- OCR errors must block automatic halal judgments.
