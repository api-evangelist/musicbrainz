# MusicBrainz

MusicBrainz is an open-source, community-maintained music encyclopedia operated by the [MetaBrainz Foundation](https://metabrainz.org/), a US 501(c)(3) non-profit. It collects metadata about artists, releases, recordings, works, labels, places, areas, events, instruments, series, URLs, and the typed relationships between them, and exposes the entire catalog through a free public REST web service at `https://musicbrainz.org/ws/2/`.

The dataset itself is released under CC0 (core data) and CC-BY-NC-SA (supplemental tables), the schema is open, and full database dumps plus a live replication feed are available. The web service is read-mostly with authenticated submission endpoints for tags, ratings, collections, barcodes, and ISRCs.

**APIs.yml:** [apis.yml](apis.yml)

## Type
- **x-type:** opensource
- **x-governance:** MetaBrainz Foundation (501(c)(3) non-profit)
- **x-license-data:** CC0 (core) / CC-BY-NC-SA (supplemental)
- **x-license-code:** GPLv2 / LGPL / MIT (varies by repo)

## API

### MusicBrainz Web Service v2
The MusicBrainz Web Service v2 is the free public REST API to the MusicBrainz open music encyclopedia.

- **Base URL:** `https://musicbrainz.org/ws/2`
- **Docs:** https://musicbrainz.org/doc/MusicBrainz_API
- **OpenAPI:** [openapi/musicbrainz-web-service-openapi.yml](openapi/musicbrainz-web-service-openapi.yml)

**Access patterns**
- **Lookup** — fetch any entity by MBID with configurable `inc` sub-resources
- **Browse** — list entities linked to a parent entity, with `limit`/`offset` pagination
- **Search** — full Lucene query syntax across the indexed catalog

**Entity types (12 + genres)**
artist, release, release-group, recording, work, label, place, area, event, instrument, series, url, genre

**Non-MBID lookups**
- `/isrc/{isrc}` — recordings by International Standard Recording Code
- `/iswc/{iswc}` — works by International Standard Musical Work Code
- `/discid/{discid}` — releases by CD Disc ID (libdiscid)
- `/url?resource={url}` — URLs by literal resource string

**Submission endpoints (authenticated, XML body)**
- `POST /tag` — user tags (upvote/downvote/withdraw)
- `POST /rating` — user ratings (0-5)
- `POST /release` — release barcodes
- `POST /recording` — recording ISRCs
- `PUT|DELETE /collection/{mbid}/{entity_type}` — collection membership

**Authentication**
HTTP Basic or OAuth 2.0 with editor credentials; required only for submissions and private/user-specific reads.

**Rate limiting**
Hard ceiling of **1 request per second per source IP**, enforced globally. A meaningful `User-Agent` header is mandatory on every request (e.g. `MyApp/1.0 ( contact@example.com )`). Default library User-Agents are blocked.

**Response formats**
MMD-2 XML (default), JSON (`fmt=json`), and `txt` for `/genre/all`.

## Artifacts

### OpenAPI ([openapi/](openapi/))
- `musicbrainz-web-service-openapi.yml` — 24 operations covering every entity lookup, browse, search, identifier lookup, collection endpoint, and submission endpoint.

### JSON Schema ([json-schema/](json-schema/))
- `musicbrainz-artist-schema.json`
- `musicbrainz-release-schema.json`
- `musicbrainz-recording-schema.json`
- `musicbrainz-work-schema.json`

### JSON Structure ([json-structure/](json-structure/))
- `musicbrainz-artist-structure.json`

### JSON-LD ([json-ld/](json-ld/))
- `musicbrainz-context.jsonld` — schema.org alignment for MusicBrainz entities.

### Spectral Rules ([rules/](rules/))
- `musicbrainz-rules.yml` — 22 governance rules enforcing MBID UUID format, ISRC pattern, `inc`/`fmt` parameters, mandatory 429 responses, User-Agent and rate-limit documentation, submission `client` parameter, and HTTPS server URLs.

### Vocabulary ([vocabulary/](vocabulary/))
- `musicbrainz-vocabulary.yml` — domain terms (MBID, ISRC, ISWC, DiscID, ISNI, IPI, Artist, Release, Release Group, Recording, Work, Track, Label, Place, Area, Event, Instrument, Series, URL, Genre, Relationship, Artist Credit, Tag, Rating, Collection, Editor, MMD-2 XML, Live Data Feed, Rate Limit, NGS).

### Naftiko Capabilities ([capabilities/](capabilities/))
Self-contained per-business-surface capabilities (each with HTTP consumer + REST adapter + MCP adapter):

- `musicbrainz-artists.yaml`
- `musicbrainz-releases.yaml`
- `musicbrainz-recordings.yaml`
- `musicbrainz-works.yaml`
- `musicbrainz-labels.yaml`
- `musicbrainz-places.yaml`
- `musicbrainz-areas.yaml`
- `musicbrainz-events.yaml`
- `musicbrainz-instruments.yaml`
- `musicbrainz-series.yaml`
- `musicbrainz-identifiers.yaml` — ISRC, ISWC, DiscID, URL lookups
- `musicbrainz-search.yaml` — Lucene-search wrappers across all entities + genres
- `musicbrainz-collections.yaml` — user collections + tag/rating/barcode/ISRC submission

### Examples ([examples/](examples/))
- `musicbrainz-lookup-artist-example.json` — Nirvana lookup with aliases, tags, rating
- `musicbrainz-search-recordings-example.json` — Lucene search across recordings
- `musicbrainz-lookup-isrc-example.json` — ISRC → recording lookup
- `musicbrainz-lookup-discid-example.json` — DiscID → release lookup

### Plans ([plans/](plans/))
- `musicbrainz-plans-pricing.yml` — three tiers: free Public Web Service, individual Donor, and commercial Supporter (with Live Data Feed access).

### Rate Limits ([rate-limits/](rate-limits/))
- `musicbrainz-rate-limits.yml` — 1 req/sec/IP, mandatory User-Agent, 503 (or 429) with Retry-After, replicate-for-volume policy.

## GitHub Organization

The [metabrainz](https://github.com/metabrainz) GitHub org hosts ~150 active repos. Highlights relevant to API consumers:

| Repo | Purpose | Language |
|---|---|---|
| [musicbrainz-server](https://github.com/metabrainz/musicbrainz-server) | Canonical server (website, API, DB tools) | Perl |
| [musicbrainz-docker](https://github.com/metabrainz/musicbrainz-docker) | Self-hosted MB replica via Docker Compose | Shell |
| [musicbrainz-docs](https://github.com/metabrainz/musicbrainz-docs) | Documentation source | Python |
| [mmd-schema](https://github.com/metabrainz/mmd-schema) | MMD-2 RELAX NG schema (canonical XML contract) | Java |
| [libmusicbrainz](https://github.com/metabrainz/libmusicbrainz) | C++ client library | C++ |
| [libdiscid](https://github.com/metabrainz/libdiscid) | C library for computing Disc IDs from CD TOC | C |
| [python-discid](https://github.com/metabrainz/python-discid) | Python bindings for libdiscid | Python |
| [mbdata](https://github.com/metabrainz/mbdata) | Python SQLAlchemy models for the MB DB | Python |
| [mb-rngpy](https://github.com/metabrainz/mb-rngpy) | Python bindings for the MMD RELAX NG schema | Python |
| [picard](https://github.com/metabrainz/picard) | Official cross-platform music tagger | Python |
| [musicbrainz-android](https://github.com/metabrainz/musicbrainz-android) | Official Android client | Kotlin |
| [musicbrainz-ios](https://github.com/metabrainz/musicbrainz-ios) | Official iOS client | Swift |
| [musicbrainz-bot](https://github.com/metabrainz/musicbrainz-bot) | Python bot for facilitating MB edits | Python |
| [listenbrainz-server](https://github.com/metabrainz/listenbrainz-server) | Sister project: listening history (uses MBIDs) | Python |
| [CAA-spec](https://github.com/metabrainz/CAA-spec) | Cover Art Archive specification | — |

## MCP Servers

- [musicbrainz-mcp-server](https://github.com/usercourses63/musicbrainz-mcp-server) (community) — FastMCP-based MCP server with 10 tools wrapping MusicBrainz queries.

## Sister Projects

- [ListenBrainz](https://listenbrainz.org/) — open listening-history platform keyed on MBIDs
- [Cover Art Archive](https://coverartarchive.org/) — release artwork keyed on release MBIDs
- [CritiqueBrainz](https://critiquebrainz.org/) — CC-licensed music reviews
- [BookBrainz](https://bookbrainz.org/) — open book metadata encyclopedia

## Tags
Music, Metadata, Encyclopedia, Open Data, Catalog, Identifiers, ISRC, ISWC, MBID, DiscID, Artists, Releases, Recordings, Works, Labels, Cover Art, Open Source, Non Profit

## Timestamps
- **Created:** 2026-05-28
- **Modified:** 2026-05-29

## Maintainers
- **Kin Lane** — kin@apievangelist.com
