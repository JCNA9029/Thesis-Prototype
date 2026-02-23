# Copilot Instructions for VirusTotal Multi-Engine Virus Scanner

## Project Overview
This project is a command-line multi-engine virus scanner that integrates with the VirusTotal API and a local machine learning model for malware detection. It supports both single and batch file/SHA256 hash scanning, and provides fallback ML-based predictions when VirusTotal has no data.

## Key Components
- **multi-engine virus scanner.py**: Main script. Handles user interaction, VirusTotal API calls, batch processing, and ML fallback.
- **dataset_antivirus.csv**: Sample dataset for ML model training (not used at runtime).
- **antivirus3**: Pickled ML model (required for local predictions).

## Core Workflows
- **Start**: User chooses to scan by SHA256, upload a file, or exit.
- **VirusTotal API**: Uses `x-apikey` (replace `YOUR-API-KEY`) for all lookups. Handles both file and hash queries.
- **Batch Scanning**: Accepts `.txt` files with SHA256 hashes for bulk lookup. Optionally saves results to a user-named file.
- **ML Fallback**: If VirusTotal has no data, predicts malware type using a local model based on file extension.

## Project-Specific Patterns
- **File extension mapping**: Only certain extensions are mapped for ML fallback. See `extension_map` in the main script.
- **User prompts**: All user input is via `input()`. The script is interactive and not designed for automation.
- **Error handling**: If VirusTotal returns no data, the script prints an error and triggers ML prediction.
- **Internet check**: Script checks for connectivity before starting.

## Integration Points
- **VirusTotal API**: Requires a valid API key. All requests use the v3 API and expect JSON responses.
- **ML Model**: Expects a file named `antivirus3` (pickle format) in the working directory.

## Example Usage
- To scan a file: Run the script, choose option 2, and drag the file into the prompt.
- To scan by SHA256: Run the script, choose option 1, and enter the hash.
- To batch scan: Choose option 2, then option 1, and provide a `.txt` file with hashes.

## Conventions