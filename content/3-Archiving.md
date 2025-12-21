---
authors:
  - name: null
---

# 3 Archiving 3D data

Selection of 3D data for archiving should be done within the context of the wider data workflow and include a consideration of points at which data are created, collected, or significantly changed. This is discussed generally within the Guides to Good Practice section on [*Data Selection: Preservation Intervention Points*](https://doi.org/10.5284/h0p2-5584) but, where data results from specific collection techniques such as laser scanning and photogrammetry, it is advised that these separate guides' sections on data workflows, selection and retention are consulted (e.g. see section 1 of the Laser Scanning guide, section 2 of the Photogrammetry guide).

## 3.1 Significant Properties

As discussed in detail in Section 2 of this guide, the various elements of 3D models - their significant properties or characteristics - can vary considerably and not all file formats support the storage of all 3D data properties. For this reason the selection of a suitable format for archiving needs to consider which properties need to be retained in order to successfully preserve all elements of the model. As highlighted by McHenry and Bajcsy (2008), in many cases file format conversion introduces information loss and it is therefore important to consider the properties of file formats used for archiving during the data creation stage. 

The following table (derived from McHenry and Bajcsy [-@mchenry2008]) gives an overview of parameters supported by a number of formats discussed in this guide. Empty cells either mean that the format lacks the ability to store these properties or that no traceable specifications for this property/format can be found.

Properties supported by the various 3D formats.
* Geometry: __F__ = ''Wire frame''; __P__ = ''Parametric''; __CSG__ = ''Constructive Solid Geometry''; __B-rep__ = ''Boundary representation''
* Appearance: __C__ = ''Colour''; __X__ = ''Texture by image''; __B__ = ''Bump mapping''; __M__ = ''Material''; __V__ = ''Viewport and camera''; __L__ = ''Light sources''; __T__ = ''Transformation''; __G__ = ''Grouping/arrangement''


```{list-table} Table 2: An overview of parameters supported by a number of 3D data formats (after McHenry and P. Bajcsy 2008)
:header-rows: 2

* - Format
  - Geometry
  - 
  -  
  -  
  - Appearance
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  - Animation
* -  
  - F
  - P
  - CSG
  - B-Rep
  - C
  - X
  - B
  - M
  - V
  - L
  - T
  - G
  - 
* - X3D
  - &#x2714;
  - &#x2714;
  -  
  -  
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
* - VRML
  - &#x2714;
  - &#x2714;
  -  
  -  
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
* - DAE
  - &#x2714;
  - &#x2714;
  -  
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
* - U3D
  - &#x2714;
  -  
  -  
  -  
  - &#x2714;
  - &#x2714;
  - &#x2714;
  -  
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
* - PLY
  - &#x2714;
  -  
  -  
  -  
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  -  
  -  
  -  
  -  
  - 
* - OBJ
  - &#x2714;
  - &#x2714;
  -  
  -  
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  -  
  -  
  -  
  - &#x2714;
  - 
* - STL
  - &#x2714;
  -  
  -  
  -  
  - &#x2714;\\(Binary\\only)
  -  
  -  
  -  
  -  
  -  
  -  
  -  
  - 
* - DXF
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  - &#x2714;
  -  
  -  
  -  
  -  
  -  
  -  
  - &#x2714;
  - 
```

The table above is not exhaustive and there are many additional special properties of 3D content that are used in specific, often proprietary, applications. For this reason, where future native editing or use of the data (i.e. software specific functionality) is required, it is advisable to additionally retain the original files.

## 3.2 File types for Archiving and Dissemination

### 3.2.1 Archival formats

As with other data types, the most stable formats for preserving 3D date are openly documented, text-based file formats which allow access to data independent of specific software (see [*Planning for the Creation of Digital Data*](https://doi.org/10.5284/h0p2-5584)). For the majority of 3D models the OBJ and PLY formats possess the ability to preserve the geometry and visual surface properties of a 3D object, but they are not suitable for complex scenes with light sources, animation, or complex interactivity. For more complex 3D datasets and visualisations the COLLADA and X3D formats are recommended. Generally not suitable for long-term storage are software specific or binary formats, such as 3DS, MAX, SKP, or BLEND.

If an export function is available, it is advisable to convert data to an archival format in the application in which it was originally created. Where this isn't an option - e.g. the desired format is not supported by the original software - then the file may have to be converted into an intermediary format which can then be converted to the target format using additional software. For example, the conversion of a 3D object created in [Blender](http://www.blender.org) to a 3D-PDF for dissemination could be accomplished via an intermediate export to OBJ from Blender and then a successive import and export to U3D in [MeshLab](http://meshlab.sourceforge.net).

The [Conversion Software Registry](http://isda.ncsa.illinois.edu/NARA/CSR/php/search/conversions.php) enables the discovery of conversion programs for various formats, including intermediary formats. For the conversion of large, complex 3D content there are also specialised commercial programs available such as Polytrans and NuGraph from [Okino](http://www.okino.com).

In certain circumstances where data migration proves difficult it is also advised that the original formats be retained and that source files (textures, visualisations, etc.) or problematic elements of a model be captured separately and stored in a suitable archival format. 

It is also advised that additional images and/or video files are captured. Such files allow a convenient preview or overview of the model and may preserve elements of 'look and feel' that may be difficult to retain in the available preservation formats.

### 3.2.2 Dissemination

In addition to archival formats, 3D models can be easily disseminated as PDF files. The PDF format supports models in the U3D and PRC formats and can additionally integrate text, images, and links alongside the 3D data. 3D PDF files can be viewed in the standard freely-downloadable Adobe Reader (although currently unavailable for Linux systems) and users can apply measurement and annotation tools in order to measure distances, radii and angles. While 3D PDF files provide a convenient, self-contained format for data dissemination, file sizes may be large and the models often require a large amount of RAM, which may not be available on every system. As a result, the 3D PDF format is better used to disseminate lower resolution or down sampled versions of 3D models with full resolution data being made available in other formats. 

Other solutions also exist if direct dissemination of 3D content on the web is required. The first is a commercial system, [Sketchfab](https://sketchfab.com/), which supports the upload, publication and visualisation of 3D models on the web. Sketchfab supports inclusion of 3D content in standard web pages and on social media; it already has a very large community of users and is becoming the de-facto standard for the publication of 3D content on the web.

A second option is the academic open-source platform, 3DHOP ([3D Heritage On-line Presenter](http://3dhop.net/)). 3DHOP is much more flexible than Sketchfab, supporting different presentation layouts and interaction modes, and allows expert users to make changes and configurations. It adopts an efficient multi-resolution format (Nexus) that allows the online publication of full-resolution models via 3D sampling technologies.

A third option is another open-source project, [Aton](http://osiris.itabc.cnr.it/scenebaker/index.php/projects/aton/). Aton is based on the same open-source library as SketchFab, focusing on scene-graph concepts and extending capabilities to multi-resolution and LOD, in order to present and visualise complex 3D datasets such as large terrains. The front-end provides support for mobile browsers and multi-touch devices, and offers several options for camera manipulation, spherical panorama support, rich annotation and immersive VR.

## 3.3 Documentation and Metadata

The documentation of 3D content should primarily follow the principles of the London Charter, specifically Principle 4:

*Sufficient information should be documented and disseminated to allow computer-based visualisation methods and outcomes to be understood and evaluated in relation to the contexts and purposes for which they are deployed.*

As with many other digital datasets, this documentation can exist on a number of levels, particularly if the creation of 3D models is part of a larger fieldwork project involving other methods of data collection and analysis. For 3D models specifically, documentation and metadata can be used to record information relating to the model's geometry, appearance, and scene information, as well as documenting derived objects such as image and video files.

__Project Documentation__

At a minimum, all datasets - 3D or otherwise - will be part of a larger project and as such require top-level metadata regarding the focus, dates, and people and organisations involved. A generic Dublin Core project metadata set is described elsewhere in these guides ([*Project Metadata*](https://doi.org/10.5284/h0p2-5584)) and also within the context of 3D data in section 5.2 of the AHDS Virtual Reality guide [@AHDS2002]. This set of metadata should be applied once at a top-level to cover project information but could also be applied to discrete sub-sets of data where different collection activities have taken place. This is demonstrated elsewhere in the Guides to Good Practice where specific metadata sets are described for [Laser Scanning](https://doi.org/10.5284/rt5g-dm24), [Photogrammetry](https://doi.org/10.5284/wngr-en16), and [CAD](https://doi.org/10.5284/k5hd-hj61) projects.

__Workflow and Processing Documentation__

Where 3D datasets are generated as part of a complex workflow incorporating multiple acquisition and processing stages, metadata and documentation should be broken into logical components according to the data chosen for preservation. Important information to record includes: the type of device used for producing the initial raw sampling; the software tool(s) used to process the sampled data; the type of processing applied to the reconstructed model (e.g. holes filling, surface smoothing, surface simplification, etc.). These elements are discussed in more detail in the guides on [laser scanning](https://doi.org/10.5284/rt5g-dm24), [photogrammetry](https://doi.org/10.5284/wngr-en16), [CAD](https://doi.org/10.5284/k5hd-hj61), and [structured light scanning](https://doi.org/10.5284/aayn-y069).

The 3D-ICONS *Report on Metadata and Thesaurii* [@dandreafernie2013, 30, 49] describes in detail the application of the CARARE2 metadata schema to 3D datasets for workflow documentation and focusses on the relationship between various digital outputs in addition to the provenance and capture/digitisation process. The [CRMdig specification](http://www.ics.forth.gr/isl/index_main.php?l=e&c=656) [@doerr2011crmdig] for provenance metadata was used by the 3D coform project to implement its repository.

The level of detail required to fully document complex workflows will vary depending upon the complexity and range of technique used. Part of this is inter alia the documentation of research resources that have been consulted in order to create the 3D model, the documentation of processes that have been passed through during its development, the documentation of applied methods and a description of relationships and dependencies between its different components.

__File-level Metadata__

In some cases, file formats will allow the storage of certain metadata within the file structure. Nevertheless, it is important that such metadata be recorded separate to the file and externally deposited so that elements can be checked against the file's content. Boeykens and Bogani [-@boeykens2008metadata] describe such sets of metadata in relation to the storage and searching of 3d models in online repositories.

The metadata listed below should be considered as the minimum required at the file level (in addition to that described in table 3 of the section on [*Project Metadata*](https://doi.org/10.5284/h0p2-5584)). These complement the metadata at project and process level discussed above.

```{list-table} Table 3: File-level metadata for 3D models (in addition to that described in table 3 of the Project Metadata section).
:header-rows: 1

* - Element
  - Description
* - Number of Vertices
  - The number of vertices (points) in the model
* - Number of Triangles or Polygons
  - The number of triangles or polygons in the model
* - Geometry Type
  - The type of geometry used within the model (wire frame, parametric, CSG, B-Rep etc. if applicable).
* - Scale
  - What scale is existent, resp. what is represented by 1 unit. 
* - Coordinate System
  - Does the model use a real world or arbitrary coordinate system?
* - Master model or processed model
  - Is the model the master model produced just after raw data processing, or is it a derived model produced from the master (e.g. after hole filling, simplification, smoothing, etc) ?
* - Level of Detail (LOD); Resolution
  - How detailed is the model, what is the resolution of the scan.
* - Layers
  - Does the model use layers? How many?
* - Colour and Texture
  - Does the model contain colour or texture information? How is this stored? If raster texture files are used then these have to be archived separately.
* - Material
  - Information about the material properties of the model and whether they match the physical properties of the actual object.
* - Light Source(s)
  - Number and accuracy of light sources used in the model.
* - Shader
  - Have special or extended shaders been used?
* - Animation
  - Whether animation is used in the model along with description of type (keyframe, motion capture).
* - External Files
  - List of external files that are required in order to correctly open the 3D model (e.g. texture or material files and images for OBJ files).
```