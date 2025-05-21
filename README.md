# Sampling-Weight

# Survey Sampling Weights Calculator

This repository provides tools to calculate post-stratification sampling weights for survey data based on known population distributions. 
It's designed for reusability across different studies.

Step-by-Step Procedure

1. Load Data from CSV:

      input_path = '/path/to/your/input.csv'
    
      data = load_data(input_path)

2. Define Population Proportions:
       Modify based on your target population
    
    
      population_distribution = {
   
          'schooltype3': {'2-year college': 0.2, '4-year university': 0.58, 'graduate school': 0.22}, 
          'age3': {'15-17': 0.01, '18-19': 0.2262, '20-24': 0.4360, '25-34': 0.1938, '35+': 0.1340}, 
          'gender2': {'male': 0.41, 'female': 0.57, 'Non-Binary': 0.01, 'Prefer not to say': 0.01},
          'major2': {'STEM': 0.5, 'non-STEMB': 0.5}
      }

4. Calculate Weights:

      weights = calculate_weights(data, population_distribution)

4. Apply Weights to Data:

      data_with_weights = apply_weights(data, weights, cap=2.5)  # Adjust cap as needed

5. Export Weighted Data:

      output_path = '/path/to/your/output.csv'
   
      export_weights(data_with_weights, id_column='uuid', output_path=output_path)

7. Check Confirmation Message

      print(f"Output file generated at: {output_path}")

      If you see, 'Output file generated at: /Users/user_id/Downloads/filename.csv', you have successfully calculated the weights


Important Note:

Replace /path/to/your/input.csv and /path/to/your/output.csv with your actual file paths. Adjust cap=2.5 in apply_weights as necessary to cap extreme weight values. This structured approach will guide users through each step in applying weights to survey data based on specified population distributions.
