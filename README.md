# Tableau Workbook Field Analyzer

A Python tool for analyzing and extracting field information from Tableau workbooks (.twb/.twbx files) and generating Excel reports.

## Overview

This tool automates the process of:
1. Processing both packaged (.twbx) and unpackaged (.twb) Tableau workbooks
2. Extracting field metadata including names, roles, data types, and calculations
3. Generating formatted Excel reports with the extracted information

## Project Structure

```
├── main.py          # Main execution script
├── tableau.py       # Tableau workbook processing functions
├── excel.py         # Excel file handling utilities
└── file.py         # File system operations
```

## Requirements

- Python 3.x
- pandas
- openpyxl
- xml.etree.ElementTree (built-in)

## Installation

1. Clone this repository
2. Install required dependencies:
```bash
pip install pandas openpyxl
```

## Usage

1. Create a directory named "Packaged" and place your Tableau workbooks (.twb/.twbx) inside it
2. Run the main script:
```bash
python main.py
```

The script will:
- Create "Unpackaged" and "Fields" directories
- Process all workbooks in the "Packaged" directory
- Generate Excel reports containing field information

## Generated Excel Reports

The tool creates Excel files with the following information for each datasource:
- Field names
- Hidden status
- Field roles
- Data types
- Calculations
- Source workbook name

Excel files are automatically formatted with:
- Color-coded sheet tabs
- Optimized column widths
- Text wrapping for calculation fields
- Organized sheet structure

## Functions Overview

### main.py
- Orchestrates the overall execution flow
- Handles directory creation and file processing

### tableau.py
- `get_datasources()`: Extracts datasource information from workbooks
- `extract_fields()`: Parses field metadata from datasources
- `process_workbooks()`: Coordinates workbook processing and report generation

### excel.py
- `to_df()`: Converts field data to pandas DataFrames
- `to_excel()`: Saves DataFrames to Excel files
- `summarize_excel()`: Combines multiple Excel files
- `colorize_and_format()`: Applies formatting to Excel reports

### file.py
- `create_directory()`: Creates new directories
- `list_files()`: Enumerates files with specific extensions
- `list_tab_files()`: Finds Tableau files in directories
- `unzip_packages()`: Extracts packaged workbooks
- `copy_unpackaged()`: Handles unpackaged workbook files

## Error Handling

The tool includes comprehensive error handling for:
- Directory operations
- File processing
- XML parsing
- Excel file operations

Each function includes try-except blocks to gracefully handle potential errors and provide meaningful feedback.

## Limitations

- Excel sheet names are truncated to 25 characters due to Excel limitations
- Requires proper file permissions for directory creation and file operations
- Assumes standard Tableau workbook XML structure

## Contributing

Feel free to submit issues, fork the repository, and create pull requests for any improvements.

## License

MIT License
(c) 2023 Dave Rintoul
