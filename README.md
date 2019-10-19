roLabelImg ========

![image](https://img.shields.io/pypi/v/labelimg.svg%0A%20%20%20%20%20:target:%20https://pypi.python.org/pypi/labelimg)

![image](https://img.shields.io/travis/tzutalin/labelImg.svg%0A%20%20%20%20%20:target:%20https://travis-ci.org/tzutalin/labelImg)

roLabelImg is a graphical image annotation tool can label ROTATED
rectangle regions, which is rewrite from 'LabelImg'.

The original version 'labelImg''s link is
here\<<https://github.com/tzutalin/labelImg>\>.

It is written in Python and uses Qt for its graphical interface.

Watch a demo by author cgvict

![image](https://raw.githubusercontent.com/cgvict/roLabelImg/master/demo/demo4.png%0A%20%20:alt:%20Demo%20Image)

Annotations are saved as XML files almost like PASCAL VOC format, the
format used by [ImageNet](http://www.image-net.org/).

Get the original 4 points of the rotbox 
Read the label of previous image
Draw direction line

XML Format
==========

``` {.sourceCode .}
<annotation verified="yes">
  <folder>hsrc</folder>
  <filename>100000001</filename>
  <path>/Users/haoyou/Library/Mobile Documents/com~apple~CloudDocs/OneDrive/hsrc/100000001.bmp</path>
  <source>
    <database>Unknown</database>
  </source>
  <size>
    <width>1166</width>
    <height>753</height>
    <depth>3</depth>
  </size>
  <segmented>0</segmented>
  <object>
    <type>bndbox</type>
    <name>ship</name>
    <pose>Unspecified</pose>
    <truncated>0</truncated>
    <difficult>0</difficult>
    <bndbox>
      <xmin>178</xmin>
      <ymin>246</ymin>
      <xmax>974</xmax>
      <ymax>504</ymax>
    </bndbox>
  </object>
  <object>
    <type>robndbox</type>
    <name>ship</name>
    <pose>Unspecified</pose>
    <truncated>0</truncated>
    <difficult>0</difficult>
    <robndbox>
      <cx>580.7887</cx>
      <cy>343.2913</cy>
      <w>775.0449</w>
      <h>170.2159</h>
      <angle>2.889813</angle>
  <p1x>613.2307</p1x>
  <p1y>835.446</p1y>
  <p2x>470.1874</p2x>
  <p2y>864.6796</p2y>
  <p3x>374.077</p3x>
  <p3y>394.4001</p3y>
  <p4x>517.1203</p4x>
  <p4y>365.1665</p4y>
    </robndbox>
  </object>
</annotation>
```

Installation
============

Download prebuilt binaries of original 'labelImg'
-------------------------------------------------

-   [Windows & Linux](http://tzutalin.github.io/labelImg/)
-   OS X. Binaries for OS X are not yet available. Help would be
    appreciated. At present, it must be [built from source](#os-x).

Build from source
-----------------

Linux/Ubuntu/Mac requires at least [Python
2.6](http://www.python.org/getit/) and has been tested with [PyQt
4.8](http://www.riverbankcomputing.co.uk/software/pyqt/intro).

### Ubuntu Linux

``` {.sourceCode .}
sudo apt-get install pyqt4-dev-tools
sudo pip install lxml
make all
./labelImg.py
./labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]
```

### OS X

``` {.sourceCode .}
brew install qt qt4
brew install libxml2
make all
./labelImg.py
./labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]
```

### Windows

Download and setup [Python 2.6 or
later](https://www.python.org/downloads/windows/),
[PyQt4](https://www.riverbankcomputing.com/software/pyqt/download) and
[install lxml](http://lxml.de/installation.html).

Open cmd and go to [labelImg](#labelimg) directory

``` {.sourceCode .}
pyrcc4 -o resources.py resources.qrc
python labelImg.py
python labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]
```

Use Docker
----------

``` {.sourceCode .}
docker pull tzutalin/py2qt4

docker run -it \
--user $(id -u) \
-e DISPLAY=unix$DISPLAY \
--workdir=$(pwd) \
--volume="/home/$USER:/home/$USER" \
--volume="/etc/group:/etc/group:ro" \
--volume="/etc/passwd:/etc/passwd:ro" \
--volume="/etc/shadow:/etc/shadow:ro" \
--volume="/etc/sudoers.d:/etc/sudoers.d:ro" \
-v /tmp/.X11-unix:/tmp/.X11-unix \
tzutalin/py2qt4
```

You can pull the image which has all of the installed and required
dependencies.

Usage
=====

Steps
-----

1.  Build and launch using the instructions above.
2.  Click 'Change default saved annotation folder' in Menu/File
3.  Click 'Open Dir'
4.  Click 'Create RectBox'
5.  Click and release left mouse to select a region to annotate the rect
    box
6.  You can use right mouse to drag the rect box to copy or move it

The annotation will be saved to the folder you specify.

You can refer to the below hotkeys to speed up your workflow.

Create pre-defined classes
--------------------------

You can edit the
[data/predefined\_classes.txt](https://github.com/tzutalin/labelImg/blob/master/data/predefined_classes.txt)
to load pre-defined classes

Hotkeys
-------
|    |  |
|  ----  | ----  |
|Ctrl + u    |  Load all of the images from a directory    |
|Ctrl + r    |  Change the default annotation target dir|
|Ctrl + s    |  Save|
|Ctrl + d    |  Copy the current label and rect box|
|Space       |  Flag the current image as verified|
|w           |  Create a rect box|
|e           |  Create a Rotated rect box|
|d           |  Next image|
|a           |  Previous image|
|s           |  Read the Label of Previous image|
|r           |  Hidden/Show Rotated Rect boxes|
|n           |  Hidden/Show Normal Rect boxes|
|del         |  Delete the selected rect box|
|Ctrl++      |  Zoom in|
|Ctrl--      |  Zoom out|
|↑→↓← | K    |  eyboard arrows to move selected rect box|
|zxcv        |  Keyboard to rotate selected rect box|


How to contribute
-----------------

Send a pull request

License
-------

[Free software: MIT
license](https://github.com/cgvict/roLabelImg/blob/master/LICENSE)

Related
-------

1.  [ImageNet Utils](https://github.com/tzutalin/ImageNet_Utils) to
    download image, create a label text for machine learning, etc
2.  [Docker hub to run it](https://hub.docker.com/r/tzutalin/py2qt4)

