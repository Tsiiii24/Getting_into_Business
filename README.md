```python
!pip install kaggle > /dev/null 2>&1

!pip install -q kaggle

from IPython.display import clear_output

clear_output(wait=True)



```

# Heading one




```python
!kaggle datasets download -d fratzcan/usa-house-prices

import zipfile
import pandas as pd
import os
import statistics
from prettytable import PrettyTable

# Define file paths
zip_file = "usa-house-prices.zip"
extract_folder = "usa_house_prices"

# Extract the ZIP file
with zipfile.ZipFile(zip_file, "r") as zip_ref:
    zip_ref.extractall(extract_folder)

# List extracted files to find the correct CSV name
extracted_files = os.listdir(extract_folder)
print("Extracted Files:", extracted_files)

# Load the dataset (replace with the correct filename)
csv_file = [file for file in extracted_files if file.endswith(".csv")][0]  # Auto-detect CSV file
df = pd.read_csv(f"{extract_folder}/{csv_file}")
clear_output(wait=True)

df.head()
```





  <div id="df-58d72faa-48c7-4bc7-994f-e46477a61256" class="colab-df-container">
    <div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>condition</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>street</th>
      <th>city</th>
      <th>statezip</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2014-05-09 00:00:00</td>
      <td>376000.0</td>
      <td>3.0</td>
      <td>2.00</td>
      <td>1340</td>
      <td>1384</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>1340</td>
      <td>0</td>
      <td>2008</td>
      <td>0</td>
      <td>9245-9249 Fremont Ave N</td>
      <td>Seattle</td>
      <td>WA 98103</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2014-05-09 00:00:00</td>
      <td>800000.0</td>
      <td>4.0</td>
      <td>3.25</td>
      <td>3540</td>
      <td>159430</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>3540</td>
      <td>0</td>
      <td>2007</td>
      <td>0</td>
      <td>33001 NE 24th St</td>
      <td>Carnation</td>
      <td>WA 98014</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2014-05-09 00:00:00</td>
      <td>2238888.0</td>
      <td>5.0</td>
      <td>6.50</td>
      <td>7270</td>
      <td>130017</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>6420</td>
      <td>850</td>
      <td>2010</td>
      <td>0</td>
      <td>7070 270th Pl SE</td>
      <td>Issaquah</td>
      <td>WA 98029</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2014-05-09 00:00:00</td>
      <td>324000.0</td>
      <td>3.0</td>
      <td>2.25</td>
      <td>998</td>
      <td>904</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>3</td>
      <td>798</td>
      <td>200</td>
      <td>2007</td>
      <td>0</td>
      <td>820 NW 95th St</td>
      <td>Seattle</td>
      <td>WA 98117</td>
      <td>USA</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2014-05-10 00:00:00</td>
      <td>549900.0</td>
      <td>5.0</td>
      <td>2.75</td>
      <td>3060</td>
      <td>7015</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
      <td>1600</td>
      <td>1460</td>
      <td>1979</td>
      <td>0</td>
      <td>10834 31st Ave SW</td>
      <td>Seattle</td>
      <td>WA 98146</td>
      <td>USA</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-58d72faa-48c7-4bc7-994f-e46477a61256')"
            title="Convert this dataframe to an interactive table."
            style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960">
    <path d="M120-120v-720h720v720H120Zm60-500h600v-160H180v160Zm220 220h160v-160H400v160Zm0 220h160v-160H400v160ZM180-400h160v-160H180v160Zm440 0h160v-160H620v160ZM180-180h160v-160H180v160Zm440 0h160v-160H620v160Z"/>
  </svg>
    </button>

  <style>
    .colab-df-container {
      display:flex;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    .colab-df-buttons div {
      margin-bottom: 4px;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

    <script>
      const buttonEl =
        document.querySelector('#df-58d72faa-48c7-4bc7-994f-e46477a61256 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-58d72faa-48c7-4bc7-994f-e46477a61256');
        const dataTable =
          await google.colab.kernel.invokeFunction('convertToInteractive',
                                                    [key], {});
        if (!dataTable) return;

        const docLinkHtml = 'Like what you see? Visit the ' +
          '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
          + ' to learn more about interactive tables.';
        element.innerHTML = '';
        dataTable['output_type'] = 'display_data';
        await google.colab.output.renderOutput(dataTable, element);
        const docLink = document.createElement('div');
        docLink.innerHTML = docLinkHtml;
        element.appendChild(docLink);
      }
    </script>
  </div>


<div id="df-1241c587-ba7a-4f91-b823-d3b5f4bf78f9">
  <button class="colab-df-quickchart" onclick="quickchart('df-1241c587-ba7a-4f91-b823-d3b5f4bf78f9')"
            title="Suggest charts"
            style="display:none;">

<svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
     width="24px">
    <g>
        <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zM9 17H7v-7h2v7zm4 0h-2V7h2v10zm4 0h-2v-4h2v4z"/>
    </g>
</svg>
  </button>

<style>
  .colab-df-quickchart {
      --bg-color: #E8F0FE;
      --fill-color: #1967D2;
      --hover-bg-color: #E2EBFA;
      --hover-fill-color: #174EA6;
      --disabled-fill-color: #AAA;
      --disabled-bg-color: #DDD;
  }

  [theme=dark] .colab-df-quickchart {
      --bg-color: #3B4455;
      --fill-color: #D2E3FC;
      --hover-bg-color: #434B5C;
      --hover-fill-color: #FFFFFF;
      --disabled-bg-color: #3B4455;
      --disabled-fill-color: #666;
  }

  .colab-df-quickchart {
    background-color: var(--bg-color);
    border: none;
    border-radius: 50%;
    cursor: pointer;
    display: none;
    fill: var(--fill-color);
    height: 32px;
    padding: 0;
    width: 32px;
  }

  .colab-df-quickchart:hover {
    background-color: var(--hover-bg-color);
    box-shadow: 0 1px 2px rgba(60, 64, 67, 0.3), 0 1px 3px 1px rgba(60, 64, 67, 0.15);
    fill: var(--button-hover-fill-color);
  }

  .colab-df-quickchart-complete:disabled,
  .colab-df-quickchart-complete:disabled:hover {
    background-color: var(--disabled-bg-color);
    fill: var(--disabled-fill-color);
    box-shadow: none;
  }

  .colab-df-spinner {
    border: 2px solid var(--fill-color);
    border-color: transparent;
    border-bottom-color: var(--fill-color);
    animation:
      spin 1s steps(1) infinite;
  }

  @keyframes spin {
    0% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
      border-left-color: var(--fill-color);
    }
    20% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    30% {
      border-color: transparent;
      border-left-color: var(--fill-color);
      border-top-color: var(--fill-color);
      border-right-color: var(--fill-color);
    }
    40% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-top-color: var(--fill-color);
    }
    60% {
      border-color: transparent;
      border-right-color: var(--fill-color);
    }
    80% {
      border-color: transparent;
      border-right-color: var(--fill-color);
      border-bottom-color: var(--fill-color);
    }
    90% {
      border-color: transparent;
      border-bottom-color: var(--fill-color);
    }
  }
