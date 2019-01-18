# How To Make Your Data Analysis Notebooks More Reproducible

[![rstudio_talk_slides](https://i.imgur.com/fYGze6k.png)](http://inundata.org/talks/rstd19/#/)

[Slide deck](http://inundata.org/talks/rstd19/#/) | Slide deck as [PDF](https://github.com/karthik/rstudio2019/blob/master/reproducible-data-analysis.pdf) 

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

- 📦 [`rrtools`](https://github.com/benmarwick/rrtools)  by Ben Marwick (also the author of the packaging data analysis paper mentioned above) *extends functions in `devtools` and provides instructions, templates, and functions to make a basic compendium suitable for doing reproducible research with R.* 
	- Also see 📦 [workflowr](https://jdblischak.github.io/workflowr/) by John Blischak and the [task view](https://github.com/jdblischak/ctv-project-workflows) on R-based data analysis projects maintained by John Blischak, Anna Krystalli, Ben Marwick, Daniel Nüst.
- 📦 [`usethis`](https://github.com/r-lib/usethis) *Many of the major function in `rrtools` are imported from `usethis.` A savvy user can get by setting up and maintaining a compendium purely with `usethis` functions.*
- 📦 [`goodpractice`](https://github.com/MangoTheCat/goodpractice) - Designed to help you build more robust packages, the package does a deep dive on your package contents and provide advice on syntax pitfalls to avoid, code formatting suggestions, and helps you improve overall package structure.
- The 📦 [`rticles`](https://github.com/rstudio/rticles) package by JJ has numerous journal templates and together with Rstudio addins like word [`countaddin` ](https://github.com/benmarwick/wordcountaddin)and [`citr`](https://github.com/crsh/citr) + [`knitcitations`](https://github.com/cboettig/knitcitations).
 

### 📈 Data management 

- 📦 [`piggyback`](https://github.com/ropensci/piggyback), [[docs]](https://ropensci.github.io/piggyback/):  This clever R package allows you to attach arbitrary data (or other) files (upto 2gb each) to a GitHub release. Given GitHub's fast [CDN](https://en.wikipedia.org/wiki/Content_delivery_network), this would be an easy way to quickly attach large files to a compendium and read them back in a local/collaborator/remote environment very easily. As always be sure to archive a long-term copy on [Zenodo](https://zenodo.org/).
- 📦 [`arkdb`](https://github.com/ropensci/arkdb) [[docs]](https://ropensci.github.io/arkdb/):  This package allows you to archive and unarchive databases as flat text files.
-  🎥 For more on setting up data packages, see this [excellent talk by Noam Ross](https://www.youtube.com/watch?v=zsEsh5QpN0U) at New York R.

### Computational environments: Binder and friends

- [My Binder](https://mybinder.org/) is a free binderhub deployment that turns any Git repo into a collection of interactive notebooks. Now with better R support!
- For instructions on how to set this up for your R project, see [my notes here](https://github.com/karthik/rstudio2019/blob/master/binder-notes.md)
- [Introducing Binder 2.0 — share your interactive research environment](https://elifesciences.org/labs/8653a61d/introducing-binder-2-0-share-your-interactive-research-environment) Paper describing the architecture of Binder in case you were interested in what was happening under the hood
- 🎥 [A talk about Binder at Scipy 2018](https://www.youtube.com/watch?v=KcC0W5LP9GM). Also see [conference proceedings PDF](http://conference.scipy.org/proceedings/scipy2018/pdfs/project_jupyter.pdf).
- [`repo2docker`](https://github.com/jupyter/repo2docker) A Python module that will turn any repo (or local folder) into a Docker Image.  

**Other hosted Binder hubs**

- [Pangeo binder](https://binder.pangeo.io/) *Pangeo encourages everyone to use it.*
- [gesis](https://notebooks.gesis.org/)
- [Syzgy](http://syzygy.ca/) *Binder + JupyterHub for Compute Canada*

**Setting up Binder for your analysis**

I have captured all the various ways to set up mybinder with a R project in a [separate document](binder-notes.md). 

Are you interested in setting up or hosting a binderhub for the R community? Get in touch via the issues.


**Also see**
- [Whole Tale](https://wholetale.org/) 
- [Computing environments for reproducibility: Capturing the “Whole Tale”](https://www.sciencedirect.com/science/article/pii/S0167739X17310695) - OA paper describing the Whole Tale project.
- [Code Ocean](https://codeocean.com/) - A commercial, blackbox, full-stack service that will accomplish something similar to the above two projects. Code Ocean links will likely start appearing in papers soon.


**Software packages related to setting up computational environments**

- 📦 [`Containerit`](https://github.com/o2r-project/containerit). [Detailed blog post](https://o2r.info/2017/05/30/containerit-package/) This sweet package will generate a Dockerfile for you by examining the code inside a folder or just from your session info. This is analogous to `repo2docker` but is very R centric
- [`stevedore`](https://github.com/richfitz/stevedore) Although there are a few docker clients (docker, harbor), this is my recommendation for managing docker containers from inside R. 


### 🔨 Workflows: drake and friends

- 📦 [`drake`](https://github.com/ropensci/drake) - An R-focused pipeline toolkit for reproducibility and high-performance computing. Install the package from here or CRAN.
- [The prequel to the drake R package](https://ropensci.org/blog/2018/02/06/drake/) *A blog post by the creator of drake describing his motivation for the package.*
- [drake manual](https://ropenscilabs.github.io/drake-manual/) A detailed `bookdown` guide on how to setup and use drake for projects of varying levels of complexity.
- [Presentation on drake](https://wlandau.github.io/drake-datafest-2019/#/) Slides from a talk by Will Landau (who is here at the conference so go pick his brain if you want to learn more!)

**Real world drake examples**
- [Pathogen modeling study](https://github.com/pat-s/pathogen-modeling)

**Miscellaneous**
- IKEA diagram inspired by [IDEA instructions](https://idea-instructions.com/)

---

### Acknowledgments

Many thanks to [Chris Holdgraf](https://bids.berkeley.edu/people/chris-holdgraf), [Carl Boettiger](https://www.carlboettiger.info/), [Will Landau](https://wlandau.github.io/), and [Ben Marwick](http://faculty.washington.edu/bmarwick/) for various discussions on these topics. Also thanks to Ciera Martinez, Kara Woo, and Nick Tierney for comments on the presentation. 

