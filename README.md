# [Containers for Machine Learning in HEP](https://indico.cern.ch/event/766872/contributions/3357988/)

Proposed talk at the [3rd IML Machine Learning Workshop (2019)](https://indico.cern.ch/event/766872/)

## Abstract

> We are interested in receiving your abstracts on the application of modern machine learning techniques in physics. This includes classification, regression, likelihood-free inference, anomaly detection, network acceleration, knowledge distillation, uncertainty mitigation, fast simulation, semi-supervised learning, or whatever else you may be working on.

Physicists want to use modern open source machine learning tools developed by industry for machine learning projects and analyses in high energy physics. The software environment that a physicist prototypes, tests, and runs these projects in is ideally the same regardless of compute site (be it their laptop or on the GRID). However, historically it has been difficult to find compute sites that have both the desired hardware resources for machine learning (i.e. GPUs) and a compatible software environment for the project, resulting in suboptimal use of resources and wasted researcher time tuning their software requirements to the imposed constraints. Container technologies, such as [Docker](https://www.docker.com/) and [Singularity](https://www.sylabs.io/singularity/), provide a scalable and robust solution to this problem.

We present work by _Heinrich_ demonstrating the use of containers to run analysis jobs in reproducible compute environments at GRID endpoints with GPU resources that support Singularity. We additionally present complimentary work by _Feickert_ that provides publicly available "base" Docker images of a HEP orientated machine learning environment: the CentOS 7 file system with the ATLAS "standalone" analysis release AnalysisBase, HDF5 support and utilities, and modern Python 3 with pip with libraries such as [NumPy](https://github.com/numpy/numpy), [TensorFlow](https://github.com/tensorflow/tensorflow) and [uproot](https://github.com/scikit-hep/uproot) installed. We further present ongoing synergetic work to expand both these efforts.

## Authors

- [Matthew Feickert](http://www.matthewfeickert.com/)
- [Dan Guest](https://github.com/dguest)
- [Lukas Heinrich](http://www.lukasheinrich.com/)

## Preferred contribution length

20 minutes
