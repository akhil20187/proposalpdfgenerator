# Invest4Edu PDF Report Generator

This project generates professional PDF reports for Invest4Edu based on JSON data input. The system produces dynamic PDF reports that match the Invest4Edu design.

## Features

- Dynamic PDF generation from JSON data
- Customizable HTML templates with Jinja2
- Professional styling with CSS
- Command-line interface for easy usage
- Support for multiple report types
- Fallback to browser-based PDF generation if WeasyPrint is not available

## Installation

1. Install the required dependencies:

```bash
pip install -r requirements.txt
```

2. For WeasyPrint functionality (optional):
   - Install WeasyPrint: `pip install weasyprint==60.1`
   - Install system dependencies for WeasyPrint (see [WeasyPrint's documentation](https://doc.courtbouillon.org/weasyprint/stable/first_steps.html#installation))

## Usage

### Recommended Method

Use the simplified report generator for the most reliable results:

```bash
python simple_report_generator.py --data sample_data.json
```

This will generate an HTML report and open it in your browser, where you can print it to PDF.

### Complete PDF Generator

For a more comprehensive solution that attempts to use WeasyPrint if available:

```bash
python complete_pdf_generator.py --data sample_data.json --output my_report
```

This will try to generate both HTML and PDF files. If WeasyPrint is not available or encounters issues, it will fall back to browser-based PDF generation.

### Command Line Options

All generator scripts support these options:

- `--data`, `-d`: Path to the JSON data file (default: sample_data.json)
- `--template`, `-t`: Name of the HTML template file (default: simple_report.html)
- `--output`, `-o`: Base name for output files (default: output_report)
- `--no-open`: Do not open the generated HTML in browser

## JSON Data Structure

The JSON data should follow this structure:

```json
{
  "report_title": "Investment Report",
  "investment_products": {
    "target": "1.00Cr",
    "mutual_fund": {
      "points": ["Point 1", "Point 2", ...],
      "top_funds": [
        {
          "name": "Fund Name",
          "category": "Category",
          "returns": {
            "one_year": 8.00,
            "three_years": 8.00,
            "five_years": 8.00
          }
        }
      ]
    }
  },
  "asset_allocation": {
    "description": "Description text",
    "benefits": ["Benefit 1", "Benefit 2", ...],
    "distribution": {
      "equity": 70,
      "debt": 30
    },
    "items": [
      {
        "name": "Item name",
        "details": ["Detail 1", "Detail 2", ...],
        "asset_class": "Asset class",
        "amount": "Amount"
      }
    ],
    "total": "Total amount"
  }
}
```

See `sample_data.json` for a complete example.

## Creating Custom Reports

To create custom reports:

1. Create a new HTML template in the `templates` directory
2. Prepare your JSON data file with the appropriate structure
3. Run the generator with your custom template and data

## Project Files

- `simple_report_generator.py`: Simplified HTML report generator (recommended)
- `complete_pdf_generator.py`: Comprehensive solution with WeasyPrint support
- `generate_pdf.py`: Alternative PDF generator
- `templates/simple_report.html`: Simplified HTML template
- `templates/invest4edu_report.html`: Original HTML template with inline CSS
- `sample_data.json`: Example data structure

## Browser-based PDF Generation

If WeasyPrint is not available or encounters issues, follow these steps to generate a PDF:

1. The HTML report will open in your default browser
2. Press Ctrl+P to open the print dialog
3. Select 'Save as PDF' as the destination
4. Click 'Save' to generate the PDF

This method works reliably across all platforms and produces high-quality PDFs.
