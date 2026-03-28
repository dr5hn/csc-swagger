# Country State City API — Playground

Interactive API documentation for the [Country State City API](https://countrystatecity.in).

**Live:** [playground.countrystatecity.in](https://playground.countrystatecity.in)

## What this is

A static [Swagger UI](https://swagger.io/tools/swagger-ui/) deployment hosted on GitHub Pages. The OpenAPI 3.0 spec lives in `config.json` and documents all geographic data endpoints, pricing tiers, data access levels, and error responses.

## Endpoints

| Method | Path | Description | Min Tier |
|--------|------|-------------|----------|
| GET | `/countries` | List all countries | Community |
| GET | `/countries/{ciso}` | Country detail by ISO2 or ID | Community |
| GET | `/countries/{ciso}/states` | States of a country | Community |
| GET | `/countries/{ciso}/states/{siso}` | State detail | Community |
| GET | `/countries/{ciso}/states/{siso}/cities` | Cities of a state | Community |
| GET | `/states` | All states globally | Supporter |
| GET | `/countries/{ciso}/cities` | All cities of a country | Professional |

## Pricing Tiers

| Tier | Price | Daily | Monthly | Data Access |
|------|-------|-------|---------|-------------|
| Community | Free | 100 | 3,000 | Basic |
| Starter | $5/mo | 300 | 9,000 | Basic |
| Supporter | $9/mo | 1,000 | 30,000 | Coordinates |
| Professional | $29/mo | 3,300 | 100,000 | Full |
| Business | $79/mo | 25,000 | 750,000 | Full |

## Data Access Levels

Fields returned depend on your plan:

- **Basic** — Core fields: id, name, iso2, iso3, phonecode, capital, currency, native, emoji, latitude, longitude, region, subregion, timezones
- **Coordinates** (Supporter+) — Basic + numeric_code, currency_name, currency_symbol, tld, nationality, population, gdp, area_sq_km, postal codes, emojiU, fips_code, type, level, native, timezone
- **Full** (Professional+) — All fields including translations (18+ languages) and wikiDataId

## Local Development

No build step required. Open `index.html` in a browser or serve with any static file server:

```bash
npx serve .
```

## Updating the Spec

Edit `config.json` directly. It's a standard [OpenAPI 3.0.3](https://spec.openapis.org/oas/v3.0.3) document. Push to `main` and GitHub Pages deploys automatically.

When updating, keep in sync with:
- **Routes:** `csc-app/api/src/routes/world.routes.ts`
- **Tier config:** `csc-app/api/src/config/pricingTiers.ts`
- **Field access:** `csc-app/api/src/services/dataAccessService.ts`

## Links

- **API Dashboard:** [app.countrystatecity.in](https://app.countrystatecity.in)
- **Main API:** [api.countrystatecity.in/v1](https://api.countrystatecity.in/v1)
- **Database repo:** [github.com/dr5hn/countries-states-cities-database](https://github.com/dr5hn/countries-states-cities-database)
