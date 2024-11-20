# DIEM Aggregated Data Export from API

## Overview

This project automates the download and export of aggregated data from the DIEM Monitoring System using the ArcGIS API for Python. 
It supports filtering based on specific conditions and exporting data in formats like CSV and File Geodatabase.

---

## Prerequisites
Install ArcGIS API for Python 
This project requires the ArcGIS API for Python, which is freely available. 
 
You can Install the library using `pip install arcgis`.

For more details, [Refer to the ArcGIS API for Python Documentation](https://developers.arcgis.com/python/latest/) 

Download Field descriptions and metadata
To understand the structure and content of the DIEM datasets, download the field description tables, metadata, and questionnaires from the [DIEM data access page](https://data-in-emergencies.fao.org/pages/data/), after logging in with your DIEM credentials. These resources provide necessary information about the available fields and their purposes. Make sure to refer to these descriptions when working with the data.

---

## Features

- Query and filter aggregated data based on ISO3 country codes and DIEM survey rounds.
- Export filtered data to various formats, including CSV, File Geodatabase, and others.
- Exclude unnecessary fields like geometry during export.
- Easy-to-configure user parameters.

---

## Prerequisites

Ensure you have the following installed:

- Python 3.6 or newer
- ArcGIS API for Python (`arcgis`)
- Jupyter Notebook

---

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/Andrampa/DIEM_API.git
   cd DIEM_API
. For more information, visit https://data-in-emergencies.fao.org/
