shpdump(1) -- dumps as text and/or validates the content of an ESRI shapefile
=============================================================================

##SYNOPSIS
`shpdump` [-_validate_] _shp_file_

##DESCRIPTION
Prints the contents of the shapefile _shp_file_ to standard output in textual format.  Shapefiles actually consist of two files with the same basename and extensions `.shp` and `.shx` (or `.SHP` and `.SHX`) containing the shape data and shape index respectively.  The files to open are determined by first stripping any filename extension from _shp_file_ and attempting to open the files _shp_file_`.shp` or _shp_file_`.SHP`, and _shp_file_`.shx` or _shp_file_`.SHX` for the respective data and index files.

Output consists of a header giving number and type of shapes in the file and the bounds for the minimum and maximum _X_, _Y_, _Z_, and _M_ values appearing in the shapes.  The header is followed by the geometric data for each shape in the file.  All shapes in the file should be of the same type, except that `NullShape` typed shapes may be intermixed with any other type.  The header has the form

    Shapefile Type: type # of Shapes: count

    File Bounds: (minX,minY,minZ,minM)
             to  (maxX,maxY,maxZ,maxM)

See section `SHAPE TYPES` below for the list of possible shape types.

Next for each shape in the file a header giving it's _shape_index_, it's type _type_, number of vertices _nVertices_, number of parts _nParts_, and bounding box is given, followed by the vertex data of each part.

    Shape:  shape_index (type) nVertices=nVertices, nParts=nParts
      Bounds: (minX,minY,minZ,minM)
          to  (maxX,maxY,maxZ,maxM)

      vertices of the first part

    + vertices of the second part...

    + vertices of the last part

The _shape_index_ of a shape is the number of the shape starting from zero in the shape file.  Each vertex has the form

    (X,Y,Z,M)

If there are multiple parts then the type of the part is appended appended to first vertex of each part, and the first vertex of the second and following parts is preceded by a plus (`+`) sign.  The part type is `Ring` for all shape types except `MultiPatch` where it is the type of a surface patch.  See below for the description of possible part types.

##SHAPE TYPES
Each type of shape except `MultiPatch` typed shapes comes in three flavours: The normal unsuffixed type, where points lie in _X/Y_-space; a type with suffix _M_ where points lie in _X/Y_-space and additionally have a _measure_ value in _M_-space; and finally a type with suffix _Z_ where points lie in _X/Y/Z_-space and also have a measure value in _M_-space.

 * `NullShape`:
 A shape without data.  Shapes of this type may be intermixed with other shapes and are sometimes used to represented deleted or missing geometric data for a shape.

 * `Point` or `PointZ` or `PointM`:
 A single point.

 * `Arc` or `ArcZ` or `ArcM`:
 Piecewise linear paths.  Shapes of this type may consist of multiple parts which may or may not intersect and/or connect.  Arcs are called `PolyLines` in the shapefile specification.

 * `Polygon` or `PolygonZ` or `PolygonM`:
 Polygon shapes consist of one or more parts, called _rings_, that each define a closed path.  Rings must contain at least four vertices with the first and last vertices being equal, and must not self-intersect.  For shapes of type `Polygon`, the rings define a polygon with optional holes by giving the vertices of inner rings a counterclockwise orientation and the vertices of outer rings a clockwise orientation.  Intersection and orientation is always computed in _X/Y_-space and never in _X/Y/M_-space.

 * `MultiPoint` or `MultiPointZ` or `MultiPointM`:
 A set of points.

 * `MultiPatch`:
 A `MultiPatch` represents one or more surfaces in `X/Y/Z`-space, and consists of a number of parts called it's _surface_ _patches_.  Each surface patch describes a either a surface or a hole in another surface,  depending  on the type of the patch.  Patches may share a common boundary but may not otherwise intersect.  The type of a patch may be one of

    `TriangleStrip`:
    A set of connected triangles.  The first three points define the first triangle and every following point defines a new triangle using the new point and the two previous points.

    `TriangleFan`:
    A  set of connected triangles.  The first three points define the first triangle and every following point defines a new triangle using the previous point, the current point, and the first point, thus forming a fan of triangles around the first point.

    `OuterRing`:
    The outer ring of a sequence of rings defining a polygon with holes.  All following parts of type `InnerRing` are taken to be the holes of the polygon.  The sequence of rings ends with the first non-`InnerRing` typed part or the part of the shape, whichever comes first.

    `InnerRing`:
    An inner ring in a sequence of rings defining a polygon with holes.  This type of part may only follow an `OuterRing` or other `InnerRing` typed parts.

    `FirstRing`:
    The first in a sequence of rings defining a polygon of unspecified type.  The following parts of type `Ring` defines the other rings in the polygon.  This type of part is used when the innerness or outerness of a polygon isn't known or applicable.  The sequence of rings defining the polygon ends with the first non-`Ring` typed part or the last part of the shape, whichever comes first.

    `Ring`:
    A ring in a sequence of rings defining a polygon of unspecified type.  It may only follow a `FirstRing` or other `Ring` typed parts.

    `UknownPartType`:
    This type is returned for parts whose type isn't recognised.

 * `UnknownShapeType`:
 This type is returned for shapes whose type isn't recognised.

