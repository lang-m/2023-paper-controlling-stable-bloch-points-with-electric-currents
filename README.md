# Controlling stable Bloch points with electric currents

This repository provides Jupyter Notebooks and pre-computed data to re-run all simulations and reproduce all figures from:

> Martin Lang, Swapneel Amit Pathak, Samuel J. R. Holt, Marijan Beg and Hans Fangohr. Controlling stable Bloch points with electric currents. \<arXiv> (2023)

Repository DOI: \<DOI>

## Reproduce results

Notebooks are grouped in individual subdirectories per (set of) figure(s). Data
generation and plotting is separated into individual notebooks, they are ordered
in the correct execution order. Preprocessed data is available so that
re-creating the figures is possible by only running notebooks with
`Fig-<number>` in the name.

## Execution in the cloud

Jupyter Notebooks hosted in this repository can be executed and modified in the cloud via Binder. This does not require you to have anything installed and no files will be created on your machine. To access Binder, click on the Binder badge below.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/lang-m/2023-paper-controlling-stable-bloch-points-with-electric-currents/HEAD)

The notebook for Figure 1 (requires pyvista) currently does not run on Binder.

## Install required software locally

All required software can be install using conda. We propose creating a
new environment that will contain all required software by using the following
command:

```
conda env create -f environment.yml
```

This repository contains some additional utility functionality in the `simtools`
subdirectory. Where required, the notebooks will import this extra functionality.

## Execution in a Docker container

This repository also contains a [Dockerfile](docker/Dockerfile) to create the required software environment in a container. The container will also automatically run all notebooks that reproduce figures. Figures are not automatically transferred back to the host system.

## License

Licensed under the BSD 3-Clause "New" or "Revised" License. For details, please
refer to the [LICENSE](LICENSE) file.


## Acknowlegdements

- EPSRC Programme Grant on Skyrmionics (EP/N032128/1)
- The [OpenDreamKit](https://opendreamkit.org/index.html) Horizon 2020 European Research Infrastructures
project (\#676541) has contributed to the [Ubermag](https://ubermag.github.io) software, which was used heavily in
this work.
