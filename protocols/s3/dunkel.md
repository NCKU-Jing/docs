Dunkel Cloud Storage
====

:::{image} _images/Dunkel_Cloud_Storage.png
:alt: Dunkel Cloud Storage Drive Icon
:width: 128px
:::

> [Dunkel Cloud Storage](http://www.dunkel.de/s3/) ist ein S3 kompatibler Cloud Storage in deutschen Rechenzentren. 

Refer also to [S3](index.md) wiki page in general.

## Connecting

### Connection Profile

{download}`Download<https://profiles.cyberduck.io/Dunkel%20Cloud%20Storage.cyberduckprofile>` the *Dunkel Cloud Storage Connection Profile* or install it from *Preferences… → Profiles* for preconfigured settings.

### Manual Configuration

- Protocol: `S3`
- Server: `dcs.dunkel.de`

## Limitations

- No bucket location support (All data is stored in Germany).
- No bucket logging configuration.
- Storage class options are not available.
- Torrent URLs are not supported.
- No content distribution ([CDN](../../protocols/cdn/index.md)) configuration.