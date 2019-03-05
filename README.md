## Branch - Specific Edits

This version contains generate_singletraj() in trajectory_generator.py that allows the user to supply their own list of met files and generate one trajectory at a time. This allows for any ARL-packaged files to be used, such as the much higher resolution NAM 12KM and HRRR 3KM data sets, which can be obtained from arlftp.arlhq.noaa.gov. 

A working example for running large numbers of regular or irreguarly time-stepped trajectories with HRRR 3KM data can be found at https://github.com/brendano257/pysplitprocessor


# PySPLIT

A package for generating [HYSPLIT](http://ready.arl.noaa.gov/HYSPLIT.php) air parcel trajectories trajectories, performing moisture uptake analyses, expediting HYSPLIT cluster analysis, and for visualizing trajectories, clusters, and along-trajectory meteorological data.  For a basic overview of PySPLIT, see the [SciPy 2015 conference proceedings](http://conference.scipy.org/proceedings/scipy2015/mellissa_cross_p.html).

A new, updated technical paper will be appearing the Sept/Oct 2018 issue of *Computing in Science and Engineering*!

### If you are running version 0.3.3 from PyPi or have not recently updated your PySPLIT from GitHub and are performing moisture uptake analyses, please update to 0.3.4 and rerun your moisture uptake analyses immediately.  Geographic points were previously assigned to ``Trajectory.uptake`` backwards.  This has been corrected.

## Coming Soon
* Python 3.6 support!
* HYSPLIT clustering fully in PySPLIT
* Increased trajectory generation functionality:
  * New modes
  * More control over trajectory initialization conditons
  * Improved meteorology discovery and better support for sub-weekly files
* Support for matrix and ensemble trajectories
* Extended library of examples
* Various quality of life/convenience updates and more!


## Past Updates

* Support for Python 3.6
* PySPLIT now uses the power of GeoPandas rather than pure NumPy
* Faster trajectory file loading/``Trajectory`` object initialization
* Need help clustering?  ``pysplit.print_clusteringprocedure()``.
* The class structure of PySPLIT has been rewritten:
  * ``Trajectory`` and ``Cluster`` objects are now subclasses of ``HyPath`` class.
  * Along-trajectory data for ``HyPath`` classes lives in the ``data`` attribute, a [GeoPandas] (http://geopandas.org/) ``GeoDataFrame``.
  * ``TrajectoryGroup`` and ``Cluster`` classes are now subclasses of the ``HyGroup`` class.  They are both iterable; they can also be added together or subtracted.
  * ``HyPath`` and ``HyGroup`` are only used internally, so the API remains essentially the same.
* Trajectory generator updates:
  * Improved efficiency
  * Improved API
  * Use *any* weekly or semi-monthly meteorology data (see docs for required filename format), not just gdas1, and not just from the 21st century!
  * Generate trajectories for every day in each month *OR* for particular slice of days in each month
  * Generate reverse trajectories at time of bulk trajectory generation OR during your analysis workflow!
* Choose the starting point for your moisture uptake analyses
* Removal of certain assumptions about trajectory file structure for HYSPLIT January 2017 (854) compatibility.
* Removal of certain assumptions about trajectory century and timepoint interval from loading process
* Check out the growing library of examples!
## Installing PySPLIT

PySPLIT is compatible with Python 2.7, 3.5, and 3.6.  It depends on:
* NumPy >= 1.6
* matplotlib >= 1.2
* Basemap >= 1.0
* GeoPandas >= 0.1

and is available on PyPi.  You can install the latest stable release by running:

```
$ pip install pysplit
```

To install from source or create a development installation, clone and fork PySPLIT then install by running:

```
$ python setup.py install
```

or develop locally by running:

```
$ python setup.py develop
```

### Installing in a conda virtual environment:

Installation difficulties with PySPLIT are typically related to GeoPandas dependencies.  An easy work-around is installing PySPLIT in a new conda virtual environment.  This is the recommended installation method.  First, add the conda-forge channel:
```
$ conda config --add channels conda-forge
```

Next, create the conda environment.  For a Python 3.5 environment named `pysplitenv`, run:
```
$ conda create --name pysplitenv python=3.5 numpy matplotlib pandas basemap six fiona shapely geopandas
```

Similarly, for a Python 3.6 environment named `pysplitenv`, run:
```
$ conda create --name pysplitenv python=3.6 numpy matplotlib pandas basemap six fiona shapely geopandas
```

Or, to create a Python 2.7 environment named `pysplitenv`, run:
```
$ conda create --name pysplitenv python=2.7 numpy matplotlib pandas basemap six fiona=1.5.1 shapely geopandas
```

Activate `pysplitenv` by running the following on Windows:
```
$ activate pysplitenv
```
If you are on Linux or OSX, instead run:
```
$ source activate pysplitenv
```

Within your virtual environment, install PySPLIT as above.

## Using PySPLIT

Updated examples can be found in docs/examples, and an updated technical paper is pending.  For now, if you use PySPLIT in your work, please cite the [SciPy 2015 conference proceedings](http://conference.scipy.org/proceedings/scipy2015/mellissa_cross_p.html).  Many thanks are due to the NOAA Air Research Laboratory for providing the HYSPLIT model.
