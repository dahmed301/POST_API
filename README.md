# **Exploratory Data Analysis for House Prices Dataset**


```python
!jupyter nbconvert --to markdown filename.ipynb
```

    [NbConvertApp] WARNING | pattern 'filename.ipynb' matched no files
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
    


##ABSTRACT
This document outlines the process of performing exploratory data analaysis on the House Prices dataset. For this project, Jupyter Notebook environment has been used through the Google Colab tool. The aim is to investigate and explore trends in the data by visualising them after ingesting, cleaning and transforming the data. Variables are chosen and some correlations are looked at in order to understand the raw data and present a story. The steps taken throughout the process, relevant explanations, the required Python code and visualisations have been provided within this Notebook. Moreover, the Notebook has been exported as a pdf file as well which is also provided along with this Notebook.

##INTRODUCTION
###Background
The House Prices dataset uses information from the Assessor's Office and is published on Kaggle containing the details of houses sold between 2006 and 2010 in a town called Ames in Iowa, USA. It characterizes the housing market of that town by comprehensively capturing a wide array of variables associated with the sales of houses such as the physical features of the property, locality information, price and also some metrics on the quality and condition of various aspects of the house.
The dataset is provided in the form of two separate text files formatted as tables which are tab separated. One contains all the available variables, and the other contains the sale price of each property along with its unique ID. These datasets can be merged to attain the full picture and perform the required investigations on it. Overall, it is a wholesome dataset which is ideal for performing exploratory data analysis to identify patterns and trends hidden in the raw data.

###Objectives
The primary objective is to explore the dataset and generate meaningful insights from it. This objective can be achieved by performing EDA (Exploratory Data Analysis) on the dataset by importing, cleaning, merging and exploring the variables. This process can be streamlined by following the steps given below:


*   Import & merge the datasets to create one DataFrame for ease of recalling
*   Check for duplicate and missing values to ensure integrity of the analysis
*   Identify important variables and their data types to give a direction to the EDA
*   Explore the variables by obtaining their distributions & summary statistics
*   Visualise and correlate some variables to generate insights
*   Derive conclusions and key findings to wrap up the EDA

##DATA CLEANING & TRANSFORMATION
To begin our EDA, we need to import the datasets and to do that, first we need to import the required Python packages which will also make the EDA more efficient and easy to perform.


```python
# Import the pandas library as 'pd' for data manipulation and analysis
import pandas as pd

# Import the numpy library as 'np' for numerical operations
import numpy as np

# Import the matplotlib.pyplot library as 'plt' for creating visualizations
import matplotlib.pyplot as plt

# Import the seaborn library as 'sns' for enhanced data visualization
import seaborn as sns

# Import the missingno library as 'msno' for visualizing missing data patterns
import missingno as msno

```

Since we are using Google Colab environment, we need to link it to a Google Drive to access files and folders because if we use the local directory, we would have to upload the file everytime we close the notebook. This happens because Google Colab uses Google's online runtime where the code is saved and executed. Once the runtime is terminated or disconnected, the saved variables and datasets are lost. Linking the datasets through Google Drive takes care of that problem and ensures seamless access to files whenever the code is executed.


```python
#Mounting the Google Drive where datasets are saved

from google.colab import drive
drive.mount('/content/drive')
```

###Data Ingestion
After mounting the drive, we ingest our datasets which are available in text format (.txt file). They can be imported using pandas which reads them in the defined drive path, unpacks them according to the given separator (tab or \t in this case) and saves them as Data Frames.


```python
#Ingesting the two datasets as DataFrames using pandas

housing1 = pd.read_table('/content/drive/MyDrive/HousingData/Housing_1.txt',sep='\t')
housing2 = pd.read_table('/content/drive/MyDrive/HousingData/Housing_2.txt',sep='\t')
```

Let's have a look at our Data Frames:


