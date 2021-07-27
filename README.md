# Analysis of science journalism reveals gender and regional disparities in coverage


<!-- usage note: edit the H1 title above to personalize the manuscript -->

[![HTML Manuscript](https://img.shields.io/badge/manuscript-HTML-blue.svg)](https://greenelab.github.io/nature_news_manuscript/)
[![PDF Manuscript](https://img.shields.io/badge/manuscript-PDF-blue.svg)](https://greenelab.github.io/nature_news_manuscript/manuscript.pdf)
[![GitHub Actions Status](https://github.com/manubot/rootstock/workflows/Manubot/badge.svg)](https://github.com/greenelab/nature_news_manuscript/actions)
<!-- usage note: delete CI badges above for services not used by your manuscript -->

## Manuscript description

<!-- usage note: edit this section. -->

Science journalism informs the public of the process and outcome of research as well as the implications of new scientific findings.
Such journalism also shapes the public’s view of scientists and legitimizes experts.
Those covering science can only cite and quote a limited number of sources.
Sources may be identified by the journalist’s research or by recommendations by other scientists.
In both cases, biases may influence who is identified and ultimately included as an expert.
To ensure our results are generalizable, we analyzed two journalism outlets with different target audiences, _Nature_ and _The Guardian_.
This resulted in 37,748 total articles, 15,747 science-related articles from _The Guardian_ and 22,001 non-research articles published by _Nature_ to quantify possible disparities.
Our analysis considered three possible sources of disparity: gender, name origin, and country affiliation.
To explore these sources of disparity, we extracted cited authors’ names and affiliations, as well as extracted names of quoted speakers.
While citations and quotations within a piece do not reflect the entire information-gathering process, they can provide insight into the demographics of visible sources.
We then used the extracted names to predict gender and name origin of the cited authors and speakers. <!-- maybe add caveat here -->

In order to appropriately quantify the level of difference, we must identify a suitable reference set for comparison.
We chose first and last authors within primary research articles in _Nature_ and a subset of _Springer Nature_ articles in the same time period as our comparator.
In our analysis, we found a very similar skew towards male quotation in both _The Guardian_ and _Nature_ science journalism-related articles.
However, quotation in _Nature_ is trending toward equal representation at a faster rate than first and last authorship in academic publishing.
Interestingly, we found that the gender disparity in _Nature_ quotes was column-dependent, with the "Career Features" column reaching gender parity.
Our name origin analysis found a significant over-representation of names with predicted Celtic/English origin and under-representation of names with a predicted East Asian origin.
This finding was observed both in extracted quotes and journal citations, but dampened in citations.
Finally, we performed an analysis to identify how countries vary in the way that they're described in scientific journalism.
We focused on two groups of countries: countries that are often mentioned in articles, but do not often have affiliated authors cited, and countries that have affiliated authors that are often cited, but the country is not typically mentioned.
We found that the articles in which the less cited countries occur tend to have more agricultural, extraction-related, and political terms, whereas articles including highly cited countries have broader scientific terms.
This discrepancy indicates a possible lack of regional diversity in the reporting of scientific output.

## Manubot

<!-- usage note: do not edit this section -->

Manubot is a system for writing scholarly manuscripts via GitHub.
Manubot automates citations and references, versions manuscripts using git, and enables collaborative writing via GitHub.
An [overview manuscript](https://greenelab.github.io/meta-review/ "Open collaborative writing with Manubot") presents the benefits of collaborative writing with Manubot and its unique features.
The [rootstock repository](https://git.io/fhQH1) is a general purpose template for creating new Manubot instances, as detailed in [`SETUP.md`](SETUP.md).
See [`USAGE.md`](USAGE.md) for documentation how to write a manuscript.

Please open [an issue](https://git.io/fhQHM) for questions related to Manubot usage, bug reports, or general inquiries.

### Repository directories & files

The directories are as follows:

+ [`content`](content) contains the manuscript source, which includes markdown files as well as inputs for citations and references.
  See [`USAGE.md`](USAGE.md) for more information.
+ [`output`](output) contains the outputs (generated files) from Manubot including the resulting manuscripts.
  You should not edit these files manually, because they will get overwritten.
+ [`webpage`](webpage) is a directory meant to be rendered as a static webpage for viewing the HTML manuscript.
+ [`build`](build) contains commands and tools for building the manuscript.
+ [`ci`](ci) contains files necessary for deployment via continuous integration.

### Local execution

The easiest way to run Manubot is to use [continuous integration](#continuous-integration) to rebuild the manuscript when the content changes.
If you want to build a Manubot manuscript locally, install the [conda](https://conda.io) environment as described in [`build`](build).
Then, you can build the manuscript on POSIX systems by running the following commands from this root directory.

```sh
# Activate the manubot conda environment (assumes conda version >= 4.4)
conda activate manubot

# Build the manuscript, saving outputs to the output directory
bash build/build.sh

# At this point, the HTML & PDF outputs will have been created. The remaining
# commands are for serving the webpage to view the HTML manuscript locally.
# This is required to view local images in the HTML output.

# Configure the webpage directory
manubot webpage

# You can now open the manuscript webpage/index.html in a web browser.
# Alternatively, open a local webserver at http://localhost:8000/ with the
# following commands.
cd webpage
python -m http.server
```

Sometimes it's helpful to monitor the content directory and automatically rebuild the manuscript when a change is detected.
The following command, while running, will trigger both the `build.sh` script and `manubot webpage` command upon content changes:

```sh
bash build/autobuild.sh
```

### Continuous Integration

Whenever a pull request is opened, CI (continuous integration) will test whether the changes break the build process to generate a formatted manuscript.
The build process aims to detect common errors, such as invalid citations.
If your pull request build fails, see the CI logs for the cause of failure and revise your pull request accordingly.

When a commit to the `main` branch occurs (for example, when a pull request is merged), CI builds the manuscript and writes the results to the [`gh-pages`](https://github.com/manubot/rootstock/tree/gh-pages) and [`output`](https://github.com/manubot/rootstock/tree/output) branches.
The `gh-pages` branch uses [GitHub Pages](https://pages.github.com/) to host the following URLs:

+ **HTML manuscript** at https://manubot.github.io/rootstock/
+ **PDF manuscript** at https://manubot.github.io/rootstock/manuscript.pdf

For continuous integration configuration details, see [`.github/workflows/manubot.yaml`](.github/workflows/manubot.yaml) if using GitHub Actions or [`.travis.yml`](.travis.yml) if using Travis CI.

## License

<!--
usage note: edit this section to change the license of your manuscript or source code changes to this repository.
We encourage users to openly license their manuscripts, which is the default as specified below.
-->

[![License: CC BY 4.0](https://img.shields.io/badge/License%20All-CC%20BY%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by/4.0/)
[![License: CC0 1.0](https://img.shields.io/badge/License%20Parts-CC0%201.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

Except when noted otherwise, the entirety of this repository is licensed under a CC BY 4.0 License ([`LICENSE.md`](LICENSE.md)), which allows reuse with attribution.
Please attribute by linking to https://github.com/manubot/rootstock.

Since CC BY is not ideal for code and data, certain repository components are also released under the CC0 1.0 public domain dedication ([`LICENSE-CC0.md`](LICENSE-CC0.md)).
All files matched by the following glob patterns are dual licensed under CC BY 4.0 and CC0 1.0:

+ `*.sh`
+ `*.py`
+ `*.yml` / `*.yaml`
+ `*.json`
+ `*.bib`
+ `*.tsv`
+ `.gitignore`

All other files are only available under CC BY 4.0, including:

+ `*.md`
+ `*.html`
+ `*.pdf`
+ `*.docx`

Please open [an issue](https://github.com/manubot/rootstock/issues) for any question related to licensing.
