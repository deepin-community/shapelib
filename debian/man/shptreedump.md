shptreedump(1) -- dump an ASCII representation of a quadtree
============================================================

##SYNOPSIS
`shptreedump` [-maxdepth _n_] [-search _xmin_ _ymin_ _xmax_ _ymax_] [-v] [-o _indexfilename_] [-i _indexfilename_] _shp_file_

##DESCRIPTION
Utility for creating and dumping an ASCII representation of a quadtree.

##OPTIONS
 * -maxdepth _n_:
 max tree depth

 * -search _xmin_ _ymin_ _xmax_ _ymax_:
 limit search to box

 * -v:
 verbose output

 * -o _indexfilename_:
 output index filename

 * -i _indexfilename_:
 input index filename

 * _shp_file_:
 the name of an existing shapefile.

##AUTHOR
`shptreedump` is part of shapelib, maintained by Frank Warmerdam.

##SEE ALSO
`dbfadd`(1), `dbfcat`(1), `dbfcreate`(1), `dbfdump`(1), `dbfinfo`(1), `shpcat`(1), `shpcentrd`(1), `shpcreate`(1), `shpdump`(1), `shpdxf`(1), `shpfix`(1), `shpinfo`(1), `shpproj`(1), `shprewind`(1), `shptest`(1)

