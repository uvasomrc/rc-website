+++
type = "rivanna"
categories = [
  "HPC",
  "software",
  "viz"
]
date = "2019-06-22T08:37:46-05:00"
tags = [
  "multi-core",
]
draft = false
modulename = "fiji"
softwarename = "Fiji"
title = "Image Processing with Fiji on Rivanna"
author = "RC Staff"
+++

# Description
{{% module-description %}}
<br>
**Software Category:** {{% module-category %}}

For detailed information, visit the [{{% software-name %}} website]({{< module-homepage >}}).

# Available Versions
The current installation of {{% software-name %}} incorporates the most popular packages. To find the available versions and learn how to load them, run:

```
module spider {{< module-name >}}
```

The output of the command shows the available {{% software-name %}} module versions.

For detailed information about a particular {{% software-name %}} module, including how to load the module, run the `module spider` command with the module's full version label. __For example__:
```
module spider {{% module-firstversion %}}
```

{{< module-versions >}}


# Interactive Use of Fiji via FastX

We recommend to launch the Graphical User Interface (GUI) of Fiji as an interactive job via FastX.  These are the steps:

1. Create or connect to a FastX session via https://rivanna-desktop.hpc.virginia.edu. If you started a MATE desktop session, open a terminal window.

2. In the terminal window, start an ijob via this command:
```
ijob -p standard -A <YOUR_ALLOCTION> -c 8 --mem=32G -t 4:00:00
```
In this example we are requesting 8 cpu cores and 32GB of memory for 4 hours. Replace `<YOUR_ALLOCATION>` with your allocation account.

3. Load the `fiji` module and start the application: 

```
module load fiji
ImageJ-linux --mem=32G &
```

# Run a Fiji script as SLURM Job

To execute a Fiji script non-interactively on a compute node, you can use the following SLURM job script template.

```
#!/bin/bash
#SBATCH --job-name=fiji_example
#SBATCH --cpus-per-task=8
#SBATCH --mem=32G
#SBATCH --time=04:00:00
#SBATCH --partition=standard
#SBATCH --account=<YOUR_ALLOCATION>

#Load the Fiji Module
module load fiji

# Change to temp working directory with example files
ImageJ-linux --mem=32G --headless <FIJI_SCRIPT> <SCRIPT_ARGS>
```

* Adjust the `--cpus-per-task`, `--mem` and `--time` options as needed. Note that not all built-in Fiji functions or Fiji scripts are designed to utilize multiple cpu cores.
 
* Replace `<YOUR_ALLOCATION>` with your allocation account.

* Replace `<FIJI_SCRIPT>` and `<SCRIPT_ARGS>` with your custom Fiji script and add script arguments as required by the particular Fiji script.
