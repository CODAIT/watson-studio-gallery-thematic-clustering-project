The notebooks in this directory will be added to the WS Gallery project. A project **must** contain at least one notebook.

Notebook rules:
 - Name the noebook using this pattern: `Part X - short task description`, replacing `X` with a numeral, starting with 1. The user will be instructed to complete the notebooks in numerical order. Examples: `Part 1 - Data Cleaning`, `Part 2 - Data Analysis`
 - A notebook must include a description. When you save a notebook in Watson Studio the description is not persisted in the `.ipynb` file. You must store each notebook description in a separate file. For example, store the description for a notebook `Part 1 - Data Cleaning.ipynb` in a file named `Part 1 - Data Cleaning.description` in the `/notebooks` directory.
 - A notebook must be associated with the **Default Python 3.6 Free ...** environment.
 - The notebook's output cells must be cleared. (`cell` > `all output` > `clear`)
 - **Remember** to delete any cells that contain **sensitive data** (in particular the Project token or Cloud Object Storage credentials).