```python
#Viewing first five rows of the housing1 Data Frame

housing1.head()
```





  <div id="df-89385c68-5fed-442f-990a-8f1e3ecc66d2" class="colab-df-container">
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
      <th>Order</th>
      <th>PID</th>
      <th>MS SubClass</th>
      <th>MS Zoning</th>
      <th>Lot Frontage</th>
      <th>Lot Area</th>
      <th>Street</th>
      <th>Alley</th>
      <th>Lot Shape</th>
      <th>Land Contour</th>
      <th>...</th>
      <th>Screen Porch</th>
      <th>Pool Area</th>
      <th>Pool QC</th>
      <th>Fence</th>
      <th>Misc Feature</th>
      <th>Misc Val</th>
      <th>Mo Sold</th>
      <th>Yr Sold</th>
      <th>Sale Type</th>
      <th>Sale Condition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>526301100</td>
      <td>20</td>
      <td>RL</td>
      <td>141.0</td>
      <td>31770</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>5</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>526350040</td>
      <td>20</td>
      <td>RH</td>
      <td>80.0</td>
      <td>11622</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>120</td>
      <td>0</td>
      <td>NaN</td>
      <td>MnPrv</td>
      <td>NaN</td>
      <td>0</td>
      <td>6</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>526351010</td>
      <td>20</td>
      <td>RL</td>
      <td>81.0</td>
      <td>14267</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Gar2</td>
      <td>12500</td>
      <td>6</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>526353030</td>
      <td>20</td>
      <td>RL</td>
      <td>93.0</td>
      <td>11160</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>4</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>527105010</td>
      <td>60</td>
      <td>RL</td>
      <td>74.0</td>
      <td>13830</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>NaN</td>
      <td>MnPrv</td>
      <td>NaN</td>
      <td>0</td>
      <td>3</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 81 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-89385c68-5fed-442f-990a-8f1e3ecc66d2')"
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
        document.querySelector('#df-89385c68-5fed-442f-990a-8f1e3ecc66d2 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-89385c68-5fed-442f-990a-8f1e3ecc66d2');
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


