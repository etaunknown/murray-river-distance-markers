# River Distance Markers

This repository contains the geofiles for the positions of known distance
markers that are found along rivers of the Murray-Darling Basin in Australia. 

## Description

Along the Murray River from the Hume Dam there are blue signs that were put up
by the NSW and SA water authorities to mark the distance from the river mouth 
in kilometres. These are based on mile marker references from older maritime 
pilots of the river.

These allow users to find their position on hard copy maps, accurately share
locations of points of interest or hazards along the river and as a way of
communicating their position to friends and family as well as various maritime
organisations in the event of an emergency.

Since these markers reflect the distance from the river mouth at the time these
were originally assigned, these do deviate from the actual mainstem of the
river as we know it today and cause some inconsistencies with distance
measurements. 

The highest blue marker found on the river is 2,224 that can be found just 
downstream from the Hume Dam / Weir. For most paddlers, the mainstem of the
river is just 2,142 km from this point with significant savings possible by
cutting corners, taking a direct path across Lake Mulwala, and going directly
to the river mouth via the Tauwitchere Barrage rather than going passing 
Goolwa.

Similar markers are found on the lower Darling River, starting at 0 at Wentworth
and extend up to around Pooncarie.   

## Shapefile attributes

The data is stored in a MultiPoint ESRI Shapefile with the following attributes:

name: The number. This is not an unique field with a number of locations
      containing duplicate signs. Numbers below 10 are prefixed with a zero.

desc: A description containing additional information about the marker, such as
      its condition, location or if hidden behind other objects.

status:
  - g: Good condition or unclassified (default)
  - d: Damaged or faded, difficult to read,
  - m: Confirmed location but it is not seen on recent trips. Potentially just
       missed or hidden behind other objects.
  - n: No known records of a sign at this location.
       i.e. any calculated position with no known historical references.

type: Describes what type of sign it is.
  - bm: normal blue marker
  - b: marker is on a bouy. These were all replaced prior to 2022.
  
    These may be extended to include:
  
  - mm: older white mile markers signs put up by the Libra Libra houseboat company.
  - mt: even older mile markers that were carved into tree trunks.
  - other custom markers.

river: Defines what river the marker is on. A single files may tracks a few locations
       on smaller tributaries.
       
src: The source reference for the marker. This is one of:
  - gps: Manually recorded GPS point of an existing sign.
  - calc: Calculated by creating a chainage between known sign locations.
  - ref: From one of the listed references, potentially moved slightly towards
         the calculated location if this is sightly unclear.

year: Year that the location or description was last updated. 

### Coordinate Reference System (CRS)

These are based on the Geocentric Datum of Australia (GDA2020) using the NSW
Lambert Projected CRS.

Name: EPSG:8058 - GDA2020 / NSW Lambert
Units: meters

I choose the NSW Lambert since the basin traverses two MGA longitude zones 54
and 55. This decision has not been vetted by anyone with formal training in
these matters, but this appeared to provide more accurate measurements than using
EPSG:1168 GDA2020.

## How to Use

You can use any GIS package (ArcGIS, QGIS, GRASS GIS, etc) to access and export 
the data according to your requirements. These may have to be reprojected into
a Coordinate Reference System that your app or device supports. 

For example, Avenza maps failed to project both EPSG:8058 (GDA2020 / NSW Lambert)
and EPSG:7854 (GDA2020 / MGA zone 54) and I had to reproject these maps to World
Mercator WGS 84 (EPSG:3395).

Alternatively, the latest version of just the sign locations is available here 
with multiple export formats World Mercator WGS 84 (EPSG:3395):

* Keyhole Markup Language (KML)
* GPS Exchange Format (GPX)
* Well Known Text (WKT)
* JavaScript Object Notation (JSON)
* Comma-separated values (CSV)

https://etaunknown.com/expeditions/murray-river/planning/markers

### Mapping software to visualise the data points

There are a number of different Apps that can be used

*Google Earth*
This allows you to import and view KML files while online.

*Avenza Maps*
The premion version allows you to add custom layers over existing maps. 

### History

The first version was a basic KML file of the known locations from my own
personal journey down the River Murray in 2020 along with the estimated 
positions of the missing locations based on a chainage made using qGIS that
followed the current course of the river.

The initial commit into this repository is an extention of this that used
other sources to better estimate the original path of the river that was
the basis of measurements done along the river.

The additional sources used can be found in the Acknowledgments section at the
bottom of this file along with other known sources that reference these markers.

## Authors

Alan Davison

## Version History

* 1.0
    Initial public release that is based on a single trip down the Murray
    with a number of trips downstream of Wentworth.

## License

This project is licensed under the Creative Commons Attribution-NonCommercial
4.0 International License (CC BY-NC 4.0) - see the LICENSE.md file for details.

Attribution: Alan Davison with a link to this repository or https://etaunknown.com/expeditions/murray-river

## Acknowledgments

As well as manual GPS corrodinates from various trips, the following sources 
were used to estimate the locations of various missing markers or simply are
alternative references that show the positions of some of these markers.

* River of Islands - River Murray Charts, Yarrawonga To Hume Dam by Kath and Leon Bentley
* [Murray River Charts](https://rivermurraycharts.com.au/) - Renmark to Yarrawonga by Maureen Wright
* Murray River Pilot Charts - Goolwa to the SA/NSW border and Lower Murray, Lakes and Coorong by Baker and Reschke
* [Murray River Access Maps](https://spatialvision.com.au/murray-river-access-guides/) by Spatial Vision
* [Paddle SA](https://paddlesa.au/) Maps
