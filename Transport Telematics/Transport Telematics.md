# Transport Telematics

===
Source: Dr.-Ing. Martin Metzner, Transport Telematics  
<https://www.iigs.uni-stuttgart.de/lehre/geoengine/transport_telematics-ws/>  
Outline: Zhouyan Qiu, msqiuzy@outlook.com

## introduction

### motivation

* telematics is transportation and processing of information and advanced telecommunication services - long distance data exchange
* transport telematics is acquisition, processing and transmission of transport relevant data and information
* application: traffic guidance systems, driver assistance systems
* why transport telematics: ensure mobility
  * enhancement of safety
  * increase of efficency
  * reduction of adverse impacts on environment

### obstacles for transpot telematics

* supply of necessary data with sufficient quality
* organizational and legal barriers/vagueness
* refinancing of development costs of telematic systems
* cost-covering operation of telematic services
* missing harmonisation and standardisation
adverse impacts due to incresing complexity and cross-linking of the components

### intelligent transport systems(ITS)

add information and communication technologies to transport infrastructure and vehicles

### Functional architecture of a navigation system

![navigation](navigation.jpg)

### data & information

data: a formalized collection of facts, concepts, and instructions, usable for communication or processing by humans or automated methods  

information: purpose-oriented knowledge necessary for acting to reach the intended aims  
information results from the application of rules and instructions on data

## digital maps

### classification of maps and geodata

* format: raster data, vector data
* type: cadastral map, city map, aerial photos/satellite images
* coordinate system/map projection: Gauß-Krüger/WGS84/UTM
* content: features, attributes
* source: public, commercial

### GDF

#### data structure

![GDF](gdf.jpg)  

* objects/features
  * road elements/roads
  * junctions/intersections
* attributes
  * street name
  * direction of the traffic flow(DF)
* relation
  * turn restrictions

#### division into three levels

![division](division.jpg)  

* geometry - level 0
  * basic geometry/topological primitives, nodes, edges and faces
  * coordinates define spatial arrangement
* simple features - level 1
  * points, lines and areas
  * every feature represents one object given in reality
* complex features level 2
  * put together using simple features
  * description of the road network from the view of the driver

#### acquisition of road geometry

![road geometry](road.jpg)  

* road element consists of edges
* edges represents the centreline of the carriageway
* separated carriageways - two road elements are captured
* edges have to be completely inside the carriageway

#### modelling of traffic flow - directed graph, direction by digitization


#### attribute model

* each feature can carry any number of attributes
* attribute belongs to a feature, has exactly one type and one value(but can be complex)
* concepts: complex, segmented, time-dependent

#### segmented attributes - different parts of the object

![segmented attributes](segmented.jpg)  

* absolute segmentation: related to the length in the geometrical representation(from a defind start point)
* relative segmentation: related to measured length by a percentage value
* advantage: less notes, less processing time

#### data model for semantic relations

* connection of two (n) objects
* relationship contains attributes, a name and a code such as features
* with relationships turns are modelled
  * prohibited manoeuvre
  * restricted manoeuvre
  * priority manoeuvre

#### topology is a branch of mathematics that is an extension of geometry

![topology](topology.jpg)  

* 3 levels: geometry(line, node, equal coordinate) - direction of traffic flow - relations
* topology from geometry
  * same nodes from two edges
  * two areas border on the same edge
* topology from thematic
  * road element is specified as one way by attribute DF
  * prohibited manoeuvre by relationship

#### GDF

* Data exchange format: simplified representation of the Media Record specification for line features
* one standard - two maps
  * different interpretation of the rules for acquisition
  * different acquisition tasks
  * usage of different data sources
  * completely independen acquisition
* acquisition
  * secondary data captureing by ortho photos, topographical maps and import of digital data bases
  * adding primary data capturing is necessary
    * attributes of road elements
    * turn restriction
    * signage
  * application of mobile mapping vehicles
    * metrological acquisition of road geometry by an positioning system
    * acquistion of road related attributes and relationships by geo coded video images

#### ATKIS - official topographic cartographic information system

* object-based, signature-based and picture-based presentation of the earch's surface
  * digital landscape model(DLM)
  * digital topographic map(DTK)
  * digital terrain model(DGM)
  * digital ortho photo(DOP)
* object catalogue - essential data are missing(e.g. oneway streets, turn relations): ATKIS data are not suitable for navigation and routing  
  ![object catalogue](catalogue.jpg)  
