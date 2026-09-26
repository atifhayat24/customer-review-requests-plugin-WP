# IR Review Requests for WooCommerce

**Free WordPress plugin that automatically asks your WooCommerce customers for a review – on Trustpilot, Google, any other review site, or your own product pages – a set time after their order is completed.**

No monthly subscription, no invitation limits, no third-party service. It runs inside your own WordPress site and sends from your own email account.

> **[⬇ Download the latest version](../../releases/latest)** – grab `ir-review-requests.zip` from the release (not "Source code").

---

## What it does

- **Automatic review requests** – when an order reaches a status you choose (Completed by default), the customer gets a review email after a delay you set in minutes, hours or days.
- **Any review platform** – switch on Trustpilot, Google, another site (Facebook, Feefo, Yell…) and/or your own WooCommerce product reviews. The first becomes the main button; the others appear underneath. Product reviews list what the customer actually bought.
- **Optional reminder** – one follow-up, automatically skipped if the customer already clicked a review link, left a product review or unsubscribed.
- **Previous customers** – queue review requests for everyone who ordered before you installed it (all time or a chosen period, one email per customer), sent gradually in the background.
- **Reliable sending** – built-in SMTP (cPanel / hosting email), PHP mail, or WordPress default. SMTP settings only affect review emails, not the rest of your site. Failed sends retry automatically (15 min, 1 h, 6 h, daily).
- **Doesn't depend on WP-Cron alone** – uses WooCommerce's Action Scheduler, plus a backup runner that sends due emails on normal page visits if the scheduler is late.
- **Dashboard & records** – emails sent, click rate, waiting, failed; full email list and activity log with CSV export; review status box on each order.
- **Unsubscribe built in** – link in every email plus one-click unsubscribe headers (Gmail / Yahoo bulk-sender requirement). Unsubscribed customers are never emailed again.
- **Sensible safeguards** – won't email cancelled/refunded orders, won't ask the same customer twice within a cooldown period, throttles sending to stay under host limits.
- **Tools & health** – checks your setup, sends test emails (with the SMTP conversation for troubleshooting), previews the email using a real order.
- Uses your **WooCommerce email design**. Compatible with **HPOS** (High-Performance Order Storage).

## Screenshots

<!-- Add your own: create a /screenshots folder in the repo and upload PNGs, then uncomment. -->
<!--
![Dashboard](screenshots/dashboard.png)
![Settings](screenshots/settings.png)
![Email](screenshots/email.png)
-->

## Requirements

| | Minimum | Tested with |
|---|---|---|
| WordPress | 5.8 | 7.1.2 |
| WooCommerce | 6.0 | 11.1.2 |
| PHP | 7.2 (8.1+ recommended) | 8.3 |

## Installation

1. Download `ir-review-requests.zip` from the **[latest release](../../releases/latest)**.
   Use the attached zip, **not** GitHub's "Source code" download – that one has a different folder name and won't update cleanly.
2. In WordPress go to **Plugins → Add New → Upload Plugin**, choose the zip, **Install Now**, then **Activate**.
3. You'll land on **Review Requests** in the admin menu.

**Updating:** upload the new zip the same way and click **Replace current with uploaded**. Settings and records are kept.

## Quick setup (5 minutes)

1. **Settings → Review platforms** – tick the platforms you want and paste their review links:
   - **Trustpilot:** `https://uk.trustpilot.com/evaluate/yourdomain.com`
   - **Google:** Business Profile → **Ask for reviews** → copy the link (looks like `https://g.page/r/…/review`). Use this rather than the "Share" link, which opens your profile instead of the review box.
2. **Settings → Sending** – choose how emails are sent:
   - **SMTP server (recommended)** – for cPanel hosting usually host `mail.yourdomain.com`, SSL, port 465, username = the full email address.
   - **WordPress default** – if you already use an SMTP plugin such as WP Mail SMTP or FluentSMTP.
   - **PHP mail** – only if your host supports it (many have it disabled).
3. **Tools & health → Send test email** – check it arrives and everything in the health list is green.
4. **Settings → General** – tick **Enabled** and save. Tip: set the delay to 2 minutes, complete a test order to see it work in real time, then set it back to days.

**Optional but recommended:** on low-traffic sites, add a server cron job so emails go out on time even when nobody is visiting. The exact command for your site is shown on **Tools & health**.

## FAQ

**Is it really free? Are there limits?**
Yes, and no limits from the plugin. Your email host's own hourly sending limit still applies – set **Emails per run** in Settings to stay under it (default 20 every 5 minutes).

**Where is my SMTP password stored?**
Encrypted in your database (AES-256 with your site's secret keys) and never shown again in the admin. For extra security you can instead add `define( 'IRR_SMTP_PASSWORD', 'your-password' );` to `wp-config.php`.

**Will it change my other WooCommerce emails?**
No. Its SMTP settings are only used for review request emails.

**What if my mail server is down?**
Emails are retried automatically. After the maximum attempts they're marked Failed and can be retried from the Emails screen with one click.

**Does it work with Trustpilot's free plan?**
Yes – it sends customers to your public Trustpilot review page, so there's no invitation limit. Reviews collected this way are not labelled "Verified" by Trustpilot (only Trustpilot's own invitations are).

**Can I translate it?**
Yes, it's translation-ready (text domain `ir-review-requests`).

## Before emailing customers

- Ask **everyone** the same way. Filtering so only happy customers are sent to Google or Trustpilot ("review gating") breaks both platforms' rules.
- Don't offer incentives for reviews.
- Make sure your privacy policy covers review requests. Every email includes an unsubscribe link. Rules differ by country – check what applies to you, especially before emailing old customers.

This plugin is a tool; you're responsible for how you use it.

## Support & contributing

- Found a bug or have an idea? **[Open an issue](../../issues)** – include your WordPress, WooCommerce and PHP versions (Tools → Site Health → Info) and anything shown on the plugin's Tools & health page.
- Pull requests are welcome.

## Disclaimer

Provided "as is", without warranty of any kind – test on a staging site or take a backup before installing on a live store. Not affiliated with or endorsed by Trustpilot, Google, Automattic or WooCommerce; names are used only to describe compatibility.

## License

[GPL-2.0-or-later](https://www.gnu.org/licenses/gpl-2.0.html), the same licence as WordPress.

Made by **Insightful Reach**.
