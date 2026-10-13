# NTE forms — production Salesforce

Production forms site: https://stevostar1234.github.io/nte-production-forms/

Ten NTE forms, in journey order: two expressions of interest; partner/sponsor,
delivery-partner and exhibitor applications; four booking updates; guest
registration. The staff chooser and thank-you page support those forms.
Volunteers are outside this release.

## Current production configuration

Submissions create records in **production Salesforce**. NTE uses live Stripe;
payments are real. These forms do not choose the Stripe mode.

The three application forms require separate privacy and terms checkboxes.
Kate's original 12 October 2026 PDFs are hosted unchanged in `assets/documents/`.
`termsUrls.exhibitor` selects exhibitor terms; `termsUrls.partnerSponsor` selects
partner/sponsor terms. The owner explicitly chose partner/sponsor terms for
Delivery Partners too. `data-terms-type` selects the document for each form.

`allowUnlinkedTermsForTesting` is false. Missing audience terms block application
submission; one audience cannot silently fall back to the other document.
The terms checkbox sends `1` to `NTE_Booking_Terms_Accepted__c`; privacy sends `1`
to `NTE_Privacy_Accepted__c`. Production's existing conversion flow preserves
them separately. Historical testing ticks are not relabelled as final consent.
Application form versions identify this release: exhibitor v14, partner v15,
and Delivery Partner v3. No Salesforce field or record changes accompany it.

PDF links open separately; PDF bytes are not embedded in Squarespace code
blocks. When the client provides their hosted PDF URLs, update `termsUrls`
and regenerate the inline bundle. The brochure and final client form URLs
remain outstanding. These terms are specific to NTE27 and need client review
before reuse for a later event.

The site is excluded from search indexing but is publicly accessible. Do not
upload Salesforce exports, credentials, applicant data or private audit files.

## Website handover

The matching inline repository is
https://github.com/stevostar1234/nte-production-inline-forms . It contains the
exact source snapshot, reproducible build and `.txt` code blocks.

Use the client-approved website addresses in Salesforce routing and the return
page configuration when the forms are installed on the NTE website. Keep this
site and the inline release consistent. The MMUAT preview remains separate at
https://stevostar1234.github.io/nte27-web-to-lead-demo/ .

No pricing, payment workflow or shared Mission layouts are changed by this
website distribution. The existing native production configuration determines
email timing, booking workflow and Stripe mode.

## Brochure handover

The package section opens the stable `partner-sponsor-brochure.html` URL in a
new tab. That page redirects to `assets/documents/nte27-partner-sponsor-brochure.pdf`.
The PDF is intentionally one blank page, explicitly requested by the owner
pending Laura's final brochure. It provides no package information yet.

To publish the brochure, replace that PDF at the same path. Alternatively,
change both URLs in the redirect page to the client's approved hosted PDF URL.
The installed forms need no edit because they retain the stable landing URL.
If browsers retain an older PDF briefly, add a new revision query to both
redirect targets, then verify a fresh anonymous visit. Publish and verify the
finished document before telling applicants to consult the brochure.
