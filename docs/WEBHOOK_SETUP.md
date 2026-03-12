# Strapi Webhook Setup for TECH DERRICK

Set up one outbound webhook in Strapi Admin to trigger immediate ISR revalidation on Next.js.

## Target URL

`POST https://techderrick.vercel.app/api/revalidate?secret=techderrick_strapi_revalidate_20260312`

## Events to enable

Enable events for these content-types:

- App (`api::app.app`): create, update, publish, unpublish, delete
- Guide (`api::guide.guide`): create, update, publish, unpublish, delete
- Homepage (`api::homepage.homepage`): create, update, publish, unpublish, delete
- Single Page (`api::single-page.single-page`): create, update, publish, unpublish, delete

If your Strapi UI only supports global events, enable all entry events and keep this webhook dedicated to TECH DERRICK.

## Verification

1. Publish or update one App entry in Strapi.
2. Confirm webhook delivery success in Strapi webhook logs.
3. Open `https://techderrick.vercel.app/tools` and verify the update appears immediately.

## Next.js env alignment

Use these values in the Next.js app (`nextjs-boilerplate/.env.local`):

```bash
STRAPI_URL=https://ingenious-baseball-715144ecf2.strapiapp.com
STRAPI_APPS_PATH=/api/apps
STRAPI_GUIDES_PATH=/api/guides
STRAPI_REVALIDATE_SECRET=techderrick_strapi_revalidate_20260312
```
