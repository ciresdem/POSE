---
title: "CUDEM/IVERT: AGU Annual Meeting 2025"
---

🤗 Welcome to our CUDEM/IVERT AGU Presentation
[American Geophysical Union (AGU) 2025 Annual Meeting](https://www.agu.org/annual-meeting)!

# CUDEM+IVERT: An Open-Source Framework for Rapid Development and Validation of High-Accuracy Digital Elevation Models

- Session Number & Title: IN42D: Cross-Disciplinary Approaches to Science Data Systems Designs and Implementations II Oral
- Date & Time: Thursday, 18 December 2025, 10:30 – 12:00 CST
- Presentation Length: 11:45 – 12:00 CST
- Location: New Orleans Convention Center, 293

## Get Involved

- Fill out this [form](https://docs.google.com/forms/d/e/1FAIpQLScK46myKuESCu81U9zdKha8NXqHny86MZinutPvvTLoGAsDVQ/viewform)
- Join our [Zulip](https://cudem.zulipchat.com/)

## Abstract

For years, the Coastal Digital Elevation Team at the University of Colorado’s Cooperative Institute for Research in Environmental Sciences (CIRES) has developed cutting-edge software tools for creating and validating seamless topographic and bathymetric digital elevation models (DEMs). CUDEM+IVERT are used to develop nested DEMs in an updatable, systematic framework constructed from a wide range of public datasets; generate rigorous uncertainty estimates of those DEMs; and independently and automatically validate DEM accuracy against ICESAT-2 satellite lidar data. Users of these DEMs include scientific researchers, hazard modelers (tsunamis, storm surges, floods), infrastructure planners (state, local, and federal), and private industries (insurance, infrastructure, etc). The team works closely alongside the Natural Hazards group at the National Oceanic and Atmospheric Administration (NOAA) National Centers for Environmental Information (NCEI), providing critical digital infrastructure for coastal planning and disaster mitigation. In addition to academic research use, the CUDEM+IVERT packages support a wide use of applications within a modular and cross-disciplinary software workflow that support data acquisition, subsetting, filtering, and validating datasets.

The CUDEM+IVERT software is housed in two code repositories that work closely together: the Continuously Updated Digital Elevation Model (CUDEM) framework and the ICESat-2 Validation of Elevations Reporting Tool (IVERT). Both repositories have been open-source and publicly accessible since their inception and are used by partner organizations and agencies. Currently with new funding support, both software packages are transitioning to an open-source ecosystem (OSE) environment to engage broader users and developers to collaboratively enhance the suite of DEM tools. We invite all interested parties in the geoscience community (software users and developers) to join us in the transition of the CUDEM+IVERT software environments toward a community-based approach for future enhancements of these open-source software tools for DEM data assembly, generation, and validation.

## Code

### Links

- [CUDEM](https://github.com/ciresdem/cudem)
- [IVERT](https://github.com/ciresdem/ivert)

### Get Started

Interested in getting started building your first high-resolution DEM of New Orleans?

First, [install the CUDEM software](https://github.com/ciresdem/cudem?tab=readme-ov-file#installation-and-setup).
 
Then download this datalist text file [CRM.datalist](/data/CRM.datalist) and put it in a working directory. Open it up and take a look, it tells CUDEM to get data from these various sources, weights the datasets in order of priority, and transforms all the data to a common horizontal and vertical datum in preparation of building it into a DEM (you can run "fetches --modules" to see all supported CUDEM dataset modules, this is just a few!).

Next, run this "waffles" command (running ‘waffles —help’ will give a brief explainer of what all these command-line options do) and it'll automatically download the datasets needed from that datalist of the New Orleans area, and from that data will generate a brand-new DEM at 1/9-arc-second (~3 m) resolution.

```bash
waffles -R-90.1/-90/29.9/30 -E.111111111s -Pepsg:4269+5703 -Amixed -Onola -Mcudem -w -m CRM.datalist
```

This will output a DEM file named 'nola.tif'. All the downloaded data will be retained in their respective directories and will be re-used in subsequent iterations of DEM generation.

If you want to visualize that DEM, use CUDEM's "perspecto" hillshade module to create a color-coded hillshade (as with our other cli tools "perspecto --help" will give a brief description of its options):

```bash
perspecto -Mhillshade nola.tif
```

![](/media/nola_hillshade.png)
 
If you'd like to learn more, check out more in-depth CUDEM Github tutorials and the various modules available.

Feel free to ask questions in our [Zulip chat space](https://cudem.zulipchat.com/)! And/or, fill out this [Google form](https://docs.google.com/forms/d/e/1FAIpQLScK46myKuESCu81U9zdKha8NXqHny86MZinutPvvTLoGAsDVQ/viewform) so the DEM team can get in touch with you.