<div id="df-36d6c219-106b-49ba-8722-1e7c71729d78">
  <button class="colab-df-quickchart" onclick="quickchart('df-36d6c219-106b-49ba-8722-1e7c71729d78')"
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
        document.querySelector('#df-36d6c219-106b-49ba-8722-1e7c71729d78 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>





```python
#Viewing first five rows of the housing2 Data Frame

housing2.head()
```





  <div id="df-688c97cd-39aa-4ae8-bc8e-09a481c4466a" class="colab-df-container">
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
      <th>Order</th>
      <th>PID</th>
      <th>MS SubClass</th>
      <th>SalePrice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>526301100</td>
      <td>20</td>
      <td>215000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>526350040</td>
      <td>20</td>
      <td>105000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>526351010</td>
      <td>20</td>
      <td>172000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>526353030</td>
      <td>20</td>
      <td>244000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>527105010</td>
      <td>60</td>
      <td>189900</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-688c97cd-39aa-4ae8-bc8e-09a481c4466a')"
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
        document.querySelector('#df-688c97cd-39aa-4ae8-bc8e-09a481c4466a button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-688c97cd-39aa-4ae8-bc8e-09a481c4466a');
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


<div id="df-672f3887-143b-4888-bf14-736a3ffb025b">
  <button class="colab-df-quickchart" onclick="quickchart('df-672f3887-143b-4888-bf14-736a3ffb025b')"
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
        document.querySelector('#df-672f3887-143b-4888-bf14-736a3ffb025b button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




###Merging Data

As noticed, the two Data Frames have the same unique identifier - the Property ID which is named 'PID' in this case. Therefore, these two objects can be merged using 'PID' to form a single DataFrame


```python
# Merge two DataFrames, 'housing1' and 'housing2', using the common column 'PID'
raw_data = pd.merge(housing1, housing2, on='PID')

# Display the first few rows of the merged DataFrame to inspect the result
raw_data.head()
```





  <div id="df-1333637f-e1bc-4177-9133-54f375b996e9" class="colab-df-container">
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
      <th>Order_x</th>
      <th>PID</th>
      <th>MS SubClass_x</th>
      <th>MS Zoning</th>
      <th>Lot Frontage</th>
      <th>Lot Area</th>
      <th>Street</th>
      <th>Alley</th>
      <th>Lot Shape</th>
      <th>Land Contour</th>
      <th>...</th>
      <th>Fence</th>
      <th>Misc Feature</th>
      <th>Misc Val</th>
      <th>Mo Sold</th>
      <th>Yr Sold</th>
      <th>Sale Type</th>
      <th>Sale Condition</th>
      <th>Order_y</th>
      <th>MS SubClass_y</th>
      <th>SalePrice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>526301100</td>
      <td>20</td>
      <td>RL</td>
      <td>141.0</td>
      <td>31770</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>5</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>1</td>
      <td>20</td>
      <td>215000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>526350040</td>
      <td>20</td>
      <td>RH</td>
      <td>80.0</td>
      <td>11622</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>MnPrv</td>
      <td>NaN</td>
      <td>0</td>
      <td>6</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>2</td>
      <td>20</td>
      <td>105000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>526351010</td>
      <td>20</td>
      <td>RL</td>
      <td>81.0</td>
      <td>14267</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>Gar2</td>
      <td>12500</td>
      <td>6</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>3</td>
      <td>20</td>
      <td>172000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>526353030</td>
      <td>20</td>
      <td>RL</td>
      <td>93.0</td>
      <td>11160</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>4</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>4</td>
      <td>20</td>
      <td>244000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>527105010</td>
      <td>60</td>
      <td>RL</td>
      <td>74.0</td>
      <td>13830</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>MnPrv</td>
      <td>NaN</td>
      <td>0</td>
      <td>3</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>5</td>
      <td>60</td>
      <td>189900</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 84 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-1333637f-e1bc-4177-9133-54f375b996e9')"
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
        document.querySelector('#df-1333637f-e1bc-4177-9133-54f375b996e9 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-1333637f-e1bc-4177-9133-54f375b996e9');
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


<div id="df-435755db-f82f-4a2c-9ae1-8dfb0e7101c3">
  <button class="colab-df-quickchart" onclick="quickchart('df-435755db-f82f-4a2c-9ae1-8dfb0e7101c3')"
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
        document.querySelector('#df-435755db-f82f-4a2c-9ae1-8dfb0e7101c3 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




Let's inspect the shape and type of our raw dataset:


```python
#Checking the dimensions and type of the raw_data object

print("Dimensions: {} rows x {} columns".format(raw_data.shape[0],raw_data.shape[1]))
print(type(raw_data))
```

    Dimensions: 2939 rows x 84 columns
    <class 'pandas.core.frame.DataFrame'>


###Removing Duplicates

Now that we know that we have 2939 observations and 84 variables in our dataset, let's see if we have any duplicate values. If there are duplicates, we need to remove them because they can impact the analysis. Since 'PID' is the unique ID, we can check that for duplicates because it must only have unique values for each property.


```python
# Identify duplicate rows based on the 'PID' column in the 'raw_data' DataFrame
duplicates = raw_data['PID'].duplicated()

# Display rows that are duplicates based on the 'PID' column
# This shows a subset of the 'raw_data' DataFrame containing only the duplicated rows
raw_data[duplicates]
```





  <div id="df-4a0bee62-c2b2-4159-b814-4bd98d51e1b5" class="colab-df-container">
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
      <th>Order_x</th>
      <th>PID</th>
      <th>MS SubClass_x</th>
      <th>MS Zoning</th>
      <th>Lot Frontage</th>
      <th>Lot Area</th>
      <th>Street</th>
      <th>Alley</th>
      <th>Lot Shape</th>
      <th>Land Contour</th>
      <th>...</th>
      <th>Fence</th>
      <th>Misc Feature</th>
      <th>Misc Val</th>
      <th>Mo Sold</th>
      <th>Yr Sold</th>
      <th>Sale Type</th>
      <th>Sale Condition</th>
      <th>Order_y</th>
      <th>MS SubClass_y</th>
      <th>SalePrice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>146</th>
      <td>146</td>
      <td>535175070</td>
      <td>20</td>
      <td>RL</td>
      <td>73.0</td>
      <td>9300</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>4</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>146</td>
      <td>20</td>
      <td>167500</td>
    </tr>
    <tr>
      <th>147</th>
      <td>146</td>
      <td>535175070</td>
      <td>20</td>
      <td>RL</td>
      <td>73.0</td>
      <td>9300</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>4</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>146</td>
      <td>20</td>
      <td>167500</td>
    </tr>
    <tr>
      <th>148</th>
      <td>146</td>
      <td>535175070</td>
      <td>20</td>
      <td>RL</td>
      <td>73.0</td>
      <td>9300</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>4</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>146</td>
      <td>20</td>
      <td>167500</td>
    </tr>
    <tr>
      <th>150</th>
      <td>147</td>
      <td>535175180</td>
      <td>20</td>
      <td>RL</td>
      <td>87.0</td>
      <td>10725</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>5</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>147</td>
      <td>20</td>
      <td>108538</td>
    </tr>
    <tr>
      <th>151</th>
      <td>147</td>
      <td>535175180</td>
      <td>20</td>
      <td>RL</td>
      <td>87.0</td>
      <td>10725</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>5</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>147</td>
      <td>20</td>
      <td>108538</td>
    </tr>
    <tr>
      <th>152</th>
      <td>147</td>
      <td>535175180</td>
      <td>20</td>
      <td>RL</td>
      <td>87.0</td>
      <td>10725</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>IR1</td>
      <td>Lvl</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0</td>
      <td>5</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>147</td>
      <td>20</td>
      <td>108538</td>
    </tr>
    <tr>
      <th>154</th>
      <td>148</td>
      <td>535179020</td>
      <td>20</td>
      <td>RL</td>
      <td>80.0</td>
      <td>10032</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>GdWo</td>
      <td>NaN</td>
      <td>0</td>
      <td>6</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>148</td>
      <td>20</td>
      <td>159500</td>
    </tr>
    <tr>
      <th>155</th>
      <td>148</td>
      <td>535179020</td>
      <td>20</td>
      <td>RL</td>
      <td>80.0</td>
      <td>10032</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>GdWo</td>
      <td>NaN</td>
      <td>0</td>
      <td>6</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>148</td>
      <td>20</td>
      <td>159500</td>
    </tr>
    <tr>
      <th>156</th>
      <td>148</td>
      <td>535179020</td>
      <td>20</td>
      <td>RL</td>
      <td>80.0</td>
      <td>10032</td>
      <td>Pave</td>
      <td>NaN</td>
      <td>Reg</td>
      <td>Lvl</td>
      <td>...</td>
      <td>GdWo</td>
      <td>NaN</td>
      <td>0</td>
      <td>6</td>
      <td>2010</td>
      <td>WD</td>
      <td>Normal</td>
      <td>148</td>
      <td>20</td>
      <td>159500</td>
    </tr>
  </tbody>
</table>
<p>9 rows × 84 columns</p>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-4a0bee62-c2b2-4159-b814-4bd98d51e1b5')"
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
        document.querySelector('#df-4a0bee62-c2b2-4159-b814-4bd98d51e1b5 button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-4a0bee62-c2b2-4159-b814-4bd98d51e1b5');
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


<div id="df-92126f88-f69f-4e22-9435-2f0d52c8d974">
  <button class="colab-df-quickchart" onclick="quickchart('df-92126f88-f69f-4e22-9435-2f0d52c8d974')"
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
        document.querySelector('#df-92126f88-f69f-4e22-9435-2f0d52c8d974 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




As we can see, there are 9 rows that are duplicated. Now let's remove them.


```python
# Remove duplicate rows based on the 'PID' column in the 'raw_data' DataFrame
data = raw_data.drop_duplicates(subset='PID')
print("No. of rows after removing duplicates: ", len(data))
```

    No. of rows after removing duplicates:  2930


Notice that there were 9 duplicates. So, our rows changed from 2939 to 2930 after removing duplicates.

###Handling Missing/NA Values

Now, let's check for any missing or null values in our data. The fraction of missing or null (NaN) values in the data can negatively effect our EDA by obsuring the findings. If a column has more missing values than a defined threshold, we need to drop those columns because they will not be of any use to us in our analysis.


```python
# Calculate the percentage of missing values in each column
null = data.isnull().sum() / len(data) * 100

# Display the top 10 columns with the highest percentage of missing values
print(null.sort_values(ascending=False).head(10))

# Identify columns with more than 40% missing values
columns_to_drop = null[null > 40].index

# Drop columns with more than 40% missing values from the DataFrame
clean_data = data.drop(columns=columns_to_drop)

#Check the null values to make sure the columns are removed
null = clean_data.isnull().sum() / len(data) * 100
print("\n")
print(null.sort_values(ascending=False).head(10))
```

    Pool QC          99.556314
    Misc Feature     96.382253
    Alley            93.242321
    Fence            80.477816
    Fireplace Qu     48.532423
    Lot Frontage     16.723549
    Garage Finish     5.426621
    Garage Cond       5.426621
    Garage Yr Blt     5.426621
    Garage Qual       5.426621
    dtype: float64
    
    
    Lot Frontage      16.723549
    Garage Cond        5.426621
    Garage Yr Blt      5.426621
    Garage Finish      5.426621
    Garage Qual        5.426621
    Garage Type        5.358362
    Bsmt Exposure      2.832765
    BsmtFin Type 2     2.764505
    BsmtFin Type 1     2.730375
    Bsmt Cond          2.730375
    dtype: float64


###Removing Outliers

Next step is to have a look at the outliers. Perhaps the most important variable in our data is the Sales Price. Another important variable is the Living Area (square feet) of the property/house. If we investigate these two continous variables, we might be able to identify some outliers. Here we make a couple of box plots to visualise the spread of the two mentioned variables.


```python
#Box & Whisker of Sales Price

plt.figure(figsize=(10,6))
sns.boxplot(clean_data['SalePrice'], color = '#595f91')
plt.title('Box & Whisker of Sales Price ($)')
plt.show()
```


    
![png](CW1_files/CW1_29_0.png)
    



```python
#Box & Whisker of Gr Liv Area

plt.figure(figsize=(10,6))
sns.boxplot(clean_data['Gr Liv Area'], color = '#595f91')
plt.title('Box & Whisker of Living Area (sq ft)')
plt.show()
```


    
![png](CW1_files/CW1_30_0.png)
    


We can notice that there are some values which are way too far from the normal range of the variable. The mean and upper quartile are around $200,000 for the SalePrice and around 2000 sqft. for the Living Area. But the values beyond the maximum bars are potential outliers on the higher end of the distribution. Let's plot a scatterplot of these two variables to have a better view.


```python
# Set the figure size to 10x6 inches for the scatterplot
plt.figure(figsize=(10, 6))

# Create a scatter plot using Seaborn, with x='Gr Liv Area' and y='SalePrice' from the 'data' DataFrame
sns.scatterplot(clean_data, x='Gr Liv Area', y='SalePrice', color='#595f91')

# Add a vertical line at x=4000 with a red dashed line style and label for annotation
plt.axvline(x=4000, color='red', linestyle='--', label='Area > 4000 sqft.')

# Set the title of the scatterplot
plt.title('Scatterplot of Sale Price vs Living Area')

# Place the legend in the center-right position
plt.legend(loc="center right")

# Display the plot
plt.show()

```


    
![png](CW1_files/CW1_32_0.png)
    


We can observe that there are 5 points that lie beyond the red line which is drawn at 4000 sqft. This indicates that these 5 properties were unusual. The top 2 are really big houses having very high prices, and the bottom 3 are very large houses with unusually low prices. These 5 points are true outliers which need to be removed from our data as they skew our distributions and affect the correlations.


```python
#Removing rows with Living Area greater than 4000

filtered_data = clean_data.loc[raw_data['Gr Liv Area'] <= 4000]
```

###Choosing Variables
Now that our data is clean, we can move ahead by choosing our variables and exoploring their data types. Upon careful examination of our data, we can select our variables of interest which can have some hidden trends and patterns.

To perform an effective analysis, we need to choose such variables that have an impact on each other and generate meaningful insights. For that purpose, we can select the following columns from our data:
*   Neighborhood
*   Year Sold
*   Overall Quality
*   Year Built
*   Living Area
*   Sale Price


```python
#Selecting variables of interest

ex_data = filtered_data[['SalePrice','Gr Liv Area','Overall Qual','Year Built','Neighborhood']]

#Checking our variables and their data types
ex_data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 2925 entries, 0 to 2938
    Data columns (total 5 columns):
     #   Column        Non-Null Count  Dtype 
    ---  ------        --------------  ----- 
     0   SalePrice     2925 non-null   int64 
     1   Gr Liv Area   2925 non-null   int64 
     2   Overall Qual  2925 non-null   int64 
     3   Year Built    2925 non-null   int64 
     4   Neighborhood  2925 non-null   object
    dtypes: int64(4), object(1)
    memory usage: 137.1+ KB


###Data Types & Descriptive Statistics

Our data now has 5 variables out of which 2 are continuous (Sale Price & Living Area) while 3 are discrete (Overall Quality, Year Built & Neighborhood). But due to their nature, the Overall Quality and Year Built variables have numerical data types despite being discrete beacuse they only take certain fixed integer values. While neighborhood has a string data type representing the names of localities.
Let's take a look at the statistical summaries of our numerical variables.


```python
#Summary statistics of the numerical variables and round the values to 2 decimal places

ex_data.describe().round(2)
```





  <div id="df-05db3db2-a1df-4654-ace4-d12de4d4707e" class="colab-df-container">
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
      <th>SalePrice</th>
      <th>Gr Liv Area</th>
      <th>Overall Qual</th>
      <th>Year Built</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>2925.00</td>
      <td>2925.00</td>
      <td>2925.00</td>
      <td>2925.00</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>180411.57</td>
      <td>1493.98</td>
      <td>6.09</td>
      <td>1971.30</td>
    </tr>
    <tr>
      <th>std</th>
      <td>78554.86</td>
      <td>486.27</td>
      <td>1.40</td>
      <td>30.24</td>
    </tr>
    <tr>
      <th>min</th>
      <td>12789.00</td>
      <td>334.00</td>
      <td>1.00</td>
      <td>1872.00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>129500.00</td>
      <td>1126.00</td>
      <td>5.00</td>
      <td>1954.00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>160000.00</td>
      <td>1441.00</td>
      <td>6.00</td>
      <td>1973.00</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>213500.00</td>
      <td>1740.00</td>
      <td>7.00</td>
      <td>2001.00</td>
    </tr>
    <tr>
      <th>max</th>
      <td>625000.00</td>
      <td>3820.00</td>
      <td>10.00</td>
      <td>2010.00</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-05db3db2-a1df-4654-ace4-d12de4d4707e')"
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
        document.querySelector('#df-05db3db2-a1df-4654-ace4-d12de4d4707e button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-05db3db2-a1df-4654-ace4-d12de4d4707e');
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


<div id="df-a27a8773-081e-4dfd-a0a9-8daa622443dc">
  <button class="colab-df-quickchart" onclick="quickchart('df-a27a8773-081e-4dfd-a0a9-8daa622443dc')"
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
        document.querySelector('#df-a27a8773-081e-4dfd-a0a9-8daa622443dc button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>




We can see that the median values (50%) are reasonably close to the respective mean values, which means that the data has no more extreme outliers. Also the Overall Quality is a discrete variable ranging from 1 to 10. The Standard deviations and the Quartiles of the variables can be seen as well. We will explore these distribution more in the following section.

##DATA EXPLORATION & VISUALISATION

Now let us dive into the exploration and visualisation of the data at hand. First we will look at some variables in isolation to perform Univariate Analysis. Later some correlations will be looked at in order to get a Bivariate Analysis.


```python
#DISTRIBUTION OF NUMERICAL VARIABLES


# Create subplots with 2 rows and 3 columns
fig, axes = plt.subplots(nrows=2, ncols=2, figsize=(10, 8))

# Flatten the axes for easier iteration
axes = axes.flatten()

# List of columns for which you want to create histograms
columns = ['Overall Qual', 'SalePrice', 'Year Built', 'Gr Liv Area']

# Loop through columns and create histograms
for i, column in enumerate(columns):
    sns.histplot(ex_data[column], bins=10, kde=True, kde_kws={'bw_adjust':2}, color='#595f91', ax=axes[i])
    axes[i].set_title(f'Histogram of {column}')
    axes[i].set_xlabel(column)
    axes[i].set_ylabel('Count')

# Adjust layout to prevent overlap
plt.tight_layout()

# Show the plot
plt.show()

```


    
![png](CW1_files/CW1_43_0.png)
    


As seen above, the Sales Price, Living Area and Overall Quality have a distribution which is similar to a bell curve or normal distribution. We can say that these three variables are somewhat normally distributed as expected. Regardless, their shapes and sizes are all different which indicates the spread and frequency of the values within these variables.

Next, let's look at the distribution of our Neighborhood variable based on the number of houses in each neighborhood.


```python
# Count the occurrences of each neighborhood
neighborhood_counts = ex_data['Neighborhood'].value_counts()

# Sort neighborhoods based on their frequency
sorted_neighborhoods = neighborhood_counts.index

# Set the figure size
plt.figure(figsize=(10, 6))

# Create a bar plot using Seaborn with neighborhoods sorted by frequency
sns.barplot(x=neighborhood_counts.index, y=neighborhood_counts, color='#595f91', order=sorted_neighborhoods)

# Add a title to the plot
plt.title('Number of Houses in Each Neighborhood', fontsize=16)

# Set the x-axis label
plt.xticks(rotation=45, ha='right')

# Set the y-axis label
plt.ylabel('Number of Houses')

# Show the plot
plt.show()


```


    
![png](CW1_files/CW1_46_0.png)
    


We can understand that **North Ames**, **College Creek**, **Old Town**, **Edwards** and **Somerset** are among the popular neighborhoods with a lot of houses. This can be due to the fact that these are tight-knit or congested neighborhoods, or because they are very large neighborhoods of the town.

Next we will look at the Neighborhoods while considering their average sale prices. This will tell us which neighborhoods are expensive to live in and which ones are cheap.
To do this, we need to group our data by Neighborhood and compute the mean of the Sale Price. Then we can plot a bar chart to visualise the results.


```python
avg_price_by_nbr = ex_data[['SalePrice','Neighborhood']].groupby('Neighborhood').mean()
```


```python
# Calculate the average price by neighborhood
avg_price_by_nbr = ex_data.groupby('Neighborhood')['SalePrice'].mean().sort_values(ascending=False)

# Set the figure size
plt.figure(figsize=(10, 8))

# Create a bar plot using Seaborn with neighborhoods sorted by average price
sns.barplot(y=avg_price_by_nbr.index, x=avg_price_by_nbr, color='#595f91')

# Add a title to the plot
plt.title('Average Sale Price by Neighborhood', fontsize=16)

# Set the y-axis label
plt.ylabel('Neighborhood')

# Set the x-axis label
plt.xlabel('Average Sale Price')

# Show the plot
plt.show()

```


    
![png](CW1_files/CW1_50_0.png)
    


By looking at this chart, we can easily identify that neighborhoods like **Stone Brook, Northridge Heights, Northridge, Green Hills & Veenker** are more expensive. This can be due to the reasons that they are elite neighborhoods, or close to the town center or consist of big houses, or recently developed neighborhoods.

Now let's have a look at the correlations between our numerical variables: Sale Price, Living Area, Built Year and Overall Quality. First we will develop a correlation matrix and a heatmap to understand mutual correlations between the variables.


```python
corr_matrix = ex_data[['Gr Liv Area','Overall Qual','SalePrice','Year Built']].corr()
corr_matrix
```





  <div id="df-43847af3-8ee2-4ac8-8a33-1a30455c1aeb" class="colab-df-container">
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
      <th>Gr Liv Area</th>
      <th>Overall Qual</th>
      <th>SalePrice</th>
      <th>Year Built</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Gr Liv Area</th>
      <td>1.000000</td>
      <td>0.564797</td>
      <td>0.719463</td>
      <td>0.239305</td>
    </tr>
    <tr>
      <th>Overall Qual</th>
      <td>0.564797</td>
      <td>1.000000</td>
      <td>0.805236</td>
      <td>0.596621</td>
    </tr>
    <tr>
      <th>SalePrice</th>
      <td>0.719463</td>
      <td>0.805236</td>
      <td>1.000000</td>
      <td>0.565110</td>
    </tr>
    <tr>
      <th>Year Built</th>
      <td>0.239305</td>
      <td>0.596621</td>
      <td>0.565110</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>
    <div class="colab-df-buttons">

  <div class="colab-df-container">
    <button class="colab-df-convert" onclick="convertToInteractive('df-43847af3-8ee2-4ac8-8a33-1a30455c1aeb')"
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
        document.querySelector('#df-43847af3-8ee2-4ac8-8a33-1a30455c1aeb button.colab-df-convert');
      buttonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';

      async function convertToInteractive(key) {
        const element = document.querySelector('#df-43847af3-8ee2-4ac8-8a33-1a30455c1aeb');
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


<div id="df-a6fc1cf9-0001-46bb-9476-aedda60a1867">
  <button class="colab-df-quickchart" onclick="quickchart('df-a6fc1cf9-0001-46bb-9476-aedda60a1867')"
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
        document.querySelector('#df-a6fc1cf9-0001-46bb-9476-aedda60a1867 button');
      quickchartButtonEl.style.display =
        google.colab.kernel.accessAllowed ? 'block' : 'none';
    })();
  </script>
</div>
    </div>
  </div>





```python
# Create a heatmap for values in the correlation matrix that are greater than 0.5
# cmap specifies the color map for the heatmap, 'coolwarm' is used here
# annot=True adds the numeric values in each cell

sns.heatmap(corr_matrix[corr_matrix>0.5], cmap = 'coolwarm', annot = True)
```




    <Axes: >




    
![png](CW1_files/CW1_54_1.png)
    


All of these variables are highly correlated with the Sale Price, especially the Overall Quality and Living Area. Let's create some scatterplots to visualise these trends among these variables.
Here the Sale Price is graphed against the other 3 variables using a scatterplot to see the trend.


```python
# Create subplots with 2 rows and 2 columns
fig, axes = plt.subplots(nrows=3, ncols=1, figsize=(8,10))

# Flatten the axes for easier iteration
axes = axes.flatten()

# List of columns for which you want to create scatterplots
columns = ['Overall Qual', 'Year Built', 'Gr Liv Area']

# Loop through columns and create scatterplots
for i, column in enumerate(columns):
    sns.scatterplot(data=ex_data, x=column, y='SalePrice', color='#595f91', ax=axes[i])
    axes[i].set_title(f'Scatterplot of Sale Price vs {column}')
    axes[i].set_xlabel(column)
    axes[i].set_ylabel('Sale Price')

# Adjust layout to prevent overlap
plt.tight_layout()

# Show the plot
plt.show()

```


    
![png](CW1_files/CW1_56_0.png)
    


We can observe that these variables have a positive linear trend with the Sale Price which is expected as well as intuitive. These trends can be put into words as follows:

*  Higher the overall Quality of the house, the higher its Sales Price and vice versa. Houses in good quality and condition sell at a higher price naturally.

*  More modern houses are sold at a higher price because they are built recently and the material is less prone to degradation, requires less maintenance etc. Plus newly built houses are definitely more attractive, hence higher price.

*   The bigger the house, the more expensive it is. Houses like villas, mansions and bungalows are obviously going to be more costly than flats or terraced houses.





##CONCLUSION

###Key Findings
The process of performing the EDA started by ingesting the datasets, merging them and cleaning them along the way wherever appropriate and necessary by removing duplicates, outliers and missing values. Subsequently, the data was filtered and transformed after careful considerations. Although the dataset contained a huge number of variables, most of them were providing the same information from different angles. To deal with this, indicative variables which represented a good part of the data and provided meaning to the EDA were selected and analysed using visualisations and correlations.

The EDA has provided a good number of insights into the data that was provided. For instance, the Sale Price was a very powerful variable which was correlated with a number of other variables such as the Living Area (in square feet), the neighbourhood in which the house is located, the overall quality of the house and the year it was built. These important variables presented a healthy picture of the house market of the town and these variables are what any buyer would most probably look at before purchasing the property.

It was found that there are certain neighborhoods which are quite popular considering the number of houses, while some others are quite expensive when it come to the price parameter. Similarly, the houses built recently were found to be more expensive than older properties. A high-quality house was found to cost more, and a larger house also means a bigger price tag.



###Limitations & Recommendations

While performing the EDA, only two variables were investigated at a time. This limits the scope of the EDA and it becomes difficult to draw meaning. If more variables are explored together, such as inspecting the neighborhoods with their average prices and the number of houses built in each neighborhood over the years, it would allow a better understanding of the market and how it changes based on certain factors. Similarly, other variables such as number of bedrooms in the house and the quality of the material could also be included in the EDA to make it richer and more effective.

It really depends on the depth and breadth of the analysis which gives more meaning to it and discovers hidden information from it. Overall, it was a good analysis which considered a number of good parameters and generated some insights about them.
