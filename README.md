## Protein Predictor

Below are steps for executing the protein predictor baseline workflow on WINGS using the docker image

### Step 1
Will need [docker](https://www.docker.com/) installed.
Download and install the image by using this command.
```
docker pull arunima2/protein_predictor
```
Any help needed with getting started with the image on docker you can consult this [detailed how to start WINGS docker image tutorial here](https://dgarijo.github.io/Materials/Tutorials/wings-docker/#running-the-docker-image-). 

As mentioned in tutorial , you will need to run the docker image by downloading the start-wings.sh file and changing a few specifics like the image name etc. 

Once successfully started you can navigate to http://localhost:8080/wings-portal in order to start working with WINGS and the designing the workflow.

The credentials for the WINGS image are

Username:admin

Password:4dm1n!23

### Step 2 - Linear Predictor
The first of the two baselining workflows is `Protein_Predictor`. This performs basic linear modeling for prediction.

Input file (variable name = input_file): To be stored under data type `data_list` (sample is given), and it contains transcript values (one per line) for which prediction needs to be performed.

Model building parameter (variable name = model_param): A string parameter. Decides what initial data builds the model. Options- `NCI` or `CRC`. Either builds the predictor based on the NCI-60 dataset or Bing Zhang's Colorectal Cancer proteogenomic dataset. Different datasets with different types of dynamic ranges and normalization will achieve different predictions.

Data for model (variable name = model_data): To be stored under data type `RData_Linear`. Already provided (namely `model_lite`). This contains the different datasets used to build the model.

### Step 2 - Polynomial Predictor
The second of the two baselining workflows is `Protein_Predictor_polynomial`. This allows polynomial modeling.

Input file (variable name = input_file): To be stored under data type `data_list` (sample is given), and it contains transcript values (one per line) for which prediction needs to be performed.

Model building parameter (variable name = model_param): A string parameter. Decides what initial data builds the model. Options- `NCI` or `CRC` or `BRCA` or `NCICRC`. Either builds the predictor based on the NCI-60 dataset or Bing Zhang's Colorectal Cancer (CRC) proteogenomic dataset or TCGA Breast Cancer (BRCA) or the NCI-60 and CRC combined. Different datasets with different types of dynamic ranges and normalization will achieve different predictions.

Data for model (variable name = model_data): To be stored under data type `RData_Polynomial`. Already provided (namely `model`). This contains the different datasets used to build the model.

Type of modeling (variable name = model_type): A string parameter. This provides the various options for different types of polynomial modeling. Options- `l` or `poly2` or `poly3`. l denotes linear, poly2 is 2nd order polynomial and poly3 is third order polynomial.

### Step 3
Once the appropriate data is uploaded (under ***Manage Data***), a workflow can be run. Navigate to `Run Workflow`, enter the string parameters and select the relevant files, click `Plan Workflow`, select the on the left hand column and click `Run Selected Workflow`. The output file will contain the predicted protein values, in the same format as the input file, i.e one value per line.


