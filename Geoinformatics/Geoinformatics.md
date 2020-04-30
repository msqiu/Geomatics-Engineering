Geoinformatics
===
Source: Dr.-Ing. Volker Walter, Lecture Geoinformatics  
https://www.ifp.uni-stuttgart.de/en/teaching/geoengine/geoinformatics/  
Outline: Zhouyan Qiu, msqiuzy@outlook.com

## Introduction
### geographical information system(GIS) - IMAP of spatial data/geodata  
computer-based systems for the acquisition and update,  storage and query, analyses and simulation as well as output and presentation of spatial data  
* acquisition and update - input
* storage and query - management
* analyses and simulation - analyses
* output and presentation - presentation
### geodata: data elements which are referenced to a part of the earth
* satellite data
* aerial data
* topographic maps
* street network data - navigation systems
* thematic maps - represent information
* cadastre data
* 3D city models
### GeoTIFF: special form of tiff  
contain information about the **georeferencing** of the image and other infomation, e.g., map projection
### GIS-Environments LNSED
* Land Information Systems(LIS): systems which are developed and operated by state surveying institutes
* Network Information Systems(NIS): Facility management of networks (for example from energy, water and gas supply companies)
* Space Information Systems(SIS): systems for the decision support for planning and development
* Environmental Information Systems(EIS)
* Domain Information Systems(DIS): systems which have special applications
### What can I do with a GIS: planning, presentation, navigation, simulation, management of geodata

## Data Acquisition

### Primary data acquisition: acquisition **directly** from the object or from an image from it
* Geodesy: measurement with theodolite, total station, gps-receiver,...
* Photogrammetry: Reconstruction of objects regarding their form and position from photographic images
  * Aerial film camera with FMC(Foward motion compensation)
    * Film format 230 x 230 mm
    * Imaging at 60-90% overlap along strip, 10-30% across strip
    * example: v = 70 m/s = 250km/h, m=1:13.000, T = 1/1000 s, FMC = 70m/s * 1/1000s / 13.000 = 0.05mm
  * Film based camera and scanner  
    aerial image scanner Zeiss - SCAI : accuracy 2 μm  
  * Digital Sensor - DPA(Digital Photogrammetric Assembly)
    * pixel size 10 μm
    * resolution 8 bit
    * spectral range: blue 440-525nm, green 520-600nm, red 610-685nm, nir 770-890nm.
    * Advantages and disadvantages of digital sensors in comparison with analogue sensors
      * Advantages 3
        * higher radiometric resolution (11 or 12 bit instead of 8 bit)
        * digital process chain
        * multispectral bands
      * Disadvantages: Images have high data volume - time expensive
* Remote sensing: classification
  * Digital image acquisition with satellite systems
    * Landsat - Landsat 7 has eight bands which may be combined in various ways by assigning one band to each of the three visible channels: red, green and blue, to create a false colour image.
    * SPOT
    * IRS-1C and 1D (Indian Remote Sensing Satellite)
    * IKONOS
    * QuickBird
  * Advantages of satellite data
    * capture large areas with high repetition rate
    * no physical or administrative barricades
    * cost effective for large geographic areas and repetitive interpretations
    * multispectral images
  * Disadvantages of satellite data
    * only by low degree of cloudiness
    * not so flexible as airborne systems
    * low resolution and accuracy as by airborne systems
* Georelated and other disciplines: specific sensors, field inspections,...


### Secondary data acquisition: acquisition of already interpreted data - Map digitizing
* manual: digitizier tablets, on-screen digitizing
  * advantage
    * low hardware costs
    * high accuracy(0.075-0.25mm)
    * direct checks and error handling
    * flexibility
  * disadvantage: time intensive
  * on-screen-digitizing
    * using image processing operations, objects in the images can be enhances - support measurement
    * already measured objects can be suppressed
    * acquisition accuracy
      * Digitizing accuracy varies from 0.075 mm to 0.25 mm -> = 0.20 mm (assumption)
      * the acquisition accuracy is calculated by: = digitizing accuracy × scale
      * digititing of 1:10.000 map: 0.2mm*10.000 = 2m
  * Transformation between systems necessary in order to directly measure world coordinates at the digitizer
* semi-automatic: operator supported measurement on scanned maps
  * Prerequisite: scanned images, manual object identification, automatic measurement
  * advantages
    * automatic tracking of objects(lines, areas, symbols, text)
    * operator only has to work in case of errors
  * disadvantages: presume high quality data
