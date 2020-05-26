# Thematic cartography

===

Source: Dr.-Ing. Li Zhang, Lecture Thematic cartography  
<https://www.iigs.uni-stuttgart.de/en/education/geoengine/thematic_cartography-ws/>  
Outline: Zhouyan Qiu, msqiuzy@outlook.com

## Introduction

A map is a planar, full-scale, generalized and content limited model of spatial information  
Cartography is a discipline, dealing with the conception, the production, the distribution and the field of study of maps.  

### Tasks of cartography

* Processing and transfer of spatial related information(interpretation, choice, generalization, presentation)  
* Compilation, design
* Realization, distribution

### Classification of maps

* Kind of realization
  * Analogue
  * Digital
* Producer
  * Official
  * Private
* Way of origin
  * Base map
    * the base maps deliever a part of thematic data
    * further data can be collected from other sources
  * Derived map
* Size of map scale
  * Large scales: >1:10,000
  * Medium scales: 1:10,000 ~ 1:300,000
  * Small scales: <1:300,000
* Content
  * Topographic map
  * Thematic map
    * Analytical and synthetic
    * Primary and derived(source) maps
    * Concrete and abstract maps
    * Inductive and deductive maps
    * Representation of unchangeable and changeable issues
    * Representation of bounded and continuous issues
    * Map and cartograms
    * Large scale and small scale maps
    * Single maps, map series, atlases
* Map types(method-oriented structure): Point maps, isopleth maps, areal maps, signature maps, diagram maps...

### Maps are never completely objective but they should transfer the highest level of objectivity - due to the different methods of generalization for map visualization

### Definition of digital map

![digital map](/digital.jpg)

### Definition of digital road map

![digital road map](/road.jpg)

### geodata

Data about objects, land forms and infrastructure on the earth's surface, resource.

* Essential characteristic - spatial relation
  * Geo data can be linked by its spatial relation
  * New information can be derived by using gis functionalities
  * Queries, analysis, and processing of certain questions and problems
* Describe the land scape's objects
* Two partitions
  * Geo/spatial base data
  * Geo/spatial thematic data
* Describes objects, directly(coordinates) or indirectly(relationship) referenceable by its position in space
* Information technology, geo data - combination of data
  * Geometric data(position and shape of objects)
  * Topology(spatial relations)
  * Graphic representation
  * Thematic data, attributes
* Geoinformation is a property, which has to be provided, administrated and maintained (to guarantee up-to-dateness)
* Geo information has to be managed. Besides the actual core data, metadata has to be provided as well
* specific and unique characteristics
  * Spatial relation: The information has a spatial location, e.g. by coordinates, addresses, indices or other forms of spatial reference
  * Portable: unbounded usage through world-wide networks
  * Divisibility: Information can be sent out and can be received
  * Extensibility: Value of information increases with frequency of usage
  * Compressibility: Information can be aggregated to support different application levels

## Map series

### Classification

* content
  * **Topographic maps**: landscape is represented in a characteristically simplified way(situation(building, roads, rails), waters, terrain profile, vegetation,…)
  * **Thematic maps**: phenomena and facts about the perception of the information are represented(e.g. cadastral maps, planning maps)
* Realization
  * Analogue: have to be brought into a computerized form by digitization
  * Digital: already available in a computerized form and can be imported

### modelling within map seies: can be modelled and represented by different object types and in various levels of detail

![modelling within map seies](/modelling.jpg)

### topographic maps

landscape is represented in a characteristically simplified way.  
main objects - situations(buildings, roads, rails), waters, terrain profile, vegetation and a number of other phenomena

#### topographic maps in germany

![topographic maps in germany](/germanymap1.jpg)  
![topographic maps in germany](/germanymap2.jpg)  
roman characters indicate the map scale  

* series of numbers indicate the location
  * first both for north-south-direction: 00 (=N) to 87 (=S)
  * last both for west-east-direction: 00 (=W) to 50 (=E)
* the normal release of the topographical map contains four layers
  * planimetric representation and text - black
  * waters - blue
  * contour lines - brown
  * forests - green
* ATKIS: official topographic cartographic information system(TOLG)  
![ATKIS](/atkis.jpg)  
  * DTK - digital topographic map (Topographische Karten)
  * DGM - digital terrain model (Geländemodelle)
  * DOP - digital ortho photo (Orthophotos)
  * DLM - digital landscape model (Landschaftsmodelle)
  
### thematic maps

* phenomena and facts about perception of the information
* types of the thematic maps
  * nature: geology/soils/temperature
  * anthropological: law/settlement/planning
