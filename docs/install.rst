=============
Installation
=============

.. note::

  **Quick note on ways of installation**

  *Requirements:*

  - An NVIDIA GPU with the `CUDA SDK/Toolkit`_ (including drivers) installed
  - Git_
  - Python 3.6 or greater (e.g. via `Anaconda or Miniconda`_)

  *Installation:*

  .. code:: sh

    pip install niftypet

  This will install all relevant packages, including nipet_ and nimpa_.

  .. tip::

    *Installation (advanced):*

    .. code:: sh

      git clone https://github.com/NiftyPET/NIMPA.git
      git clone https://github.com/NiftyPET/NIPET.git

      export PATHTOOLS=$HOME/NiftyPET_tools
      export HMUDIR=$HOME/mmr_hardwareumaps

      conda install -c conda-forge python=3 \
          numpy scipy scikit-image matplotlib ipykernel ipywidgets
      pip install --verbose -e ./NIMPA
      pip install --verbose -e ./NIPET

    This will install an \"editable\" distribution at the source locations for both ``nimpa`` and ``nipet`` (allowing easy modification and/or updating using ``git pull``).

  Detailed steps for installation are given below.

.. _CUDA SDK/Toolkit: https://developer.nvidia.com/cuda-downloads
.. _Git: https://git-scm.com/downloads
.. _Anaconda or Miniconda: https://docs.conda.io/projects/conda/en/latest/user-guide/install/download.html#anaconda-or-miniconda
.. _nipet: https://github.com/NiftyPET/NIPET
.. _nimpa: https://github.com/NiftyPET/NIMPA

*NiftyPET* is a `Python namespace package <https://packaging.python.org/guides/packaging-namespace-packages>`_, primarily encompassing the two packages ``nimpa`` and ``nipet``. Currently, these are available for Python 3.6 or greater for Linux and Windows systems. It has been deployed and tested on CentOS 6.8 and 7, Ubuntu 14.04, 16.04, 18.04 and 20.04, as well as Windows 10 (limited) -- including Python C extensions for the core CUDA routines. Linux systems are recommended due to their robustness and stability (support for Windows is comparatively limited).


Dependencies
------------

Hardware
^^^^^^^^

- **GPU device**: One or more GPU devices from NVIDIA with a CUDA compute capability of at least 3.5. It is also recommended to have at least 5 GB of GPU memory. The following devices have been tested with *NiftyPET*:

  * NVIDIA Tesla K20/40,
  * NVIDIA Titan Xp,
  * NVIDIA Quadro P6000,
  * NVIDIA GeForce GTX 1060,
  * NVIDIA GeForce GTX 1080/Ti/Max-Q, and
  * NVIDIA  Tesla V100.

- **CPU host**: The GPU device can be accessed by a CPU host, with a reasonable computing power for some other image processing routines (e.g. image registration, etc.).  It is recommended to have at least 16 GB of RAM, although we have managed to run dynamic reconstruction using old PC workstations with as little as 11 GB of RAM.

Software
^^^^^^^^

*NitfyPET* installation needs the following software pre-installed:

- **C/C++ compiler**

  *GCC* and *Clang* are commonly using on Linux systems, and *Visual Studio* on Windows.

  * Ubuntu Linux:

    .. code:: sh

      apt-get install build-essential

  * CentOS Linux:

    .. code:: sh

      yum group install "Development Tools"

  * Windows: `Visual Studio <https://visualstudio.microsoft.com>`_

- **CUDA GPU & Software**

  The `CUDA SDK/Toolkit`_ (click the link to download) is a parallel computing platform and programming model. This includes the CUDA compiler (``nvcc``) and runtime API. For extra guidance, consult the `CUDA documentation <https://docs.nvidia.com/cuda>`_.

  .. tip::

    In CentOS, it is necessary to install DKMS (Dynamic Kernel Module Support). Download from `here <https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm>`_ and install as follows:

    .. code:: sh

      rpm -ivh epel-release-latest-7.noarch.rpm
      yum -y install dkms

  .. tip::

    Make sure that CUDA is installed with appropriate paths to CUDA resources setup, e.g. on Linux systems:

    .. code:: sh

      export PATH="/usr/local/cuda/bin:$PATH"
      export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"

    This can be added to ``~/.profile`` or ``~/.bashrc`` files. For more details see http://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions.

