---
title: Generate Stream Branches
---


The **Generate Stream Branches** tool dissolves the line network based on GNIS name and stream order attributes, to create stream branches in the stream network polyline feature class. The resulting stream branches can then by used by the [Segment Stream Network](http://gnat.riverscapes.xyz/Segment-Stream-Network) tool for splitting the stream network by the longest, continuous stretches of stream.

![example]({{site.baseurl}}/images/branchID_example.png)

_______________________________________________________________
## Usage

![form]({{site.baseurl}}/images/branchID_form.PNG)

### Input Parameters
 
**Input Stream Network** (with Stream Order)

Stream network with Stream Order Attributes (from stream order tool). 

**Input Junction Points** (Optional)

Junction points output from the [Calculate Stream Order](http://gnat.riverscapes.xyz/Calculate-Stream-Order) tool which will be used to split branches at stream order convergences. Otherwise, the tool will dissolve all stream order segments that converge with the same stream order value.

**Primary Stream Name Field** (i.e. GNIS Name)

Attribute field with stream names (i.e. GNIS_Name). Not all stream reaches need to have a stream name - the tool will use stream order for segments without a stream name.

**Stream Order Field** (optional)

Attribute field that contains the stream order value for each line feature.

**Output Line Network with Branch ID**

File geodatabase polyline feature class. Existing datasets will be overwritten. 

**Dissolve Output Network by BranchID?** (optional)

* `Checked`: The output stream network will contain all features dissolved by the BranchID. Feature attributes will be dropped due to the dissolve.

* `Unchecked`: The output stream network will retain its original features and attributes, with the addition of the `BranchID` field.

**Scratch Workspace** (optional)

* Can be a file geodatabase or folder, for saving temporary processing datasets.
* If a workspace is not designated, the tool will use the "in_memory" workspace. Temporary files will not be accessible, but the tool's processing speed will be improved.

_______________________________________________________________
## Technical Background

### Calculation Method

1. Input polyline features are selected by GNIS_Name, then dissolved by GNIS_Name.
2. The selection is switched, then dissolved by stream order, if present as an attribute
3. Output datasets from 2 and 3 are merged.
5. Split line at point, using the input junction points feature class
	> This fixes the issue when two tributaries with the same stream order (and no GNIS) are dissolved together. Mainly occurs at the headwaters (i.e. stream order = 1).
5. Add a unique ID field (`BranchID`) to identify each branch.
6. The original input is intersected with the Branches feature class, if the output is not to be dissolved. Otherwise, the output is simply copied over from Branches.
