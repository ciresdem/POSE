---
title: "CUDEM/IVERT: POSE Phase I"
---

<link rel="stylesheet" href="style.css" />

# CUDEM+IVERT

🤗 Welcome to our CUDEM/IVERT POSE Project

> An Open-Source Framework for Rapid Development and Validation of High-Accuracy Digital Elevation Models

## Highlights
<img src="/POSE/media/etopo22_northAmerica_t.png" alt="ETOPO22" width="40%" align="right" style="margin-left: 10px;" />

* Funded by the National Science Foundation, this project aims to scope and plan a sustainable Open-Source Ecosystem (OSE) around the CUDEM and IVERT software packages.
* The project focuses on drafting a long-term governance framework, expanding documentation, and establishing best practices to support a growing community of users and contributors.
* The team is actively hosting community workshops, virtual meetings, and student training sessions to gather feedback and democratize access to high-accuracy coastal elevation modeling tools.
* By hardening these tools for wider public use, the project directly supports disaster prevention, infrastructure planning, and climate resilience efforts across public and private sectors.
* Our software includes **CUDEM**, a suite of tools for fetching public data, processing point clouds and rasters, gridding via various interpolation algorithms, and transforming datums.
* Out companion software **IVERT** porvides a command-line tool that rapidly validates raster DEMs against NASA’s ICESat-2 photon data by applying smart masking to exclude unreliable areas (e.g., water, buildings), performing automatic datum transformations, and generating detailed statistical reports and error maps.

## Links

- [CUDEM](https://github.com/ciresdem/cudem) - FOSS DEM generation suite.
- [IVERT](https://github.com/ciresdem/ivert) - Validation of DEMs using IceSat2.
- [Zulip Channel](https://cudem.zulipchat.com/) - Join our Zulip Channel to connect and engage with us.

## Get Started

Interested in getting started building your first high-resolution DEM? Here is an example for New Orleans:

First, [install the CUDEM software](https://github.com/ciresdem/cudem?tab=readme-ov-file#installation-and-setup).
 
Then download this datalist text file [CRM.datalist](/data/CRM.datalist) and put it in a working directory. Open it up and take a look, it tells CUDEM to get data from these various sources, weights the datasets in order of priority, and transforms all the data to a common horizontal and vertical datum in preparation of building it into a DEM (you can run `fetches --modules` to see all supported CUDEM dataset modules, this is just a few!).

Next, run this `waffles` command (running `waffles —help` will give a brief explainer of what all these command-line options do) and it'll automatically download the datasets needed from that datalist of the New Orleans area, and from that data will generate a brand-new DEM at 1/9-arc-second (~3 m) resolution.

```bash
waffles -Rloc:"new orleans" -E.1s -Pepsg:4269+5703 -Amixed -Onola -Mcudem -w -m CRM.datalist
```

This will output a DEM file named 'nola.tif'. All the downloaded data will be retained in their respective directories and will be re-used in subsequent iterations of DEM generation.

If you want to visualize that DEM, use CUDEM's `perspecto` hillshade module to create a color-coded hillshade (as with our other cli tools `perspecto --help` will give a brief description of its options):

```bash
perspecto nola.tif
```

<img src="/POSE/media/nola_hillshade.png" alt="NOLA Hillshade" width="50%" />

If you'd like to learn more, check out more in-depth CUDEM Github tutorials [1](https://github.com/ciresdem/cudem/blob/main/docs/example_crm_malibu.md) [2](https://github.com/ciresdem/cudem/blob/main/docs/example_crm_norcal.md)  and the various [modules](https://github.com/ciresdem/cudem/blob/main/README.md#modules) available.

Feel free to ask questions in our [**Zulip chat space**](https://cudem.zulipchat.com/)! And/or, fill out this [**Google form**](https://docs.google.com/forms/d/e/1FAIpQLScK46myKuESCu81U9zdKha8NXqHny86MZinutPvvTLoGAsDVQ/viewform) so the DEM team can get in touch with you.