</style>

  <script>
    async function quickchart(key) {
      const quickchartButtonEl =
        document.querySelector('#' + key + ' button');
      quickchartButtonEl.disabled = true;  // To prevent multiple clicks.
      quickchartButtonEl.classList.add('colab-df-spinner');
      try {
        const charts = await google.colab.kernel.invokeFunction(
            'suggestCharts', [key], {});
      } catch (error) {
        console.error('Error during call to suggestCharts:', error);
      }
      quickchartButtonEl.classList.remove('colab-df-spinner');
      quickchartButtonEl.classList.add('colab-df-quickchart-complete');
    }
    (() => {
      let quickchartButtonEl =
        document.querySelector('#df-1241c587-ba7a-4f91-b823-d3b5f4bf78f9 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>

    </div>
  </div>





```python
colnames=(df.columns)  # Print the column names


# Create a DataFrame with column names as a single column
col_table = pd.DataFrame({"Column Names": df.columns})

# Print the table in markdown format
print(col_table.to_markdown(index=False))

```

    | Column Names   |
    |:---------------|
    | date           |
    | price          |
    | bedrooms       |
    | bathrooms      |
    | sqft_living    |
    | sqft_lot       |
    | floors         |
    | waterfront     |
    | view           |
    | condition      |
    | sqft_above     |
    | sqft_basement  |
    | yr_built       |
    | yr_renovated   |
    | street         |
    | city           |
    | statezip       |
    | country        |





```python



# Find the earliest (min) and latest (max) date
start_date = df['date'].min()
end_date = df['date'].max()

print("Date Range:", start_date, "to", end_date)

# Find the earliest (min) and latest (max) date
city = df['city']
zipc=df['statezip']
country=df['country']
collection=city+zipc+country
table = PrettyTable()

table.field_names = ["Feature", "Mean", "Median", "Mode", "Range","Std_deviation"]

for col in df.select_dtypes(include=["number"]).columns:
    mean_val = df[col].mean()
    median_val = df[col].median()
    mode_val = df[col].mode().iloc[0]
    range_val = df[col].max() - df[col].min()
    std_val=df[col].std()

    # Add feature name as the first element in the row

    table.add_row([col, round(mean_val, 2), round(median_val, 2), mode_val, round(range_val, 2), round(std_val, 2)])

# Print the table
print(table)








```

    Dataset URL: https://www.kaggle.com/datasets/fratzcan/usa-house-prices
    License(s): apache-2.0
    Downloading usa-house-prices.zip to /content
    100% 119k/119k [00:00<00:00, 561kB/s]
    100% 119k/119k [00:00<00:00, 560kB/s]
    Extracted Files: ['USA Housing Dataset.csv']
    Index(['date', 'price', 'bedrooms', 'bathrooms', 'sqft_living', 'sqft_lot',
           'floors', 'waterfront', 'view', 'condition', 'sqft_above',
           'sqft_basement', 'yr_built', 'yr_renovated', 'street', 'city',
           'statezip', 'country'],
          dtype='object')
    Date Range: 2014-05-02 00:00:00 to 2014-07-10 00:00:00
    +---------------+-----------+----------+------+------------+---------------+
    |    Feature    |    Mean   |  Median  | Mode |   Range    | Std_deviation |
    +---------------+-----------+----------+------+------------+---------------+
    |     price     | 553062.88 | 460000.0 | 0.0  | 26590000.0 |   583686.45   |
    |    bedrooms   |    3.4    |   3.0    | 3.0  |    8.0     |      0.9      |
    |   bathrooms   |    2.16   |   2.25   | 2.5  |    6.75    |      0.78     |
    |  sqft_living  |  2143.64  |  1980.0  | 1720 |    9670    |     957.48    |
    |    sqft_lot   |  14697.64 |  7676.0  | 5000 |  1073580   |    35876.84   |
    |     floors    |    1.51   |   1.5    | 1.0  |    2.5     |      0.53     |
    |   waterfront  |    0.01   |   0.0    |  0   |     1      |      0.09     |
    |      view     |    0.25   |   0.0    |  0   |     4      |      0.79     |
    |   condition   |    3.45   |   3.0    |  3   |     4      |      0.68     |
    |   sqft_above  |  1831.35  |  1600.0  | 1200 |    7650    |     861.38    |
    | sqft_basement |   312.29  |   0.0    |  0   |    4820    |     464.35    |
    |    yr_built   |  1970.81  |  1976.0  | 2005 |    114     |     29.81     |
    |  yr_renovated |   808.37  |   0.0    |  0   |    2014    |     979.38    |
    +---------------+-----------+----------+------+------------+---------------+



```python
# Identify Missing Values
missing_values = df.isnull().sum()
missing_percentage = (missing_values / len(df)) * 100

# Display missing values and their percentages
missing_df = pd.DataFrame({
    'Missing Values': missing_values,
    'Percentage (%)': missing_percentage
}).sort_values(by='Percentage (%)', ascending=False)

print("Missing Values Summary:\n", missing_df)

# Optional: Visualize missing data pattern
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))
sns.heatmap(df.isnull(), cbar=False, cmap='viridis')
plt.title('Missing Values Heatmap')
plt.show()

# Handling Missing Values - Example Strategies
# 1. Drop rows with missing values (if few)
df_dropped = df.dropna()

# 2. Fill missing numeric values with mean
df_filled = df.fillna(df.mean(numeric_only=True))

# 3. Fill missing categorical values with mode
for col in df.select_dtypes(include=['object']).columns:
    df_filled[col] = df_filled[col].fillna(df[col].mode()[0])

print("\nDataset after filling missing values:\n", df_filled.info())
```

    Missing Values Summary:
                    Missing Values  Percentage (%)
    date                        0             0.0
    price                       0             0.0
    statezip                    0             0.0
    city                        0             0.0
    street                      0             0.0
    yr_renovated                0             0.0
    yr_built                    0             0.0
    sqft_basement               0             0.0
    sqft_above                  0             0.0
    condition                   0             0.0
    view                        0             0.0
    waterfront                  0             0.0
    floors                      0             0.0
    sqft_lot                    0             0.0
    sqft_living                 0             0.0
    bathrooms                   0             0.0
    bedrooms                    0             0.0
    country                     0             0.0



    
![png](README_files/README_6_1.png)
    


    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4140 entries, 0 to 4139
    Data columns (total 18 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   date           4140 non-null   object 
     1   price          4140 non-null   float64
     2   bedrooms       4140 non-null   float64
     3   bathrooms      4140 non-null   float64
     4   sqft_living    4140 non-null   int64  
     5   sqft_lot       4140 non-null   int64  
     6   floors         4140 non-null   float64
     7   waterfront     4140 non-null   int64  
     8   view           4140 non-null   int64  
     9   condition      4140 non-null   int64  
     10  sqft_above     4140 non-null   int64  
     11  sqft_basement  4140 non-null   int64  
     12  yr_built       4140 non-null   int64  
     13  yr_renovated   4140 non-null   int64  
     14  street         4140 non-null   object 
     15  city           4140 non-null   object 
     16  statezip       4140 non-null   object 
     17  country        4140 non-null   object 
    dtypes: float64(4), int64(9), object(5)
    memory usage: 582.3+ KB
    
    Dataset after filling missing values:
     None



```python
# Price Distribution
plt.figure(figsize=(10, 6))
sns.histplot(df['price'], bins=30, kde=True)
plt.title('Distribution of House Prices')
plt.xlabel('Price')
plt.ylabel('Frequency')
plt.show()
```


    
![png](README_files/README_7_0.png)
    



```python
# Price by Top 10 Cities
top_cities = df['city'].value_counts().head(10).index
plt.figure(figsize=(12, 6))
sns.boxplot(x='city', y='price', data=df[df['city'].isin(top_cities)])
plt.title('Price Distribution in Top 10 Cities')
plt.xticks(rotation=45)
plt.show()
```


    
![png](README_files/README_8_0.png)
    


## Correlation Analysis

Here we are goignt ot explire if any of the features are corrected to each other to have a better understing of X.

A you can see from the plot below,


```python
# Correlation Heatmap
plt.figure(figsize=(10, 8))
sns.heatmap(df.select_dtypes(include=['number']).corr(), annot=True, fmt=".2f", cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()
```


    
![png](README_files/README_10_0.png)
    



```python
# Scatter Plot: Price vs. Square Footage
plt.figure(figsize=(10, 6))
sns.scatterplot(x='sqft_living', y='price', data=df)
plt.title('Price vs. Square Footage (Living Area)')
plt.xlabel('Square Footage (Living Area)')
plt.ylabel('Price')
plt.show()
```


    
![png](README_files/README_11_0.png)
    



```python

```

# 3. Expanding YOur Investubt



# h1
## h2


jhgf **bold text**

*hgg*




```python
!pwd
```

    /content



```python
!jupyter nbconvert --to markdown Capstone1.ipynb --output README

```

    [NbConvertApp] WARNING | pattern 'Capstone1.ipynb' matched no files
    This application is used to convert notebook files (*.ipynb)
            to various other formats.
    
            WARNING: THE COMMANDLINE INTERFACE MAY CHANGE IN FUTURE RELEASES.
    
    Options
    =======
    The options below are convenience aliases to configurable class-options,
    as listed in the "Equivalent to" description-line of the aliases.
    To see all configurable class-options for some <cmd>, use:
        <cmd> --help-all
    
    --debug
        set log level to logging.DEBUG (maximize logging output)
        Equivalent to: [--Application.log_level=10]
    --show-config
        Show the application's configuration (human-readable format)
        Equivalent to: [--Application.show_config=True]
    --show-config-json
        Show the application's configuration (json format)
        Equivalent to: [--Application.show_config_json=True]
    --generate-config
        generate default config file
        Equivalent to: [--JupyterApp.generate_config=True]
    -y
        Answer yes to any questions instead of prompting.
        Equivalent to: [--JupyterApp.answer_yes=True]
    --execute
        Execute the notebook prior to export.
        Equivalent to: [--ExecutePreprocessor.enabled=True]
    --allow-errors
        Continue notebook execution even if one of the cells throws an error and include the error message in the cell output (the default behaviour is to abort conversion). This flag is only relevant if '--execute' was specified, too.
        Equivalent to: [--ExecutePreprocessor.allow_errors=True]
    --stdin
        read a single notebook file from stdin. Write the resulting notebook with default basename 'notebook.*'
        Equivalent to: [--NbConvertApp.from_stdin=True]
    --stdout
        Write notebook output to stdout instead of files.
        Equivalent to: [--NbConvertApp.writer_class=StdoutWriter]
    --inplace
        Run nbconvert in place, overwriting the existing notebook (only
                relevant when converting to notebook format)
        Equivalent to: [--NbConvertApp.use_output_suffix=False --NbConvertApp.export_format=notebook --FilesWriter.build_directory=]
    --clear-output
        Clear output of current file and save in place,
                overwriting the existing notebook.
        Equivalent to: [--NbConvertApp.use_output_suffix=False --NbConvertApp.export_format=notebook --FilesWriter.build_directory= --ClearOutputPreprocessor.enabled=True]
    --coalesce-streams
        Coalesce consecutive stdout and stderr outputs into one stream (within each cell).
        Equivalent to: [--NbConvertApp.use_output_suffix=False --NbConvertApp.export_format=notebook --FilesWriter.build_directory= --CoalesceStreamsPreprocessor.enabled=True]
    --no-prompt
        Exclude input and output prompts from converted document.
        Equivalent to: [--TemplateExporter.exclude_input_prompt=True --TemplateExporter.exclude_output_prompt=True]
    --no-input
        Exclude input cells and output prompts from converted document.
                This mode is ideal for generating code-free reports.
        Equivalent to: [--TemplateExporter.exclude_output_prompt=True --TemplateExporter.exclude_input=True --TemplateExporter.exclude_input_prompt=True]
    --allow-chromium-download
        Whether to allow downloading chromium if no suitable version is found on the system.
        Equivalent to: [--WebPDFExporter.allow_chromium_download=True]
    --disable-chromium-sandbox
        Disable chromium security sandbox when converting to PDF..
        Equivalent to: [--WebPDFExporter.disable_sandbox=True]
    --show-input
        Shows code input. This flag is only useful for dejavu users.
        Equivalent to: [--TemplateExporter.exclude_input=False]
    --embed-images
        Embed the images as base64 dataurls in the output. This flag is only useful for the HTML/WebPDF/Slides exports.
        Equivalent to: [--HTMLExporter.embed_images=True]
    --sanitize-html
        Whether the HTML in Markdown cells and cell outputs should be sanitized..
        Equivalent to: [--HTMLExporter.sanitize_html=True]
    --log-level=<Enum>
        Set the log level by value or name.
        Choices: any of [0, 10, 20, 30, 40, 50, 'DEBUG', 'INFO', 'WARN', 'ERROR', 'CRITICAL']
        Default: 30
        Equivalent to: [--Application.log_level]
    --config=<Unicode>
        Full path of a config file.
        Default: ''
        Equivalent to: [--JupyterApp.config_file]
    --to=<Unicode>
        The export format to be used, either one of the built-in formats
                ['asciidoc', 'custom', 'html', 'latex', 'markdown', 'notebook', 'pdf', 'python', 'qtpdf', 'qtpng', 'rst', 'script', 'slides', 'webpdf']
                or a dotted object name that represents the import path for an
                ``Exporter`` class
        Default: ''
        Equivalent to: [--NbConvertApp.export_format]
    --template=<Unicode>
        Name of the template to use
        Default: ''
        Equivalent to: [--TemplateExporter.template_name]
    --template-file=<Unicode>
        Name of the template file to use
        Default: None
        Equivalent to: [--TemplateExporter.template_file]
    --theme=<Unicode>
        Template specific theme(e.g. the name of a JupyterLab CSS theme distributed
        as prebuilt extension for the lab template)
        Default: 'light'
        Equivalent to: [--HTMLExporter.theme]
    --sanitize_html=<Bool>
        Whether the HTML in Markdown cells and cell outputs should be sanitized.This
        should be set to True by nbviewer or similar tools.
        Default: False
        Equivalent to: [--HTMLExporter.sanitize_html]
    --writer=<DottedObjectName>
        Writer class used to write the
                                            results of the conversion
        Default: 'FilesWriter'
        Equivalent to: [--NbConvertApp.writer_class]
    --post=<DottedOrNone>
        PostProcessor class used to write the
                                            results of the conversion
        Default: ''
        Equivalent to: [--NbConvertApp.postprocessor_class]
    --output=<Unicode>
        Overwrite base name use for output files.
                    Supports pattern replacements '{notebook_name}'.
        Default: '{notebook_name}'
        Equivalent to: [--NbConvertApp.output_base]
    --output-dir=<Unicode>
        Directory to write output(s) to. Defaults
                                      to output to the directory of each notebook. To recover
                                      previous default behaviour (outputting to the current
                                      working directory) use . as the flag value.
        Default: ''
        Equivalent to: [--FilesWriter.build_directory]
    --reveal-prefix=<Unicode>
        The URL prefix for reveal.js (version 3.x).
                This defaults to the reveal CDN, but can be any url pointing to a copy
                of reveal.js.
                For speaker notes to work, this must be a relative path to a local
                copy of reveal.js: e.g., "reveal.js".
                If a relative path is given, it must be a subdirectory of the
                current directory (from which the server is run).
                See the usage documentation
                (https://nbconvert.readthedocs.io/en/latest/usage.html#reveal-js-html-slideshow)
                for more details.
        Default: ''
        Equivalent to: [--SlidesExporter.reveal_url_prefix]
    --nbformat=<Enum>
        The nbformat version to write.
                Use this to downgrade notebooks.
        Choices: any of [1, 2, 3, 4]
        Default: 4
        Equivalent to: [--NotebookExporter.nbformat_version]
    
    Examples
    --------
    
        The simplest way to use nbconvert is
    
                > jupyter nbconvert mynotebook.ipynb --to html
    
                Options include ['asciidoc', 'custom', 'html', 'latex', 'markdown', 'notebook', 'pdf', 'python', 'qtpdf', 'qtpng', 'rst', 'script', 'slides', 'webpdf'].
    
                > jupyter nbconvert --to latex mynotebook.ipynb
    
                Both HTML and LaTeX support multiple output templates. LaTeX includes
                'base', 'article' and 'report'.  HTML includes 'basic', 'lab' and
                'classic'. You can specify the flavor of the format used.
    
                > jupyter nbconvert --to html --template lab mynotebook.ipynb
    
                You can also pipe the output to stdout, rather than a file
    
                > jupyter nbconvert mynotebook.ipynb --stdout
    
                PDF is generated via latex
    
                > jupyter nbconvert mynotebook.ipynb --to pdf
    
                You can get (and serve) a Reveal.js-powered slideshow
    
                > jupyter nbconvert myslides.ipynb --to slides --post serve
    
                Multiple notebooks can be given at the command line in a couple of
                different ways:
    
                > jupyter nbconvert notebook*.ipynb
                > jupyter nbconvert notebook1.ipynb notebook2.ipynb
    
                or you can specify the notebooks list in a config file, containing::
    
                    c.NbConvertApp.notebooks = ["my_notebook.ipynb"]
    
                > jupyter nbconvert --config mycfg.py
    
    To see all available configurables, use `--help-all`.
    

