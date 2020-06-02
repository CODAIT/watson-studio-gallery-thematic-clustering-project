This directory contains the packaged Watson Studio project ZIP file along with any other information required for formal publication.

## Packaging instructions

1. [Log in to Watson Studio and create an empty project](https://dataplatform.cloud.ibm.com/projects/new-project?context=wdp).
   - Choose meaningful name
   - As description paste the customized content from [`metadata/project_description`](/metadata/project_description.md)
   - Uncheck `Restrict who can be a collaborator`
1. In the _Overview_ tab edit the project `Readme`.
   - Paste the content of [your customized project readme](/metadata/project_readme.md).
1. In the _Assets_ tab add every notebook from the [`notebooks` directory](/notebooks) to the project.
   - Choose _Notebook from File_.
   - As notebook name enter the notebook's file name.
   - Add the notebooks' description from the notebook's `.description` file. 
   - Associate the `Default Python 3.6 Free ...` environment with the notebook.
1. In the _Assets_ tab add every data file from the [`data_assets` directory](/data_assets) to the project.
   - If a data file is compressed decompress it before adding it as a data asset.  
1. Export the project to the desktop.

## Validation instructions

1. Import the exported project from the generated ZIP file.
1. Verify the readme content.
1. verify that all notebook output cells are empty.
1. Verify that the notebook does not contain any hidden cells.
1. Verify that each notebook works as expected.

## Publication instructions
1. Add the validated exported project archive to the `dist` directory on GitHub.

The uploaded archive will be used by the content team to publish the project in the Watson Studio Gallery.

## Notebook preview instructions

We publish previews of the completed notebooks in Cloud Object Storage and link to them from the data set's landing page. Follow the instructions in https://github.ibm.com/CODAIT/DAX-notebook-previewer to generate the assets. Once you've completed the process, copy the `.html` files and `.json` file into this `dist` directory. The preview files need to be refreshed if a notebook is changed or when a notebook is added.
