# Snort Rules and MITRE ATT&CK Framework Correlation

This Python notebook analyzes Snort rules and correlates the most frequent terms found in those rules with techniques described in the MITRE ATT&CK framework. The correlation is based on the presence of the term in the description of the MITRE technique. 

## How it works

The script performs the following tasks:

1. It initializes an `attack_client` object to interact with the MITRE ATT&CK framework and retrieves all enterprise techniques.

2. It parses each Snort rule to create a dictionary that represents its structure and contents.

3. It then tokenizes the 'msg' field in each rule (this field often contains a summary of what the rule is designed to detect) and calculates the frequency of each term.

4. It removes stop words (common words that typically do not carry significant meaning) from these tokens.

5. It orders the terms by frequency and correlates the top 200 with the MITRE ATT&CK framework. 

6. It calculates the confidence of the correlation as the frequency of the term in a technique description over the total frequency of the term in all technique descriptions.

7. It finally creates a Lookup Table (LUT) that maps the top two MITRE techniques and their confidence scores to each keyword. Additional techniques are noted but not included as main mappings.

8. The LUT is then exported to a CSV and Excel file.

## Required libraries

To use this script, you will need the following Python libraries:
- os
- re
- nltk
- attackcti
- pandas

Ensure that these are installed in your Python environment.

## Usage

Make sure the path to the Snort rules files is correctly set in the `folder_path` variable. 

Run the script using a Python 3 interpreter. The script will output a CSV and Excel file named 'keyword_MITRE_LUT' that you can use for further analysis or integration into other systems.

This script is ideal for security analysts or researchers looking to make connections between Snort IDS/IPS alerts and the tactics and techniques used by attackers as cataloged in the MITRE ATT&CK framework.

## Important Notes

This script does not provide a definitive or authoritative correlation between Snort rules and MITRE techniques. The correlation is based on keyword occurrence and does not take into account the context in which the term is used. 

Therefore, the output should be used as a starting point for further investigation and analysis, not as a conclusive mapping.
