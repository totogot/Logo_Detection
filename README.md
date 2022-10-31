# Logo Detection

Repository showing a example project developed to perform logo detection in image frames. This project gives a view of how to leverage open-source packages to custome train a logo detection model and identify the presence of the logo in video imagery.

The main.ipynb contains the run code, with accompanying commentary, while the sma package contains helper functions and wrappers.

This repo was used to train a Faster RCNN model using a custom tagged dataset of images featuring the Petronas company logo, before using the model to nfer the presence of the logo in a video of Formula 1 racing. The intention is to see how often the logo appears in the frames, and how much screen space the logo takes up.


## Initial setup
The first thing you are going to want to do is to clone this repository. To do this, you can use CLI to do the following:
```
$ cd C:\Users\jdoe\Documents\PersonalProjects
$ git clone https://github.com/totogot/Logo_Detection.git
```

Next set up a virtual environment for installing all package requirements into
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

This last command will install all dependencies outlined in the setup.cfg file. 
Note: ipykernel has been included to enable the main.ipynb to be run also and for relevant visualisations to be outputted also.


## Image data 

This project was built using a custom made training dataset with 50 images containing the "Petronas" company logo, with fine-grained (annotated, including bounding boxes) labelled data obtained through manual tagging myself. 

It is worth noting that 50 logos is unlikely to lead to a high degre of accuracy, and in the real world you would anticipate providing a far larged dataset during training in order to develop a robust and accurate model for deployment. However, for the purpose of showing an end to end project, and to reduce the time and compuational power required for training, I deemed 50 images as sufficient.


## Labelling data

To label the images myself, I decided to utilise LabelStudio (https://labelstud.io/), as it is a free open-source VoTT (Viual Object Tagging Tool), with simple download.

To get started simply open up a terminal (in my case I use Windows Command Prompt), and execute the following commands:
```
$ pip install label-studio
$ label-studio start
```

This will install the LabelStudio requirements and then launch the programme in a new browser window. From there you should set up your tagging task, following the instructions found here (https://labelstud.io/guide/index.html#Quick-start). Once you have completed your tagging task, you can export the annotated dataset (in one of many different formats). 

For the purpose of this project, and to ensure that only one single annotation file is created, I opted for the COCO JSON format