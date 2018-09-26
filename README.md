DCASE2017 Baseline system
=========================
[Audio Research Group / Tampere University of Technology](http://arg.cs.tut.fi/)

[![Build Status](https://travis-ci.org/TUT-ARG/DCASE2017-baseline-system.svg?branch=master)](https://travis-ci.org/TUT-ARG/DCASE2017-baseline-system) [![Coverage Status](https://coveralls.io/repos/github/TUT-ARG/DCASE2017-baseline-system/badge.svg?branch=master)](https://coveralls.io/github/TUT-ARG/DCASE2017-baseline-system?branch=master)

**Authors**

| Name                  |                                                                    |                                                              |
| --------------------- | -----------------------------------------------------------------  | ------------------------------------------------------------ |
| **Toni Heittola**     | Baseline system, DCASE Framework, Documentation                    | <toni.heittola@tut.fi>, <http://www.cs.tut.fi/~heittolt/>, <https://github.com/toni-heittola>   |
| **Aleksandr Diment**  | Dataset synthesis (Task 2)                                         | <aleksandr.diment@tut.fi>, <http://www.cs.tut.fi/~diment/>   |
| **Annamaria Mesaros** | Documentation                                                      | <annamaria.mesaros@tut.fi>, <http://www.cs.tut.fi/~mesaros/> |

Documentation
=============

See https://tut-arg.github.io/DCASE2017-baseline-system/ for detailed instruction, manuals and tutorials.


Getting started
===============


1. Clone repository from [Github](https://github.com/TUT-ARG/DCASE2017-baseline-system) or download [latest release](https://github.com/TUT-ARG/DCASE2017-baseline-system/releases/latest).
2. Install requirements with command: ``pip install -r requirements.txt``
3. Run the application with default settings: ``python applications/task1.py``

The data download is throwing an error. Possibly an outdated url.

System description
==================

This is the baseline system for the [Detection and Classification of Acoustic Scenes and Events 2017 (DCASE2017) challenge](http://www.cs.tut.fi/sgn/arg/dcase2017/) tasks.

The baseline system is intended to lower the hurtle to participate the DCASE challenges. It provides an entry-level
approach which is simple but relatively close to the state of the art systems to give reasonable performance for all
the tasks. High-end performance is left for the challenge participants to find.

In the baseline, one single low-level approach is shared across the tasks by application specific extensions.
Main idea of this is to show the parallelism in the tasks settings, and show how easily one can jump between
tasks during the system development.

The main approach implemented in the baseline system:

- *Acoustic features*: Log Mel-band energies extracted in 40ms windows with 20ms hop size.
- *Machine learning*: neural network approach using multilayer perceptron (MLP) type of network (2 layers with 50 neurons each, and 20% dropout between layers).

### Directory layout

    .
    ├── applications            # Task specific applications (task1.py, task2.py, and task3.py) 
    │   └── parameters          # Default parameters for the applications
    ├── dcase_framework         # DCASE Framework code
    ├── docker                  # Docker container to reproduce baseline results
    ├── docs                    # Docs in HTML format
    ├── documentation           # Documentation sources (Sphinx)  
    ├── examples                # Examples how to extend the DCASE Framework
    ├── tests                   # Unit tests
    ├── EULA.pdf                # End-user license agreement
    ├── README.md               # This file
    └── requirements.txt        # External module dependencies 


Installation
============

The system is developed for [Python 2.7](https://www.python.org/) and [Python 3.6](https://www.python.org/).
The baseline system is tested to work with Linux, Windows and MacOS operating systems.

To ensure that all external modules are installed, run command:

``pip install -r requirements.txt``

See more detailed instructions from [documentation](https://tut-arg.github.io/DCASE2017-baseline-system/install.html).

Changelog
=========

#### 1.2 / 2017-06-20

* Introduced recognizer classes: SceneRecognizer, EventRecognizer
* Introduced Keras callbacks: ProgressLoggerCallback, ProgressPlotterCallback, StopperCallback, StasherCallback
* Added new learner classes: SceneClassifierKerasSequential, EventDetectorKerasSequential
    * Full support for Keras sequential API 
    * Epoch-by-epoch processing, with external metric evaluation (using sed_eval)
    * DataProcessor class to embed feature processing and data processing chains
    * Feature generators to allow loading feature data from disk during training procedure
* Added possibility to use constant and simple math equations in the keras based learner parameters 
        
#### 1.1.1 / 2017-06-06

* feature_stacker parameter hash added to the data paths. This broke backward compatibility, previously stored models and results has to be re-calculated or moved to correct paths.

#### 1.1 / 2017-04-02

* Added Docker container to reproduce baseline results 
* Fixed training data ordering (might have been different on different computer setups)
* Added Windows compatibility

#### 1.0 / 2017-03-20

* First public release

License
=======

The DCASE Framework and the baseline system is released **only for academic research** under [EULA.pdf](EULA.pdf) from Tampere University of Technology.