---
authors:
  - name: null
---

# 2 Creating 3D Data

## 2.1 Project Planning and Requirements

As with all projects creating digital data, certain elements have to be considered at the outset to ensure effective preservation and documentation of 3D content. While a brief overview of the theoretical considerations of 3D and virtual reality models is provided by the AHDS Virtual Reality guide [@AHDS2002, section 5], the [London Charter](http://www.londoncharter.org/) provides the "de facto benchmark to which heritage visualization processes and outputs should be held accountable." When planning a project involving the creation of 3D data, the principles of the London Charter should be taken into account before - although they logically lead into - a consideration of specific documentation or metadata specifications and file formats.

### 2.1.1 London Charter

In 2006 the London Charter was conceived as a means of ensuring the intellectual and technical rigour of computer-based visualisations of cultural heritage. The London Charter strives to define strict rules in dealing with computer-based visualization methods. It contains six principles:

* Principle 1: Implementation, addresses the intended use, purpose, and scope of the London Charter.
* Principle 2: Aims and methods, advises on the importance of the appropriate application of computer based visualisation methods and whether these are the most suitable approaches to accomplish project goals.
* Principle 3: Research Sources, broaches the issue of identification and documentation of relevant sources used for 3D visualisations.
* Principle 4: Documentation, advises on what information should be documented during the development process of 3D content in order to facilitate understanding and use of 3D visualisations. 
* Principle 5: Sustainability, addresses the planning of long-term sustainability and usability of 3D content.
* Principle 6: Access, advises on planning for the effective dissemination of 3D visualisations within the wider cultural heritage sphere.

In the context of this guide, the first three principles of the London Charter can be seen to relate to project planning, data capture, and data creation, while the latter three principles relate to data documentation, formats for preservation, and formats or methods for data dissemination.

# 2.2 Sources and Types of 3D Data

As described in section 1, 3D models can be the end result of a workflow involving a variety of different data acquisition techniques including scanning and image-based modelling techniques. These techniques are described in detail in the 3D-ICONS Guidelines [-@3dicons2014] and in the project's Final Report on Post-processing [@deluca2014]. From an archiving and preservation perspective, these techniques are also covered in the [Laser Scanning](https://doi.org/10.5284/rt5g-dm24), [Photogrammetry](https://doi.org/10.5284/wngr-en16), and [Structured Light Scanning](https://doi.org/10.5284/aayn-y069) guides and case study. Some 3D models may also involve an element of Computer Aided Design (CAD) within their workflow and this is discussed with regards to archiving in the [CAD Guide to Good Practice](https://doi.org/10.5284/k5hd-hj61). While this guide will not go into detail regarding individual acquisition techniques it is important to understand that workflows resulting in 3D models will invariably incorporate a number of acquisition and processing techniques and that the data arising from these stages should be dealt with according to the relevant guidelines.

### 2.2.1 3D Data and Model Types

McHenry and Bajcsy [-@mchenry2008] break down the elements of 3D models into three main categories: geometry, appearance, and scene information. Additionally, data relating to animation or interaction can also be stored within certain models. From these properties the visualisation is computed through a procedure called rendering and results in either static raster graphics, or videos, or interactive models.

__Geometry__

Within geometry, McHenry and Bajcsy identify four general methods that are used to describe the shape of a 3D model: vertex-based wire-frame models (also called triangle-meshes), parametric surfaces mathematically described by curves and surfaces (Non-Uniform Rational B-Splines/NURBS), geometric solids (Constructive Solid Geometry/CSG), and boundary representations (B-reps).

The most common type of 3D models consist of vertices (three dimensional points) which form the corners of polygons commonly created through the subdivision of the surface into triangular patches or quadrilateral faces (see figure 1). A vertex in a 3D-model is described by its position in a Cartesian coordinate system on an x-, y- or z-axis, in which the z-axis usually denotes the depth or, less frequently, the height of the model. Some applications and formats support the use and storage of real-world coordinate systems whereas others use arbitrary systems. Models that are only represented by vertices and the connecting edges are called ''wire-frame models'' or ''meshes'' whereas models consisting of only unconnected vertices are known as ''point clouds'' (figure 2). Point clouds are commonly generated by techniques such as 3D laser scanning and are usually further processed to form a mesh model [@3dicons2014, 18-21]. Wire-frame mesh models can be rendered easily but lack detailed representation of convex or concave surfaces and the sharp edges of the polygons are always visible on closer examination. By using so-called shading algorithms they can be rendered to a smoother, more even appearance although the polygonal origin is often visible in the contour of the object. One method to create a smoother surface is to increase the number of polygons although this also results in a corresponding increase in file size.

```{figure} ../images/3d_fig1.png
:alt: Figure 1

__Figure 1__: The yellow marked vertices describe the highlighted triangle in the 3D model.
```

```{figure} ../images/3d_fig2.png
:alt: Figure 2

__Figure 2__: The Stanford Bunny as wire frame (left) and point cloud model (right).
```

Additionally, many curves and surfaces can also be mathematically calculated to achieve a smoother surface using a few parameters. In 3D graphics the ''parametric representation'' is often achieved by ''NURBS'' (Non-Uniform Rational B-Splines) where the use of mathematically described curves and surfaces allows scalability without the loss of detail. During data migration, if parametric representation is not supported by a target 3D file format, the model then has to be converted to a wire-frame model, leading to information loss about surface structure. The degree of loss of information is comparable to the conversion from vector graphics to raster graphics.

In addition to vertices, surfaces or curves, 3D models can also be constructed using the union, difference, or intersection of simple geometric solids, a process called ''Constructive Solid Geometry (CSG)''.  A traffic cone for example, can be built through the union of a cone and a flat cuboid. CSG requires the storage of the individual geometric solids as well as their associated operations and transformations in order to facilitate subsequent editing of the model. CAD file formats in particular support these properties. A conversion from formats using CSG to those without will result in constraints or restrictions to the editability of the model since it will only be possible to alter the model's polygons and vertices. A reconversion from a polygon-format to a CSG-format may not be trivial.

A further possibility to store 3D geometries in the field of CAD applications is by using ''boundary representation (B-Rep)''. B-rep models indirectly describe 3D objects by describing their bounding surfaces. B-rep models can represent complicated objects but, as a result, the data structure can be complex and memory-intensive.

__Appearance (Surface Properties)__

In addition to 3D model geometry, surface properties also have to be stored in order to describe the complete appearance of a model. The combination of colour information, textures, and material properties can create a highly realistic 3D model.

At a very basic level, point cloud datasets from photogrammetry or laser scanning can have intensity or colour (RGB) values associated with each vertex. The colour information contained in a photographic sampling can also be projected back on to the point-cloud or triangle mesh by assigning a single colour value (either a single RGB pixel value or some intelligent interpolation of multiple pixels projected on the same surface point) to each vertex of the 3D model [@callieri2011processing]. In other 3D models, colour information can also be associated with faces, and/or objects (but this produces representations which are not sufficiently detailed in terms of colour encoding) . Alternatively, a texture image can be applied and wrapped around a model using texture coordinates e.g. an image of wood grain can be applied to a cylinder in order to create a realistic impression of a digital tree trunk. This approach works quite well when assigning a synthetic texture (representing a given material) to a 3D object. When, conversely, there is a need to project back the real color (usually sampled with photographs) on to a 3D model, firstly a mesh parameterization method is applied to the triangulated surface (aimed at producing a transformation linking each point over the 3D surface to points in the 2D texture space). A texture can then be resampled from the input set of images, at the proper resolution required by the specific application, and used at the rendering stage [@callieri2011processing].

In addition to textures, materials can also be modelled in order to assign the correct reflectance properties to an object, e.g. a wooden table will have different reflective properties to that of a glass table. This is done using parameters to describe reflection and refraction of diffuse light, specular light, ambient light, transparency, emissive light etc.

Additional techniques used to modify the appearance of a model include the use of bump, normal, and transparency maps. Using a texture, these maps store values (i.e. height, normals, transparency) which are then applied to the underlying model, changing the rendering of shadows, transparency, and reflections and simulating elements such as the bumpiness of the surface beyond that which exists in the geometry (figure 3). The use of bumps, normal, and transparency maps requires as well a parameterization to be defined on the surface of the 3D model. 

```{figure} ../images/3d_fig3.png
:alt: Figure 3

__Figure 3__: A texture and its application on a 3D model (left). The model (right) has had the IANUS-logo applied to it using bump mapping. The application appears to have altered the model surface in a three dimensional way despite the geometry of the model remaining the same.
```

Surface properties are implemented by 'shaders' during the rendering process. Shaders are essentially sets of instructions that describe how each vertex or pixel should be displayed and, by using different algorithms, and considering various light sources,  a shader can give the impression of various surface properties e.g. a smooth surface (see figure 4 below). Modern approaches typically target a set of specific physical properties in order to realistically represent complex materials (often referred as "PBR" or Physically-based rendering models) for instance albedo, roughness, metallic, and emissive.

```{figure} ../images/3d_fig4.png
:alt: Figure 4

__Figure 4__: The model on the left has been rendered without a shader, making the individual polygons visible. A smoothing shader applied to the same model (right) gives the impression of a smooth, even surface.
```

__Scene Information: Light Sources and Camera Parameters__

The way a 3D model is displayed depends on the scene settings and elements including the size of the viewport, the positioning of the model, the position of the camera and light sources. The viewport is comparable to a stage, defining a frame for the model in terms of height, width and depth. For the camera not only the position but also the viewing direction needs to be stored.

If rendered without light, only a black image of the 3D model is created so light settings, i.e. properly positioned and configured light sources, are necessary to illuminate 3D scenes. Without this information it is up to the user to determine new settings although they may be automatically pre-set by the software.

A scene can contain one or multiple models which in turn can consist of any number of object groups. Grouping is necessary when a model consists of several individual parts or objects. When a group is set, the positioning of the parts also has to be stored and can be described by transformations such as the shifting, rotating, or scaling of objects.

3D scanning devices or image-based techniques produce huge amounts of data and it is quite easy to produce 3D models so complex that it is impossible to fit them in RAM or to display in real-time. This complexity is usually reduced in a controlled manner, either by producing discrete Level Of Details (LOD) or Multiresolution representations. For large and complex scenes it can be useful to store different Levels Of Detail for individual objects to increase the efficiency of the rendering phase [@di2014web]. Adopting an LOD representation means that each single object in the scene is represented by means of several different models (in practice from 3 to 5 models, each one associated to a distance from viewer interval). An object in the foreground of the scene, close to the camera, would be displayed at a high level of detail whereas trees or other objects in the background will be displayed using a lower resolution level. LOD representations can be easily built using geometric simplification algorithms, provided in many geometry processing tools (e.g. see the simplification features of [MeshLab](http://meshlab.sourceforge.net/)). The level of detail for 3D models is dependent on the quantity of polygons. By definition, LOD representations are characterised by a small number of different models. Conversely, Multi-resolution approaches allow the production of a very large number of different models from a single representation and in real time (adopting view-dependent criteria). Several multiresolution representation schemes have been defined in literature [@di2014web].

```{figure} ../images/3d_fig5.png
:alt: Figure 5

__Figure 5__: Effects of different Levels of Detail applied to the Stanford Bunny 3D model (left to right: 69451, 3851 and 948 polygons).
```

__Animation and interaction__

Animation and interaction require the storage of additional data and need to be considered both when assessing archiving formats and levels of metadata and documentation. Where animations are exported to video formats then the guidelines for [Digital Video](https://doi.org/10.5284/q8fe-gq36) should be followed. 

## 2.3 File formats 

As described by McHenry et al. [-@mchenry2008; -@mchenry2011], a vast array of file formats exist for 3D data, each with varying properties and capabilities with regard to how they store geometry, textures, light sources, viewport and cameras. An overview of common formats is given below (table 1, after @mchenry2008). Recommended formats are discussed in more detail in Section 3 alongside the specific storage properties of common formats (table 2). 


```{list-table} Table 1: Overview of common 3D data formats
:header-rows: 1

* - Format
  - Properties / Technologies
  - Description
  - Recommendations
* - .x3d
  - ISO standard XML-based format developed by the Web3D consortium
  - The [X3D](http://www.web3d.org/what-x3d-graphics) format (extensible 3D graphics) was developed by the Web3D Consortium and has been ISO certified since 2006. The format is suitable for the storage of single 3D models as well as of complex 3D content such as virtual reality. The format succeeds VRML and, as such, should be preferred to it. The format is core to 3D in HTML5.
  - Suitable for preservation and recommended for complex 3D content.
* - .dae
  - [COLLADA](http://www.khronos.org/collada) XML-based exchange format
  - COLLADA  (collaborative design activity) is an XML-based format developed by the not-for-profit Khronos Group consortium and designed as an interchange format for complex 3D data. ISO/PAS 17506:2012 provides a standardised specification for the [COLLADA schema](http://www.iso.org/iso/catalogue_detail.htm?csnumber=59902).
  - Suitable for preservation and recommended for 3D content where x3d is not an option.
* - .obj (also includes optional .mtl and .jpg files)
  - Wavefront OBJ file
  - The open OBJ format was developed by Wavefront Technologies and is supported by a large user community with open specifications. Specifications are available for both the [OBJ](http://local.wasp.uwa.edu.au/~pbourke/dataformats/obj/) and [MTL](http://paulbourke.net/dataformats/mtl/) components. The format stores both geometry and textures and consists of an obj file (ascii or binary format) together with an mtl (material/texture) file and image (actual texture).
  - Suitable for preservation of wire frame or textured models. ASCII format is preferred for preservation.
* - .ply
  - Stanford polygon file format
  - The PLY format, also known as the Stanford Triangle Format, is a simple format with ASCII and binary versions developed at Stanford University primarily for 3D scanning data. The format is inspired by OBJ but allows extension to incorporate a variety of properties including colour and transparency, surface normals, texture coordinates and data confidence values. The format also allows different properties for the front and reverse of a polygon. While the addition of certain extensions will not make the format unreadable, not all software supports all extensions so data may at best be unread or, in a worst case scenario, be discarded when files are resaved.
  - Suitable for preservation (ASCII version) although file content should be clearly documented.
* - .vrml, .wrl, .wrz
  - [Virtual Reality Modelling Language](http://www.web3d.org/standards)
  - Virtual Reality Modelling Language is a text-based standard (ISO/IEC 14772) for representing 3D interactive vector graphics and is the predecessor of X3D. The most recent version was published in 1997 as VRML97
  - Suitable for preservation although now replaced by X3D.
* - .u3d
  - [Universal 3D format](http://www.ecma-international.org/publications/standards/Ecma-363.htm)
  - The Universal 3D format has been developed by the 3D Industry Forum and was standardised by Ecma international (ECMA) in 2005. U3D is a compressed format, designed for data exchange, and offers a similar functional range as X3D and COLLADA and has been especially developed for 3D contents of PDF-documents.
  - Unsuitable for preservation.
* - .stl
  - Stereolithography or [Standard Tessellation Language](http://www.ennex.com/~fabbers/StL.asp)
  - STL was developed by 3D Systems and is prevalent in the field of 3D printers and digital fabrication. The ASCII version of STL only stores 3D model geometry (no textures) whereas the binary version, with the help of an extension, also saves colour information and requires less storage space. While an old format, STL is still well supported, particularly by 3d scanners, and is easy to transfer data to due to its simple structure and human readable format. As the format only exports surfaces not lines it is not suitable for photogrammetry.
  - Suitable for preservation (ASCII format) for very basic datasets (see supported properties in table 2).
* - .dxf
  - Autodesk Drawing Interchange Format
  - The Autodesk DXF format is primarily a CAD data exchange format and should only be used for 3D content created by CAD software. The format itself has undergone many revisions and updates over its long history with the format capability evolving over time. More information on the DXF format is available in the [CAD guide](https://doi.org/10.5284/k5hd-hj61).
  - Only suitable for preservation of native CAD datasets.
* - .fbx
  - Autodesk 3D asset exchange format
  - A proprietary interchange format owned by Autodesk. The FBX formats aims to support data exchange between 3D software such as Maya and 3DS Max and files can include animation, textures, and geometry.
  - Not suitable for preservation.
* - .3ds, .max
  - Autodesk 3DS Max files
  - roprietary binary formats used by Autodesk 3DS Max.
  - Not suitable for preservation.
* - .skp
  - Google Sketchup format
  - Native format used by Google SketchUp.
  - Not suitable for preservation.
* - .blend
  - Blender format
  - Native Blender binary format for complex 3D datasets.
  - Not suitable for preservation.
* - .prc
  - Product Representation Compact format
  - PRC is a highly compressed format for storing 3D design data and is largely used in CAD/CAE/CAM environments and within the 3D PDF format. The format was adopted as the ISO standard [ISO14739-1](http://www.iso.org/iso/catalogue_detail.htm?csnumber=54948) in 2014.
  - Not suitable for preservation.
* - .pdf
  - Adobe Portable Document Format
  - 3D content in PDF files is based on the U3D and/or PRC formats (see above).\\The PDF format is self-contained and allows basic operations such as measuring, cross sections, light sources, wireframe views. While convenient for viewing data without specialist software the format is largely a 'dead end' in that data cannot easily be extracted.
  - Not suitable for preservation.
* - .nxs
  - [Nexus format](http://vcg.isti.cnr.it/nexus/index.php)
  - Nexus is an open source multiresolution format developed by CNR-ISTI. The Nexus software package includes a format specification alongside tools for the conversion of .ply files to the multiresolution format and a visualisation library aimed at the interactive rendering of very large surface models. The format is used by 3DHOP, an open source platform for web-based visualisation of large 3D meshes.
  - Not suitable for preservation 
```