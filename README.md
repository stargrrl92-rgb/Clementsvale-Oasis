# Clementsvale Oasis

Property website and Wix/Velo availability/request calendar.

## Status
Source code installed in this repository. Original JPG photographs must still be uploaded to assets/images/ using the filenames listed in assets/images/UPLOAD-PHOTOS.txt. The live Wix integration must be installed and tested; committing code is not deployment. Existing preview.html and features.html redirect to the new website.

## Website
Open index.html locally to preview. Grey #d9d9d9, black, orange #ff5e1a; 195px logo; exterior hero; eight photo groups; direct phone/email links. Photos are referenced, not included in this source-only commit.

Use Wix or suitable commercial hosting for the business website. Do not assume GitHub Pages is appropriate for commercial booking-site hosting; review https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits . GitHub stores source; it does not execute Velo.

## Wix calendar
Follow wix/SETUP.md. Install npm package ical.js in Wix. Store private feed URLs ONLY in Wix Secrets Manager as OASIS_AIRBNB_ICAL and OASIS_VRBO_ICAL. No real feed tokens are in this repository.

Red = imported booked/blocked nights or local confirmed records. Blue = website requests pending for 24 hours. White = available to request. Checkout is exclusive. Imported feed events do not prove payment. Unsupported timed/recurring events or a failed feed disable availability rather than advertise unknown nights as free.

This is inbound synchronization only. Pending/local confirmed dates do NOT block Airbnb/Vrbo. Sherry must verify availability and block channels before confirming direct bookings. Check-and-insert is not atomic: simultaneous requests can race. No payments, automatic email/SMS notifications, or production rate limiter is included. Configure notifications separately and verify receipt. CAPTCHA is not comprehensive abuse protection.

## Privacy
Keep CMS collection admin-only. Public responses contain date arrays, not guest identities. Do not commit secrets, ICS exports, or guest records. Apply an appropriate privacy/retention policy before collecting real requests.

## Validation
This source commit has not been executed in Wix or tested against the private feeds. Test known Airbnb/Vrbo dates, CAPTCHA, pending/confirmed/cancelled records, expiry, checkout boundaries, mobile sizing, and failure behaviour before launch.
