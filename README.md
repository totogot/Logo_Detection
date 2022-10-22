## Logo Detection

Repository showing a example project developed to perform logo detection in image frames. This project gives a view of how to leverage open-source packages to custome train a logo detection model and identify the presence of the logo in video imagery.

The main.ipynb contains the run code, with accompanying commentary, while the sma package contains helper functions and wrappers.

# Initial setup
The first thing you are going to want to do is set up a virtual environment for installing all package requirements into

```
$ cd C:\Users\jdoe\Documents\PersonalProjects\Logo_Detection
$ python -m venv venv
```

Then from within the terminal command line within your IDE (making sure you are in the project folder), you can install all the dependencies for the project, by simply activating the venv and leveraging the setuptools package and the setup.cfg file created in the project repo. 

Note: for IDEs where the CLI uses PowerShell by default (e.g. VS Code), in order to run Activate.ps1 you may find that you first need to update your settings such that Command Prompt is the default terminal shell - see here: https://support.enthought.com/hc/en-us/articles/360058403072-Windows-error-activate-ps1-cannot-be-loaded-because-running-scripts-is-disabled-UnauthorizedAccess-

```
$ .\venv\Scripts\activate
$ pip install --upgrade pip
$ pip install .
```

This last command will install all dependencies outlined in the setup.cfg file. ipykernel has been included to enable the main.ipynb to be run also and for relevant visualisations to be outputted also.


# Loading data

This project was built using an open-source dataset with images containing company logos, with fine-grained (annotated, including bounding boxes) labelled data set to accompany. 

While this could be developed specifically for your custom task, I used the Flickr Logos dataset. There are several versions available (e.g. FlickrLogos 47, or 32), but the easiest to find online is the FlickrLogos27: http://image.ntua.gr/iva/datasets/flickr_logos/ (Y. Kalantidis, LG. Pueyo, M. Trevisiol, R. van Zwol, Y. Avrithis. Scalable Triangulation-based Logo Recognition. In Proceedings of ACM International Conference on Multimedia Retrieval (ICMR 2011), Trento, Italy, April 2011.)

You can download the dataset as a tar archive file, and move it to the "./data/" folder in this repository.

```
tar -xvzf .\data\flickr_logos_27_dataset.tar.gz -C .\data
```

then unpack the images
```
tar -xvzf .\data\flickr_logos_27_dataset\flickr_logos_27_dataset_images.tar.gz -C .\data\flickr_logos_27_dataset
```
