gbifloc
=======

[![Project Status: Concept – Minimal or no implementation has been done yet, or the repository is only intended to be a limited example, demo, or proof-of-concept.](https://www.repostatus.org/badges/latest/concept.svg)](https://www.repostatus.org/#concept)

GBIF occurrence data is getting rather large, about 2TB. Even the simplest version of their data is ~650 GB. Both of these are too large for most people's personal laptops. I personally have a 500 GB hard drive on this laptop, so I'm out of luck. Of course one could plug in an external HD to make it work.

GBIF is working on having their data in cloud environments (see https://discourse.gbif.org/t/gbif-exports-as-public-datasets-in-cloud-environments/1835) - which will be a great option for working with large amounts of GBIF data.

This package aims to accumulate records as you use `rgbif`, making future requests faster. It takes all of your GBIF queries and caches those results in a local database that you can query later.

How it will work:

- Get some GBIF data: `rgbif::occ_data()` or `rgbif::occ_download()`
- Set up the cache: `gbifloc::config(db = "sqlite")`
- Pass the above request outputs to `gbifloc::cache()`, and the data is cached in a local cache folder
- Use `gbifloc` functions to search your locally cached data:
    - occurrences: `gbifloc::locc_search()`
    - occurrences: `gbifloc::lname_search()`
- And you can query the cached SQL data any other way you choose, with dplyr, etc.
- Citing data will hopefully be easy, use `rgbif::gbif_citation()` as with all `rgbif` functions (leverage datasetkey's in the database)
