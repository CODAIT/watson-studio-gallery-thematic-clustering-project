# Watson Studio Gallery project for the IBM Debater® Thematic Clustering of Sentences data set

DAX data set URL: https://developer.ibm.com/exchanges/data/all/thematic-clustering-of-sentences/

## Getting started

- Open https://github.com/CODAIT/watson-studio-gallery-dax-project-template
- Click **Use this template** and create a new dataset project repository in https://github.com/CODAIT/ naming it `watson-studio-gallery-XXX-project`  replacing `XXX` with the data set short name.
- Create an issue in https://github.com/CODAIT/DAX-Datasets/issues/new/choose tracking development/publication progress
- Add a link to the newly created project in this [status document](https://github.ibm.com/CODAIT/DAX-Datasets/blob/master/OWNERS.md).
- Review the content of this sample project https://dataplatform.cloud.ibm.com/exchange/public/entry/view/a7432f0c29c5bda2fb42749f363bd9ff to familiarize yourself with the typical content of a DAX project:
  - Description
  - README
  - Data assets
  - Notebooks
  
  > The source for this project is located here: https://github.ibm.com/CODAIT/watson-studio-gallery-dax-weather-project

## Prepare for notebook development in Watson Studio

This is a one-time setup of your "development" environment. (Most notebooks will use a proprietary Watson Studio package to load and store data files. Therefore notebook development should not be performed in a local Jupyter environment.)

### Prepare the data set files

1. Download the compressed data set archive (`.tar.gz`) from Cloud Object Storage into a temporary directory.
1. Extract the archive.
1. If the data files are not of type `.csv` DO NOT PROCEED.

### Prepare the Watson Studio development project

1. [Log in to Watson Studio and create an empty project](https://dataplatform.cloud.ibm.com/projects/new-project?context=wdp).
   - Choose meaningful name
   - Add a short project description.
   - Uncheck `Restrict who can be a collaborator`
1. Add a project token.
   - Click **Settings**.
   - Add an **Access token** (any name, role must be **Editor**).
1. Add the extracted (raw) data set files.   
   - Click **Assets**.
   - Click **Add to project** > **Data** and add each raw data set file (e.g. `.csv`) to the project.
1. Try to export the data assets. If an error is raised because the archive is larger than 500MB, use the `Part 0 - Import Data.ipynb` notebook. Customize the notebook as follows:
   - Change the `dataset_download_url` 
   - Change the `data_path_name`. 
   - In the last code cell, customize the `if file.suffix != '.tgz':` filter as needed if the extracted archive contains files that should not be added as data assets.
   
## Notebook development instructions

Review the notebook development instructions in [`/notebooks`](/notebooks).

1. Add new notebooks ("from file") to the project using the `template-notebook.ipynb` in `/notebooks`.
1. Before saving the notebook in GHE make sure to complete the following steps in Watso Studio:
   - remove the first cell, which should look as follows
     ```
     # @hidden_cell
     # The project token is an authorization token that is used to access project resources like data sources, connections, and used by platform APIs.
     from project_lib import Project
     project = Project(project_id='4...', project_access_token='p...')
     pc = project.project_context
     ```
    > This cell is automatically inserted when a user imports the project from the Watson Studio gallery. The project id and token are different for every user and every project instance and the content that works for you will not work for another user.
   - clear all output cells
   
### Review notebooks using ReviewNB tool

We use [`ReviewNB`](https://www.reviewnb.com/) to better visualize updates to notebooks in Github. Due to several restrictions with using this tool, this is the process for getting notebook's ready to review:

1. Create a new repository in [github.com/codait](github.com/codait) if you are migrating the project from Github Enterprise.
   - Make the repository private.
   - Copy in all of the files created thus far in the project's Github Enterprise repository (we are only able to use the public Github version of [`ReviewNB`](https://www.reviewnb.com/) at this time, hence the need for this step).
2. Add a branch called `production` to the new repository.
   - In the repository's `Settings/Branches` page, make the `production` branch the default (base) branch (Watson Studio currently can only push commits directly to the `master` branch of a repository, hence the need for this step).
3. Make sure you are assigned the `Admin` role in the Watson Studio project that you will push code to Github from:
   - If you are not assigned this role yet, you can have a current `Admin` grant you this privilege. 
4. If your Watson Studio account does not yet have Github integration setup with your public Github account:
   - Add a Github personal access token in Watson Studio's [`Settings/Integration`](https://dataplatform.cloud.ibm.com/settings/integrations) page. 
   - You can create this token by visiting your public Github's [`Settings/Developer settings/Personal access tokens`](https://github.com/settings/tokens) page and clicking `Generate new token`. Make sure to give the token repo scope. 
5. Inside of the Watson Studio project's `Settings` page:
   - Scroll to the `Integrations/Github repository` section and add the link to the new Github repository you created to which you will push your code.  
6. Now you are able to push commits to the `master` branch of the new repository you created. 
   - To push a commit, open a notebook in edit mode, click the `Github integration` button in the top menu bar, click `Publish on Github`. 
   - In the dialogue box, ensure the target path points to `./notebooks/your_target_notebook.ipynb`, add a commit message, select `All content except hidden code cells`, and click `Publish`. 
   - Follow this set of steps every time you need to make a commit.
7. Once you are ready for your notebook to be reviewed: 
   - Open a PR from the `master` branch against the `production` branch. 
   - Within this PR, `ReviewNB` will automatically add a button to `Check out this pull request on  ReviewNB`. 
   - Make sure `ReviewNB` is an Authorized Github App in your Github account's [`Settings/Applications/Authorized Github Apps`](https://github.com/settings/apps/authorizations) page to be able to use the tool to add comments and code suggestions to individual cells of a notebook. 


## Source control instructions

Use this github repository to store all the artifacts that will be used to create the Watson Studio project for this data set.

- Copy the raw data set files into `/data_assets` following the instructions in [/data_assets](/data_assets).
- Copy the downloaded notebook files into `/notebooks` following the instructions in [/notebooks](/notebooks).
- Customize the metadata files in `/metadata` following the instructions in [/metadata](/metadata).
- Complete the legal documents in `/legal` following the instructions in [/legal](/legal).


## Packaging instructions

1. Follow the packaging instructions in [dist](dist/). 

## Publication instructions

1. Make sure you have completed the packaging instructions.
1. Complete the [notebook publication checklist](https://github.ibm.com/CODAIT/watson-studio-gallery-dax-project-template/blob/master/legal/Watson%20Studio%20Legal%20Checklist%20-%20notebook_tutorial%20(updt%20May%2030%2C2018).docx) for **each** notebook.
   * In the checklist document add a (company-wide readable) link to the completed data set publication **approval request form**.
   * In the checklist document add a (company-wide readable) link to the data set publication **approval**. 
   * Save a copy of each completed document in the [`legal`](legal/) directory.
1. Send an email to @gdq:
   * **subject**: Publication approval request for DAX/[insert-dataset-name] notebooks  
   * **recipient**: `gdq@ibm.com`
   * **cc**: `Ashley.Zhao@ibm.com`
   * **body**:
      * `Requesting your approval to publish and license the following notebooks, including its source code under the terms of the MIT license.`
      * for each notebook
        * include a link to the corresponding file in the source GH repository
        * attach the completed publication checklist
      * include a link to the data set's legal approval request form
      * include a link to the data set's legal approval document

1. Once the request was approved the content team will work with the legal team to require clearance for the notebooks.
1. ...
