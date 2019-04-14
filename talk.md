class: middle, center, title-slide
count: false

# Containers for
# Machine Learning in HEP

Matthew Feickert<br>
[matthew.feickert@cern.ch](mailto:matthew.feickert@cern.ch)

[3rd IML Machine Learning Workshop](https://indico.cern.ch/event/766872/contributions/3357988/)

April 16th, 2019

---
# Talk Notes for Lukas and Dan

<br><br>

- INDICO page: https://indico.cern.ch/event/766872/contributions/3357988/
- Talk time window: _20_ minutes
   - Presentation time: _17_ minutes
   - Question time: _3_ minutes
- Talk Goals:
   - Motivate and introduce applications of containers on GRID for ML
   - 1st half: Lukas et.al work in Containers + GRID
   - 2nd half: Matthew and Dan work on AML base images

---
# Collaborators

<br><br>

.grid[
.kol-1-2.center[
<!-- .circle.width-80[![Lukas](https://avatars1.githubusercontent.com/u/2318083?s=400&v=4)] -->
.center.circle.width-80[![Lukas](figures/collaborators/heinrich.jpg)]

[Lukas Heinrich](https://github.com/lukasheinrich)

NYU
]

<!-- https://www.weizmann.ac.il/conferences/SRitp/Summer2017/sites/conferences.SRitp.Summer2017/files/styles/gallery_full_image/public/dsc07727.jpg?itok=Z6VbTmy9 -->
.kol-1-2.center[
.center.circle.width-70[![Dan](figures/collaborators/guest.png)]
<!-- .circle.width-80[![Dan](https://avatars3.githubusercontent.com/u/1979581?s=400&v=4)] -->
<!-- .center.circle.width-80[![Dan](figures/collaborators/guest_2.png)] -->
<!-- .center.circle.width-70[![Dan](figures/collaborators/guest_3.png)] -->

[Dan Guest](https://github.com/dguest)

UC Irvine
]
]

<!-- https://indico.cern.ch/event/708041/contributions/3276174/attachments/1810633/2956920/ATL-SOFT-SLIDE-2019-073.pdf#page=2 -->
---
# Current HEP Computation

<br><br>

.grid[
.kol-1-2[
<br>
- Highly parallelizable
- Good for distributed, bulk computation
- Worldwide LHC Computing Grid provides global infrastructure
   - Storage and compute
   - _Code goes to where the data is_
]
.kol-1-2[
.center.width-100[![WLCG_logo](figures/WLCG_logo.png)]
]
]

<!-- https://indico.cern.ch/event/708041/contributions/3276174/attachments/1810633/2956920/ATL-SOFT-SLIDE-2019-073.pdf#page=2 -->
<!-- https://indico.cern.ch/event/791372/contributions/3286861/attachments/1783932/2903509/AML_Containers_Grid.pdf#page=3 -->
---
# Problem: Software Distribution

- Need to get the _runtime environment_ to data location
- Breakdown of typical software stack  

.width-100[![software_stack](figures/software_stack.png)]

- Relies on three parties to work (sys admins, experiments, users)
- Great for distributing crucial software, not for experimenting with new tools

---
# Containers
.grid[
.kol-2-3[
<br>
- ML needs are challenge for current system
   - moves fast
   - experiments with bleeding edge tools
   - non-traditional HEP stack developed by industry
- Idea: Distribute software stack with .blue[containers]
   - let the user assemble the full stack and optimize GRID for running containers
]
.kol-1-3.center[
.center.width-50[![Docker](https://www.linuxjournal.com/sites/default/files/styles/max_650x650/public/u%5Buid%5D/12282f3.png)]
<!-- .width-40[![Tensorflow](figures/logos/Tensorflow_logo.svg)] -->

.center.width-50[![Singularity](https://singularity.lbl.gov/images/logo/logo.svg)]
<!-- .width-100[![PyTorch](figures/logos/pytorch-logo-dark.svg)] -->
]
]

.center.width-100[![container_view](figures/container_view.png)]
.center[Docker Image (think: executable filesystem snapshot)]

<!-- https://indico.cern.ch/event/791372/contributions/3286861/attachments/1783932/2903509/AML_Containers_Grid.pdf -->
---
# Containers for ML

- ML applications currently one area that can realistically and usefully utilize hardware accelerators (GPUs)
- New HPC machines coming online ability to support HEP workloads
- Use of GPU requires _custom compiled software_
   - Example. TensorFlow GPU with CUDA
- With containers this is plug and play compute!

.center.width-100[![container_with_GPU](figures/container_with_GPU.png)]

---
# Containers for Physics

.grid[
.kol-1-2[
- With containers can run large-scale jobs on WLCG infrastructure
   - hyperparameter scans
   - flavour tagging retraining

<br>

.center.width-100[![hyperparameter_ROC](figures/hyperparameter_ROC.png)]
.left[Flavour taggigng ROC for hyperpameter scans [[A. C. Forti, L. Heinrich, M. Guth, ACAT 2019](https://cds.cern.ch/record/2665661?ln=en)]]
]
.kol-1-2[
.center.width-90[![Lukas_tweet](figures/Lukas_tweet.png)]
.center[[@lukasheinrich_](https://twitter.com/lukasheinrich_/status/1066055036197892098/photo/1)]
]
]

---
# Containers for Physics

<br>

.center.width-100[![btagging_GRID_job](figures/btagging_GRID_job.jpg)]
.center[Flavour tagging hyperpameters scans on the GRID in container]

<br>

.center.width-90[![btagging_prun_command](figures/btagging_prun_command.jpg)]
.center[Submitted to GPU site at Manchester]

<!-- https://indico.cern.ch/event/708041/contributions/3276174/attachments/1810633/2956920/ATL-SOFT-SLIDE-2019-073.pdf#page=13 -->
<!-- https://carbon.now.sh/?bg=rgba(255%2C255%2C255%2C1)&t=seti&wt=none&l=application%2Fx-sh&ds=false&dsyoff=20px&dsblur=68px&wc=true&wa=true&pv=48px&ph=32px&ln=false&fm=Hack&fs=14px&lh=133%25&si=false&code=prun%2520%255C%250A%2520%2520--containerImage%2520docker%253A%252F%252F%253Cimage%253E%2520%255C%250A%2520%2520--exec%2520%2522%253Cshell%2520script%253E%2522%2520%255C%250A%2520%2520--inDS%2520%253Cinputdataset%253E%2520%255C%250A%2520%2520--outDS%2520%253Coutput%2520dataset%253E%2520%255C%250A%2520%2520--outputs%2520%253Coutputfiles%253E%2520%255C%250A%2520%2520--forceStaged&es=4x&wm=false -->
---
# User Interface

Integrated into main command line interface for GRID submission (PanDA):
.center.width-80[![user_interface](figures/carbon_user_interface.png)]

Future: dedicated _pcontainer_ CLI (drop all software related flags)

---
# Machine Learning Base Images
.grid[
.kol-1-3.center[
<br><br>
<br><br>
<!-- .center.width-100[![AML_DockerHub](figures/AML_DockerHub.png)] -->
.center.width-100[![ML_Docker](figures/ML_Docker.jpg)]
]
.kol-2-3[
- ML base images
   - OS flavors
      - Ubutnu 18.04
      - CentOS 7
   - Goal: To provide _modern Pythonic_ machine learning _stack, tools, environment_
- ATLAS ML base images
   - Copying ATLAS Software Infrastructure Team to make stack of images
      - ATLAS OS (CentOS 7)
      - AnalysisBase (CentOS 7)
      - ATLAS ML base (CentOS 7)
   - Goal: Provide AnalysisBase and ATLAS tools along _with ML base_
<!-- - _Singularity compatible_ mount points for _GRID_ -->
]
]
- _Singularity compatible_ mount points for _GRID_
- Common ML tools and _starting image_ for personal ML workflows

---
# Base Image Development

.grid[
.kol-1-2.center[
.center.width-100[![AML_docker_repo](figures/AML_docker_repo.png)]
.center[[Dockerfiles versioned on GitLab](https://gitlab.cern.ch/aml/containers/docker)...]
]
.kol-1-2.center[
.center.width-80[![AML_DockerHub](figures/AML_DockerHub.png)]
.center[...and [deployed to Docker Hub](https://hub.docker.com/u/atlasml)]
]
]
.center.width-50[![CI_pipeline](figures/CI_pipeline.png)]
.center[...[built by CI](https://gitlab.cern.ch/aml/containers/docker/pipelines)...]

<!-- ---
# Base Image Environment
.center.width-70[![image_environment](figures/carbon_image_environment.png)] -->

---
# Base Image Environment
.center[Modern _Pythonic_ ML environment with common (HEP)ML tools]
.grid[
<!-- https://carbon.now.sh/?bg=rgba(255%2C255%2C255%2C1)&t=seti&wt=none&l=application%2Fx-sh&ds=false&dsyoff=20px&dsblur=68px&wc=true&wa=true&pv=48px&ph=32px&ln=false&fm=Hack&fs=14px&lh=133%25&si=false&code=%2524%2520python3%2520--version%250APython%25203.6.8%2520%2523%2520From%2520CPython%2520source%250A%2524%2520pip3%2520--version%250Apip%252019.0.3%250A%2524%2520cat%2520requirements.txt%2520%250Anumpy~%253D1.16%250Ascikit-learn~%253D0.20%250Atensorflow~%253D1.12%250Akeras~%253D2.2%250Atorch~%253D1.0%250Auproot~%253D3.4%250Amatplotlib~%253D3.0%250Apandas~%253D0.24%250Ajupyter~%253D1.0%250A&es=4x&wm=false -->
.kol-1-2.center[
.center.width-110[![image_environment](figures/carbon_image_environment.png)]
]
<!-- https://carbon.now.sh/?bg=rgba(255%2C255%2C255%2C1)&t=seti&wt=none&l=application%2Fx-sh&ds=false&dsyoff=20px&dsblur=68px&wc=true&wa=true&pv=48px&ph=32px&ln=false&fm=Hack&fs=14px&lh=133%25&si=false&code=%2524%2520git%2520--version%250Agit%2520version%25202.17.1%250A%2524%2520h5ls%2520--version%250Ah5ls%253A%2520Version%25201.10.0-patch1%250A%2524%2520jq%2520--version%250Ajq-1.5%250A%2524%2520pip3%2520freeze%2520%257C%2520grep%2520h5py%250Ah5py%253D%253D2.9.0%250A%2523%2520and%2520more%250A&es=4x&wm=false -->
.kol-1-2.center[
.center.width-110[![image_extras](figures/carbon_image_extras.png)]
]
]
<!-- - [tab complete for h5ls](https://github.com/dguest/_h5ls) -->
<!-- - [git-fatlas](https://github.com/dguest/git-fatlas) (ATLAS ML base only) -->

---
# Supports Interactive Sessions
.center.width-80[![jupyter_example](figures/jupyter_example.png)]

---
# Upcoming: GPU optimized images

.grid[
.kol-1-2[
<br><br>
<br><br>
- Images with CUDA/cuDNN support for GPU acceleration
- GPU support for TensorFlow and PyTorch
- Slimmed and specialized base images for size optimization
   - Example: Don't distribute Jupyter if only want to train models on GRID
]
.kol-1-2[
.center.width-80[![CUDA_logo](figures/CUDA_logo.jpg)]

<br>

.center.width-80[![cuDNN_logo](figures/cuDNN_logo.png)]
]
]

---
# Summary

- HEPML needs non-traditional software stack. Served well by _containers_
- Containers allow for _local_ and _production_ to be the _same_ environment
- _GRID submission CLI_ of jobs with containers live now
- GRID + containers allows for unique workflows _at scale_ and _efficient use_ of GPU site resources
- ATLAS Machine Learning Forum provides ML base images openly distributed on Docker Hub
   - Part of CVMFS sync, so on CVMFS now
   - Contributions welcome on [GitLab](https://gitlab.cern.ch/aml/containers/docker)

<!-- .center.width-50[![Docker_nyan_whale](figures/Docker_nyan_whale.gif)]
.center.width-50[![LHC_schedule](figures/LHC_schedule.png)] -->
.grid[
.kol-1-2[
.center.width-100[![Docker_nyan_whale](figures/Docker_nyan_whale.gif)]
]
.kol-1-2[
.center.width-100[![LHC_schedule](figures/LHC_schedule.png)]
]
]

---
class: end-slide, center

Backup

---
# Can I use these on the GRID?

<br>

- Yes

---
# Can I use these to make my own images?

<br>

- Yes

---
# References

1. L. Heinrich, .italic[[Continuous Analysis in ATLAS: Running User-Defined Container Images on the Grid](https://indico.cern.ch/event/708041/contributions/3276174/)], ACAT 2019, March 10, 2019
2. L. Heinrich, .italic[[Docker On the Grid](https://indico.cern.ch/event/791372/contributions/3286861/)], ATLAS Machine Learning Forum, January 23, 2019
3. A. C. Forti, L. Heinrich, M. Guth, .italic[[Hardware Accelerated ATLAS Workloads on the WLCG](https://cds.cern.ch/record/2665661?ln=en)], ACAT 2019, March 11, 2019

---

class: end-slide, center
count: false

The end.