* feature representation of roads  
  ![feature representation of roads](roads.jpg)  
  * road
    * linear
    * complex feature composed of centre lines(represent spatial basic feature)
  * road with divided carriageway
    * linear and areal
    * road is a complex feature composed of carriageway axes(for both directions) and a centre line(midway division)
    * areas between are classified with feature type(road traffic)

#### GDF & ATKIS - difference in data model

![GDF & ATKIS](difference.jpg)  

### OKSTRA - Feature catalogue for road engineering and transportation

* realization of a continuous information flow by data exchange without lost of any data and information
* concerned parties
  * surveying agencies, road administration, federal government, federal states and municipalities
  * planning and engineering offices, commercial suppliers of map series

### Openstreetmap - more users, more detailed, may have mistakes, license model

* collaborative project to create a free editable map of the world
* OSM has all rights to the data
* congested urban areas are good acquired, other regions are acquired only partly or not at all
* data Model
  * own data model realized in XML
  * points(node), lines(way) and relations are available
  * no restrictions on attributes for the objects - differend by tags
* data format
  * export in common raster data - jpg, png, pdf
  * export in vector based format(XML)
  * convert OSM in common geodata format like GML, KML, SHAPE...
* license - open content license, the author has no copyright

### NDS - navigation data standard

* NDS association member: car manufacturers, application/compiler developers, map data providers, service providers
* comparing to GDF: new support for road conditions(more lines to represent the road)
* challenge
  * localize the user's own car
  * to plan the path on streets
* Open Lane Model
  * Improves localization and path planning on routes
  * stores lane topology and high-precision geometries of up to 1-cm resolutions
  * assign standard attributes, such as speed limits, to lanes with high accuracy
  * the model shows boundaries, such as walls or tubes and colored lane markings
  * complex intersections are described by a sophisticated connectivity model
  * faces two challenges of autonomous driving: to localize the user’s own car and to plan the path on streets

### geographic data

#### dimension

 * 0D - POI - point
 * 1D - road - line
 * 2D- area of soil - polygon
 * 2.5D - (x, y, name, height)
 * 3D (x, y, z) TIN

#### scale

 * scale is in the detail - spatial resolution or the level of detail in data
 * scale is about extent - large scale project covers large area
 * scale of a map - representation fraction: the ratio of distance on the map to distance on the ground

#### georeference

* requirement
  * unique, one location associated with a given georeference
  * shared meaning
  * persistent through time
* georeference without metric
  * problem: name change
  * postal address, postal code...
* georeference with metric
  * problem: change of the definition of the system + yearly continious changes
  * lablic land survey system, latitude/longitude...

#### types of attributes

* nominal: identify or distinguishi one entity from another, includes numbers, letters, and even colors
* ordinal natural order, averging make no sens
* interval: the diference make sense: the scale of Celsius temperature
* ratio: eg. weight
* cyclic: categories beyond these four mention above(e.g. traffic flow direction)

#### geometric primitives: point, line, polygon

#### topological primitives: node, edge, face

#### geometry classes defined by the OGC: definition is used in databases(like PostGIS, MYSQL,...)

### data model

* a set of constructs for describing and representing selected aspects of the real world in a computer
* provides systems developers and users with a common understanding and reference point
* there is no single type of all encompassing GIS data model that is best for all circumstances
* 4 levels of abstraction relevant to GIS data models  
  ![4 levels of abstraction relevant to GIS data models](levels.jpg)  
  ![ 4 levels of abstraction relevant to GIS data models ](models.jpg)  
* object-oriented concepts in GIS
  * an object is a self-contained package of information describing the characteristics and capaibilities of an entity
  * an interaction between objects is called a relationship
  * a collection of objects of the same type is called class.
  * each class/object might include properties defining its state
  * each class/object might include methods defining the behavior
  * three key facets of object data models
    * encapsulation: describe the fact that each object packages together is a description of its state and behavior
    * inheritance: the ability to reuse some or all of the characteristics of one object in another object
    * polymorphism: describe the process whereby each object has its own specific implementation for operations
* database management system(DBMS)
  * relational(RDBMS)
    * set of tables, each of a 2D list of records containing attributes about the objects under study
    * simple, flexible, and useful structure
  * object(ODBMS) - address weaknesses of RDBMS
    * the inability to stor complete objects directly in the database
    * deal with rich data types such as geographic objects, sound and video
    * poor performance of RDBMS for many types of geographic query
  * object-relational(ORDBMS)
    * a RDBMS engine with an extensibility framwork for handling objects