* cadastral maps
  * land survey register maps proves the partitioning of the ground with field parts and indicates their location, size and kind-of-use
  * three parts
   ![cadastral maps](/cadastral.jpg)  
    * cadastre numbering series with survey sketches and coordinate catalogs
    * cadastral map series: field parts with their number and boundary, buildings, topographical objects and kind-of-use
    * cadastral book series: field parts with their area, ownership, location, kind-of-use and result of official land classification for valuation purposes
  * integrated AFIS – ALKIS – ATKIS-model(AAA-Model)
    * AFIS: official bench mark database(gravity, heights,...)
    * ALKIS: official land property cadastre information system
    * ATKIS: official topographic cartographic information system
* maps of settlements
  * geographical settlement maps provide information on types of settlement, structure(downtown, borderland, kind of build-up area), function(administration, industry, traffic, grassland, etc.) and formation of the settlement
  * map with large to medium scale(city maps, property maps, topographical maps) are the bases for thematic city maps
* maps for spatial planning
  * general planning: land development plan, regional plan, land use plan, local development plan  
   ![spatial planning](/spatial.jpg)  
  * department planning
    * representation of redevelopment of specific sections, e.g. transport routes, agrarian structure, recreation areas
    * large scale maps
    * technical view of departmental planning
  * GDF: geographic data file
    * standardized format for geodata in transport/traffic section
    * GDF describes a system for the exchange of digital traffic geoinformation, consider the requirements of the application in section of street transport and transport telematic
    * data structure: specified in object, attribute, and relationship catalogues
      * object/features
        * road elements/roads
        * junctions/intersections
      * attributes
        * street name
        * direction of traffic flow(DF)
      * relations: turn restrictions
      * GDF vs. ATKIS
        * GDF: integration of a junction, for each lane, there is an own road element
        * ATKIS: new object due to attribute change

## data processing

### digitizing

#### digital methods

![digital methods](/digitizing.jpg)  

* manual
  * digitizer tablets
    * acquisition of coordinate pairs
    * identification of point
    * the integrated grid provides coordinates w.r.t. the reference frame defined by the software
  * on screen digitizing
    * digital acquisition of geometry directly on the screen
    * raster data in the background are used to create a digital representation of the objects found in the raster data(e.g. satellite image)
* semi automatic
  * a line is automatically traced down within an analog map using a sensor
  * start and end of the line as well as crossroads have to be entered manually
  * advantage: faster than manual digitalising
  * disadvantage: complex and expensive hardware
* automatic
  * scanning: the analog image is transformed into a digital image(raster data)
  * raster-vector-transformation: the captured raster data(grid) is transformed into vector data. In order to derive areas, symbols and fonts for object recognition
  * pattern recognition: image processing

#### digitising hardware

digitizing workplace  
drum scanner  
flatbed scanner  

#### digitizing software: arcgis

* homogenization: geometric restrictions were applied to the result of digitization. This is to ensure quality and contour accuracy.
  * rectangularity, straightness, parallelism
  * large scale
* possible sources of error: overlap and gap
* solotions: GIS support edit-functions like complete, copy, delete,...

### data. processing

#### georeference and coordinate transformation

* importance
  * get the other points in the map as accurate as possible
  * represent new data in the right place
* georeferencing: assigns a reference system to a data set
  * geodetic datum: a set of parameters and points used to exactly define the 3D shape of the earth
  * coordinate system: consists of two or three coordinate axes and/or reference bearing within a plane or space
  * map projections: the mathematical relationship between an ellipsoidal or spherical earth model and the mapping plane. - define the transformation from a 3D earth model into 2D coordinates
* transformations
  ![transformations](/transformations.jpg)  
  * euclidian - 3 parameter, 2 points
    * translation in X and Y, rotation - 3 parameters
    * measurement with fixed scale
  * similarity - 4/5 parameter, 2/3 points
    * translation in X and Y, rotation, scale
    * standard case/ direction dependent paper distortion(scale in X and Y)
  * affine translation - 6 parameter, 3 points
    * translation, rotation, scale, shearing
    * deformation of the axes multi-parameter
  * rubber sheeting
    * all data points are adjusted in order to achieve a better correlation at a small number of known points within the data set
    * connections between elements within a dataset(topology) remain the same
    * distances between points are changed by expansion, contraction or other manipulations
    * application: paper distortion, unknown map projection and generalisation
* distortion of maps
  * analog
    * generalization
    * storage(vertically hanging maps)
    * folding of the map
    * production process
  * digital
    * map projection
    * generalization
    * incorrected coordinates
    * individual data sources

#### matching & merging

