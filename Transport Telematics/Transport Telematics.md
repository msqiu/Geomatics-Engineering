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

#### GDF, Geographical Data File

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

### requirement engineering(RE)

* objective
  * selected aspects for spatial data related projects are to understand
  * aspects of functional requirement analysis(requirement engineering, data cost, and data quality) are important
* requirements engineering - design - implementation - final check
* important techniques and methods
  * research techniques - analysis of requirements
  * modeling methods - requirements are documented and structured(e.g. UML)
* Customers requirements regarding the system are to be documented completely, free of contradictions and auditable within the summary of the specifications(detailed description of the services)

### data quality

* definition
  * totality of characteristics of an entity that bear on its ability to satisfy stated and implied needs
  * Degree to which a set of inherent characteristics fulfils requirements
  * avaliability, completeness and correctness
* quality model
  * dependability characteristics - discribe the time related aspect of information quality
    * availability, up-to-dataness
  * integrity characteristics - discribe the applicability of information
    * completeness, consistency, correctness
  * accuracy characteristics - describe the limitation of accuracy and resolution of measurement and interpretation
    * metric accuracy, semantic accuracy
  * Possible sources of error with GIS analyses
  ![sources of error](error.jpg)  

### data costs

* basis costs: hardware, soft ware, personal costs
* project specific costs

### topology

#### intruduction

* application
  * network: electric power supply, natural gas piprline, water supply/waste water, transportation networks
  * location: optimally locating p facilities to serve n customer demand at n > p locations
* topological properties
  * distinction between point, line, area (and volume)
  * adjacency, including the touching of land parcels, counties, and nation states
  * connectivity, including junctions between streets, roads, railroads, and rivers
  * containment, when a point lies inside rather than outside an area

#### OGC(open geospatial consortium) OpenGIS Simple Features Specification

