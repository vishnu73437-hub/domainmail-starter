# DomainMail Starter

A mobile-friendly Node.js website with a contact form, admin sign-in, test email sender, consent-based bulk email (max 50 recipients per batch), and delivery logs.

## Requirements
- Node.js 20+
- Resend account and a verified sending domain for production sending
- A host that supports Node.js server routes. For durable logs, use a persistent disk or replace JSON logs with a managed database.

## Run locally
1. Copy `.env.example` to `.env`.
2. Set `RESEND_API_KEY`, `FROM_EMAIL`, `ADMIN_PASSWORD`, and a long random `SESSION_SECRET`.
3. Run `npm install` then `npm start`.
4. Open `http://localhost:3000`.

Never expose provider API keys in browser code. Configure secrets in your hosting provider instead of committing `.env`.

## Deploy
Deploy this folder to a Node.js-capable host (for example, a platform with a free tier if currently available). Set the same environment variables in the host's secret/environment settings. Add the custom domain in the hosting dashboard and publish the exact DNS records it provides. For email, add the sending domain in Resend and copy its current DKIM/SPF (and recommended DMARC) DNS records exactly. Do not use guessed DNS values.

## Important limitations
- Free plan limits change. Domain registration is normally paid, and custom domains, persistent storage, or email volume may incur costs.
- JSON logs are for a starter/demo. Some hosts erase local files during redeploy or use ephemeral storage. Use a managed database or persistent disk for production.
- The admin password is shared-secret authentication, suitable only for a small starter. Add stronger user management before public production use.
- Bulk sending is intentionally limited to 50 addresses per request and requires confirmation of recipient consent. Follow applicable privacy, anti-spam, and unsubscribe requirements.
- The website is not live until deployed to a hosting provider and configured with secrets and DNS records.
