# Installation

## Zipfile

GNAT is provided as a zip file containing a .pyt file and supporting script files. 

1. Download the zipfile and unzip the contents to your computer (keep all files together).
2. Open ArcGIS.
3. Add the .pyt file to Arctoolbox as you would any other Geoprocessing Toolbox.

# Downloads

## Version 2.3.8
**[Version 2.3.8](Downloads/arcGNAT_2.3.8.zip)** 2017-NOVEMBER-28
```markdown
* Fixed issue with how Sinuosity and Planform handle attribute fields. Also fixed small bug with Planform parameters.
```

**[Version 2.3.7](Downloads/arcGNAT_2.3.7.zip)** 2017-NOVEMBER-21
```markdown
* Cleaned up comments and attribute fields output for Sinuosity.
```

**[Version 2.3.6](Downloads/arcGNAT_2.3.6.zip)** 2017-NOVEMBER-20
```markdown
* Sinuosity attribute field can be added back to Realization's segmented network for Riverscapes projects.
```

**[Version 2.3.5](Downloads/arcGNAT_2.3.5.zip)** 2017-NOVEMBER-20
```markdown
* Separated the **Stream Sinuosity and Planform** tool into two new tools, **Channel Sinuosity** and **Planform**.
```

**[Version 2.3.4](Downloads/arcGNAT_2.3.4.zip)** 2017-NOVEMBER-14
```markdown
* Changed valley centerline output from optional to required.
```

**[Version 2.3.3](Downloads/arcGNAT_2.3.3.zip)** 2017-NOVEMBER-7
```markdown
* Changed name of output dataset for geomorphic attribute analyses.
```

**[Version 2.3.2](Downloads/arcGNAT_2.3.2.zip)** 2017-OCTOBER-27
```markdown
* Fixed issue another issue with how segmented networks filepaths are stored in the Riverspaces project xml.
```

**[Version 2.3.1](Downloads/arcGNAT_2.3.1.zip)** 2017-OCTOBER-26
```markdown
* Fixed issue with how the input stream network parameter is changed when using Riverscapes 
inputs.
```

**[Version 2.3.0](Downloads/arcGNAT_2.3.0.zip)** 2017-OCTOBER-19
```markdown
* Refactored the geomorphic attribute tools to better manage Riverscapes project information.
* Updated help files for geomorphic attribute tools.
* Renamed tool menus.
```

**[Version 2.2.0](Downloads/arcGNAT_2.2.zip)** 2017-SEPTEMBER-21
```markdown
* Geomorphic attribute tools (i.e. Calculate Gradient, Calculate Threadedness) moved to the
the **Geomorphic Attributes** group. All **Geomorphic Attribute** tools now save calculated attributes
as new fields in the input stream network polylie feature class.
```

**[Version 2.1.13](Downloads/arcGNAT_2.1.13.zip)** 2017-AUGUST-21
```markdown
* Minor change to Sinuosity and Planform tool, adding default output parameters.
```

**[Version 2.1.12](Downloads/arcGNAT_2.1.12.zip)** 2017-AUGUST-14
```markdown
* Fixed minor issue with how a field was populated in the Commit Stream Network tool.
```

**[Version 2.1.11](Downloads/arcGNAT_2.1.11.zip)** 2017-AUGUST-4
```markdown
* Removed the junction points output, which was causing an exception.
```

**[Version 2.1.10](Downloads/arcGNAT_2.1.10.zip)** 2017-JULY-21

```markdown
* Added the Calculate Braidedness tool.
```

**[Version 2.1.09](Downloads/arcGNAT_2.1.09.zip)** 2017-JULY-13

```markdown
* Added the Calculate Gradient tool.
```

**[Version 2.1.08](Downloads/arcGNAT_2.1.08.zip)** 2017-JULY-12

```markdown
* Fixed several issues with the Transfer Line Attributes tool.
```

**[Version 2.1.07](Downloads/arcGNAT_2.1.07.zip)** 2017-JUNE-22

```markdown
* Changed buffer distance used in the Build Network Topology tool when selecting upstream stream reaches.
```

**[Version 2.1.06](Downloads/arcGNAT_2.1.06.zip)** 2017-MAY-26

```markdown
* Fixed issue with Transfer Line Attributes tool and buffering tiles.
* Build Network Topology tool now write nodes as a point feature class.
```

[Version 2.1.04](Downloads/arcGNAT_2.1.04.zip) 2017-MAY-16

```markdown
* Fixed issue with Segmentation UI
* Updated to better Handle TO lines with no attributes
```

[Version 2.1.02](Downloads/arcGNAT_2.1.02.zip) 2017-MAY-03

```markdown
* Revised Transfer Line Attributes to better handle networks with differing spatial extents.
```

[Version 2.1.01](Downloads/arcGNAT_2.1.01.zip) 2017-APR-28 
```markdown
* Updated Riverscapes Project (integrated with Riverscapes Project Python module)
```

[Version 2.1](Downloads/GNAT_2.1_20170303.zip) 2017-March-03