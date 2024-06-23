---
title: Python and Jupyter Notebook on HiPerGator
summary: This guide provides detailed instructions on how to access and use Jupyter Notebooks on HiPerGator, as well as how to manage Python environments effectively.
weight: 3
---

## Jupyter Notebook

### Starting and Connecting to Jupyter Notebooks

Jupyter Notebooks offer a flexible, web-based development environment ideal for coding, visualization, and teaching. Here's how to start using Jupyter Notebooks on HiPerGator:
- **JupyterHub**: The simplest option, allowing you to start a Jupyter Lab server with just a few clicks. Choose your resources from a dropdown menu.
- **Jupyter via Open On Demand**: Offers more customization than JupyterHub, allowing for specific resource requests and group selections.
- **Batch Job Submission**: For advanced users, connect to a Jupyter session through SSH tunnels after submitting a batch job.

### Accessing Blue and Orange Directories

By default, Jupyter can only access your home directory. To access other directories like `/blue` or `/orange`, we need to create symbolic links using the following commands in the terminal:
```bash
# Open a terminal in Jupyter
# Retrive group id
id
# uid=12345(agator) gid=12345(gator-group) groups=12345(gator-group),12346(orange-group),12347(blue-group)
# Change directories to your home directory and create symbolic links to group directories for easier access
cd
ln -s /blue/gator-group blue_gator-group/
ln -s /orange/gator-group orange_gator-group/
```
Replace `gator-group` with your actual group id retrived using `id`. The links will appear in your JupyterLab home directory now.

## Managing Python Environment on HiPerGator

### Using Existing Python Kernels
1. Load the conda module via:
```module load conda```

2. Activate the environment:
```conda activate your_environment_name```

### Creating and Managing Jupyter Kernels
Create custom Jupyter kernels to use with your projects:
```bash
# Navigate to the Jupyter kernels directory
cd ~/.local/share/jupyter/kernels

# Copy a template kernel
cp -r /apps/jupyterhub/template_kernel/ your_kernel_name

# Edit the kernel configuration
nano your_kernel_name/kernel.json
```
Adjust the `kernel.json` to point to your Python executable and specify other configurations as needed.

### Using Containers in Open On Demand
To run Jupyter within a container environment:

1.Load the `conda` module with:
```
module load conda
```
2.Create python environment with:
```
mamba create -n your_env_name
```
3.Install the `jupyterlab` package with:
```
mamba install jupyterlab
```
4.Prepare the kernel:
```
cp -r /apps/jupyterhub/template_kernel/ ~/.local/share/jupyter/kernels/your_env_name
nano ~/.local/share/jupyter/kernels/your_env_name/kernel.json
```
5.Configure the kernel to use your container by first open `kernel.json`:
```
nano ~/.local/share/jupyter/kernels/your_env_name/kernel.json
```
Modify the `kernel.json` file as below:
```
{
 "language": "python",
 "display_name": "DISPLAY_YOUR_ENV_NAME",
 "argv": [
  "~/.local/share/jupyter/kernels/your_env_name/run.sh",
  "-f",
  "{connection_file}"
 ]
}
```
Next, edit the `run.sh` file by first open `run.sh` with
```
nano ~/.local/share/jupyter/kernels/hfrl/run.sh
``` 
The file looks like:
```
#!/usr/bin/bash
CONTAINER=/route/to/your/containers/example.sif 

singularity exec --cleanenv $CONTAINER \
	python -m ipykernel "$@"
```
You need to modify it by replacing the `/route/to/your/containers/example.sif` with the location of your container file.

6.Refresh or start JupyterLab via OOD and you will be able to select your custom environment.


### Clearing Jupyter Notebook Outputs

Before sharing your Jupyter notebooks on GitHub or other platforms, it's important to clear the output to keep the repository clean and to prevent the accidental sharing of sensitive data displayed in outputs. You can clear outputs both from the Jupyter notebook interface and via the command line.

- **Using the Jupyter Notebook Interface**:
To clear outputs using the Jupyter Notebook toolbar:
    1. Open your Jupyter notebook.
    2. Navigate to the top menu and select `Kernel`.
    3. Click on `Restart Kernel & Clear All Outputs`.

This will restart the notebook's kernel and remove all outputs from the notebook, ensuring that only the code and markdown cells remain. Alternatively, if you do not wish to restart the kernel, you can clear the output by navigating to `Edit` in the top menu and clicking on `Clear All Outputs`. 

- **Using the Command Line**: For a command-line approach, particularly useful for automating the process or clearing multiple notebooks at once, you can use the `nbconvert` tool:
```bash
jupyter nbconvert --ClearOutputPreprocessor.enabled=True --inplace your_notebook.ipynb
```

### Exporting Notebooks as Executable Scripts

Notebooks are a great method for testing and development, but can be cumbersome when it comes to production runs. It is simple to export a Jupyter Notebook as an executable script (.py file for example).
```
Select File > Export Notebook As... > Export Notebook to Executable Script.
```
You can also export notebooks as PDFs, HTML and other formats.

