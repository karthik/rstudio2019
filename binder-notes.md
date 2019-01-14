![](https://mybinder.org/static/logo.svg?v=f9f0d927b67cc9dc99d788c822ca21c0)

# How to set up a My Binder for your R project

[My Binder](https://mybinder.org/) has had R support for about a year but it is getting better. When passed a Git repo (hosted on GitHub, Gitlab or from any arbitrary location), it will look for patterns (such as the presence of a DESCRIPTION file, `install.R` etc) and create a Dockerfile and start to build an instance from a pre-configured build pack (there is one for R projects and this is extensible to meet other needs).

## ⚙ Simplest  setup

For the simplest setup, you'll just need two files in your repo. 
- `runtime.txt` Here you can specify your R version by date (e.g. `r-2018-12-31`) and also versions of Python and Julia. In the case of R, this will also lock down CRAN packages to this R release (Rocker takes care of pulling packages from MRAN matching this date. You should specify the version based on a date:

- Select a MRAN date corresponding to your desired R version or just choose latest.  

|R version | MRAN date  | RStudio version | RStudio date |
|----------|------------|-----------------|--------------|
| 3.1.0    | 2014-09-17 | NA              | NA           |
| 3.2.0    | 2015-06-18 | NA              | NA           |
| 3.2.5    | 2016-05-03 | NA              | NA           |
| 3.3.0    | 2016-06-21 | NA              | NA           |
| 3.3.1    | 2016-10-31 | 1.0.44          | 2016-11-01   |
| 3.3.2    | 2017-03-06 | 1.0.136         | 2016-12-21   |
| 3.3.3    | 2017-04-21 | 1.0.143         | 2017-04-19   |
| 3.4.0    | 2017-06-30 | 1.0.143         | 2017-04-19   |
| 3.4.1    | 2017-09-28 | 1.0.153         | 2017-07-20   |
| 3.4.2    | 2017-11-30 | 1.1.383         | 2017-10-09   |
| 3.4.3    | 2017-03-15 | 1.1.442         | 2018-03-12   |
| 3.4.4    | 2018-04-23 | 1.1.447         | 2018-04-18   |
| 3.5.0    | 2018-07-02 | 1.1.447         | 2018-04-18   |
| 3.5.1    | 2018-12-20 | 1.1.463         | 2018-10-29   |
| 3.5.2    | latest     | latest          | latest       |

 [more information here](https://github.com/rocker-org/rocker-versioned/blob/master/VERSIONS.md).
- `install.R` A list of `install.packages('package_name')` commands, one per line.
- If you have non-R binaries you'd like installed, just add them to a file called `apt.txt` and those will be installed before these steps. You just need to name one per line (e.g. `openssl`).
- All of these files will need to be committed to the top level of your repo.s

You can now head to `mybinder.org`, paste in your URL, specify a branch if it is something other than master, and then build. There is also a badge you can copy into your README (`usethis` also has a `use_binder_badge()` function which can do this for you (it needs some updating, more below).

To launch a Rstudio server instead of a Jupyter notebook, you will need to append the URL with add `?urlpath=rstudio` after `/master/`

📉 **Downsides to this approach**

This is by far the slowest way to set up a binder. Depending on the packages you depend on (e.g. tidyverse)  it can take several hours (only for R packages) for the first image to be built and it may stall sometimes, requiring you to kick off a new build all over again.

## 🏇 A faster approach

A much faster approach is to include a Dockerfile. If mybinder detects one, it will skip over all other configuration methods and proceed to build your container. If using a Rocker image, you can also install additional package dependencies with [`installGithub.r`](https://github.com/eddelbuettel/littler/blob/master/inst/examples/installGithub.r) (the most concise way to install CRAN and GitHub packages; Comes bundled with rocker images).

You will need to gather dependencies in your scripts/notebooks. This can be done using helper functions (more notes on this here), or using packages like `Containerit` that will write a Dockerfile for you. 

I also prefer this approach because it provides an additional layer of usefulness for a user who may not want to use binder or Docker. For such users the `DESCRIPTION` file is a concise way to install the compendium locally.

### ⚠ Caution

*If your base Docker image does not include binder specific components, then you will not be able to launch Rstudio server (or even a Jupyter notebook). To prepare your Dockerfile for binder, read [this guide](https://mybinder.readthedocs.io/en/latest/tutorials/dockerfile.html#preparing-your-dockerfile). Binder will get through the setup but not launch an instance for you. My recommendation is to use the Rocker binder image as your base and then add other packages you need.*


## 🚀 Fastest and best recommendation for a compendium

- Create a minimal `DESCRIPTION` file for your project (TODO: more on this soon)
- Create a minimal Docker file that uses rocker/binder as base, copies files into your container and then uses `devtools`' `install_deps` to install everything from your binary. 

This will build the container on the first run (and cache after that assuming your Git repo does not accrue further commits) and launch quickly from then on.

### Limitations of mybinder
- Each instance is limited to 2 gb of RAM and will get destroyed after 10 minutes of inactivity. More on [memory issues](https://mybinder.readthedocs.io/en/latest/faq.html#how-much-memory-am-i-given-when-using-binder).
- Each instance can run for a maximum of 24 hours before it will get killed.
- You can get around these limitations by hosting your own binder hub but this will require compute + devops resources from your side. Read more at the [binder deployment guide](https://binderhub.readthedocs.io/en/latest/).
