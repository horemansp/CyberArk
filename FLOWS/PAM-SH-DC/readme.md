Example of a dual control with PAM self hosted ticketing system integration.
Pre-requisites:
- CyberArk identity with connectors setup to AD
    - User enrolled in CyberArk identity and setup with mobile app push authentication (no number matching) and/or email OTP only (no password required) in a single step
- CyberArk PAM self hosted setup with custom ticket integration for flows (requires the installation of a .dll file for this purpose. this is not provided here, speak to your CyberArk representative)

When prompted for a ticket ID the following can be entered in the ticketID field: (in this example, but can be changed to anything...)
- mobile (will trigger a push to mobile app for approval)
- email (will send an email with clickable link for approval)
- breakglass (will not enforce any approval and grant access immediately but sends warning emails)

