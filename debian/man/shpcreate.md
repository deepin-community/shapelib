shpcreate(1) -- create an empty ESRI shapefile
==============================================

##SYNOPSIS
`shpcreate` _shp_file_ [`point`|`arc`|`polygon`|`multipoint`]

##DESCRIPTION
Creates an empty shapefile supporting shapes of the given type.  Shapefiles actually consist of two files with the same basename and extensions `.shp` and `.shx` (or `.SHP` and `.SHX`) containing the shape data and shape index respectively.  The files to create are determined by first stripping any filename extension from _shp_file_ and attempting to create the files _shp_file_`.shp` or _shp_file_`.SHP`, and _shp_file_`.shx` or _shp_file_`.SHX` for the respective data and index files.  The supported values for the _shapetype_ argument are: `point`, `arc`, `polygon`, and `multipoint`.

##OPTIONS
 * _shp_file_:
 the name of the shapefile to be created. Doesn't need the extension

 * `point`|`arc`|`polygon`|`multipoint`:
 the type of shapefile that you wish to create. Must specify a valid option.

##EXAMPLE
`shpcreate` _testpolygon_ `polygon`

this will create a polygon shapefile named testpolygon (in fact _testpolygon_`.shp` and _testpolygon_`.shx` will be created).

##EXIT STATUS
 * `0`:
 Successful program execution.

 * `1`:
 Missing _shp_file_ or _shapetype_ argument.

 * `2`:
 Unknown shapetype.

 * `3`:
 Unable to create the shapefile.

##DIAGNOSTICS
The following diagnostics may be issued on stdout:

Shape Type `_shapetype_' not recognised.

Unable to create:_shp_file_

##AUTHOR
`dbfdump` is part of shapelib, maintained by Frank Warmerdam. This guide was created by Eduardo Patoo Kanegae and converted to manpage by Johan Van de Wauw. It was further enhanced with the man page written by Joonas Pihlaja (jpihlaja@cc.helsinki.fi).

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpadd`(1), `shpcat`(1), `shpcentrd`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

