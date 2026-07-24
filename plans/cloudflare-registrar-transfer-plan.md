# Cloudflare registrar transfer plan

_Set aside on July 24, 2026 to revisit this over the weekend._

## Current state

- The domain is already using Cloudflare DNS.
- Active nameservers: `clyde.ns.cloudflare.com` and `mariah.ns.cloudflare.com`.
- The Cloudflare zone for `merkhetventures.com` is active.
- The website is running on the Cloudflare Pages project `merkhet-ventures`.
- Both `https://merkhetventures.com` and `https://www.merkhetventures.com` are active Pages custom domains and currently return HTTP 200.
- Google Workspace MX records are present in Cloudflare and should remain unchanged.
- The current registrar is 1API through the existing registrar account.
- The domain is currently transfer-locked (`clienttransferprohibited`).
- Current registrar expiration: August 9, 2026.

## Recommendation

Do not start the registrar transfer in a rush. The important DNS migration is already complete, so there is no need to transfer the registrar just to keep the website or email working.

When ready, transfer the registrar separately from DNS:

1. Confirm access to the current registrar account.
2. Confirm the renewal and transfer price at Cloudflare.
3. Unlock the domain at the current registrar.
4. Request the EPP/Auth transfer code.
5. Export or record the Cloudflare DNS records before starting.
6. Start the transfer into Cloudflare Registrar.
7. Leave the Cloudflare nameservers exactly as they are.
8. After completion, test the website, `www`, Gmail send/receive, calendar, and any Google service subdomains.

## Downtime expectation

A registrar transfer by itself should not interrupt the website or Google Workspace because DNS remains on Cloudflare. The transfer may take hours or days, and registrar controls may be temporarily unavailable while it processes, but there should be no planned DNS outage.

The main risk would be changing nameservers or DNS records during the transfer. Do not combine those actions.

## Email verification follow-up

The Google Workspace MX records are present. Before the registrar transfer, also verify whether SPF, DKIM, and DMARC should be added or restored in Cloudflare. Their absence does not necessarily mean Gmail is down, but these records improve mail authentication and deliverability.

## Decision checkpoint

Before starting, confirm:

- [ ] The domain is unlocked.
- [ ] The EPP/Auth code is available.
- [ ] Cloudflare confirms the transfer cost and renewal extension.
- [ ] The domain expiration date will not create a timing problem.
- [ ] The current DNS record list is backed up.
- [ ] Website and Google Workspace tests pass.
- [ ] No nameserver changes are planned during the transfer.
