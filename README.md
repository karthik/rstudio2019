# How To Make Your Data Analysis Notebooks More Reproducible

![rstudio_talk_slides](https://i.imgur.com/fYGze6k.png)

Slide deck (link TBD) | Slide deck as PDF (link TBD)

## Resources
I have included a handful of links to papers, software packages and tutorials/manuals about some tools I mention in my talk. Pull requests or issues on additional ones to include are welcome.

### Research Compendia

- [Statistical Analysis and reproducible research ](https://biostats.bepress.com/bioconductor/paper2/)
- [Packaging Data Analytical Work Reproducibly Using R (and Friends)](https://www.tandfonline.com/doi/abs/10.1080/00031305.2017.1375986) ([OA preprint](https://peerj.com/preprints/3192/)). A practical introduction to setting up a research compendium in R. 
- [The rOpenSci reproducibility guide](https://ropensci.github.io/reproducibility-guide/) *Slightly dated but still very useful*

**Examples of Research Compendia on GitHub**
Below are a few links to real world examples of research compendia in R. To have a minimal compendium, all you really need is a valid [`DESCRIPTION`](https://github.com/boettiger-lab/pomdp-intro/blob/master/DESCRIPTION) file containing a handful of fields such as type, name, version and dependencies. See Marwick et al 2017 for a detailed description of the different types of compendia.

**Small**
- [Code and data associated with Duffy, James, and Longworth Applied and Environmental Microbiology paper describing the ecology, virulence, and phylogeny of a brood parasite of Daphnia, Blastulidium paedophthorum;](https://github.com/duffymeg/BroodParasiteDescription)
 
**Medium**
- [Resolving the measurement uncertainty paradox in ecological management](https://github.com/boettiger-lab/pomdp-intro)

**Large**

- [Non-parametric Bayesian Inference for Conservation Decisions ](https://github.com/cboettig/nonparametric-bayes)

- Find various other compendia on [Github](https://github.com/topics/research-compendium) and [Zenodo](https://zenodo.org/communities/research-compendium?page=1&size=20) using the `research-compendium` tag.

**Software packages related to research compendia**

- [`rrtools`](https://github.com/benmarwick/rrtools)  *extends functions in `devtools` and provides instructions, templates, and functions to make a basic compendium suitable for doing reproducible research with R.* 
- [`usethis`](https://github.com/r-lib/usethis) *Many of the major function in `rrtools` are imported from `usethis.` A savvy user can get by setting up and maintaining a compendium purely with `usethis` functions.*
- [`goodpractice`](https://github.com/MangoTheCat/goodpractice) - Designed to help you build more robust packages, the package does a deep dive on your package contents and provide advice on syntax pitfalls to avoid, code formatting suggestions, and helps you improve overall package structure.
- The [`rticles`](https://github.com/rstudio/rticles) package by JJ has numerous journal templates and together with Rstudio addins like word [`countaddin` ](https://github.com/benmarwick/wordcountaddin)and [`citr`](https://github.com/crsh/citr) + [`knitcitations`](https://github.com/cboettig/knitcitations).
 

### 📈 Data management 

- [`piggyback`](https://github.com/ropensci/piggyback), [[docs]](https://ropensci.github.io/piggyback/):  This clever R package allows you to attach arbitrary data (or other) files (upto 2gb each) to a GitHub release. Given GitHub's fast CDN, this would be an easy way to quickly attach large files to a compendium and read them back in a local/collaborator/remote environment very easily. As always be sure to archive a long-term copy on [Zenodo](https://zenodo.org/).
- [`arkdb`](https://github.com/ropensci/arkdb) [[docs]](https://ropensci.github.io/arkdb/):  This package allows you to archive and unarchive databases as flat text files.

### Computational environments: Binder and friends

- [My Binder](https://mybinder.org/) - Turns any Git repo into a collection of interactive notebooks. Now with R support!
- [Introducing Binder 2.0 — share your interactive research environment](https://elifesciences.org/labs/8653a61d/introducing-binder-2-0-share-your-interactive-research-environment) Paper describing the architecture of Binder in case you were interested in what was happening under the hood
- 🎥 [A talk about Binder at Scipy 2018](https://www.youtube.com/watch?v=KcC0W5LP9GM). Also see [conference proceedings PDF](http://conference.scipy.org/proceedings/scipy2018/pdfs/project_jupyter.pdf).
- [`repo2docker`](https://github.com/jupyter/repo2docker) A Python module that will turn any repo (or local folder) into a Docker Image.  

**Other hosted Binder hubs**

- [Pangeo binder](https://binder.pangeo.io/) Pangeo encourages others to use it.
- [gesis](https://notebooks.gesis.org/)
- [Syzgy](http://syzygy.ca/) Binder + JupyterHub for Compute Canada

Are you interested in setting up or hosting a binder for the R community? Get in touch via the issues.


**Also see**
- [Whole Tale](https://wholetale.org/) 
- [Computing environments for reproducibility: Capturing the “Whole Tale”](https://www.sciencedirect.com/science/article/pii/S0167739X17310695) - OA paper describing the Whole Tale project.
- [Code Ocean](https://codeocean.com/) - A commercial, blackbox, full-stack service that will accomplish something similar to the above two projects. Code Ocean links will likely start appearing in papers soon.


**Software packages related to setting up computational environments**

- [`Containerit`](https://github.com/o2r-project/containerit)
- [Stevedore: Docker client for R](https://github.com/richfitz/stevedore)
- 

### 🔨 Workflows: Drake and friends

- [`Drake`](https://github.com/ropensci/drake) - An R-focused pipeline toolkit for reproducibility and high-performance computing. Install the package from here or CRAN.
- [The prequel to the drake R package](https://ropensci.org/blog/2018/02/06/drake/) *A blog post by the creator of Drake describing his motivation for the package.*
- [Drake manual](https://ropenscilabs.github.io/drake-manual/) A detailed `bookdown` guide on how to setup and use Drake for projects of varying levels of complexity.
- [Presentation on Drake](https://wlandau.github.io/drake-datafest-2019/#/) Slides from a talk by Will Landau.

**Real world Drake examples**
- [Pathogen modeling study](https://github.com/pat-s/pathogen-modeling)

---

### Acknowledgments

Many thanks to [Chris Holdgraf](https://bids.berkeley.edu/people/chris-holdgraf), [Carl Boettiger](https://www.carlboettiger.info/), [Will Landau](https://wlandau.github.io/), and [Ben Marwick](http://faculty.washington.edu/bmarwick/) for various discussions on these topics. Also thanks to Ciera Martinez and Nick Tierney for comments on the presentation. 

