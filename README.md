# Automated Analytical Method Validation Interface

## Introduction
This project is a Python script designed to validate an analysis method using various statistical criteria. It performs tests on the provided data and generates detailed reports in Word format. The validation criteria include:

- **Linearity**: Validates the linear relationship between variables.
- **Accuracy**: Validates the method's precision against reference values.
- **Repeatability**: Validates the consistency and variability of measurements.
- **Robustness**: Validates the stability of the method using a Hadamard matrix.
- **Exactness**: Validates the method according to specified levels and tolerance limits.
- **LOD/LOQ**: Calculates the Limits of Detection and Quantification.

## Excel Files and Data Structure
The project requires several Excel files to validate the analysis method according to different criteria. Below is a guide to properly structure your Excel files:

### 1. Linearity Validation
- **Table for Active Ingredient (PA) only**: Contains data to validate linearity with the active ingredient alone.
- **Table for PA + FPR**: Contains data to validate linearity with the active ingredient and the reconstituted dosage form (FPR).

**Expected Structure for Each Linearity File:**

| Factor  | x (independent variable) | y (response) |
|---------|--------------------------|--------------|
| Level 1 | 10                       | 12           |
| Level 2 | 20                       | 25           |
| Level 3 | 30                       | 35           |

### 2. Accuracy Validation
The Excel file for accuracy contains data for PA + FPR.

**Expected Structure for the Accuracy File:**

| Level | xij | yij  | Reference |
|-------|-----|------|-----------|
| 1     | 10  | 9.8  | 10        |
| 2     | 20  | 19.5 | 20        |
| 3     | 30  | 29.2 | 30        |

### 3. Repeatability Validation
The Excel file for repeatability contains data for variability and repeatability between series.

**Expected Structure for the Repeatability File:**

| Series | Trial | Quantity Introduced | Air | Response |
|--------|-------|---------------------|-----|----------|
| 1      | 1     | 5                   | 2.1 | 5.2      |
| 1      | 2     | 5                   | 2.3 | 5.3      |
| 2      | 1     | 10                  | 3.0 | 10.1     |

> **Important**: For accuracy and repeatability validation, the "Day Constants" represent a calibration factor for each testing day. These constants are obtained by dividing the measured response (`yij`) by the introduced quantity (`xij`) for each repetition on the respective day:
> - **Day Constant 1**: Calculated as the ratio of `yij` to `xij` for day 1.
> - **Day Constant 2**: Similarly calculated for day 2.
> - **Day Constant 3**: Similarly calculated for day 3.  
> These constants adjust measurements based on specific experimental conditions for each testing day.

### 4. Robustness Validation
The files for robustness contain a Hadamard matrix with the responses in the last column.

**Expected Structure for the Robustness File:**

| x1 | x2 | Response |
|----|----|----------|
| 1  | 0  | 10       |
| 0  | 1  | 12       |
| 1  | 1  | 11       |

### 5. Exactitude Profile
For exactness, you need to choose the number of levels and then import tables based on the specified number of levels. For each level, you must enter a reference value.

**Expected Structure for the Exactness Files:**

| Level | xij | yij  | Reference |
|-------|-----|------|-----------|
| 1     | 10  | 9.8  | 10        |
| 2     | 20  | 19.5 | 20        |
| 3     | 30  | 29.2 | 30        |

### 6. LOD/LOQ Validation
The Excel file for LOD/LOQ should contain blank measurements in a single column.

**Expected Structure for the LOD/LOQ File:**

| Blank |
|-------|
| x1    |
| ...   |
| xi    |

## Usage Instructions
1. **Check Each Excel File**: Ensure your Excel files are structured as per the examples provided above.
2. **Run the Script**: Once the files are prepared, import them into the script to perform the different validations.
3. **Analyze Results**: The script will generate reports detailing the results of the various analyses (linearity, accuracy, repeatability, robustness, exactitude profile, and LOD/LOQ).


## Download the Executable
You can download the compiled executable package (Windows) from the latest release: [Release v1.0.0](https://github.com/samibnz1/Analytical-Method-Validation-Interface/releases/tag/v1.0.0)  
The release contains a ZIP file (`ValidationTool-v1.0.0.zip`) with the executable, required DLLs, and example datasets. Extract the ZIP file and run `validation_tool.exe` directly.  
**Note**: Ensure your antivirus is up to date before running the executable. This tool has been developed as part of an academic project at FST Fès and is safe to use, but always exercise caution with executables from the internet.
