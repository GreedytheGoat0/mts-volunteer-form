# MTS Volunteer Interest Form

A standalone volunteer intake page for **Motivating the Teen Spirit** — ready to deploy at `motivatingtheteenspirit.com/volunteer` and wire to Keap/Infusionsoft in under 15 minutes.

**Live Demo:** https://GreedytheGoat0.github.io/mts-volunteer-form/

---

## What This Is

Motivating the Teen Spirit (MTS) equips teens with emotional intelligence and life skills through in-person programs across California, Oregon, and Washington. This form collects volunteer applications — vetting candidates appropriately given MTS works directly with teens in emotionally sensitive environments.

The form is a single self-contained HTML file. No build tools, no framework, no backend required. Drop it into the site, fill in two Keap values, and it's live.

---

## Keap / Infusionsoft Setup

The form submits directly to Keap's web form processor. Two values in `index.html` need to be replaced before going live.

### Step 1 — Create a Web Form in Keap

1. Log in to your Keap/Infusionsoft account
2. Go to **Marketing → Forms → Web Forms**
3. Click **New Form**
4. Name it `Volunteer Interest Form` and save
   (Fields and design inside Keap don't matter — this form is just a registration point)

### Step 2 — Get Your App Name and Form XID

1. Look at your browser's address bar while logged in — your subdomain is the app name
   - Example: `ab123.infusionsoft.com` → app name is `ab123`
2. From the web form you created, click **Embed Code**
3. In the embed snippet, find the value after `xid=`
   - Example: `xid=abc123def456` → your XID is `abc123def456`

### Step 3 — Update `index.html`

Find the `<form>` tag near the top of the `<main>` section and replace both placeholders:

```html
<!-- BEFORE -->
<form action="https://KEAP_APP_NAME.infusionsoft.com/app/form/process" ...>
  <input type="hidden" name="inf_form_xid" value="KEAP_FORM_XID" />

<!-- AFTER (example) -->
<form action="https://ab123.infusionsoft.com/app/form/process" ...>
  <input type="hidden" name="inf_form_xid" value="abc123def456" />
```

### Step 4 — Create Custom Fields in Keap

Standard contact fields (name, email, phone, city, state) map to Keap's built-in fields automatically.

The fields below require custom fields to be created in Keap under **CRM → Settings → Custom Fields → Contacts**. After creating each one, update the matching `name` attribute in `index.html`:

| Form label | `name` in HTML | Field type in Keap |
|---|---|---|
| Current occupation / role | `inf_custom_Occupation` | Text |
| Worked with teens before? | `inf_custom_TeenExperience` | Radio |
| Describe that experience | `inf_custom_TeenExperienceDetail` | Text Area |
| Why do you want to volunteer? | `inf_custom_VolunteerMotivation` | Text Area |
| How did you hear about us? | `inf_custom_ReferralSource` | Text |
| Availability: Weekday mornings | `inf_custom_AvailWeekdayMornings` | Checkbox |
| Availability: Weekday evenings | `inf_custom_AvailWeekdayEvenings` | Checkbox |
| Availability: Weekends | `inf_custom_AvailWeekends` | Checkbox |
| Interest: Program facilitation | `inf_custom_InterestFacilitation` | Checkbox |
| Interest: Event support | `inf_custom_InterestEvents` | Checkbox |
| Interest: Community outreach | `inf_custom_InterestOutreach` | Checkbox |
| Interest: Admin & operations | `inf_custom_InterestAdmin` | Checkbox |
| Interest: Social media & content | `inf_custom_InterestSocial` | Checkbox |
| Background check consent | `inf_custom_BackgroundCheck` | Radio |
| Anything else | `inf_custom_AdditionalNotes` | Text Area |

---

## Deployment

### Option A — Custom / Static HTML site
Upload `index.html` to your server in the directory that maps to `/volunteer`:
```
/public_html/volunteer/index.html
```

### Option B — WordPress
1. Create a new Page with the slug `volunteer`
2. Add a **Custom HTML** block and paste the full contents of `index.html`
3. Or ask your host to serve `index.html` as a static file at `/volunteer`

### Option C — Any other CMS
Host `index.html` as a static file on your server and configure your CMS to route `/volunteer` to it.

---

## Full Field Reference

| Label | Keap field name | Type | Required |
|---|---|---|---|
| First name | `inf_field_FirstName` | text | yes |
| Last name | `inf_field_LastName` | text | yes |
| Email address | `inf_field_Email` | email | yes |
| Phone number | `inf_field_Phone1` | tel | yes |
| City | `inf_field_City` | text | yes |
| State | `inf_field_State` | text | yes |
| Current occupation / role | `inf_custom_Occupation` | text | yes |
| Worked with teens before? | `inf_custom_TeenExperience` | radio | yes |
| Describe teen experience | `inf_custom_TeenExperienceDetail` | textarea | no |
| Why volunteer with MTS? | `inf_custom_VolunteerMotivation` | textarea | yes |
| How did you hear about us? | `inf_custom_ReferralSource` | text | yes |
| Availability (3 checkboxes) | `inf_custom_Avail*` | checkbox | yes (1+) |
| Areas of interest (5 checkboxes) | `inf_custom_Interest*` | checkbox | yes (1+) |
| Background check consent | `inf_custom_BackgroundCheck` | radio | yes |
| Anything else | `inf_custom_AdditionalNotes` | textarea | no |

---

## Brand

| Token | Value | Usage |
|---|---|---|
| Teal | `#00a0af` | Primary color, CTAs, section labels |
| Orange | `#e47e3d` | Required field indicator |
| Olive | `#505642` | Hero background, footer |
| Purple | `#8f6c95` | Available for secondary use |
| Font | Inter (Google Fonts) | All text |

---

## Contact

**Motivating the Teen Spirit** — a program of Motivating the Masses, Inc.
- Website: [motivatingtheteenspirit.com](https://motivatingtheteenspirit.com)
- Email: jelani@motivatingthemasses.com
