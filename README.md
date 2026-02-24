# Dataset Information

This repository contains analysis code for San Francisco Police Department Incident Reports.

## Data Files

Due to file size limitations, the following large CSV files are not stored in this Git repository:

- `Police_Department_Incident_Reports__2018_to_Present_20260210.csv` (421MB)
- `Police_Department_Incident_Reports__Historical_2003_to_May_2018_20260210.csv` (506MB)

## Data Access

You can access the data files through one of these methods:

### Option 1: Cloud Storage
Upload the CSV files to:
- Google Drive
- Dropbox
- OneDrive
- AWS S3
- Google Cloud Storage

Then share the download links here.

### Option 2: Data Source
These files appear to be from the San Francisco Open Data portal. You can download them directly from:
- [SF Open Data - Police Department Incident Reports](https://data.sfgov.org/)

### Option 3: Script to Download Data
Create a script that automatically downloads the data when needed:

```python
# download_data.py
import requests
import os

def download_data():
    # Add URLs for the datasets
    urls = {
        'current': 'https://data.sfgov.org/api/views/wg3w-h783/rows.csv?accessType=DOWNLOAD',
        'historical': 'https://data.sfgov.org/api/views/tmnf-yvry/rows.csv?accessType=DOWNLOAD'
    }
    
    for name, url in urls.items():
        filename = f'police_incidents_{name}.csv'
        if not os.path.exists(filename):
            print(f"Downloading {filename}...")
            response = requests.get(url)
            with open(filename, 'wb') as f:
                f.write(response.content)
            print(f"Downloaded {filename}")
        else:
            print(f"{filename} already exists")

if __name__ == "__main__":
    download_data()
```

## Usage

1. Run the data download script (if using Option 3)
2. Open and run `Assignment1.ipynb`