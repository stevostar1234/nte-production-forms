# NTE forms — production Salesforce

Client testing site: https://stevostar1234.github.io/nte-production-forms/

Ten NTE forms, in journey order: two expressions of interest; partner/sponsor,
delivery-partner and exhibitor applications; four booking updates; guest
registration. The staff chooser and thank-you page support those forms.
Volunteers are outside this release.

## Current testing configuration

Submissions create records in **production Salesforce**, not MMUAT. Use fictional
applicant details and the agreed test mailbox. Stripe is currently configured
for the client's Stripe sandbox; these forms do not choose Stripe mode.

The three application forms show independent required privacy and terms
checkboxes. Final Terms & Conditions are awaited. The owner explicitly approved
showing unlinked terms for client testing, using the existing
`NTE_Booking_Terms_Accepted__c` checkbox field. The exception is
`allowUnlinkedTermsForTesting: true` in `assets/config.js`. Test ticks are not
acceptance of the client's final terms and must not be carried forward as such.

Before public launch, set `termsUrl` to the approved terms document and set
`allowUnlinkedTermsForTesting: false`; regenerate the inline package from the
same files. Ordinary production configuration blocks application submission if
terms are missing. Privacy uses its own existing link and field. No new
Salesforce consent field or picklist is required.

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
