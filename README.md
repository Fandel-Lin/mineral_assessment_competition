# DARPA Critical Mineral Assessment Competition / Map Feature Extraction Challenge - Polygon Extraction

This repo provides the code for `isi-umn` team in the DARPA Mineral Competition.

## Overview
The polygon extraction consists of four components: 1) target-area cropping; 2) color-based extraction; 3) text-template matching; 4) color-shift amendment. The target-area cropping first identifies the map area and sets a mask for it irrespective of the shape. We then apply the color-based rules to extract the pixels with their color falling under the targeted legend. Meanwhile, we adopt template matching to rule out extracted polygons that are labeled with different names but under similar colors. Finally, for color-shift maps, the fourth component aims to re-color the map based on the available legends with mismatched colors.

1. <b>Target-area cropping</b>: Find the largest connected component that holds enough color diversity.
2. <b>Color-based extraction</b>: Extract pixels with color falling under the targeted legend, and backfill the gaps to form complete polygons.
3. <b>Text-template matching</b>: Identify legend names located in or nearby the extracted polygon, and rule out areas labeled with competitive legends.
4. <b>Color-shift amendment</b>: Detect mismatch between map and legends, and re-color the map with decayed colors from the legends if needed.

## Environment Setting
Due to the large amount of polygon features, the script automatically enables multiprocessing; one can turn off the setting.
The script was run with Amazon AWS instance r6id.24xlarge for the validation.
