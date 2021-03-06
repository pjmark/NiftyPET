|UCL|

===========================================================
NiftyPET: High-throughput image reconstruction and analysis
===========================================================

|Docs| |Tests|

**Documentation**: https://niftypet.readthedocs.io

|brain1| |brain2|

.. ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
.. taken from docs/highlights.rst

*NiftyPET* is a software platform and a Python namespace package encompassing sub-packages for high-throughput PET image reconstruction, manipulation, processing and analysis with high quantitative accuracy and precision.  See below for the description of the above image, reconstructed using *NiftyPET* [*]_.

*NiftyPET* includes two packages:

- ``nimpa``:  https://github.com/NiftyPET/NIMPA (neuro-image manipulation, processing and analysis)
- ``nipet``:  https://github.com/NiftyPET/NIPET (quantitative PET neuro-image reconstruction)

The core routines are written in CUDA C and embedded in Python C extensions.  The scientific aspects of this software platform are covered in two open-access publications:

- *NiftyPET: a High-throughput Software Platform for High Quantitative Accuracy and Precision PET Imaging and Analysis* Neuroinformatics (2018) 16:95. https://doi.org/10.1007/s12021-017-9352-y
- *Rapid processing of PET list-mode data for efficient uncertainty estimation and data analysis* Physics in Medicine & Biology (2016). https://doi.org/10.1088/0031-9155/61/13/N322

.. [*] The above dynamic transaxial and coronal images show the activity of  :sup:`18`\ F-florbetapir during the one-hour dynamic acquisition.  Note that the signal in the brain white matter dominates over the signal in the grey matter towards the end of the acquisition, which is a typical presentation of a negative amyloid beta (Abeta) scan.

.. ::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::


================
Acknowledgements
================

This project is being developed at University College London (`UCL <https://www.ucl.ac.uk/>`_). Initially, it was supported and funded by the Engineering and Physical Sciences Research Council (`EPSRC <https://epsrc.ukri.org/>`_) of the United Kingdom (UK).  Currently, the project is being further developed under the following funding streams:

1. The `Innovative Medicines Initiative 2 <https://www.imi.europa.eu/about-imi>`_ Joint Undertaking under grant agreement No 115952. This Joint Undertaking receives support from the European Union’s `Horizon 2020 <https://ec.europa.eu/programmes/horizon2020/en/>`_ research and innovation programme and `EFPIA <https://www.efpia.eu/>`_.

2. The `Dementias Platform UK <https://www.dementiasplatform.uk/>`_ `MR-PET Partnership <https://gtr.ukri.org/projects?ref=MR%2FN025792%2F1>`_, supported by the Medical Research Council (`MRC <https://mrc.ukri.org/>`_) in the UK.

We gratefully acknowledge the support of `NVIDIA Corporation <https://www.nvidia.com>`_  with the donation of the Tesla K20 and Titan X Pascal GPUs used for this research and work.

+----------+----------+----------+
| |AMYPAD| | |DPUK|   | |NVIDIA| |
+----------+----------+----------+
| |EFPIA|  | |IMI|    | |EU|     |
+----------+----------+----------+

|Licence|

Copyright 2018-21

- `Pawel J. Markiewicz <https://github.com/pjmark>`__ @ University College London
- `Casper O. da Costa-Luis <https://github.com/casperdcl>`__ @ King's College London
- `Contributors <https://github.com/NiftyPET/NiftyPET/graphs/contributors>`__

.. |Docs| image:: https://readthedocs.org/projects/niftypet/badge/?version=latest
   :target: https://niftypet.readthedocs.io/en/latest
.. |Tests| image:: https://img.shields.io/github/workflow/status/NiftyPET/NiftyPET/Test?logo=GitHub
   :target: https://github.com/NiftyPET/NiftyPET/actions
.. |Licence| image:: https://img.shields.io/pypi/l/niftypet.svg?label=licence
   :target: https://github.com/NiftyPET/NiftyPET/blob/master/LICENCE
.. |brain1| image:: ./docs/images/gim_magna_t.gif
   :width: 45%
.. |brain2| image:: ./docs/images/gim_magna_c.gif
   :width: 45%
.. |UCL| image:: ./docs/logos/ucl.png
   :target: https://www.ucl.ac.uk
.. |NVIDIA| image:: ./docs/logos/Nvidia_logo.png
   :target: https://www.nvidia.com/en-us/research
.. |EFPIA| image:: ./docs/logos/efpia.jpg
   :target: https://www.efpia.eu/
.. |IMI| image:: ./docs/logos/imi.jpg
   :target: https://www.imi.europa.eu/
.. |EU| image:: ./docs/logos/eu.png
   :target: https://europa.eu/european-union/index_en
.. |AMYPAD| image:: ./docs/logos/amypad.jpg
   :target: https://amypad.eu/
.. |DPUK| image:: ./docs/logos/dpuk.jpg
   :target: https://www.dementiasplatform.uk
