# Wix installation

Not a one-box installation: use a Velo-enabled Wix Editor/Studio site. No backend executes on GitHub. This is a custom request form, not Wix Forms.

1. Enable Velo developer tools and install npm package ical.js in Wix.
2. Create backend/oasisCalendar.web.js in Wix. Paste this repository's wix/backend/oasisCalendar.web.js into it. Resolve all compilation errors.
3. In Wix Secrets Manager create OASIS_AIRBNB_ICAL and OASIS_VRBO_ICAL with the complete private URLs supplied in the conversation. Never commit their values or return them to the browser.
4. Create CMS collection ID OasisRequests. Set ALL direct view/add/update/delete permissions to Admin only. Fields: title, name, email, phone, notes, startDate, endDate, status = Text; guests = Number; expiresAt = Date and Time. Dates are YYYY-MM-DD TEXT and endDate is exclusive. Do not connect a public dataset. Verify live/sandbox settings.
5. Add an HTML Embed element on the Wix Reservations page; ID availabilityCalendar. Paste wix/calendar-embed.html. Replace ORIGIN with your exact published Wix origin, no trailing slash or path. For https://account.wixsite.com/site-name use https://account.wixsite.com . For a custom domain use its exact scheme and hostname. Preview may have another origin; test published site. Start around 900px high and check mobile clipping.
6. Add INDIVIDUAL native Wix elements OUTSIDE/below the iframe with IDs: selectedDates (Text), requestStatus (Text), guestName (Text input), guestEmail (Email input), guestPhone (Text/Phone input), guestCount (Number input, default 2), guestNotes (Text box), requestCaptcha (CAPTCHA), submitRequest (Button labelled Request These Dates). Enter IDs without #. Do not attach dataset submission actions. Confirm maximum 4 guests with Sherry.
7. Paste wix/page-code.js into this page's PAGE code, not the HTML iframe or site-wide code. Merge carefully with any existing custom code.
8. Publish and compare known booked nights from both feeds. A failed feed or unsupported recurring/timed event disables available dates. Complete CAPTCHA and submit a test inquiry. Verify the live CMS pending record and another browser's blue dates after refresh.
9. Manage status privately in CMS: pending (blue until expiresAt), confirmed (local red), declined/cancelled (clears). Extend expiresAt if needed. Confirmation is manual; payment is not verified. Delete/cancel test records after testing.
10. Install and TEST separate notifications or monitor CMS manually. A custom CMS insert does not automatically trigger Wix Forms email workflows. No email/SMS notification is installed here.

## Mandatory launch checks
Verify photo uploads, date matching, exclusive checkout/same-day turnover, range crossing red/blue nights, pending expiry, confirmation/cancellation, CAPTCHA failure, CMS privacy, origins, mobile sizing, feed failure behaviour, malformed inputs and upstream latency. Code is not live-tested in your account.

## Limits
Inbound feeds only. Local requests/confirmations do not block Airbnb/Vrbo. No outbound feed, payments, atomic inventory locking, or production abuse rate limiter. Two simultaneous requests can race; Sherry must check before confirming or accepting payment. External feed blocks are not proof of payment. Blue is local website pending, not a reliable import of external tentative status. Keep request button wording, not Confirm Booking.

## Troubleshooting
Connecting forever: origin, embed ID, page code, published domain. Availability error: secret names/URLs, parser installation, backend imports, live CMS fields, feed format. Disabled submit: CAPTCHA ID and verification. Missing record: CMS/live data and backend response. Never log private feed URLs or guest details in public logs.
