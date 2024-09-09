# msdial2cytoscape for lipidomics

<!-- badges: start -->
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)


<!-- badges: end -->

## Overview

This Shiny application is designed to facilitate the analysis of non-targeted lipidomics data. It allows users to easily upload alignment result tables generated by MS-DIAL and, optionally, integrate sample class information for further data exploration. The application provides interactive data visualizations, enabling users to inspect lipid species distributions, compare sample groups, and generate pathway analysis diagrams.

Key features include:

- Simple file upload interface for MS-DIAL alignment results
- Integration of sample metadata for enhanced analysis
- Interactive visualizations for exploring lipid species across samples
- Customizable generation of pathway analysis diagrams with Cytoscape desktop app



## Run msdial2cytoscape for lipidomics locally

### Step 1: Clone this repository

Open the terminal and run:

``` bash
git clone "https://github.com/systemsomicslab/msdial2cytoscape-for-lipidomics.git"
```

### Step 2: Bulid Docker image

``` bash
docker build -t msdial2cytoscape-for-lipidomics .
```

### Step 3: Run Docker image

Run the container on your terminal once it has been bulied.

``` bash
docker run --rm -p 1028:1028 -p 9000:9000 msdial2cytoscape-for-lipidomics
```

### Step 4: Run msdial2cytoscape for lipidomics in your browser

Open your browser and paste `http://localhost:1028`. 

## Code of Conduct



