# CGIT-Project-Setup-Windows
A comprehensive guide to setup local development environment in Windows for CGIT Django projects.

## GIT Setup:

### 1. Clone the repository in your local dev folder or create a separate CGIT folder to keep a separate workspace.

### 2. Once inside the git project, check the below configs:
> ```git config user.name```

> ```git config user.email```

> Reset these configs to your VT PID and VT Email-ID respectively if they are different.

## GDAL Installation:

### 1. Download required GDAL whl file with specific versions depending on your setup 

> Link: https://www.lfd.uci.edu/~gohlke/pythonlibs/#gdal

> ex: For a 3.9 python setup on a 64-bit windows processor: GDAL‑3.4.3‑cp39‑cp39‑win_amd64.whl
  
### 2. Move this whl file into the project

> You need to move it to the \venv\Lib\site-packages location of the venv of the project
   
> Now install the whl file using the following command: $pip install GDAL‑3.4.3‑cp39‑cp39‑win_amd64.whl
   
### 3. Post Installation 

> There are errors even with a successful installation of all pip packages including GDAL.

>> Most of the times we run into the below issue:
>>> ```File "C:\Users\ankit\Documents\CGIT\geovine\venv\lib\site-packages\django\contrib\gis\gdal\driver.py", line 5, in <module>```
>>> ```from django.contrib.gis.gdal.prototypes import ds as vcapi, raster as rcapi```
>>> ```File "C:\Users\ankit\Documents\CGIT\geovine\venv\lib\site-packages\django\contrib\gis\gdal\prototypes\ds.py", line 9, in <module> ```       
>>> ```from django.contrib.gis.gdal.libgdal import GDAL_VERSION, lgdal```
>>> ```File "C:\Users\ankit\Documents\CGIT\geovine\venv\lib\site-packages\django\contrib\gis\gdal\libgdal.py", line 43, in <module>```
>>> ```raise ImproperlyConfigured(```
>>> ```django.core.exceptions.ImproperlyConfigured: Could not find the GDAL library (tried "gdal301", "gdal300", ```
>>> ```"gdal204", "gdal203", "gdal202", "gdal201", "gdal20"). Is GDAL installed? If it is, try setting GDAL_LIBRARY_PATH in your settings.``` 

>> To resolve the above error, in the libgdal.py file
>>> Locate the libgdal.py file at \venv\lib\site-packages\django\contrib\gis\gdal\libgdal.py
>>> Add ```'gdal304'``` in the ```lib_names``` list at line 23.
>>> Above addition will change depending on the GDAL whl file version you have in steps 1 & 2.
  
  

