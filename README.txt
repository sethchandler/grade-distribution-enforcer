# Grade Distribution Generator - User Guide

## Overview
This is a pure client-side JavaScript application that generates grade distributions for faculty members. All processing happens in your web browser - no data is sent to any server.

## How to Use

### Step 1: Open the Tool
1. Download the `grade_distribution_tool.html` file
2. Double-click the file to open it in your web browser (Chrome, Firefox, Safari, or Edge)
3. No installation required!

### Step 2: Prepare Your Data
Your input file (Excel or CSV) must have exactly **two columns**:

**Column 1: Student ID** (can be text or numbers)
- Examples: "STU001", "12345", "John Doe"

**Column 2: Raw Score** (must be numbers)
- Examples: 85, 92.5, 78

**Important:**
- Include a header row (e.g., "student_id", "raw_score")
- The tool will automatically use the first two columns
- Sample files are provided: `sample_data.csv` and `sample_data.xlsx`

### Step 3: Upload Your File
1. Click "Choose File" 
2. Select your Excel (.xlsx) or CSV (.csv) file
3. The tool will validate and display the number of students loaded

### Step 4: Configure Parameters
- **Desired Mean Grade**: Enter a value between 3.2 and 3.4 (default: 3.3)
  - 3.2 = stricter grading
  - 3.4 = more lenient grading
  
- **Number of Distributions**: Choose how many different grade distributions to generate (1-10)
  - More distributions give you more options to choose from

- **Output Format**: Choose Excel or CSV for the output file

### Step 5: Generate Distributions
1. Click "Generate Grade Distributions"
2. The tool will create multiple valid distributions that satisfy all constraints
3. Review the results displayed on screen

### Step 6: Download Results
1. Click "Download Results" 
2. Your file will be downloaded with all distributions included
3. Each distribution appears in a separate column (grade_1, grade_2, grade_3, etc.)

## Output Format

The output file contains:
- **student_id**: Original student identifier
- **raw_score**: Original raw score
- **grade_1, grade_2, ..., grade_n**: The generated grade distributions

Grades are displayed as decimal numbers (e.g., 3.330, 4.000) to three decimal places.

## Grading Constraints

All generated distributions satisfy these requirements:
- ✓ 5-30% of students receive A (4.0)
- ✓ 50-90% of students receive A-, B+, or B (3.67, 3.33, 3.0)
- ✓ 5-20% of students receive B- or lower (≤2.67)
- ✓ Mean grade between 3.2 and 3.4
- ✓ Students with identical raw scores receive identical grades
- ✓ Higher raw scores receive higher or equal grades (monotonicity)

## Understanding the Results

Each distribution shows:
- **Mean**: Actual mean grade (closer to your target is better)
- **Deviation**: How far from your target mean
- **Min Gap**: Minimum score difference between grade boundaries (larger is better)
- **Percentages**: Distribution across grade categories with ✓ or ✗ indicators

Distributions are ranked by:
1. **Primary**: Closeness to desired mean (weighted 80%)
2. **Secondary**: Maximum gap between grade boundaries (weighted 20%)

## Grade Scale

The tool uses the following grade scale:
- 4.00 = A
- 3.67 = A-
- 3.33 = B+
- 3.00 = B
- 2.67 = B-
- 2.33 = C+
- 2.00 = C
- (and lower grades if needed)

## Privacy & Security

- **100% Client-Side**: All processing happens in your browser
- **No Server**: Your data never leaves your computer
- **No Storage**: Data is not saved or tracked
- **Offline Capable**: Works without internet (after initial load)

## Troubleshooting

**"Error: File must have at least 2 columns"**
- Check that your file has at least two columns
- Make sure there's a header row

**"Error: No valid data found"**
- Ensure column 2 contains numbers only
- Check for empty cells in the score column

**"Could not find any valid distributions"**
- Try adjusting the desired mean slightly
- Check that you have enough students (at least 20 recommended)
- Verify raw scores have reasonable spread

**Browser Compatibility**
- Works best in: Chrome, Firefox, Safari, Edge (latest versions)
- If having issues, try a different browser

## Technical Details

The algorithm:
1. Groups students by unique raw scores (ties handled correctly)
2. Generates multiple candidate grade assignments using different strategies
3. Validates each candidate against all constraints
4. Ranks valid solutions by composite score
5. Returns the top N unique distributions

## Contact & Support

For questions or issues with the tool, please contact your IT department or the developer who provided this tool.

## Sample Data Included

Two sample files are provided for testing:
- `sample_data.csv` - 50 students in CSV format
- `sample_data.xlsx` - 50 students in Excel format

Try these files first to familiarize yourself with the tool before using your own data.
