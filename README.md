<!--
***
*** To avoid retyping too much info. Do a search and replace for the following:
*** template-svce, twitter_handle, email
-->

<!-- PROJECT SHIELDS -->
<!--
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
![Build][build-shield]

<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/EOEPCA/rm-resource-catalogue">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">EOEPCA Resource Catalogue</h3>

  <p align="center">
    This repository includes the documentation of the EOEPCA Resource Catalogue
    <br />
    <a href="https://github.com/EOEPCA/rm-resource-catalogue/tree/readme#documentation"><strong>Explore the docs »</strong></a>
    <br />
    <a href="https://resource-catalogue.demo.eoepca.org/">View Demo</a>
    ·
    <a href="https://github.com/EOEPCA/rm-resource-catalogue/issues">Report Bug</a>
    ·
    <a href="https://github.com/EOEPCA/rm-resource-catalogue/issues">Request Feature</a>
  </p>
</p>

<!-- TABLE OF CONTENTS -->

## Table of Contents

- [Description](#description)
  - [Built With](#built-with)
  - [Interfaces](#interfaces)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Testing](#testing)
- [Documentation](#documentation)
- [Usage](#usage)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [Acknowledgements](#acknowledgements)

<!-- ABOUT THE PROJECT -->

## Description

The EOEPCA Resource Catalogue building block is built upon the upstream pycsw project.

pycsw is an OGC API - Records and OGC CSW server implementation written in Python. 

Started in 2010 (more formally announced in 2011), pycsw allows for the publishing and discovery of geospatial metadata via numerous APIs (CSW 2/CSW 3, OGC API - Records, STAC API, OpenSearch, OAI-PMH, SRU), providing a standards-based metadata and catalogue component of spatial data infrastructures. 

pycsw is Open Source, released under an MIT license, and runs on all major platforms (Windows, Linux, Mac OS X). It is an official [OSGeo Project](https://www.osgeo.org/projects/pycsw/).

pycsw is [Certified OGC Compliant](https://www.ogc.org/resources/product-details/?pid=1661) and is an [OGC Reference Implementation](https://demo.pycsw.org/)

[![Resource Catalogue Architecture][architecture]](https://resource-catalogue.demo.eoepca.org/)


### Built With

- [Python](https://www.python.org/)
- [pycsw](https://pycsw.org/)

### Interfaces

The Resource Catalogue provides the following interfaces:
* OGC CSW 2.0.2 ([OGC Reference Implementation](https://www.ogc.org/resources/product-details/?pid=1661))
* OGC CSW 3.0.0 ([OGC Reference Implementation](https://www.ogc.org/resources/product-details/?pid=1661))
* OGC API - Records - Part1:Core ([Early Implementation](https://github.com/opengeospatial/ogcapi-records/blob/master/implementations.md#pycsw))
* STAC API 1.0.0 ([Listed in STAC API Servers](https://stacspec.org/en/about/tools-resources/))
* OpenSearch with OGC EO, Geo and Time extensions

[![Resource Catalogue Landing Page Screen Shot][screenshot]](https://resource-catalogue.demo.eoepca.org/)

The Resource Catalogue data model is based on ISO 19115-1/2

Metadata registration can be done by the following ways:
* Transaction interfaces (OGC CSW-T or OGC API - Features - Part4: Create, Replace, Update, Delete)
* Data Access Registrar
* Data Access Harvester
* Workspace API
* Registration API
* pycsw Python API
* pycsw admin CLI utility

<!-- GETTING STARTED -->

## Getting Started

To get a local copy up and running in 4 minutes follow these simple steps.

    # Setup a virtual environment:
    python3 -m venv pycsw && cd pycsw && . bin/activate
        
    # Grab the pycsw source code:
    git clone https://github.com/geopython/pycsw.git && cd pycsw
    pip3 install -e . && pip3 install -r requirements-standalone.txt
        
    # Create and adjust a configuration file:
    cp default-sample.cfg default.cfg
    vi default.cfg
    # adjust paths in
    # - server.home
    # - repository.database
    # set server.url to http://localhost:8000/
        
    # Setup the database:
    pycsw-admin.py setup_db --config default.cfg
        
    # Load records by indicating a directory of XML files, use -r for recursive:
    pycsw-admin.py load_records --config default.cfg --path /path/to/xml/
        
    # Run the server:
    python ./pycsw/wsgi.py
        
    # See that it works!
    curl http://localhost:8000  # OGC API - Records      
    curl http://localhost:8000/csw?service=CSW&version=2.0.2&request=GetCapabilities  # CSW


### Deployment

Resource Catalogue deployment is described [here](https://deployment-guide.docs.eoepca.org/current/eoepca/resource-catalogue/) in the [EOEPCA Deployment Guide](https://deployment-guide.docs.eoepca.org/current/eoepca/resource-catalogue/).


## Documentation

The component documentation can be found at https://docs.pycsw.org/en/latest/.

EOEPCA related documents:
* [Resource Catalogue Interface Control Document](https://eoepca.github.io/rm-resource-catalogue/ICD/)
* [Resource Catalogue Software Design Document](https://eoepca.github.io/rm-resource-catalogue/SDD/)

<!-- USAGE EXAMPLES -->

## Usage

Resource Catalogue usage documentation is provided through the upstream pycsw project.

* [pycsw Home Page](https://pycsw.org/)
* [pycsw Documenation](https://docs.pycsw.org/en/latest/)

A basic example of the Resource Catalogue usage:

Using the landing page, the user can browse [collections](https://resource-catalogue.demo.eoepca.org/collections) and metadata [records](https://resource-catalogue.demo.eoepca.org/collections/metadata:main/items) through the HTML interface (provided by OGC API - Records)

[![Resource Catalogue Items Page][screenshot1]](https://resource-catalogue.demo.eoepca.org/collections/metadata:main/items)

The user can find a catalogue record and browse the [metadata](https://resource-catalogue.demo.eoepca.org/collections/metadata:main/items/S2A_MSIL1C_20190920T104021_N0208_R008_T31UFQ_20190920T111121.SAFE)

[![Resource Catalogue Item Page][screenshot2]](https://resource-catalogue.demo.eoepca.org/collections/metadata:main/items/S2A_MSIL1C_20190920T104021_N0208_R008_T31UFQ_20190920T111121.SAFE)

Alternatively the user can browse through the [JSON interface](https://resource-catalogue.demo.eoepca.org/collections/metadata:main/items?f=json)

[![Resource Catalogue JSON Record][screenshot3]](https://resource-catalogue.demo.eoepca.org/collections/metadata:main/items/S2A_MSIL1C_20190920T104021_N0208_R008_T31UFQ_20190920T111121.SAFE?f=json)

<!-- ROADMAP -->

## Roadmap

See the [open issues](https://github.com/geopython/pycsw/issues) for a list of proposed features (and known issues).

<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<!-- LICENSE -->

## License

The EOEPCA components are distributed under the Apache-2.0 License. See `LICENSE` for more information.

<!-- CONTACT -->

## Contact

Angelos Tzotsos - [@tzotsos](https://twitter.com/tzotsos) - https://www.osgeo.org/member/angelos-tzotsos/

Project Link: [https://github.com/EOEPCA/rm-resource-catalogue](https://github.com/EOEPCA/rm-resource-catalogue)

<!-- ACKNOWLEDGEMENTS -->

## Acknowledgements

- README.md is based on [this template](https://github.com/othneildrew/Best-README-Template) by [Othneil Drew](https://github.com/othneildrew).

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/EOEPCA/rm-resource-catalogue.svg?style=flat-square
[contributors-url]: https://github.com/EOEPCA/rm-resource-catalogue/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/EOEPCA/rm-resource-catalogue.svg?style=flat-square
[forks-url]: https://github.com/EOEPCA/rm-resource-catalogue/network/members
[stars-shield]: https://img.shields.io/github/stars/EOEPCA/rm-resource-catalogue.svg?style=flat-square
[stars-url]: https://github.com/EOEPCA/rm-resource-catalogue/stargazers
[issues-shield]: https://img.shields.io/github/issues/EOEPCA/rm-resource-catalogue.svg?style=flat-square
[issues-url]: https://github.com/EOEPCA/rm-resource-catalogue/issues
[license-shield]: https://img.shields.io/github/license/EOEPCA/rm-resource-catalogue.svg?style=flat-square
[license-url]: https://github.com/EOEPCA/rm-resource-catalogue/blob/master/LICENSE
[build-shield]: https://www.travis-ci.com/EOEPCA/rm-resource-catalogue.svg?branch=master
[architecture]: images/resource_catalogue.png
[screenshot]: images/screenshot.png
[screenshot1]: images/screenshot1.png
[screenshot2]: images/screenshot2.png
[screenshot3]: images/screenshot3.png
