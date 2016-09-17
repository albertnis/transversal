# Transversal
### The world is going on a holiday

At some stage in your life, you've probably thought about what lies on the opposite side of the world. I sure have, and I was recently speaking with friends about what it would be like to able to teleport instantly to this opposite location. What if everyone could do it? 

The project seeks to answer the following question:

***If the entire population of earth was simultaneously and instantaneously transported to the other side of the world, how many would survive?***

Of course, we need to make some assumptions:
- Teleportation is real and just as simple as it sounds.
- People are teleported to a point located on the other side of earth, through the core.
- This point is at surface level, meaning nobody dies due to object interference or similar.
- Teleportations to a point over land result in survival.
- Teleportations to a point over water result in death.

### Approach

Both population density and topography maps are downloaded from [NASA Earth Observations](http://neo.sci.gsfc.nasa.gov/]) as GeoTIFF files. These maps are manipulated and compared at a pixel level using GDAL in Python to determine the "survival" of each pixel. A value for proportional survival is subsequently calculated. 

Later down the track, it might be worth experiment with stacking maps to obtain a more precise survival figure by reducing assumptions. For instance, if a pixel is teleported to an area which is on fire, they will perish. Perhaps people teleporting into warm water on a common shipping route will survive.

### Prerequisites

This project requires GDAL and Python to be installed. Here's how I managed to install GDAL in Windows:

1. Go to the [binary downloads page at GISInternals](http://www.gisinternals.com/release.php).

2. In the *GDAL 2.1.0* section, select the download link corresponding to your Python install. The architecture **and** compiler version must match. These can be found by reading the Python startup message. For instance, my install is 32 bit and MSC v1500, so I selected *release-1500-gdal-2-1-0-mapserver-7-0-1*.

3. In the following screen, download and install, in order, the following:

    1. Generic installer for the GDAL core components (e.g. *gdal-201-1500-core.msi*).

    2. Installer for the GDAL python bindings (e.g. *GDAL-2.1.0.win32-py2.7.msi*).

4. Add the GDAL install directory to PATH (e.g. *C:\Program Files (x86)\GDAL*).

5. Add a new environment variable named **GDAL_DATA** and assign to it the address of the *gdal-data* subdirectory (e.g. *C:\Program Files (x86)\GDAL\gdal-data*).

You should be good to go. Run the following code in Python to test the installation

```python
from osgeo import gdal
gdal.__version__
```

No exceptions should be thrown and the version should display as `'2.1.0'`.