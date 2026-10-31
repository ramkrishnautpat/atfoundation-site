# AT Foundation website — CMS-enabled Netlify version

This package keeps the current AT Foundation design and adds a browser-based content editor using **Decap CMS**. The owner can edit text, programme cards, impact highlights, founder details and upload replacement images without editing HTML.

## What the CMS can edit

Open `/admin/` after authentication. Under **Website Content → Homepage, About & Impact**, the editor can update:
- Hero heading, description and location note
- Homepage impact counters
- About text, vision and mission
- Add/edit/reorder/remove programme cards and upload their photos
- Impact highlights and headline number
- Founder biography and credentials
- CTA and footer description
- Hero, About and Founder photos

The public website reads these fields from `content/site.json`. Changes are committed to GitHub by the CMS and Netlify redeploys the site.

## 1. Upload / deploy

1. Extract this ZIP. Upload the **contents** into the root of your GitHub repository (keep `index.html` at root).
2. Confirm the repository is named `atfoundation-site` and owned by `ramkrishnautpat`. If not, update `repo:` in `admin/config.yml` to `YOUR_GITHUB_USERNAME/YOUR_REPOSITORY`.
3. Connect that repository to Netlify. Set build command blank and publish directory `.`.
4. Deploy.

## 2. Configure CMS login (GitHub OAuth)

This package uses Decap CMS's GitHub backend. This avoids relying on Netlify Git Gateway, which Netlify currently marks deprecated for new configurations. Editors must have a GitHub account and **Write** access to the website repository.

1. In GitHub, open **Settings → Developer settings → OAuth Apps → New OAuth App**.
2. Application name: `AT Foundation CMS`.
3. Homepage URL: `https://atfoundation.netlify.app`.
4. Authorization callback URL: `https://api.netlify.com/auth/done`.
5. Create the app and copy its Client ID and Client Secret.
6. In Netlify, open the site/project's access or OAuth provider settings and configure the GitHub authentication provider with that Client ID and Client Secret. The exact menu label may vary in Netlify's current UI.
7. In GitHub repository **Settings → Collaborators**, invite the owner/editor with **Write** access. They must accept the invitation and have a GitHub account.
8. Visit `https://atfoundation.netlify.app/admin/` and choose **Login with GitHub**.

If your Netlify project does not expose a GitHub OAuth provider configuration, do not share the Client Secret in chat or commit it to the repository. Use a supported OAuth proxy/Decap Turbo setup instead.

## 3. How the owner updates content

1. Visit `https://atfoundation.netlify.app/admin/`.
2. Select **Login with GitHub** and authorize access.
3. Open **Website Content → Homepage, About & Impact**.
4. Edit the relevant fields. To change a programme, use the Programmes list; add a card, edit its title/description, upload a photo, or reorder cards.
5. Click **Save**, then **Publish** (or the CMS publish action shown).
6. Wait for the Netlify deployment to finish, then refresh the public website.

## 4. Images

New CMS uploads are saved in `assets/uploads/`. Use compressed JPG/WebP images where possible. Only upload photographs AT Foundation owns or has permission to publish; obtain guardian consent before publishing identifiable photos of children.

## 5. Volunteer / enquiry form

The existing enquiry form is configured for Netlify Forms. After deployment, submit a test enquiry and confirm it appears under the Netlify site's **Forms** area. Configure email notifications in Netlify. It is a basic enquiry form, not a full volunteer CRM or application tracker.

## Important limitations

- This is a lightweight CMS, not WordPress. The editor manages the fields listed above; it does not provide arbitrary page-layout editing.
- Editors need GitHub accounts and repository write permission. If the owner should not have GitHub access, choose a managed CMS/authentication service instead.
- Events, blog publishing, historical event archive and a dedicated volunteer application workflow are not included in this basic CMS phase.
- Verify all impact numbers, dates, founder credentials and programme claims with AT Foundation before publishing. Replace remote demo images with approved organization photographs.
