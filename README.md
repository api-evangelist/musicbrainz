# MusicBrainz (musicbrainz)

MusicBrainz is an open-source, community-maintained music encyclopedia operated by the MetaBrainz Foundation, a US 501(c)(3) non-profit. It collects metadata about artists, releases, recordings, works, labels, places, areas, events, instruments, series, URLs, and the relationships between them, then exposes the catalog through a free public REST web service at https://musicbrainz.org/ws/2/. The dataset itself is released under CC0 (core data) and CC-BY-NC-SA (supplemental tables), the schema is open, and full database dumps and a live replication feed are available. The web service is read-mostly with authenticated submission endpoints for tags, ratings, collections, barcodes, and ISRCs, and is rate-limited to one request per IP per second with a mandatory descriptive User-Agent header.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/musicbrainz/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/musicbrainz/main/apis.yml)

## Tags

- Music
- Metadata
- Encyclopedia
- Open Data
- Catalog
- Identifiers
- ISRC
- ISWC
- MBID
- DiscID
- Artists
- Releases
- Recordings
- Works
- Labels
- Cover Art
- Open Source
- Non Profit

## Timestamps

- **Created:** 2026-05-28
- **Modified:** 2026-05-29

## APIs

### MusicBrainz Web Service v2

The MusicBrainz Web Service v2 provides a free read-mostly REST API over the entire MusicBrainz catalog of music metadata. It supports three primary access patterns - lookup (fetch one entity by MBID), browse (list entities linked to a parent entity), and search (Lucene query across the indexed catalog) - across twelve core entity types (artist, release, release-group, recording, work, label, place, area, event, instrument, series, url, genre). Non-MBID lookups are available for ISRC (recordings), ISWC (works), disc IDs (releases), and URLs. Authenticated submission endpoints (HTTP Basic or OAuth2) allow clients to submit tags, ratings, collection membership, barcodes, and ISRCs. Responses are returned in XML (default) or JSON via the `fmt=json` parameter. The service enforces a strict one-request-per-second-per-IP rate limit and requires a meaningful User-Agent header on every request.

- **Human URL:** [https://musicbrainz.org/doc/MusicBrainz_API](https://musicbrainz.org/doc/MusicBrainz_API)
- **Base URL:** `https://musicbrainz.org/ws/2`

#### Tags

- Artists
- Releases
- Release Groups
- Recordings
- Works
- Labels
- Places
- Areas
- Events
- Instruments
- Series
- URLs
- Genres
- ISRC
- ISWC
- DiscID
- Browse
- Search
- Collections
- Submission

#### Properties

- [Documentation](https://musicbrainz.org/doc/MusicBrainz_API)
- [OpenAPI](openapi/musicbrainz-web-service-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/musicbrainz-web-service.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/musicbrainz-web-service.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Getting Started](https://musicbrainz.org/doc/MusicBrainz_API)
- [Authentication](https://musicbrainz.org/doc/MusicBrainz_API/Authentication)
- [Rate Limits](https://musicbrainz.org/doc/MusicBrainz_API/Rate_Limiting)
- [Search](https://musicbrainz.org/doc/MusicBrainz_API/Search)
- [Examples](https://musicbrainz.org/doc/MusicBrainz_API/Examples)
- [Schema](https://musicbrainz.org/doc/MusicBrainz_Database/Schema)
- [Identifiers](https://musicbrainz.org/doc/MusicBrainz_Identifier)
- [JSON Schema](json-schema/musicbrainz-artist-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/musicbrainz-release-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/musicbrainz-recording-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/musicbrainz-work-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/musicbrainz-artist-structure.json)
- [JSON-LD](json-ld/musicbrainz-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Spectral Rules](rules/musicbrainz-rules.yml)
- [Vocabulary](vocabulary/musicbrainz-vocabulary.yml)
- [Plans](plans/musicbrainz-plans-pricing.yml)
- [Rate Limits Spec](rate-limits/musicbrainz-rate-limits.yml)
- [SDK](https://pypi.org/project/musicbrainzngs/)
- [SDK](https://www.npmjs.com/package/musicbrainz-api)
- [SDK](https://github.com/metabrainz/libmusicbrainz)
- [SDK](https://github.com/metabrainz/mbdata)
- [SDK](https://github.com/metabrainz/mb-rngpy)
- [Schema](https://github.com/metabrainz/mmd-schema)

## Common Properties

- [Website](https://musicbrainz.org/)
- [Foundation](https://metabrainz.org/)
- [GitHub Organization](https://github.com/metabrainz)
- [Documentation](https://musicbrainz.org/doc/MusicBrainz_API)
- [Developer](https://musicbrainz.org/doc/Developer_Resources)
- [Forum](https://community.metabrainz.org/)
- [I R C](ircs://irc.libera.chat/#musicbrainz)
- [Blog](https://blog.metabrainz.org/)
- [Terms of Service](https://metabrainz.org/social-contract)
- [Privacy Policy](https://metabrainz.org/privacy)
- [License](https://musicbrainz.org/doc/About/Data_License)
- [Donate](https://metabrainz.org/donate)
- [Database](https://musicbrainz.org/doc/MusicBrainz_Database)
- [Schema](https://musicbrainz.org/doc/MusicBrainz_Database/Schema)
- [Download](https://musicbrainz.org/doc/MusicBrainz_Database/Download)
- [Replication](https://musicbrainz.org/doc/Replication_Mechanics)
- [Mirror](https://musicbrainz.org/doc/MusicBrainz_Database/Mirror)
- [Identifiers](https://musicbrainz.org/doc/MusicBrainz_Identifier)
- [Style Guide](https://musicbrainz.org/doc/Style)
- [A P I](https://musicbrainz.org/doc/MusicBrainz_API)
- [Rate Limits](https://musicbrainz.org/doc/MusicBrainz_API/Rate_Limiting)
- [Authentication](https://musicbrainz.org/doc/MusicBrainz_API/Authentication)
- [GitHub Repository](https://github.com/metabrainz/musicbrainz-server)
- [GitHub Repository](https://github.com/metabrainz/musicbrainz-docker)
- [GitHub Repository](https://github.com/metabrainz/musicbrainz-docs)
- [GitHub Repository](https://github.com/metabrainz/mmd-schema)
- [C L I](https://github.com/metabrainz/libdiscid)
- [Tools](https://picard.musicbrainz.org/)
- [Tools](https://github.com/usercourses63/musicbrainz-mcp-server)
- [Source Code](https://github.com/metabrainz/musicbrainz-server)
- [Mobile](https://github.com/metabrainz/musicbrainz-android)
- [Mobile](https://github.com/metabrainz/musicbrainz-ios)
- [Sister Project](https://listenbrainz.org/)
- [Sister Project](https://coverartarchive.org/)
- [Sister Project](https://critiquebrainz.org/)
- [Sister Project](https://bookbrainz.org/)
- [Public APIs Listing](https://github.com/public-apis/public-apis)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