- **Git**

  Git_ is a version control system used for downloading *NiftyPET* and other necessary tools, i.e. *NiftyReg* and ``dcm2niix``. For more details on installing ``git`` see https://git-scm.com/book/en/v2/Getting-Started-Installing-Git.

  On Linux systems it can be installed as follows:

  * Ubuntu Linux:

    .. code:: sh

      apt-get install git

  * CentOS Linux:

    .. code:: sh

      yum install git

  * Windows: Git_

- **Python 3.6** or greater

  A free high-level programming language, through which all the GPU routines are available for the user.
  The easiest way to run *NiftyPET* in Python is by using the `Anaconda or Miniconda`_ distributions.

  .. tip::

    *Optional Python packages*

    *Jupyter Notebook* (``notebook``) is a useful development interface.

    Additionally, when using Anacoda or Minconda, it is recommended to use ``conda`` to install some dependencies rather than rely on *NiftyPET* to automatically install them via ``pip``.

    .. code:: sh

      # useful mathematical & plotting libraries
      conda install -c conda-forge python=3 numpy scipy scikit-image matplotlib nibabel pydicom
      # jupyter noebook support
      conda install -c conda-forge python=3 ipykernel ipywidgets

.. _niftypet-install:

*NiftyPET* installation
-----------------------

.. tip::

  To avoid prompts during installation, specify configuration directories in advance:

  .. code:: sh

    export PATHTOOLS=$HOME/NiftyPET_tools
    export HMUDIR=$HOME/mmr_hardwareumaps

Using ``pip``
^^^^^^^^^^^^^

To install the entire suite of packages, use:

.. code:: sh

  pip install niftypet

.. tip::

  Instead of installing everything, follow these steps to install individual components separately.

  * nimpa_

    .. code:: sh

      pip install --verbose nimpa

  * nipet_

    The core of *NiftyPET* image reconstruction.

    .. code:: sh

      pip install --verbose nipet

    This will also install nimpa_ if not already present.

From source
^^^^^^^^^^^

The source code of full version of ``nimpa`` and ``nipet`` packages can be downloaded to a specific folder using ``git`` as follows:

.. code:: sh

  git clone https://github.com/NiftyPET/NIMPA.git
  git clone https://github.com/NiftyPET/NIPET.git


After a successful download, navigate to folder ``nimpa`` and run inside one of the following:

1) ``pip install --verbose .``
2) ``pip install --verbose -e .``

The last option with the ``-e`` makes the installation \"editable\", allowing the user to modify the source code themselves or by pulling newer versions from ``git`` using ``git pull``.

Identically for ``nipet``, run one of the following:

1) ``pip install --verbose .``
2) ``pip install --verbose -e .``

The installation will download and call on ``cmake``, which will run automatically and generate Ninja files, and then run ``ninja`` to build all the CUDA C routines and Python C extensions. Following this, the compiled Python modules will be installed into the specific Python package location.

Third party software installed with *NiftyPET*
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*NiftyPET* will automatically install additional third party software (used for capabilities such as image registration and conversion). *NiftyReg* and *dcm2niix* will be installed in the ``NiftyPET_tools`` folder specified during the installation process:

- **dcm2niix**: conversion of DICOM images to NIfTI images (v1.0.20171204).  If for some reason the automatic installation fails (e.g., due to a problem with dependencies), try to download the source code from https://github.com/rordenlab/dcm2niix and compile it, or use the pre-complied version with current release available at https://github.com/rordenlab/dcm2niix/releases/.

- **NiftyReg**: image registration and resampling tool.  The stable version (16 Nov 2017) is fetched and installed automatically from https://github.com/KCL-BMEIS/niftyreg. Some details for a manual install can be found at http://cmictig.cs.ucl.ac.uk/wiki/index.php/NiftyReg_install (can be outdated).

