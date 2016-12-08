The **Find Network Errors** tool finds topological errors within a stream
network polyline feature class. The stream network  is assumed to be a single-part 
non-braided topological network. Currently the  **Find Network Errors** tool can 
find the following topological errors:

* Braids
* Duplicate reaches
* Overlapping reaches 
* Crossed reaches
* Disconnected reaches
* Upstream flow direction
* Other potential errors

The **Find Network Errors** tool relies on two inputs: a stream network polyline
 feature class, and the network topology table generated by the **Build Network 
 Topology Table** from the stream network feature class, which should be named
 _StreamNetwork_.

The resulting **Find Network Errors** table, _NetworkErrors_, stores records for 
each stream reach,and each record includes the reach unique ID and a numeric code 
for each error type. This table can then be joined back to the input stream network 
polyline feature class and symbolized in ArcMap to highlight stream reaches with 
topological errors, which the user can then manually fix using ArcGIS editing tools.

##Geoprocessing Environment

* We recommend that the **Find Network Errors** tool be run using 64-bit python geoprocessing.
* Disable Z and M values in the stream network feature class Shape field.

##Input Parameters

**Processed Input Stream Network**

Stream network polyline feature class that has been output by the **Build Network
Topology Table** tool.  The feature class name should include "_processed" as a
suffix. 

**Stream Network Table**

Stream network topology table, in a file geodatabase format.  Output from the 
**Build Network Topology Table**. The table hould be named _StreamNetworkTable_.

**Downstream Reach ID**

Object ID of the downstream reach (i.e. the outflow) in the stream network polyline 
feature class. This is also the first record in the output network topology table.


##Calculation Method

Methods for finding each error type differ, and can rely on either the stream
network polyline feature class or the network topology table. 

* Braids: calls the **Find Braids in Stream Network** tool. *error_code = 2*
* Duplicate reaches: stream reaches with identical lengths. *error_code = 3*
* Overlapping reaches: each stream reach is compared to neighboring upstream reach. They are considered overlapping if they share nodes other than their beginning/ending nodes. *error_code = 4*
* Crossed reaches: each stream reach is compared to neighboring upstream reach. They are considered crossed if no they cross, but do not share beginning/ending nodes. *error_code = 5*
* Disconnected reaches: reaches that are present in the stream network polyline feature class, without associated records in the network topology table are considered disconnected. *error_code = 6*
* Upstream flow direction: reaches with identical FROM nodes indicate an error in flow direction (see Troubleshooting and Potential Issues section below for known limitations). *error_code = 7*
* Other potential errors: based on reach records in the network topology table where UpstreamID = -11111. *error_code = 8*

##Outputs

**NetworkErrors**

The resulting network topology table, including error codes stored in a new attribute field: *ERROR_CODE*. This will be saved to the same file geodatabase where the input stream network is stored.

##Troubleshooting and Potential Issues

Because the method for finding flow direction errors is performed in a pairwise fashion
(i.e. the reach and the neighboring upstream reach), a reach is considered to have 
an incorrect flow direction only in relation to the neighboring reach, due to 
both reaches having the same FROM node values. In the case of a stream branch where
all of the reaches comprising that branch have an incorrect flow direction, the tool 
will only tag one reach with the flow direction error code.

Therefore, the user should use caution when reviewing reaches where *error_code = 2*. Nearby
stream reaches should also be examined to ensure proper flow directionality.