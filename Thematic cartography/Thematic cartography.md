Thematic cartography
===
Source: Dr.-Ing. Li Zhang, Lecture Thematic cartography  
https://www.iigs.uni-stuttgart.de/en/education/geoengine/thematic_cartography-ws/  
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