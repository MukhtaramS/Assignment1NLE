
## 🎯 Task Breakdown

### **Task 1: Data Normalization**
**Objective**: Convert diverse cooking measurements to standardized units

**Key Features**:
- **Unit Conversion**: Handles 20+ German cooking units (g, kg, ml, l, EL, TL, Tasse, etc.)
- **Smart Normalization**: Converts to grams (weight), liters (volume), or pieces (count)
- **Backup Mechanisms**: Handles fractions (1/2 → 0.5), approximations, and edge cases
- **Statistical Analysis**: Analyzes unit frequency and distribution patterns

**Output Files**:
- `normalized_data.csv`: Ingredients with standardized values
- `conversion_table.csv`: Conversion factors for all units
- `unit_analysis.csv`: Frequency analysis of units found in data

### **Task 2: Nutritional Analysis**
**Objective**: Fetch nutritional information for ingredients via API

**Key Features**:
- **API Integration**: Connects to nutrition calculator API
- **Smart Ingredient Cleaning**: Removes adjectives, packaging terms
- **Error Handling**: Manages unrecognized ingredients gracefully
- **Data Enrichment**: Combines nutritional data with normalized measurements

**API Endpoint**: `https://smarthome.uni-regensburg.de/naehrwertrechner/`

**Output Files**:
- `nutritional_results.csv`: Nutritional data for recognized ingredients
- `unrecognized_ingredients.json`: Ingredients the API couldn't identify
- `improved_prompts.json`: Enhanced prompts based on analysis

### **Task 3: Prompt Engineering**
**Objective**: Develop better prompts for ingredient and amount extraction

**Key Features**:
- **Pattern Analysis**: Identifies common issues in original data
- **Improved Prompts**: Creates refined prompts addressing discovered issues
- **Rule-based Cleaning**: Removes brand names, packaging terms, adjectives
- **Better JSON Structure**: More consistent output formatting

**Key Improvements**:
1. **Removes unnecessary modifiers**: (frisch, getrocknet, gemahlen)
2. **Handles packaging terms**: (Päckchen, Dose, Glas)
3. **Manages brand names**: (Ja!, Dr. Oetker)
4. **Better unit classification**: Clear weight/volume/count distinction
5. **Fraction support**: Converts ½, ¼, 1/2 to decimal values

## 🔧 Technical Implementation

### **Core Algorithms**
1. **Unit Normalization**:
```python
def normalize_measurement(amount_json):
    # Converts diverse units to grams/liters/pieces
    # Handles fractions, approximations, edge cases