Conda environments
^^^^^^^^^^^^^^^^^^

One of the advantages of using ``conda`` is the possibility of having separate environments for different versions of Python and/or packages installed in them. Thus ``conda`` environments enable the user to set up *NiftyPET* differently for various applications (e.g., different image resolution, radio-pharmaceutical-optimised attenuation and/or scatter correction, etc.). Below is an example of installation of *NiftyPET* into environment called `niftypet`.

Create environment called, for example, `niftypet`, by running this command:

.. code:: sh

  conda create --name niftypet

Activate the conda environment:

.. code:: sh

  conda activate niftypet

.. note::

  On Windows, this may be simply  ``activate niftypet``, and on Linux ``source activate niftypet``.

.. tip::

  It may be quicker to also install additional required packages with ``conda`` (rather than relying on ``pip`` to automatically do this during installation of ``niftypet``):

  .. code:: sh

    # useful mathematical & plotting libraries
    conda install -c conda-forge python=3 numpy scipy scikit-image matplotlib nibabel pydicom
    # jupyter noebook support
    conda install -c conda-forge python=3 ipykernel ipywidgets

*NiftyPET* can now be installed as described above in :ref:`niftypet-install`, while making sure that the ``conda`` environment is active.

.. warning::

  Make sure to ``conda activate niftypet`` whenever opening a new terminal to ensure the correct environment is active.

Jupyter Notebook
^^^^^^^^^^^^^^^^

Jupyter Notebooks are useful for sharing and replicating image reconstruction methods written in Python. They allow introspection, plotting and sharing of any intermediate results (e.g. sinograms and images generated during the reconstruction pipeline) or any end results. It is easiest to use ``conda`` to install Jupyter in the ``base`` environment in order to automatically pick up kernels for all other enviroments (``conda install --name base notebook``). See http://jupyter.readthedocs.io/en/latest/tryjupyter.html for more details and http://jupyter.readthedocs.io/en/latest/install.html for a manual installation.

.. warning::

  When using Jupyter, make sure to select the correct *kernel* (corresponding to the desired conda environment name) within the notebook.

Post-installation checks
------------------------

Configuration
^^^^^^^^^^^^^

A ``.niftypet`` folder is created during the installation (in ``$HOME`` or ``%APPDATA%``).
Additional subfolders may be present corresponding to the ``conda`` environment name.
Configuration information is stored in ``resources.py`` within this folder.

.. warning::

  It is recommended to rerun ``pip install`` rather than manually editing paths and device properties in ``resources.py``.

Default CUDA device
~~~~~~~~~~~~~~~~~~~

The default CUDA device used for GPU calculations is chosen during the installation together with the corresponding optimal ``nvcc`` (CUDA compiler) flags. For example, for the NVIDIA Titan Xp with compute capability of 6.1, ``resources.py`` will have a section showing:

.. code:: python

  # DO NOT MODIFY BELOW--DONE AUTOMATICALLY
  ### start GPU properties ###
  DEV_ID = 0
  CC_ARCH = '-gencode=arch=compute_61,code=compute_61;'
  ### stop GPU properties ###

Any available (installed) CUDA device can be chosen within Python for any image reconstruction or part of the reconstruction pipeline.

Search paths for third-party software
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Paths to tools for image registration, resampling, and conversion (DICOM -> NIfTI) can also be found in ``resources.py``:

.. code:: python

  # paths to apps and tools needed by NiftyPET
  ### start NiftyPET tools ###
  PATHTOOLS = '/path/to/NiftyPET_tools/'
  RESPATH = '/path/to/NiftyPET_tools/niftyreg/bin/reg_resample'
  REGPATH = '/path/to/NiftyPET_tools/niftyreg/bin/reg_aladin'
  DCM2NIIX = '/path/to/NiftyPET_tools/dcm2niix/bin/dcm2niix'
  HMUDIR = '/path/to/mmr_hardware_mumaps'
  ### end NiftyPET tools ###

Note that the proprietary hardware :math:`\mu`-maps (``HMUDIR``) are not distributed with this software, and have to be obtained from the Siemens Biograph mMR scanner.