* automatic: fully automatic process, pattern recognition and image understanding
  * raster-vector transformation
  * pattern recognition: numbers, letters, graphical objects, symbols
  * later checks and interactive error removal
  * special software for specific map types
### Geo basis data
* Geo-basis data in Germany: ATKIS – Amtliches Topographisch Kartographisches Informationssystem(official topographic cartographic information system)
  * DLM25: 1:25.000 (accuracy +- 3m)
  * DLM250: 1:250.000 (accuracy +- 30m)
  * DLM1000: 1:1.000.000 (accuracy +- 100m)
* Street network data
* GDF - Geographic Data File: International Standard for the acquisition and exchange of road network data
* Navigation Systems
* Volunteered Geographic Information(VGI)
  * provision of tools to create, assemble, and disseminate geographic data provided voluntarily by individuals
  * Wikimapia
  * Google My Maps
  * OpenStreetMap - a free project open to everyone to collect spatial data
    * GPS receiver - most important data source
    * images: landsat 7 images & areal images
    * local knowledge
    * import data

## Data Modeling  
reality - data model(abstraction selection) - data structure(computer readable) - file structure(physical storage)

### 4 layer model of a GIS
* external view - external model - selection of objects and relations  
transition from reality to computer system involves abstraction process. thus the model only reflects certain aspects of reality
* conceptual view - geometric topologic - thematic modeling
  * describes the transformation of the objects of the external model into computer readable data structures
$$objects<\frac{thematric}{geometry<\frac{position}{topology}}$$
  * Queries to Spatial Information System
    * give identification of the line the cursor points - geometry
    * give attributes of the area the cursor pointss - geometry+thematic
    * give all houses in the given rectangles - geometry+thematic
    * give all parcels adjacent to street - thematic
    * who is owner of house - thematic
* Metric
Definition: a distance function d: $X \times X \Rightarrow \Re_{0}^{+}$ is a metric if the following three conditions are fulfilled for all $(P, Q) \in X \times X:$  
One dimension  
$\sqrt{(q-p)^{2}}=|q-p|$  
Three dimensions  
$d(p, q)=\sqrt{\left(p_{1}-q_{1}\right)^{2}+\left(p_{2}-q_{2}\right)^{2}+\left(p_{3}-q_{3}\right)^{2}}$  
n dimensions  
$d(p, q)=\sqrt{\left(p_{1}-q_{1}\right)^{2}+\left(p_{2}-q_{2}\right)^{2}+\cdots+\left(p_{i}-q_{i}\right)^{2}+\cdots+\left(p_{n}-q_{n}\right)^{2}}$
* logical view - data relation model - caption
* internal view - how you store data

### Different types of GIS
![gis](gis.jpg)
* raster GIS: store and analyses raster data
* vector GIS: store and analyses vector data
* hybrid GIS: store and analyses raster and vector data
* advantages and disadvantages of raster and vector data
  * simple strcuture - complex structure
  * large amount data - compact data structure
  * positional presition depends on resolution - precise coodinate positions through continous coordinate space
  * graphical representation is less aesthetical - accurate graohical representation
  * weak topology - complete encoding of topology
  * various kinds of spatial analysis are easy - overlay operation are difficult to implement

### 2.5D and 3D Data
* 2.5D: for every Position (x, y) exactly one z-Value (Surfaces)
* 3D: one (x, y) Position can have several z-Values (Bodies or Solids)

### Modeling of Surfaces
* Surface Reconstruction with Polynoms: only simple forms are possible
* Surface Reconstruction with Irregular Triangulated Networks (TIN)
  * TIN - triangulated irregular networks
    * network of the triangules connected together to create a 3D surface with no overlaps and no gaps
    * analysis of a surface's slope and aspect and for modelling 2.5D data.
  * The height at a position (x, y) is calculated by interpolating in the corresponding triangle - interpolatio in triangles
  * **brute force triangulation**  
  ![brute force triangulation](brute.jpg)  
    * triangulation
      * calculate the distance between all point pairs: n points -> n(n-1)/2 cost
      * search for minimum distance and delete all distance which larger that distance
      * calculate with 1 until no line intersections
    * pros and cons
      * easy implyment
      * good results
      * high computing time
    * Linear Interpolation in Triangles $z = f(x, y) = a_0 + a_1x + a_2y$

## Data Analysis