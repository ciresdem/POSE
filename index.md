---
title: "CUDEM/IVERT: POSE Phase I"
---

🤗 Welcome to our CUDEM/IVERT POSE Project

# CUDEM+IVERT: An Open-Source Framework for Rapid Development and Validation of High-Accuracy Digital Elevation Models

![](/media/nola_hillshade.png)

## Code

### Links

- [CUDEM](https://github.com/ciresdem/cudem) - FOSS DEM generation suite.
- [IVERT](https://github.com/ciresdem/ivert) - Validation of DEMs using IceSat2.

### Get Started

Interested in getting started building your first high-resolution DEM? Here is an example for New Orleans:

First, [install the CUDEM software](https://github.com/ciresdem/cudem?tab=readme-ov-file#installation-and-setup).
 
Then download this datalist text file [CRM.datalist](/data/CRM.datalist) and put it in a working directory. Open it up and take a look, it tells CUDEM to get data from these various sources, weights the datasets in order of priority, and transforms all the data to a common horizontal and vertical datum in preparation of building it into a DEM (you can run "fetches --modules" to see all supported CUDEM dataset modules, this is just a few!).

Next, run this "waffles" command (running ‘waffles —help’ will give a brief explainer of what all these command-line options do) and it'll automatically download the datasets needed from that datalist of the New Orleans area, and from that data will generate a brand-new DEM at 1/9-arc-second (~3 m) resolution.

```bash
waffles -Rloc:"new orleans" -E1s -Pepsg:4269+5703 -Amixed -Onola -Mcudem -w -m CRM.datalist
```

This will output a DEM file named 'nola.tif'. All the downloaded data will be retained in their respective directories and will be re-used in subsequent iterations of DEM generation.

If you want to visualize that DEM, use CUDEM's "perspecto" hillshade module to create a color-coded hillshade (as with our other cli tools "perspecto --help" will give a brief description of its options):

```bash
perspecto nola.tif
```
 
If you'd like to learn more, check out more in-depth CUDEM Github tutorials and the various modules available.

Feel free to ask questions in our [Zulip chat space](https://cudem.zulipchat.com/)! And/or, fill out this [Google form](https://docs.google.com/forms/d/e/1FAIpQLScK46myKuESCu81U9zdKha8NXqHny86MZinutPvvTLoGAsDVQ/viewform) so the DEM team can get in touch with you.