* Spatial Relations - a and b are two geometries; I(x) ist the interior of x; dim(x) is the dimenson of x, or maximum dimension if x is the result of a relational operation
  * Spatially equal to: $a=b$
  * Spatial disjoint: equivalent to a $\cap \mathrm{b}=\emptyset$
  * Spatially touches: equivalent to $[\mathrm{a} \cap \mathrm{b} \neq \emptyset \text { and } \mathrm{I}(\mathrm{a}) \cap \mathrm{f}(\mathrm{b})=\emptyset] ;$ does not apply if a and b are points
  * Spatially crosses: equivalent to $[\operatorname{dim}(|(a)) \cap \operatorname{dim}(|(b))<\max \{\operatorname{dim}(|(a)), \operatorname{dim}(|(b))\} \text { and } a \cap b \neq a \text { and } a \cap b \neq b]$
  * spatially contains: [a contains(b)] is equivalent to [b within(a)]
  * spatially within: within(b) is equivalent to $[a \cap b=a \text { and }|(a) \cap|(b) \neq \emptyset]$
  * spatially overlaps: equivalent to $[\operatorname{dim}(|(a) \cap|(b)=\operatorname{dim}(|(a))=\operatorname{dim}(|(b)) \text { and } a \cap b \neq a \text { and } a \cap b \neq b]$
  * spatially relates, tested by checking for intersections between the interior, boundary and exterior of the two components
* Spatial analysis
  * the shortest distance between any two points in the two geometries as calculated in the spatial reference system of this geometry
  * Buffer: all points whose distance from this geometry is less than or equal to a specified distance value
  * the convex hull of this geometry. For point sets in the plane the convex polygon of smallest area that completely encloses the set (it may also be used for line and polygon sets)
  * the point set intersection of the current geometry with another selected geometry
  * the point set union of the current geometry with another selected geometry
  * the point set difference of the current geometry with another selected geometry
  * the point set symmetric difference of the current geometry with another selected geometry (logical XOR)
* Dimensionally Extended Nine - Intersection Model - DE-9IM
  ![Dimensionally Extended Nine](dim.jpg)  

#### topology of a network

* techniques developed for graphs
  * measuring connectivity
  * finding shortest path
  * Network connectivity
  * Network distance
  * Traveller salesman problem
  * Distance analysis
  * Optimum “place” analysis
* terminology  
    ![terminology](terminology1.jpg)  
    ![terminology](terminology2.jpg)  
    ![terminology](terminology3.jpg)  
    ![terminology](terminology4.jpg)  
  * GDF
    * 0 Dimensional: point, node(vertex), junction
    * 1 Dimensional: line(polyline), edge, road elements
    * 2 Dimensional: polygon, face, area
* incidence and adjacency  
  ![incidence and adjacency](ia.jpg)  
  * Incidence names the meeting of different topologic primitives
    * Incidence matrix
      * $B(i, j)=1$ if edge i starts in node $j$
      * $B(i, j)=-1$ if edge i ends in node $j$
  * Adjacency names the meeting of same topologic primitives
    * Adjacency matrix
      * Main diagonal contains number of adjacent nodes
      * Nodes adjacent to each other -1
      * symmetrical
    * The adjacency matrix A can be calculated directly from the incidence matrix
  * Pointer structure
    * edges: Edge_Id \{Node_Id, Node
    * nodes: Node_Id \{Edge_Id, Edge_Id, $\ldots \ldots .\}$
* Requirements of transportation network
  * Topological correct street network: Feature model: Junction / Road elements
  * Network is „orientated“ For each road element a start- and end-junction is defined
  * Attributes can be modelled “orientated”
  * The concept of segmented attributes is realised
  * Semantic relations are supported to define manoeuvres
* digitalization of a street network
  * Hints for manual digitization
    * Produce a correct topologic geometry
    * Set junction points first! (Time consuming)
    * This is definitely necessary at complex crossings!
    * At simple crossings you may use GIS functions to generate the crossings!
  * Complex crossing
    * set all juction crossings
    * snap on the crossings
  * simple crossing
    * digitizing the roads
    * generate the crossings automatically
* network analysis
  * Some key optimisation problems in network analysis
    * Hamiltonian circuit (HC) - all nodes, bussiness man  
    ![Hamiltonian circuit](hc.jpg)  
    If a cycle exists from a given vertex that passes through every other vertex exactly once it is called a Hamiltonian circuit. Testing for the existence of Hamiltonian circuits in a graph is known as the Hamiltonian circuit problem (HCP).
    * eulerian circuit(EC) - all network at one time, postman
    ![eulerian circuit](ec.jpg)  
    A circuit in a directed graph that visits every arc exactly once. A condition that a graph contains an Eulerian circuit is that the number of arcs arriving at every included vertex, i, must be the same as the number of arcs leaving vertex i
    * shortest path(SP) - time or distance
    A path between two vertices that minimises a pre-defined metric such as the total number of steps, total distance or time, is called a shortest path. Hence this term is relative to the metric applied and even then may not be unique for any given network. Determination of shortest paths is often described as shortest path analysis (SPA). This is perhaps the central computational problem in network analysis. There are many variants of this problem, including finding the 2nd, 3rd… nth shortest path, finding the shortest path from a given node to all other nodes, and finding the longest path. Can be solved in linear time or better
    * spanning tree(ST)
    Given a fixed set of vertices, find a set of edges such that every vertex is connected and the network contains no cycles. Many spanning trees are possible for a given vertex set
    * minimal spanning tree(MST)  
    ![minimal spanning tree](mst.jpg)  
    Find a (Euclidean) spanning tree of minimum total length. Typically this will be unique, but uniqueness is not guaranteed. Solvable in near linear time
    * Steiner MST, Steiner tree
      * As per the MST but with additional nodes permitted that are not co-located with the original vertex set.
      * In the (spatially) constant cost model, each additional point (known as a Steiner point) will be placed intermediate to three existing vertices and will provide a connection between these via three branches that are equally spaced (i.e. at 120 degrees) about the Steiner point.
      * Steiner points are added to the MST, replacing MST links, if the total network length is reduced by their inclusion.
    * Travelling salesman problem (TSP)  
    ![Travelling salesman problem](tsp.jpg)  
      * Given a set of vertices and symmetric or asymmetric distance matrix for each pair of vertices, find a Hamiltonian circuit of minimal length (cost).
      * Typically the start location (vertex) is pre-specified and the vertices are not necessarily assumed to lie on a pre-existing network. If certain nodes must be visited before others, the task is known as a sequential ordering problem (SOP)
    * Transportation problem, Transshipment problem
      * The general problem of completely servicing a set of target locations with given demand levels from a set of source locations with given supply levels such that total costs are minimised is known as the transportation problem.
      * The unit cost of shipping from each supply point to each demand point is a key input to this problem specification. This problem is an example of a Minimum Cost Flow Problem (MCFP). A generalisation of the transportation problem is the trans-shipment problem. In the latter case flows from sources to targets can go via trans-shipment points, e.g. factories to warehouses to customers, rather than simply direct to customers
    * Vehicle routing problem (VRP)
      * This class of problems relates to servicing customer demand (e.g. deliveries of fuel to retail garages) from a single depot, where each vehicle may have a known capacity (CVRP).
      * If capacity is not restricted the problem is known simply as a vehicle routing problem (VRP). The number of vehicles and the number of tours of subsets of nodes are variables. The customer locations, depot location and customer demand levels are assumed to be known. The problem is to minimise the overall length of the tours, subject to the constraints.
      * There are many variants of this problem, notably those in which there are pre-defined time windows for deliveries, problems involving pickups and deliveries, problems involving a series of depots, problems where demand is dynamically variable, problems in which link capacity constraints exist and hence may become congested, and problems where customer locations are generalised rather than fixed.
    * Arc routing problem (ARP)
      * Given a network (typically a street network or subset of a street network) find a route that completely traverses every edge, generally in both directions, that has the least cost (distance or time) subject to selected constraints (e.g. cost of turning).
      * This problem applies to street cleaning, snow-ploughing, postal deliveries, meter reading, garbage collection etc. The capacitated version of the problem is known as CARP.
    * Facility location: p-median/ p-centre/ coverage
      * A collection of problems where the objective is to optimally locate one or more facilities within a network in order to satisfy customer requirements (demand, service level).
      * The most commonly cited problem is minimisation of total (or average) travel cost/time to or from customers (the p-median problem). Minimisation of maximum distance or time is known as a p-centre problem. A related set of problems seeks to ensure that all customers can be served within a fixed upper time or cost, or at least, as many as possible are served within a fixed time or cost. These are known as coverage problems.
      * They are not explored further in this lecture, mainly because their very restrictive constraints tend to generate solutions that are too costly or ineffective to be implemented in practice. Customer demand is often assumed to be located at vertices in which case p-median solutions for p facilities serving n>p customer sites will always result in the facilities being located at network vertices (although this solution may not be unique). It is the network equivalent of the plane or free-space median location problem — a form of location-allocation task whereby facilities are located and customers are allocated to facilities.
  * Sample network analysis problem parameters
    * Objective function: How do we measure the"length" of a path? Options include the Euclidean length, Lp length, link distance/time/cost etc
    * Constraints on the path: Are we simply to get from point s to point t, or must we also visit other points or other regions along a path or cycle?
    * Input geometry: What types of obstacles or other entities are specified in the input map?
    * Dimension of the problem: Are we in 2D-space, 3D-space, or higher dimensions? Typically within GIS we only consider 2D, but transport networks may not be planar
    * Type of moving object: Are we moving a single point along the path, or is movement specified by some more complex geometry? In GIS off-road vehicular modelling is usually performed using Accumulated Cost Surface (ACS) or Distance Transform (DT) procedures applied to grid datasets rather than vector networks. Constraints on routes may also be applied to vehicles of particular sizes, types or weights (e.g. height restrictions)
    * Single shot vs. repetitive mode queries: Do we want to build an effective data structure for efficient queries? Many network problems involve very similar searches — for example determining an alternative route (2nd, 3rd best)
    * Static vs. dynamic environments
      * Do we allow obstacles to be inserted or deleted, or do we allow obstacles to be moving along known trajectories?
      * Flow and event dynamics may also be important considerations
    * Exact vs. approximate algorithms
      * Are we content with an answer that is guaranteed to be within some small margin of optimal?
      * Larger problems in many cases cannot be solved exactly in a finite amount of time. Ideally real-world problems should be solved to within a specified level of the optimum for suitably defined subset problems
    * Known vs. unknown map
      * Is the complete geometry of the map known in advance, or is it discovered on-line, using some kind of sensor?
      * Typically the geometry is known (map-able) in advance, but flows or events may not be
* routing algorithm
  * finding an algorithm to calculate an optimal path is solved
  * The main problem is the organisation of mass data to guaranty a quick data access
  * Traveling-salesman problem (TSP)
    * a number of places must be visited in a tour from the depot and the distances between pairs of places are known
    * select the best tour out of all possible orderings, in order to minimize the total distance traveled
    * if n places to be visited, including the depot, then there are (n-1)!/2 possible tours
    * this number grows very rapidly (n=5 - 12; n=8 - 2,520; n=10 - 181,440)
  * Not the best result will be achieved in some cases. There will be a optimised result
    * In big datasets the calculating time of such algorithms increase
    * Data access strategies (Quadtree, ... ) has to be used to get response time
    * Heuristics are implemented to get acceptable response time
  * Not the complete network will be used for the optimisation - restriction
    * Direction to the destination
    * Network hierarchy
  * Attributes associated with the network's links, such as length, travel speed, restrictions on travel direction, and level of congestion are often taken into account
  * The path that is strictly shortest is often not suitable, because it involves too many turns or uses too many narrow streets, and algorithms will often be programmed to find longer routes that use faster highways, particularly freeways

## location referencing - transfer attributes/information between two maps

### exchange of georeferenced information

* Infrastructure to vehicle
  * Map updates
  * Traffic information
  * Road safety feature updates
* Vehicle-to-vehicle
  * Problems with own vehicle
  * Detected problems on the road
  * Information from other vehicles (hand-on)
* Vehicle-to-Infrastructure
  * Accident information
  * Detected traffic jams
* referenced on digital road maps
  * Pre-coded location references (e.g. TMC used by TPEG)
  * Dynamic location references (e.g. ISO 17572-3 [AGORA], OpenLR®)

### motivation - tranfer map information automatically

location is described with geometry, topology, and semantics

### problem

* sender and receiver may use different maps
* Different representation of the road network
  * The road elements (named "links") differ between different maps
  * Missing or surplus objects
  * Different object IDs
  * Different locations / positions

### TPEG (Transport Protocol Experts Group)

* protocol specification for the exchange of RTTI (Real Time Traffic Information)
* provide road users with comprehensive, up-to-date traffic and traveler information across multiple transport modes
* aim to describe real-world events and situational data with their spatio-temporal scope
  * geographical location
  * point in time resp. duration associated with
    * municipal traffic management systems
    * public transport operation
    * weather observation
* distributed to vehicle-based and other mobile client devices through the RDS-TMC system
  * RDS: radio data system
  * TMC: traffic message channel
* use DAB(digital audio broadcast)/DAB+ for transmission
* further distribution of RTTI data is obstructed because of the limitation of the TMC
  * low and restricted bandwidth and capacity
  * only static positions
  * low coverage of the road network
* besides the classis area of applications of TMC, TPEG support information resp.
  * public transport
  * weather
  * traffic flow (incl. forecast)
  * parking information, etc

### ISO 17572–2 Pre-coded Location References

* regulate static Location Referencing methods in general
* disadvantage
  * we need this system in every static navigation system
  * no possibilities of updates for the table in the car-system
  * only part of the network is included (generally the highways and motorways)
* alternative: ISO 17572 Family

### Location referencing

* Exchange of Road Safety Attribute(RSA) updates independent from certain maps
  * not as a map object's attribute
  * information about its location / extend
    * Locations of intersections
    * Locations of other important shape points
    * Attributive information
      * Street names
      * Road class
      * Road type
    * Topological information
* Introduction
  * Location Reference (LR) is a clear identification of a spatial object
  * one spatial object of the real world is represented by one element - feature in a spatial database
  * In Intelligent Transport Systems (ITS) especially parts of the transportation network were coded as LR
  * The LRs will be used to share and exchange information between databases

### ISO 17572–3 Dynamic Location References (AGORA-C)

* produce Location Reference at the point in time at it is required
* on-the-fly Location Referencing
* fundamental workflow
  * produce Location Reference from the information of the sending map (geometry, topology, semantic)
  * often use of binary data format for efficient data transfer (encoded)
  * transfer of Location Reference to the receiver (normally via Internet)
  * decoding of the Location Reference in the target map - information of traffic only
  * after decoding the Location Reference is not longer needed in the target map and will be deleted
* Mapbased Location Referencing
* The AGORA Project
  * objective: develop a method for generating Location References, which is robust within differences in databases (data model or content) on part of the submitter or receiver(hit rate of minimum 95%)
  * Code-Length and bandwidth not defined
* AGORA – the principle
  * Intersection Locations (ILOCs) - Insufficient results
  * Small group continues improving ILOC - Start of AGORA
  * Inclusion of 2 additional approaches - Pivot Point (Siemens VDO) & GoodLane (Bosch)
* AGORA - Approach
  * Combination of three existing methods
    * Advanced ILOC(Intersection Locations)
    * Pivot Point approach (Siemens VDO)
    * GoodLane approach (Bosch)
  * Integration of the methods leads to complex algorithm
    * Four Point classes
    * Five Location Reference Types
    * 34 rules for Encoding of Locations
    * Less efficient binary data format
  * Implementing and testing
    * hit rate of 95% reach
    * average code size was unduly large (about 250 bytes)
  * encoding rules were perceived as rather complex
* AGORA – Advanced ILOC Approach
  * first, Intersection Locations (ILOC) coded  
  ![first, Intersection Locations (ILOC) coded](first.jpg)  
  attributes: speed limit, location coordinates, direction, type​​
  * pivot point: Intersection Locations often modeled very different in the maps. Therefore: Points coded outside of ILOCs (Pivot = axis)  
  ![pivot point: Intersection Locations often modeled very different in the maps. Therefore: Points coded outside of ILOCs (Pivot = axis)](pivot.jpg)  
  * good lane: If the coded geometry is simple (Shape Point 1 and 2) than, additional points will be chosen and added to the ILOC  
  ![good lane: If the coded geometry is simple (Shape Point 1 and 2) than, additional points will be chosen and added to the ILOC](good.jpg)  
  * AGORA Location Referencing method combines the three further mentioned approaches  
  ![AGORA Location Referencing method combines the three further mentioned approaches](combines.jpg)  
* An AGORA-C Location Reference consists of
  * list of all points along the path, which describe the coded element in the sending map
  * elements - lines
  * the sorting of the points describe the logical order of the points along the path
  * if the path along a link with physical cut-off between different lanes, the LR should follow the lane which will be referenced
  * Each point have to belong to one or more of the following categories according to its meaning - Location point
    * the shape of the LR is described by the sequence of the Location Points
    * Start and end point of a LR is automatically also a Location Point
    * further Location Points must inserted in that way that the difference between the route length and the air line distance between the Location Points is not larger than 10m or 5% of the air line distance
    * Location Points are described by longitude and latitude resp. WGS 84
  * Intersection point
  ![Intersection point](intersection.jpg)  
    * A Location Point is also a Intersection Point, if one or more of the following attributes changes
      * Functional Road Class, FC
      * Form of Way, FW
      * Road descriptor, RD (Official national Road-Number, apart from that the road name)
      * Driving Direction, DD
    * within complex intersections, the intersection point is inserted at the first branch off inside the intersection
    * additional Intersection Points outside the object, which will be coded, will inserted, if they are along the road network less than Dsearch−area away from the end of the Location Reference  
    ![additional Intersection Points](additional.jpg)  
    * Intersection Point Attribute
      * Functional Road Class, FC
      * Form of Way, FW
      * Road descriptor, RD (Official national Road-Number, apart from that the road name)
      * Driving Direction, DD
      * Number of intermediate Intersections (NIT)
      * Intersection Type (IT)
  * Routing point
    * A Location Point is also a Routing Point, if the road segment which determine the azimuth, has the minimum length of Dm−bearing
    * An Intersection Point is also a Routing Point, if the connected side road segments has the minimum length Dm−co−angel
    * the first and the last point of the LR has to be a Routing Point. If they do not fulfill the length requirements the next point outside the LR which fulfill the length requirements is chosen
    * The LR is extended with the additional points
    * the road segment between two following Routing Points is clearly defined, if the following three requirements are fulfilled  
     ![requirements](requirements.jpg)  
      * length of the segment not longer than the double Euclidian distance between those rooting points
      * the segment have the lowest weighted distance (factor * distance) between the routing points The factor is defined by the functional road class
      * the weighted distance of every fully different alternative route between those points have to be 25% larger than the segment itself
    * if these requirements are not fulfilled, additional Routing Points will be defined
    * Routing Point Attribute  
    ![Routing Point Attribute](rpa.jpg)  
      * Bearing, BR
      * Accessible for Routing flag (AFR)
      * distance to the next Routing Point (PD), calculated along the route
      * Parallel Carriageway Indicator (PCI)
      * Side road signature (for the side road with the smallest change of the bearing)
      * change of bearing (= Connection angle, CA)
      * Accessible for Routing flag (AFR)
* An AGORA-C LR has the following attributes:
  * Location Direction (LD)
    * aligned, if the points describes the same lane direction
    * both, if the LR includes both directions
  * Location Type (LT)
    * Intersection
    * limited access road
    * ferry
    * housing area
    * Point-of-interest (POI)
    * road

### Open Location Reference

* Definition
  * Open, Compact and Royalty-free Dynamic Location Referencing
  * dynamic location referencing method which enables reliable data exchange and cross-referencing using digital maps of different vendors and versions (TomTom)
* Objectives
  * free and successful exchange of location-relevant content through introduction of a universal standard
  * To enable market growth and enhance the successful deployment of a wealth of ITS and LBS applications, free of license fees and supported by leading industry players
  * Quicker enhancement by the expert community, thanks to the Open Source Model
* Collaboration Model without standardized dynamic location referencing  
  ![Collaboration Model without standardized dynamic location referencing](collaboration.jpg)  
* OpenLRTM was originally designed for transferring traffic information from a centre to in-vehicle systems and taken into account
  * Map vendor and version independency
  * Covering all roads, including urban and low level roads
  * Minimum bandwidth usage
  * Communication channel independency
  * Maintenance independency
  * Potentially capable to replace TMC codes in future
  * Encoding and decoding independent from system operation location e.g. Service centre, in-vehicle systems, etc.
* Main idea: describing a line location completely with a concatenation of (several) shortest-paths
  * The concatenation of such shortest-paths shall cover the location completely
  * Each shortest-path is specified by information about its start and its end
* Start/End information is combined in so called location reference points (LRPs)
  * The location reference points are ordered from the start of the location to the end of the location
  * The shortest-path between two subsequent location reference points covers a part of the location
  * The concatenation of all such shortest-path(s) is called location reference path
* Example
  * Basic idea: a concatenation of a shortest path between location reference points (LRPs) covers the location completely  
  ![concatenation](concatenation.jpg)  
  * At least two location reference point needed for start and end of the location
  * Intermediate location reference points serve as a guide for the route calculation
* requirements
  * Map requirements on basis of GDF parameters
    * Functional road class (FRC): indicating the importance in the network
    * Form of way (FOW): indicating physical properties
    * Geometrical shape: lines shall not be abstracted by a straight line
    * Coordinates in WGS84: every node in the network should have coordinates
    * Length: indicating the real dimension along the geometrical shape
  * The map attributes FRC and FOW need to be mapped to corresponding OpenLR™ values
    * OpenLR™ defines its own FRC and FOW values
  * all attributes need to be mapped to corresponding OpenLR™ values according the schema
* Logical Data Format
  * First / Intermediate location reference points
    * point coordinates
    * bearing
    * Functional Road class FRC
    * Form of Way FOW
    * lowest FRC to the next location reference point
    * offset, as the difference of the start point of the location and the start point of the desired location along the location reference path (optional)
  * Last location reference point
    * point coordinates
    * bearing
    * Functional Road Class FRC
    * Form of Way FOW
    * offset, as the difference of the start point of the location and the start point of the desired location along the location reference path (optional)
* Process of Encoding
  * Check validity of the location and offsets to be encoded.
  * Adjust start and end node of the location to represent valid map nodes
  * Determine coverage of the location by a shortest-path.
  * Check whether the calculated shortest-path covers the location completely. Go to step 5 if the location is not covered completely, go to step 7 if the location is covered.
  * Determine the position of a new intermediate location reference point so that the part of the location between the start of the shortest-path calculation and the new intermediate is covered completely by a shortest-path.
  * Go to step 3 and restart shortest path calculation between the new intermediate location reference point and the end of the location.
  * Concatenate the calculated shortest-paths for a complete coverage of the location and form an ordered list of location reference points (from the start to the end of the location).
  * Check validity of the location reference path. If the location reference path is invalid then go to step 9, if the location reference path is valid then go to step 10.
  * Add a sufficient number of additional intermediate location reference points if the distance between two location reference points exceeds the maximum distance. Remove the start/ end LR-point if the positive/ negative offset value exceeds the length of the corresponding path.
  * Create physical representation of the location reference.
* Process of Decoding
  * Decode physical data and check its validity
  * For each location reference point find candidate nodes
  * For each location reference point find candidate lines
  * Rate candidate lines for each location reference point
  * Determine shortest-path(s) between two subsequent location reference points
  * Check validity of the calculated shortest-path(s)
  * Concatenate shortest-path(s) to form the location and trim path according to the offsets

## communication technologies

### classification

phone network, radio, short range communication

### Telecommunication: Umbrella term for all kinds of information transmission containing

* Equipment of telecommunications
* Organisational and operating facilities
* legal regulation for introduction, operation and use of these facilities

### Uni-directional vs. bi-directional data transfer

* unidirectional: Data exchange only in one direction, mostly collective approaches (broadcast)
  * radio - receiver
* bidirectional: Data exchange / communication in both directions, mostly individualised information
  * phone - id of sending and receiving

### RDS/TMC

* RDS (Radio Data System)
  * Method for sending small amounts of digital data using conventional analogue FM radio broadcasts (e.g. station abbreviation, textual information about the programme like title and artist of the currently-playing song)
* TMC (Traffic Message Channel)
  * Special RDS data for transmitting traffic and travel information (e.g. weather situation, congestions), geo-referenced: TMC - locations
  * Transmission can be limited on specific routes/areas
* Characteristics
  * low transmission rate
  * Already used by a large number of services

### DAB (Digital Audio Broadcast)

* designed for mobile use (e.g. cars) using a simple rod antenna
* TMC also be transmitted by DAB
* Advantages in comparison with RDS/TMC: higher data rate
* Multi-path effects are used to improve receiving quality
  * Incoming signals are synchronized after a protection interval
* Further developments
  * DAB+
    * DAB+ - Upgrade to DAB Digital Radio
    * DAB uses MPEG Audio Layer II (better known as MP2) DAB+ uses MP4
    * More stations can be broadcast on a multiplex
    * More efficient use of radio spectrum
    * Lower transmission costs for digital stations
  * DMB
    * DMB = Digital Multimedia Broadcasting
    * Digital Multimedia Broadcasting (DMB) is a video and multimedia technology based on DAB.
    * Robust reception of mobile TV at highway speeds (>300km/h)
    * DMB is an open European Standard

### GSM (Global System for Mobile Communications)

* Data transmission between vehicle and service centre can be carried out without additional infrastructure
* Characteristics
  * Subscriber and devices authentication
  * Subscriber localisation
  * Data encoding
  * Digital data transmission: 9,6 kBit/s
  * SMS: Short message service (max 160 characters)
  * GPRS: package-switched data transmission
* 3 subsystems  
  ![subsystems](subsystems.jpg)  
  * Base Station Subsystem - Connection of subscriber at the network
    * Mobile phone communicated with the network by Base Transceiver Station (BTS)
    * One antenna per radio cell
    * A-bis-interface
    * Processing via Base Station Controller (BSC)
    * BSC carries out handover (subscriber pass to a new cell)
  * Network and Switching Subsystem - Switching within the network and connection to other (telecommunication) networks
    * Processing of network traffic between BSC (A-interface)
    * Localisation of subscriber during dial-up
  * Network and Switching Subsystem - Administration and control of the network
    * Administration of business-relevant data
    * Security management
    * Net configuration
* Data communication with GSM
  * Data communication with GSM
  * SMS (Short Message Service)
  * GPRS (General Packet Radio Services)

### UMTS (Universal Mobile Telecommunications System)

* Transmission protocol: Wideband-CDMA (Code-Division-Multiple-Access): higher speed, support of more users
* Parallel transmission and receiving of several data streams
* Services
  * Communication (Audio- und Video telephony, ...)
  * News services (Video-Speech-Mail, Chat, ...)
  * Information dissemination (WWW, information services, ...)
  * Localization (PDA, LBS, ...)
  * Mass service (e-Commerce, online-banking, ...)

### Satellite-based communication systems: Iridium, Globalstar, Teledesic, Annotations

### private mobile radio

* Part of non-public mobile land broadcasting
* Subdivided into several application areas according to groups of public utility providers
* Radio network consists of stationary radio installations with appended mobile radio sets

### trunking - trunked radio

![trunking](trunking.jpg)  

* like private mobile radio
* railway company/police fire station
* Better frequency utilisation: dynamic frequency allocation using a pool of channels

### private mobile radio vs. trunking

![private mobile radio vs. trunking](private.jpg)  

### Short range communication

![Short range communication](range1.jpg)  
![Short range communication](range2.jpg)  

### Communication inside the vehicle

![Communication inside the vehicle](communication.jpg)  
![Communication inside the vehicle](inside.jpg)  

* CAN BUS: Controller Area Netwok
  * Networking of control units in cars
  * Line structure with stubs
* CAN-B: supports intelligent sensors / low data rate / max. 10 stations
* CAN-C: for drive and chassis electronics / higher data rates / max. 24 stations

### Further BUS systems - real time, capability

* FlexRay
* MOST (Media Oriented Systems Transport Bus)
* LIN (Local Interconnect Network)

## Positioning and Navigation

### Introduction

* reference system
  * WGS84: ellipsoid, unique coordinate system, global reference system for GPS
  * projected system: distortion, calculate between the system and measurement
  * local reference system in the vehicle: different kinds of sensors define different coordinate systems and different zero points
* container: segmentation cells link to the antenna - not geodetic
* beacons, where bus/train is passing logical routing - not geodetic
* GPS error
  * junks - change of satellite
  * multi path
  * shadowing
* advantages of GPS or GNSS used for positioning: global position in the map, global coordinates
  * gyroscopem odometer, compass, speed senser are relative
* odometer: skip between the real wheel moving direction+distance - calculation from one point to anothers

### classification of location methods

![classification of location methods](classification1.jpg)  
![classification of location methods](classification2.jpg)  

* global
  * in a superior (global) reference system
  * no previous position information is necessary
  * measurement of absolute position
  * problem: signal loss
* local
  * measurement of position changes
  * lack of absolute position can be compensated for short time periods (dead-reckoning)
* self-positioning
  * positioning is realised by mobile object itself
* remote-positioning
  * positioning is realised by a reference system
  * data privacy has to be considered
* coordinate system (n-dim)
  * positioning related to a coordinate system (e.g. WGS84)
* traffic network resp. road/route (1-dim)
  * positioning related to a line
* predefined objects - area-related (containment) or pointrelated (e.g. beacon)
  * for a specific location
  * accuracy depends on size of container

### terms

![terms](terms.jpg)  

* Positioning - coordinates
  * Determination of the current geometric position
* Location - information about the surroundings
  * Determination of the current position related to an element (e.g. a node on a graph) of a (digital) map (e.g. the traffic network)
* Map-Matching: Allocation of the current geometric position or trajectory (sequence of positions) to the traffic network represented as digital map
* Route calculation: Determination of the optimal path between two or more places within the traffic network concerning a given optimisation criteria
* Navigation = positioning and guidance
  * includes positioning, location and route calculation between current location and target
  * guidance commands to reach the target
  * dynamic navigation includes
    * comparison of the calculated route with the actual route
    * deviations or incidents require the calculation of a new route including new guidance commands

### Sensors and their typical errors

![errors](errors.jpg)  

#### Odometer - use gyroscope to check

![odometer](odometer.jpg)  

#### GPS/DGPS

* Errors
  * jumps and deviations
    * multipath/shadowing - detection of the junks, check vehicle speed model
    * shadowing and reflections
    * changes and faulty in satellite configutation
    * loss of correction signal
  * 90%-95% availability of GPS-signal in urban area
* GPS raw signal not directly usable
* filter necessary
* areas without GPS have to be bridged
* DGPS
  * improvement of accuracy
  * availability of correction signal
* carrier phase - very low availability due to determination of ambiguities
* GPS Quality  
  ![GPS Quality](quality.jpg)  
  * a measurement of the time required for a GPS receiver to acquire satellite signals and navigation data, and calculate a position solution
  * GPS SiRF III delivers better quality
    * High sensitive
    * Very short TTFF(time to first fix)
    * High-performance correlation unit
    * Shadowing effect is still existing
    * Gross errors are still given, but to less extent
  * GPS-mouse
    * Sensor fusion with internal gyro (+ speedometer)
    * Dynamic model of vehicle for filtering

#### Dead reckoning errors

##### use gyros and speed odometer only, speed effects 𝜎Δy, so accuracy error~time  

![GPS accuracy](accuracy.jpg)  

##### Error ellipses with different initial accuracies at the starting point

![Error ellipses](ellipses.jpg)  

##### accuracy of dead reckoning depend on

* shape of the track
* number of measurements(frequency of measurement, driving dynamics)
* accuracy of measurement

### map matching - match the position of the car to the digital road map

![map matching](match.jpg)  

#### principle

![principle](principle.jpg)  

* accuracy - how we measure accuracy - standard deviation
* A reliable algorithm which is suitable real time applications has to be developed, taken into account the accuracy, performance, and the speed of the algorithm.
  * Different used techniques (simple techniques, medium in difficulty, and complex method).
  * According to the degree of complexity, the speed is different.
  * Each algorithm has been developed for a specific purpose.
  * Real time applications vs. Post processing.
  * Real time (urban, suburban, or rural environments)
  * Some algorithms are more accurate than the others.
  * Different sensors are in use, and thus different input data.
* Geometric map matching algorithms - shortest distance to the edge/node  
  rely on the geometric information of the spatial road network data to determine the correct segment, by considering only the shape of the links.
  ![shape](shape.jpg)  
  * Point-to-point matching
    * shape point: do not influence the attributes
    * node - incl. attributes
  * Point-to-curve matching
  * curve-to-curve matching: transformation - shift, rotation, scale
* Topological map matching algorithms - make use of the geometry of different entities of the spatial road network data, as well as the spatial relationships between the different entities (lines and nodes)
  * Historical data (previous correct segment)
  * Connectivity information
  * Turn restriction data - traffic sign
  * topology derived from geometrical information - connection related to the coordinates
* Probabilistic map matching algorithms
  * take all(accuracy, measurement error) into consideration
  * an error region (rectangular, elliptical, or circular) has to be generated around each of the positioning fixes which are obtained from the navigation solution.
  * Sometimes, the error ellipse is generated around each point of the GPS fixes, sometimes it is only used at junctions
* Advanced map matching algorithms
  * mathematic methods
  * category of algorithms which uses more difficult and strong concepts than geometry, and topology, although it uses such information in most cases
  * kalman filter, particle filter, artificial neural network or a fuzzy logic model

#### Characteristics of map-matching

* Transformation of local positioning information into global positioning information for georeferencing
* TRealisation of a logical connection between vehicle position and road network stored in the map (geo database)
  * TLogical connection enables access to further route-related data from the map (locations !)
* TCompensation of system-immanent measurement errors cause an enhanced quality regarding accuracy, correctness and availability

#### trajectory: curve to curve matching

* Representations of planar graphs  
  ![planar](planar.jpg)  
* Evaluation procedures
  * Map-Matching with coordinate pattern
    * Similarity transformation - corresponding point coodinates
    * Affine transformation
  * Map-Matching with azimuth or curvature pattern
    * Cross-correlation
    * Least squares adjustment
    * Recursive parameter estimate (Kalman filter)
* Map-matching based on coordinates
  * Translation (2 parameters)
    * Does not considers systematic sensor errors at all
    * Possible useable for DGPS
  * Similarity transformation (4 parameters)
    * Translation, rotation
    * Scale unusable due to equidistant line segments
    * Determination of initial values for dead reckoning
  * Affine transformation (6 parameters)
    * Translation, rotation, shearing, reflection
    * Most precise allocation due to most degrees of freedom
* Procedure: Assignment via coordinates  
  ![planar](planar.jpg)  
  * problem: scale - segment, corner
  * Map-Matching in angle or curvature image  
    ![angle or curvature](winkel.jpg)  
    * cross correlation: $c(i)=\sum_{j=-\infty}^{\infty} \varphi_{2}(j) \cdot \varphi_{1}(i+j)$
    * Maximum shows the offset between both functions
* Procedure: Map-matching with azimuths  
  ![azimuths](azimuths.jpg)  
  * Adjustment
    * offset of arc length
    * Scale of arc length
    * Offset of azimuth
    * Scale of azimuth
  * Procedure - Overview  
  ![procedure](procedure.jpg)  
    * Area selection: raw definition of map matching area by absolute positioning(in genaral: GPS)s
    * net thining: by azimuth or distance information of measured trajectory
    * Route identification
      * Composition and conversion of the routes corresponding to chosen evaluation procedure
      * Matching of the path to each alternative route
      * Longitudinal determination: Shifting the trace along selected route
* Selection of alternative routes
  * Offline evaluation (service centre)
    * all measured position are available
    * accuracy of measurement defines the area in scope
    * Set-up of topologies from the segments within the fixed area
    * Pre-selection based on checks of directions and lengths
  * Online evaluation
    * Road element at the beginning is given
    * Limitation of area based on positioning accuracy
    * Consider topology in course of the road
    * Each branch is a new alternative route

#### Impact of the map on location quality

* Up-to-dateness of the map
* Map information disturbs accuracy and correctness of location, if the map does not represent reality
* Here: used map does not represent the new constructed roundabout 
  * solution: kalmann filter

#### Evaluation with Kalman filter

![Basic principle](principle1.jpg)  

Example: travelling ship
![Example: travelling ship](travelling.jpg)  

##### Kalman filter: Trajectory approach

##### Parameterization of vehicle movement on plain trajectory -applied parameters (arc length, curvature / radius)

##### Vehicle model: 'kinematic' approach – uniform motion on a circle with constant speed (within on sampling interval e.g. t = 1 sec)

* Condition vector
  * $Y, X$
  * Speed $v$
  * Orientation of vehicle $\alpha$
* Measurement
  * Absolute GPS $Y, X$
  * Odometer $\Delta s, \Delta \alpha$
  * Gyro $\Delta \alpha$
* Transformation into a global reference system

$$\left(\begin{array}{l}
Y_{k+1} \\
X_{k+1}
\end{array}\right)=\left(\begin{array}{l}
Y_{k} \\
X_{k}
\end{array}\right)+\left(\begin{array}{cc}
\cos (\alpha) & \sin (\alpha) \\
-\sin (\alpha) & \cos (\alpha)
\end{array}\right)\left(\begin{array}{c}
\Delta Y^{L} \\
\Delta X^{L}
\end{array}\right)$$

![Transformation into a global reference system](global.jpg)  

* System equation

![System equation](equation.jpg)  

* Filter design

![Filter design](design.jpg)  

#### Positioning with GSM: Structure of GSM Network

![Positioning with GSM](gsm.jpg)  

* MS = Mobile Station (Cell Phone)
* BTS = Base Tranceiver Station (Antenna): controls one antenna respectively cell
* BSC = Base Station Controller: controls several BTS
* MSC = Mobile Switching Centre: controls several BSC = one Location Area (LA)

#### Mobile Phone Positioning

##### Signal dispersion - the signal strength decreased as the square of the distance

* shading
  * large object(building, trees) attenuate the signal so that there is no reception behing them
  * the higher the frequency, the stronger the attenuation
* reflection: after reflection of the signal, e.g. on buildings, the absorption of the signal strength is reduced
* scattering: one signal is split into several weaker signals which preceed in different directions
* diffraction: signal are diffracted on the edges from the original spreading direction(recipient is accesible behing mountains)

##### Measurements usable for PositioningMeasurements usable for Positioning

![Measurements usable for PositioningMeasurements usable for Positioning](usable.jpg)  

* Cell ID: unique number assigned to one cell resp. BTS
* Handover
  * point of time when a MS changes from one cell (BTS) to another one
  * phone switch from one to another antenna
* Location Area Update: point of time when a MS changes from one LA (MSC) to another one
* Timing Advance (TA) value - syncronazation: approximation of the distance between MS and the serving BTS, resolution of approx. 550 m
* Received Signal Strength (RXLEV-value): signal attenuation between MS and up to 7 BTS, resolution 1 dB

##### Positioning methods

* Cell-based procedure  
  ![Cell-based procedure](cell.jpg)  
  * Cell Of Origin (COO)
    * in city, one antenna may be full(e.g., 500 register) - solution: overlapping
    * Localisation on cell basis (Cell-ID)
    * Precision: 100 – 20.000 metres (depending on the size of the cell)
    * Requires countrywide cell structure
    * used for Location Based Services (LBS)
  * Cell Of Origin with Cell Sector
* Runtime measurement
  * Timing Advance (TA)
    * In order to meet the time slots, signal runtimes between mobile station and base station are considered
    * Runtime measurement for several base stations - increase precision
  * Time Of Arrival (TOA)  
    ![Time Of Arrival (TOA)](toa.jpg)  
    * Direct runtime measurement (TOA)
    * Synchronisation of signals is required
    * Multipath effects  
  * Time Difference Of Arrival / Uplink Time Of Arrival (TDOA)  
    ![Time Difference Of Arrival / Uplink Time Of Arrival (TDOA)](tdoa.jpg)  
    * Two reference stations are sending simultaneous signals
    * Base station measures time difference for the reception of the signals
    * Advantage (over TOA): The imprecision of the watches is the same in both measurements and thus drops out on the subtraction.
    * **sycronazation**
  * Enhanced Observed Time Difference (E-OTD): Mobile phone measures runtime differences
* Angle measurement
  * Angle Of Arrival (AOA)  
    ![Angle Of Arrival (AOA)](aoa.jpg)  
    * Measurement of the angle of arrival of the receiving signal on at least two stations
    * Calculation on a centralised basis
    * Base stations have to be upgraded with special directional antennas
* Signal strength measurement
  * Received Signal Strength
    * Signal strength decreases as the square of the distance
    * Output signal strength is known
    * Deduction of a route through signal strength,  transmission power of the antenna and attenuation type
    * Susceptible to obstacles and multipath effects
    * antenna, shading
* Reference data procedure
  * Principle: Measurement of radio field environment data and comparison with previously measured and georeferenced data
  * Example: Signal strength chart to several BTS
  * Collection of reference data
    * By measurement (extremely time-consuming)
    * From planning (with disperson models)
  * Precision: depending on the discretisation depth

##### Mobile phone positioning methods

![Mobile phone positioning methods](mppm.jpg)  

##### Positioning with GSM: Positioning Methods

![Positioning with GSM: Positioning Methods](pgsm.jpg)  

### Mobile phone positioning with A data

#### Input data

* Telephone call: handover (= result of cell changes)
  * Time
  * Former LAC(location area code); former CI(cell ID);
  * New LAC; new CIs
* Standby mode - Location Area Update
  * Time
  * Former LAC; * 
  * New LAC; new CI

#### Mobile phone data

* Handover
* Location Area Updates
* Corrections required

#### Mobile phone network

* Antennas (position, orientation, frequences)
* Best Server Plot
* Generalisation / data reduction

#### Map basis

* Navtech GDF -> Localisation network
* Elimination of residential streets

#### Route calculation

* Graph covering all location areas
* Start and target node on the first and last change
* Shortest distances in all combinations
* Selection of the route with frequency

### Map-based mobile phone positioning - Project Do-iT (data optimization for integrated telematics)

![Project Do-iT](doit.jpg)  

* Least squares adjustment
  * Further improvement by smoothing (moving average filter) and Kalman filtering
* Map Aiding
  * definition: Create logical references to road map
  * Procedure
    * Projection of position sequence on road map
    * Determination of search area
    * Selection of start and target node
    * Calculation of all possible (shortest) routes
    * Selection of most probable route through standard deviation of perpendiculars on measured position sequence
  * Strong jumping of single items / Real and "planned" signal strengths differ significantly.
* Positioning with GSM: Conclusions
  * GSM network may be used for positioning
  * Classification of positioning methods is presented
    * based on GSM network structure
    * available measurements
  * Availability of positioning methods for net-based anonymous approach is limited
* Near field communication
  * WLAN navigation system
    * WLAN location is intended as alternative to the satellite Global Positioning System (GPS)

### Routing - Identify the best way between different locations within a given transport network taking specified requirements into account

#### Application

* Adoption of traffic requirements for transport networks
* Navigation systems
* Fleet management systems / Route planning

#### problem of calculation: efficiency - calculating through the all map algrithoms are time consuming

#### Based on the Graph Theory and its node-edge model

##### A Graph is an amount of distinguishable elements with the same properties having a specific structure. This structure is described by relationships between the different elements

![Graph](graph.jpg)  

##### Basic objects

* Node
* Edge: directed/undirected

##### A directed graph $G=(V,E)$ consists of

* a limited amount V of nodes
* a limited amount $E ⊂ V × X$ of (directed) edges

##### Adjacency: Relation between node and node

##### Incidence: Relation between node and edge

##### Distance matrix

$$
D=\left(d_{i, j}\right)=\left\{\begin{array}{cc}
d\left(x_{i}, x_{j}\right) & \text { if } a_{i, j}=1 \\
\infty & \text { else }
\end{array}\right.
$$

![Distance matrix](distance.jpg)  

The search for the shortest path is always a search for the best node-edge sequence.

#### Routing algorithms / Best-Way Search

##### Shortest path by Moore

![Shortest path by Moore](moore.jpg)  

* Input
  * Graph $𝐺(𝑉; 𝐸)$ with cost function $𝑙( 𝑖, 𝑗)$
  * Start node $𝑣_1$
* Output
  * Tree of the shortest paths
  * List $𝑑 (𝑣_1, ⋯ , 𝑣_𝑛)$ , costs from start node to all other nodes
* Initialisation
  * ShortestPathTree = {};
  * SetOfCandidates {}= ; /* already identified nodes */
  * Add start node $𝑣_1$ to the set of candidates
  * Costs of the start node: $𝑑 (𝑣_1) = 0$;
  * Costs of all other nodes: $𝑑 (𝑣_2 ⋯ 𝑣_𝑛) = ∞$;

##### Dijkstra algorithm

![Dijkstra algorithm](dijkstra.jpg)  

* process
  * Mark all nodes unvisited. Create a set of all the unvisited nodes called the unvisited set.
  * Assign to every node a tentative distance value: set it to zero for our initial node and to infinity for all other nodes. Set the initial node as current.
  * For the current node, consider all of its unvisited neighbors and calculate their tentative distances through the current node. Compare the newly calculated tentative distance to the current assigned value and assign the smaller one.
  * When we are done considering all of the unvisited neighbors of the current node, mark the current node as visited and remove it from the unvisited set. A visited node will never be checked again.
  * If the destination node has been marked visited (when planning a route between two specific nodes) or if the smallest tentative distance among the nodes in the unvisited set is infinity (when planning a complete traversal; occurs when there is no connection between the initial node and remaining unvisited nodes), then stop. The algorithm has finished.
  * Otherwise, select the unvisited node that is marked with the smallest tentative distance, set it as the new "current node", and go back to step 3.
* distance/direction restriction
* highways function road class
* proper ways and store the calculation
* maybe not the best result

### Tour planning - Travelling-Salesman-Problem (TSP)

* Connect several given destinations using the shortest possible path forming a closed tour
* Using the Distance Matrix we get the following function $f\left(s_{k}\right)=\sum_{i=1}^{n} d_{i, j}=\min$

#### Solution: Nearest-Neighbour-Approach

The nearest neighbour of a starting point is used to create a Hamilton Path  
Bad connections may arise if only few points remain

##### Christophides' Algorithm

![Christophides' Algorithm](christophides.jpg)  

* Construction of a minimal-spanning tree (undirected graph) via all points (a)
* Minimum-Matching for all nodes with uneven degree (b)
* Find an Euler Path (c), each edge has to be passed at least once
* Create a Hamilton Path (d)

### Functional architecture of navigation system

![Functional architecture of navigation system](navigationsys.jpg)  

* Kinds of navigation systems
  * Mobile systems
    * PDA, Smartphone, …
    * Usually only GPS-based
    * Map representation
    * Some devices include TMC/RDS, ...
    * Without permanent mounting
    * advantage: bi-direction communication
    * disadvantage - ID
  * Radio-integrated systems
    * Integrated in the radio bay
    * Display with pictogram
    * Location using GPS
    * Usually TMC/RDS-capable
    * disadvantage
      * broadcast for all simple table
      * only one direction, can only receive information
  * Stand-alone systems
    * External monitor
    * Map representation
    * sensors: gyro, odometer, GPS
* User interface (MMI)
  * Tasks of the MMI
    * Menu-based handling
    * Input of various destination/s
    * Display of the recommended way / path to the target = graphical guidance
    * Acoustic output of the recommended way / path = acoustic guidance
  * MMI Requirements
    * Simple handling
    * No distraction of the driver with respect to current traffic - Pictograms and voice output
* Route guidance information - Depending on velocity and distance: confirmation, notification and advice
* Database within a navigation system
  * Database within a navigation system: All road segments and junctions
  * High level 3: All motorways, interstate roads and country roads
  * High level 2: All motorways and interstate roads
  * High level 1: All motorways
  * Land Use Maps: Object for map generation and representation (water, railroads)
  * Points of Interest (POI): Symbols and additional textual information

### Localisation for regional public transportation

#### Logical localisation (beacons)

![Logical localisation (beacons)](beacons.jpg)  

* Reliable, but inflexible
* Expensive, as it requires many devices along the tracks

#### Localisation by GPS - Independent from defined way, but not 100 % reliable

### location of rail vehicle

#### Current Situation: Trains are located using coupled coils. - Location of trains using installed infrastructure

![Current Situation](trains.jpg)  

* High installation costs
* Expensive maintenance
* Trains have to keep a large distance to each other
* Low comfort for passengers

#### Objective: Rail vehicles determine their position itself and communicate the position to a central office or control system - Board-autonomous rail vehicle location

* Position of the trains is known at any time
* More flexibility regarding distance between trains
* Better information of passengers about current traffic situation

## Traffic Data Acquisition

### Traffic Data Acquisition

![Traffic Data Acquisition](tda.jpg)  

* Usage of traffic information
  * User-related transmission of traffic information
  * Off-board computation of route in service centres
  * On-board computation of route regarding the current traffic situation (dynamic routing)
  * Traffic prediction
* Tasks of traffic data acquisition: Collection of the traffic parameter at discrete locations to sustain simulations of traffic situations by measurements
* Tasks of traffic data collection: Detection of the parameters at discrete locations to support traffic models with these measurements
* To influence the traffic information on traffic conditions as basic data are required
* to avoid traffic jam
  * capacity of the road
  * speed & capacity
  * higher speed, higher distance
  * speed ->constant, limited

### Traffic parameters

* presence/ absence of vehicle
* direction of traffic
* velocity
* vehicle class e. g. "8+1"  
   ![vehicle class e. g. "8+1"](81.jpg)  
* durability of allocation (period of presence)
* time gap (e. g. announcement vehicle1 -announcement vehicle2)
* traffic volume [vehicles/h] (= traffic flow) - how many in time
* traffic density [vehicles/km] - how many in length

### Analysis / interpretation of acquired data

#### Path-Time Diagram

![Path-Time Diagram](pathtime.jpg)  

##### display of movement of individual traffic participants

* part time diagram
* driven route of an indicidual traffic participant subject to time

##### observation methods

![observation methods](observation.jpg)  

##### Description of motion-sequence

![motion-sequence](motion.jpg)  

* spatial-temporal description of traffic situation
* feasibility of predicting formation, development and reduction of traffic jamming

### Sequence of Traffic-Data Acquisition

![Traffic-Data Acquisition](traffic.jpg)  