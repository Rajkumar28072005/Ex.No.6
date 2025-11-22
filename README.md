# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools
# Date: 22-11-2025
# Register no.: 212223230166

# Aim
To develop a single Python function that can automatically read both .csv and .json files into a list of dictionaries, ensuring compatibility with multiple AI tools following the Persona Pattern approach.

# Apparatus Required
Python 3.x
Built-in libraries: csv, json, os
Sample dataset files:
data.csv
data.json
Text editor or IDE (VS Code / PyCharm / Jupyter Notebook)
# Explanation
In AI and data-driven applications, different tools often require a uniform input format. The Persona Pattern emphasizes creating adaptable, reusable functions that act as a "persona" for different AI tools.

Here, we create a single function load_data() that:

Accepts a file path.
Automatically detects the file type (.csv or .json).
Converts the contents into a list of dictionaries format.
For .csv, each row becomes a dictionary using headers as keys.
For .json, the file is loaded directly into a list of dictionaries.
Returns the processed data for further use in AI models, pipelines, or analytics.
This ensures that AI tools get standardized input data, regardless of the original file format.
# Prompt:
Write a Python program for my IoT-based smart environment project that
fetches temperature and humidity data from an IoT sensor API and the
OpenWeatherMap API, then displays both values side by side in a Pandas table

# Generate python code for interacting python code with multiple APIs:
<img width="318" height="158" alt="image" src="https://github.com/user-attachments/assets/697b182e-e7f0-4841-8aee-0de28c21b9e3" />


# Python Code:
```
import csv
import json
import os

def load_data(file_path):
    """
    Loads data from either a CSV or JSON file into a list of dictionaries.
    
    Args:
        file_path (str): Path to the file (.csv or .json)
    
    Returns:
        list[dict]: Data as list of dictionaries
    """
    if not os.path.exists(file_path):
        raise FileNotFoundError(f"{file_path} does not exist")

    extension = os.path.splitext(file_path)[1].lower()  # get file extension

    data = []
    if extension == ".csv":
        with open(file_path, mode="r", encoding="utf-8") as f:
            reader = csv.DictReader(f)
            data = [row for row in reader]

    elif extension == ".json":
        with open(file_path, mode="r", encoding="utf-8") as f:
            data = json.load(f)
            # Ensure it's a list of dicts
            if isinstance(data, dict):
                data = [data]

    else:
        raise ValueError("Unsupported file format. Please use .csv or .json")

    return data
```

# Example Usage
if __name__ == "__main__":
    csv_data = load_data("data.csv")
    print("CSV Data:", csv_data)

    json_data = load_data("data.json")
    print("JSON Data:", json_data)

# Gemini Output:
```
# Assuming 'data.csv' exists in the same directory
data_list = load_data('data.csv')
print(data_list)
[
    {'name': 'Alice', 'age': '30', 'city': 'NY'},
    {'name': 'Bob', 'age': '24', 'city': 'LA'}
]
[
    {"name": "Charlie", "role": "Dev"},
    {"name": "Diana", "role": "PM"}
]
# Assuming 'data.json' exists in the same directory
data_list = load_data('data.json')
print(data_list)
[
    {'name': 'Charlie', 'role': 'Dev'},
    {'name': 'Diana', 'role': 'PM'}
]
# Assuming 'non_existent_file.txt' does not exist
try:
    load_data('non_existent_file.txt')
except FileNotFoundError as e:
    print(e)
```
# Compare Outputs:
| Feature                       | First snippet (just the function)       | Second snippet (function + example usage & error handling)                    |
| ----------------------------- | --------------------------------------- | ----------------------------------------------------------------------------- |
| Content                       | Only the function definition            | Function + example usage + error handling                                     |
| Example usage included        | No                                      | Yes — shows `load_data('data.csv')`, `load_data('data.json')`, and error case |
| File paths in examples        | None                                    | Includes `'data.csv'`, `'data.json'`, `'non_existent_file.txt'`               |
| Output examples provided      | No                                      | Yes — shows expected list of dictionaries from CSV & JSON                     |
| Error handling demonstration  | Not shown                               | Shows catching `FileNotFoundError`                                            |
| Imports and definition block  | Yes — `import csv, json, os` + function | Same imports + same function                                                  |
| Documentation (docstring)     | Present                                 | Present                                                                       |
| Format detection & conversion | Same logic in both                      | Same logic in both                                                            
# Conclusion:
In this experiment, we successfully developed a Python function load_data() that can automatically read both .csv and .json files and convert their contents into a standardized list of dictionaries. This approach ensures that data from multiple sources can be easily integrated and used across different AI and IoT applications. By following the Persona Pattern, the function acts as a flexible and reusable data-loading component that adapts to different input formats. This standardization simplifies data preprocessing, making it efficient for use in AI pipelines, IoT systems, and smart environment projects.

# Result: 
The corresponding Prompt is executed successfully.
