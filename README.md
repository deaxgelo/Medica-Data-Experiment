# Blood Test Analysis

## Overview

This C# Windows Forms application analyzes fake blood test results from patients with Hepatitis and cross-references them with hospital medical records to determine correlations between blood markers and patient outcomes (lived or died). The goal is to identify patterns that may help inform future diagnoses or prognosis from 2 external datasets XML and Linq.

The program performs statistical analysis (mean and standard deviation) on four key blood test values—**Bilirubin**, **Alk Phosphate**, **SGOT**, and **Albumin**—and separates results based on whether the patient survived or not.

---

## What It Does When Run

1. Reads **blood test data** from two sources: a plain text file (`BloodTests.txt`) and an XML file (`BloodTests.xml`).
2. Connects to a **hospital database** (FAKE) (`MedicalRecords1400.mdf`) to retrieve patient outcome data (Alive or Died).
3. Uses LINQ and array structures to:
   - Filter and match patient data by `PatientID`
   - Skip any invalid entries (e.g., values set to `-99`)
4. For each of the four blood attributes:
   - Separates values into two categories: **patients who lived** and **patients who died**
   - Calculates the **mean** and **standard deviation** for each group using an optimized single-pass formula
5. Displays the results in a list box with neatly formatted output to 2 decimal places

---

## Code Structure

- **Main Form**: Contains a ListBox and an "Analyze" button.
- **Analyze Button**: On click, performs all the data loading and calculations.
- **Data Loading**:
  - Uses LINQ to parse blood test values and patient records.
  - Builds structured arrays of matched data using `PatientID` as a key.
- **Statistical Calculations**:
  - Done using separate loops for each attribute to handle partial missing data.
  - Uses the **alternative method** for standard deviation:  
    \[
    \text{std dev} = \sqrt{\frac{\sum{x^2}}{n} - \left(\frac{\sum{x}}{n}\right)^2}
    \]

---

## Output Example

Average Bilirubin (Lived): 0.64
Std. Dev Bilirubin (Lived): 0.12
Average Bilirubin (Died): 1.23
Std. Dev Bilirubin (Died): 0.35
... (continued for Alk Phosphate, SGOT, Albumin)

## Requirements

- Visual Studio 2019 or later  
- .NET Framework (WinForms support)  
- BloodTests.txt, BloodTests.xml, and MedicalRecords1400.mdf files  

---

## How to Run

1. **Download and unzip** the lab project folder.
2. Open the `.sln` file using **Visual Studio**.
3. Build the project).
4. Run the program.
5. Click the **Analyze** button to view results in the list box.

---

## Additional Notes

- Invalid values like `-99` are automatically excluded from calculations.
- The program demonstrates how statistical data processing can aid in health analysis.
- The output can be used to graph normal distributions for visual comparison between the patient groups.

---

## Future Enhancements (Optional Ideas)

- Visual graph plotting of the data using WinForms chart controls.
- User-selectable attributes for analysis.
- Export analysis results to CSV or PDF.
- Add filtering for age, sex, or other symptoms in future versions.

## License

This project was developed as part of a coursework assignment and is intended for educational use.