* map matching: absolute coordinates are transformed into local coordinates within the graph
* edge matching
  * comparison and adjusting of edge along the borders of the digital map or other saved units
  * goal: agreement in position, form, and attributes
* merging
  * join objects(line, polygon) from the same or different data sets into one data set
  * forms
    * geometry
      * Deletion of Duplicates
      * Changes in topology/ deletion and insertion of identical points
      * Geometric adjustment/ extension and contraction of objects
    * attributes
      * usage of segmented attributes
      * add the information as attribute tables linked to the objects - a fully automatical process is not possible because the classification of different kinds of information have to be done manually
      * choose new object segmentation
      * generalization of information
    * relations: introduction of relations between service station and road network

#### generalization

![generalization](/generalization.jpg)  

* visualization of the same information in different(usually smaller) scales
* derived from orthophoto
  * simplification, smoothing, classification, creating signatures, evaluation
* advantage - definition
  * reducing the information content of maps due to scale change, map purpose, intended audience, and/or technical constraints
* disadvantage
  * main problem: geometric distortion - streets are wider and buildings are displaced and combined
  * loss of details
* digital data storage reduction, scale manipulation, statistical classification, symbolization
* line smoothing
  * there are more coordinates contained in the data set than needed to define the line or polygon
  * decrease the number or coordinates
  * simplification of lines by mean of vector procedures
    ![simplification](/simplification.jpg)  
    * douglas-peucker line smoothing: check whether a point is outside the tolerance band. If yes, draw a straight line to the point furthest away
    <https://upload.wikimedia.org/wikipedia/commons/3/30/Douglas-Peucker_animated.gif>
    ![douglas-peucker](/peucker.jpg)  
* semantic generalization
  * creation and classification of object classes
    * content: data have to be classified by an appropriated method
      * class limits: upper and lower limit of each class
      * class interval or width and mid-point of class
    * graphical aspect: choice of an appropriated display
  * choice of a framework: geographic/geometric/administrative
  ![choice of a framework](/framework.jpg)  

### data analysis

#### aggregation: information is not only in one dataset

![aggregation](/aggregation.jpg)

#### measuring, counting, calculating

![measuring](/measuring.jpg)

#### overlay: determine whether two area objects overlap, to determine the area of overlap, and to define the area formed by the overlap as one or more new area objects

attributes are tranferred to the new objects  
boolean logic operators(And, or, not)

#### digital terrain model(DTM)

interpolation of points  
calculation of contour lines  
calulation of visibility  
3D visualization  

## Thematic maps

**map elements: graticule, map content and map margin**
![map elements](/elements.jpg)

### graticule

### map content

* Visual variables
  ![Visual variables](/variables.jpg)  
  * Map Coloring
    ![Map Coloring](/colouring.jpg)  
    * conjure up associations for cleaness
      * natural colors(forest=green, water=blue,..)
      * symbolic colors(black = coal; blue = iron; yellow = gold; climate/ temperature: red-orange-yellow = warm, blue-green = cold; …)
    * little-much visualized as bright-dark
    * symphony of colors
      * strong colors for small faces
      * subdued, neutal colors for the background
    * differentiability of the colour ranges: max 12 different colours in one map, better only 6-8
    * accurate interpretability is more important than the cartographer's favourite colors
  * map fonts
    ![map fonts](/fonts.jpg)  
    * intention of using fonts
      * conment on the topic and the visualization of the map: title, legend
      * create georeferences inside the map: geographic names, graticule
    * fonts as symbol
      * classes: systematic use of charater sets, size, style and colour
      * hierariches: systematic use of upper/lower case, size, style and brightness
      * geographic names
      * places: positioning, enlargement
    * Properties of map fonts
      * single words or small complex phrases
      * No fixed rows or columns
      * Linked with objects
      * Not only placed horizontally
      * Placed diagonal or curved type
      * Implied object ranking
      * In front of homogeneous background
      * rapidly understandable
    * Criteria for font styles
      * Simple character sets
      * Not only upper cases
      * Neither too small nor wide
      * Use bold fonts only in exceptional cases
      * Only use a few fonts within one map
      * justifiable!
    * rules for text placement
      * areal features: horizontal or in direction of greatest extension
      * linear features: parallel to the line
      * point feature: at the above right of the signature
* organization of map elements
![organization of map elements](/organization.jpg)  
![organization of map elements](/organization1.jpg)  
  * resulting in visual harmony and balance
  * avoid to place legend parts without a recognizable order principle on the map
  * legend parts should always be presented as connected blocks

### map margin