##OPTIONS
 * -_validate_:
 count the number of objects that have invalid ring ordenings

   Performs validation on the orientation of inner and outer rings in `Polygon`, `PolygonZ`, and `PolygonM` objects.  According to the shapefile specification outer rings should be given a clockwise orientation, and inner rings that define holes a counterclockwise orientation.  If some rings of a shape are oriented the wrong way around then the following message is output after dumping that shape:

   _count_ rings wound in the wrong direction.

   In addition the total number of shapes with problem rings is output after the last shape has been dumped:

   _count_ object has invalid ring orderings.

 * _shp_file_:
 the name of an existing shapefile.

##EXIT STATUS
 * `0`:
 Successful program execution.

 * `1`:
 No shapefile _shp_file_ was given or it couldn't be opened.

##EXAMPLE
    $ shpdump shapefile.shp

    Shapefile Type: Arc   # of Shapes: 3

    File Bounds: ( 3531586.750, 7253086.100,0,0)
             to  ( 3536417.463, 7778375.875,0,0)

    Shape:0 (Arc)  nVertices=2, nParts=1
      Bounds:( 3536397.797, 7253086.100, 0, 0)
          to ( 3536417.463, 7253163.597, 0, 0)
         ( 3536397.797, 7253163.597, 0, 0) Ring
         ( 3536417.463, 7253086.100, 0, 0)

    Shape:1 (Arc)  nVertices=3, nParts=1
      Bounds:( 3458966.390, 7373335.808, 0, 0)
          to ( 3459141.856, 7373474.681, 0, 0)
         ( 3458966.390, 7373474.681, 0, 0) Ring
         ( 3458979.042, 7373466.273, 0, 0)
         ( 3459141.856, 7373335.808, 0, 0)

    Shape:2 (Arc)  nVertices=7, nParts=1
      Bounds:( 3531586.750, 7777880.500, 0, 0)
          to ( 3532930.206, 7778375.875, 0, 0)
         ( 3531586.750, 7777880.500, 0, 0) Ring
         ( 3532228.265, 7778072.455, 0, 0)
         ( 3532310.897, 7778119.445, 0, 0)
         ( 3532367.866, 7778144.877, 0, 0)
         ( 3532440.559, 7778168.920, 0, 0)
         ( 3532506.504, 7778190.785, 0, 0)
         ( 3532930.206, 7778375.875, 0, 0)

    $

##DIAGNOSTICS
The following diagnostics may be issued on stdout:

Unable to open:_shp_file_

##AUTHOR
`shpdump` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw. It was further enhanced with the man page written by Joonas Pihlaja (jpihlaja@cc.helsinki.fi).

##BUGS
The `-`_validate_ option supports only one outer ring in a polygonal shape and assumes that the first ring in a shape is the outer ring.  It doesn't support polygons inside `MultiPatch` shapes.  The _X_ and _Y_ coordinates of a point are printed to three decimal places only.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

