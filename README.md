# msdial2cytoscape4lipidomics

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



## Run msdial2cytoscape4lipidomics locally

### Step 1: Clone this repository

Open the terminal and run:

``` bash
git clone "https://github.com/systemsomicslab/msdial2cytoscape-for-lipidomics.git"
```

### Step 2: Bulid Docker image

``` bash
docker build -t msdial2cytoscape4lipidomics .
```

### Step 3: Run Docker image

Run the container on your terminal once it has been bulied.

``` bash
docker run --rm -p 1028:1028 -p 9000:9000 msdial2cytoscape4lipidomics
```

### Step 4: Run msdial2cytoscape for lipidomics in your browser

Open your browser and paste `http://localhost:1028`. 

## Prepare input files
msdial2cytoscape4lipidomics does not accept raw data input. It is highly recommended to use the alignment table processed by MS-DIAL5. This application utilizes the alignment table from MS-DIAL to visualize lipidomics data in Cytoscape.

Additionally, we support a data frame format where lipid molecules are arranged in columns, and sample IDs are placed in rows. In this format, the second row must contain metadata about the samples. 

Furthermore, you need to prepare a CSV file that maps lipid molecules to their respective lipid classes. This file should have lipid names in the first column and their corresponding lipid classes in the second column. 

The file format must be CSV.

Examples of supported data formats can be found in the inst/examples folder.

### Metadata file
In msdial2cytoscape4lipidomics, you can provide sample metadata separately using a CSV file. This metadata file offers detailed information about each sample, which is essential for visualization and analysis in Cytoscape.

Please ensure that the metadata file follows these guidelines:

- Sample IDs must be listed in rows, and they should match those in the alignment table or data frame.
- Sample attributes (e.g., group, treatment condition, time points) should be listed in columns.
- The file format must be CSV.
Using a metadata file allows you to incorporate additional information about each sample, enabling more comprehensive analysis in Cytoscape. Examples of the metadata file format can be found in the inst/examples folder.

## Load data files
![Data upload](inst/www/DataUpload.png?raw=true "Data upload")
1. Select the data file format.
2. Load your data files.
3. (optional) You can also upload metadata files and transcriptome data if needed.
4. Enter a unique project name.
5. Click the "Submit" button to metabolite data and metadata, converting them into a format suitable for analysis.
Once step 4 is completed and , navigate to the Plot Data tab to continue.

## Data Plot
![Data plot](inst/www/DataPlot.png?raw=true "Data plot")
The Plot Data tab consists of two main sections: the Data Plot Panel and the Side Bar.

The Data Plot Panel displays a plot showing the average values for each lipid class and another plot showing the values of lipid molecules belonging to the selected lipid class.
 
The Side Bar provides functions for variable selection, adjusting plot aesthetics, changing the order of the x-axis, modifying the colors of sample classes, and generating figures for pathway analysis. 

## Generating Figures for Pathway Analysis
![Plot dialog](inst/www/PlotDialog.png?raw=true "Plot dialog")
In the Plot tab, you can view the figures used for pathway analysis by clicking the Mapping Option button located at the bottom of the sidebar. Once the dialog appears, you can proceed to pathway analysis by pressing the Pathway mapping button.

## Pathway Analysis
![Patheay analysis](inst/www/PathwayAnalysis.png?raw=true "Pathway analysis")
The Pathway analysis tab consists of two main sections: the Pathway Analysis Panel and the Plot Panel for the selected lipid class. 
First, select the metabolic pathway you want to display from the sidebar on the left, and press the Pathway Analysis button. This will project the selected pathway onto the Pathway Analysis Panel.

You can select lipid class nodes on the metabolic pathway and press the blue button on the Plot Panel to display a detailed plot for the lipid class. The plot will show the values of lipid molecules belonging to the selected lipid class, and a heatmap at the bottom will display the z-scores of those lipid molecules.

Additionally, you can switch the plot tab to the Correlation Analysis Plot Tab and select two nodes on the metabolic pathway by holding Ctrl to display a correlation plot between them.

## Creating Pathway Analysis Figures
From the left sidebar of the Pathway Analysis tab, you can export .cyjs files and style.yaml files for use in the Cytoscape desktop app. Using Cytoscape desktop app, you can load these files to edit the pathway analysis results and create figures in SVG or PDF format.