* Map title
* Legend
  * to figure out the information on the map: signs and symbols of all used points, line or areal signatures
  * to design the map: definition of the symbol, part of the editorial
  * not only abbreviation, also used as translation between cartographer and map user
  * demands on the legend
    * expalain about topic and statement of a map
      * clearly arranges, explict connection to the map
      * interconnected system
    * strcutured with hieracrical groups, e.g., in context of the feature classes
    * values are comparable to the values on the map
* North arrow or compass rose
* Map scale and scale bar
* Name of author and cartographer
* Indication of sources
* Publishing house(manufacture, editor or publisher)
* Printing press
* Year of production
* Map projection
* Copyright note
* Other texts

## Cartographic animations & current trends in cartography

### cartographic animations

#### basic of animations

![basic of animations](/animations.jpg)  
* variation
  * sychronisation
  * frequency
  * intensity
  * sequence
  * duration
  * point in time
* acousic variable
  * position
  * volume
  * ton pitch
  * sound
  * swang
  * jitter
  * rhythm
* computer animation offers the oppetunity, to leave the currently static and isolated forms of representation
* comperter animation is a sequential presentation, i.e., only the factor time is new

#### components of animation

* animation objects(=basic animation objects)
  * graphic objects - information carrier
  * camera definition(point of observation, distance, angle) displayed map detail, scale and perspective
  * source of light
* scene(frames)
  * composition of animation objects to a overall picture
  * dedicated scenes - key frames
  * inbetweens are derived
* sequences
  * all scenes depending to a particular action, are combined to sequence
  * transitions connect the different sequences
* changes
  * time series
  * parameter changes in the data pre-processing(e.g., variation of classification)
  * parameter changes in the graphical presentation(e.g., change of point of view)
* sound audio or sound track
  * additional information medium
  * steering of perception and attention

#### The animation process: Design

![basic of animations](/design.jpg)

#### The animation process: Realisation

![basic of animations](/realisation.jpg)

#### classification of cartographic animations

* morphing animation
  * transfers starting form into final form
  * represent distortions of an area due to various map projection
* path animation
  * moving an object along a defined path
  * this path is committed on an own path level within the animation program
  * an animation is generated moving the animation object along this path
* camera animation
  * for 3d animation with variable camera adjustment and light sources
  * camera flight around the earth
* colour animation
  * produced directed colour waves
  * representing continually flowing movements
* actors animations
  * leads animation objects according certain scripts on a determined background level

### current trends in cartography

#### internet cartpgraphy

* intersection of the system classes  
  ![intersection of the system classes](/system.jpg)  
* client server communication
  * take the different functions of the various GIS into account
  * Server(database+middlewave) - url - browser(client)
* map server  
  ![map server](/mapserver.jpg)  
  * static map server allows the visualization of spatial data via the Internet, clients can get prefabricated预制 maps  
  ![map server](/static.jpg)  
  * interactive map servers allow users to have an impact on the visualization e.g. the colouring  
  ![map server](/interactive.jpg)  
  * online information system, map-based information retrieval systems allow access to static or interactive maps and furthermore first simple thematic or spatial queries  
  ![map server](/online.jpg)  
  * online-GIS offers unlimited access to the data and function of a GIS  
  ![map server](/onlinegis.jpg)  
  * function-server offers GIS function and algorithms as a web-service, results are visualized by the client, often combined with a e-commerce system  
  ![map server](/function.jpg)  
  * geodata server/spatial data warehouse offers geographic data via the Internet
* products and technologies
  * GIS system: geomedia professional(Intergraph)
  * application server: geomedia webmap professional(Intergraph)
  * database management system(DBMS)
  * Web Server: Internet Information Server (Microsoft)
  * Programming/ scripting language: Active Server Pages/PHP/HTML
* current development of open geospatial consortum(OGC)
  * web map service(WMS): specification to publish spatial data as map
  * web feature service(WFS): de-facto standard for access of vertor-based spatial data
    * geodata stored within a database or files
    * harmonisation of data access by definition of a standardised interface
    * xml-based query

#### spatial data infrastructure: distributed data and services inside the internet

* worldwide: global spatial data infrastructure(GSDI)
* europe: INSPIRE
* germany: GDI
* federal states of germany

#### open street map

* collaborative project to create a free editable map of the world
* created by users worldwide

#### 3D cartography

graphic representation of a part of the ground in a perspectively inclined view with topographical information about the ground

#### mobile cartography

* theories and technologies of dynamic cartographical visualisation of spatial data and their inter-active use on mobile devices
* chanllege: get the data anywhere and any time
* small display and limited computing server: web server, readable information

#### dynamic cartography