shputils(1) -- shapefile utility
================================

##SYNOPSIS
`shputils` _in_shp_file_ _out_shp_file_ _args_

##DESCRIPTION
The program will append to an existing shape file or it will
create a new file if needed.
Only the items in the first output file will be preserved.
When an item does not match with the append theme then the item
might be placed to an existing item at the same position and type.

OTHER FUNCTIONS:

- Describe all items in the dbase file (Use ALL for more than 5000 recs.)

- Select a group of shapes from a comma separated selection list.

- UnSelect a group of shapes from a comma separated selection list.

- Clip boundary extent or by theme boundary.
    Touch writes all the shapes that touch the boundary.
    Inside writes all the shapes that are completely within the boundary.
    Boundary clips are only the min and max of a theme boundary.

- Erase boundary extent or by theme boundary.
    Erase is the direct opposite of the Clip function.

- Change coordinate value units between meters and feet.
    There is no way to determine the input unit of a shape file.
    Skip this function if the shape file is already in the correct unit.
    Clip and Erase will be done before the unit is changed.
    A shift will be done after the unit is changed.

- Shift X and Y coordinates.

Finally,

There can only be one select or unselect in the command line.

There can only be one clip or erase in the command line.
There can only be one unit and only one shift in the command line.

Examples:

 shputils in.shp out.shp   SELECT countycode 3,5,9,13,17,27

 shputils in.shp out.shp   CLIP   10 10 90 90 Touch   FACTOR Meter Feet

 shputils in.shp out.shp   FACTOR Meter 3.0

 shputils in.shp out.shp   CLIP   clip.shp Boundary Touch   SHIFT 40 40

  shputils in.shp out.shp   SELECT co 112   CLIP clip.shp Boundary Touch

USAGE: shputils  <DescribeShape>   {ALL}

USAGE: shputils  <InputShape>  <OutShape|AppendShape>

   { <FACTOR>       <FEET|MILES|METERS|KM> <FEET|MILES|METERS|KM|factor> }

   { <SHIFT>        <xshift> <yshift> }

   { <SELECT|UNSEL> <Item> <valuelist> }

   { <CLIP|ERASE>   <xmin> <ymin> <xmax> <ymax> <TOUCH|INSIDE|CUT> }

   { <CLIP|ERASE>   <theme>      <BOUNDARY>     <TOUCH|INSIDE|CUT> }

Note: CUT is not complete and does not create intersections.
     For more information read programmer comment.

