# DIEM Aggregated Data Export from API

## Overview

This project automates the download and export of aggregated data from the DIEM Monitoring System using the ArcGIS API for Python. 
It supports filtering based on specific conditions and exporting data in formats like CSV and File Geodatabase.

---

## Prerequisites
To programmatically download data from the DIEM Monitoring System, you must first [create a DIEM account](https://hqfao.maps.arcgis.com/sharing/rest/oauth2/signup?client_id=aEXLMtXxljlIrgPN&response_type=token&expiration=20160&showSocialLogins=true&locale=en-us&redirect_uri=https%3A%2F%2Fdata-in-emergencies.fao.org%2Ftorii-provider-arcgis%2Fhub-redirect.html). After creating your account, please allow a few minutes for the necessary privileges to be assigned before you can access the DIEM API.

Install ArcGIS API for Python 
This project requires the ArcGIS API for Python, which is freely available. 
 
You can Install the library using `pip install arcgis`.

For more details, [Refer to the ArcGIS API for Python Documentation](https://developers.arcgis.com/python/latest/) 

Download Field descriptions and metadata
To understand the structure and content of the DIEM datasets, download the [field description tables](https://data-in-emergencies.fao.org/documents/04287fcadb994341b0b70d19c8a02035/about), [metadata](https://ago-item-storage.s3.amazonaws.com/01595314154948719aca7325d88c782a/DIEM_aggregated_metadata.pdf?X-Amz-Security-Token=IQoJb3JpZ2luX2VjEPX%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJIMEYCIQDV%2Bl000msMM6U3npAh2f4vubEwqw0Bd9nnujNsdf4%2B3wIhALGwFXnKzhnKhcAu%2FtzD1nzfe694%2FvLmQAN5JQSmcKG9KrwFCI7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQABoMNjA0NzU4MTAyNjY1IgzFDmcd20Vzkjqf01cqkAXmSo9gAJe51ys%2BmIDUpKdNrw%2BTGxnIk1wQVxalBBLvYd0mTpRdfBLSAQyihWlSZd%2BMINjF1vHF%2B3Vhlsftx4Ucer4Bcm4myJrvugYndMjtdgixbuXc15gv3yJ5ERF6vhLz5OnmgynI0GqXzCqEdjfDneY8qlKLIWhsLBUIl%2FBKTXssrN9pE6FLZY%2B%2BtWCfcJaBdQdIKWmDsK2KIve74Llr%2BkE%2FA%2B1cJuoX5H4nAVttba35T7X0wo87iEmkDTSAMkT9M%2Fpfq8XMzOoNXp%2Bzg6d0mFjRGFjNKvIMlckgbi%2Bjg9H07c%2BfL8gSwYhFPEM4NLlrLrQBFEA1MmH0kP3k4NrafJ2bIOGVgclhv1bJBpnPf5dQPHAI6Mu6hbv0JN7HD2Oen9%2F2lLZMXIrOpVWQ%2B7O8Q9DFd4D6bcGnobi6jSC9ohudT1S27Qm2%2FgGwoZ5TmsgNpAVLLBfVsKdxmDdD3vm4vKZVcyUH7QwxNPyEIWr0vle2FwKhYidsVl7hVY3fA2t3LySvhk8i6rkQUzRy0iZeqyV1S9YbzFDL6KMEglqK65oXgeBXzaroWZafOdVWdQO1MIVSgvwaIAYWGxuFm21zpD%2Fvov1H%2FVdG7Wd2ek3meAzU%2F%2BIbNakzuaVIf8%2FySEjQdal8P5JGwwWQk%2Fzo5wyfm3f91rGpcyZp%2BmK7AJAhhul2fSpXYpTiKiaYI%2BSFck1%2BiV8MCZZD%2BDJz3JuIW%2Biq4z8y4QBDrVh4CIYfA2eG7fgTwTpCHkJoQz4gEsp8M81QGabqVeg3M1LmcmKtNwhSzAEqrm%2FzFmuuj5%2BC%2BWqlKJG9U76dOiFpn0vdxwc0frYM%2FwmTr260%2BVy29gwVphLW9dDLiTdJawNwVNygUXWB3jCJsPe5BjqwAQ6rI4%2F0w3iy2wFPviKD4EmCVGcLFZYAdX2dZ%2BP4WiRactxyEKwJ6GAQTzVnWrwBbhTs5naPy%2Bt9DKJN1gUlmnH28yYH5n61SIyrhA1qto%2FThWU4A3RFVTss03ovV0p29e2DwtyqjmEwLVjlfpsTLPpgVDhlTENH1IZe%2B5HKo0BQdIti%2FECfhusmTxj2eqehGB4O4Qy%2BJBvSODblunV3gzCpiMYAeJI%2FMZIuDX4qDvcM&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20241120T132023Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIAYZTTEKKEVO3CAXFB%2F20241120%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=aef2e2e05026eea9f2f042268104b1cd76693d87123b83ba012470faf68744f3), and [survey-specific questionnaires](https://data-in-emergencies.fao.org/search?tags=household%2520survey%2520questionnaire) from the [DIEM data access page](https://data-in-emergencies.fao.org/pages/data/), after logging in with your DIEM credentials. These resources provide necessary information about the available fields and their purposes. Make sure to refer to these descriptions when working with the data.

---

## Features

- Query and filter aggregated data based on ISO3 country codes and DIEM survey rounds.
- Export filtered data to various formats, including CSV, File Geodatabase, and others.
- Exclude unnecessary fields like geometry during export.
- Easy-to-configure user parameters.

---

## Prerequisites

First [create a DIEM account](https://hqfao.maps.arcgis.com/sharing/rest/oauth2/signup?client_id=aEXLMtXxljlIrgPN&response_type=token&expiration=20160&showSocialLogins=true&locale=en-us&redirect_uri=https%3A%2F%2Fdata-in-emergencies.fao.org%2Ftorii-provider-arcgis%2Fhub-redirect.html), if you don't have one yet.
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

## How to run the notebook

1. Ensure that you have a working python environment and the arcgis api for python installed.
2. Open a terminal or command prompt in the cloned repository's directory.
3. Start jupyter notebook:
   ```bash
   jupyter notebook
4. Update the `USERNAME` and `PASS` variables in the notebook with your diem credentials.  
5. Open a terminal or command prompt in the cloned repository's directory.
6. Run the notebook cells sequentially to execute the code and download or export the data.


## Assistance and technical support
If you experience any issues accessing DIEM data or with your DIEM account, please [reach out to the DIEM Hub](https://data-in-emergencies.fao.org/pages/contactus) team for technical support.
