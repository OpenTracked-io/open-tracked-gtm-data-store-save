# Open Tracked Data Store Save

_Server tag template for Google Tag Manager (server container)._

Remembers what an event tells you about a visitor (hashed email and phone, hashed name, an external ID, Meta click and browser IDs) in your Open Tracked Data Store. Later events of the same visitor can then be completed from it with the companion **Open Tracked Data Store Lookup** variable, so a returning visitor who only browses still reaches Meta, TikTok and Google Ads with the details given at checkout.

## How to use

1. Switch on **Data Store** in your Open Tracked dashboard (Container, Power-Ups). Copy the address and the token it shows.
2. Add this tag to your server container. Paste the address and token (a Constant variable is the easiest place to keep them).
3. Fire it on the events where a visitor identifies themselves: begin checkout, add payment info, purchase, lead.
4. Read the saved details back with **Open Tracked Data Store Lookup**.

## Fields

| Field | Name | What it does |
|---|---|---|
| Data Store address | `apiUrl` | From the Data Store power-up in your Open Tracked dashboard, for example https://app.opentracked.io/api/ds/v1/123. |
| Data Store token | `token` | From the same page. |
| Remember the visitor by | `keySource` |  |
| Email (hashed) | `saveEmail` |  |
| Phone (hashed) | `savePhone` |  |
| First and last name (hashed) | `saveName` |  |
| External ID / user ID | `saveExternalId` |  |
| Meta click and browser IDs (fbc, fbp) | `saveClickIds` |  |
| Keep for (days) | `ttlDays` | After this the entry is deleted. Each new save starts the days again. |

## Privacy

- Email, phone and names are normalised and hashed with SHA-256 **before** they leave your server container. A value that already is a SHA-256 hash is kept as it is. Phone numbers are reduced to digits first.
- The visitor is never stored under their ID: the key is `cid:` or `uid:` followed by the SHA-256 hash of the GA4 client ID or user ID.
- Entries are deleted after the number of days you set (default 90). Each save starts the days again.
- Nothing is saved when the event carries none of the chosen details.

## Permissions

- **Reads event data**: Reads the visitor details and the client ID from the event.
- **Sends HTTP requests**: Only to `https://app.opentracked.io/api/ds/` and `https://app.openserver.digital/api/ds/` (your Open Tracked Data Store).

## Notes

Requires an Open Tracked account. The Data Store is available on every Open Tracked plan; the number of entries depends on the plan.

## About Open Tracked

[Open Tracked](https://opentracked.io) is a first-party tracking service: a tagging server on your own domain, an analytics pixel and a CRM. Documentation: https://docs.opentracked.io/google-tag-manager

## License

Apache License 2.0, see [LICENSE](LICENSE).
