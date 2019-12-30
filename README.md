# gpcj
General Poly Clipper Algorithm in Java

## Note

GPCJ was original[1] written by Daniel Bridenbecker

The purpose of this repository is to bring back the source and create a buildable, tested version.
So this can be used again.

## Build
1. Checkout
2. `mvn clean install`


## Original page
GPCJ is a Java version of the General Poly Clipper algorithm developed by Alan Murta (gpc@cs.man.ac.uk). The home page for the original source can be found at http://www.cs.man.ac.uk/aig/staff/alan/software/.

Alan's algorithm was converted because an algorithm in Java was needed for finding the intersection of two non-convex polygons. After a lot of web surfing, a sutible algorithm could not be found. Alan had an algorithm that appeared to be exactly what was needed but it was in C.

### Features

This conversion of the algorithm does NOT support all of the features in the original. However, the following is a list of features it does support (list from Alan's website with editing):

* Intersection, exclusive-or and union clip operations are supported.
* Polygons may be comprised of multiple disjoint contours.
* Contour vertices may be given in any order - clockwise or counter-clockwise.
* Contours may be convex, concave or self-intersecting.
* Contours may be nested (i.e. polygons may have holes).
* Hole and external contours are differentiated in the result.
* Coincident edges and degenerate regions are handled correctly.

In converting the algorithm from C to Java, changes were maded and not all of the original features were supported. Below is a list of the known changes:

* Polygon Differences - The algorithm is there to support it, but a public method has not been provided nor has it been tested.
* Output - No tristrips.
* Output - New Poly interface.
* Sorted output so that holes are always last in the list of contours/inner polygons.
* Slightly changed things to be more object oriented, especially with the output.
* Created a starter set of unit tests for intersection, union, and xor.

### Demo

So that others could see the algorithm in action, a simple demo tool has been created.

### Source

The source code for GPCJ is provided with an Apache type license where the intent is that you can use the source any way you want, but you must acknowledge SEI in your documentation. Also, the source has an "as is" warranty, so you can't take us to court. :)

* License Agreement
* Download GPC Source code - includes javadocs
* API documentation
The heart of the algorithm is found in com.seisw.util.geom.Clip.java. The class is public and static but the intent is for the user to use the com.seisw.util.geom.PolyDefault. PolyDefault is a polygon type class that has methods such as intersection() and union() that call the algorithm. The Clip class was made public because the user create their own class that implements the com.seisw.util.geom.Poly interface.

The java.awt.Polygon class was not used because the clipper algorithm required the ability to have a "Polygon" that was made up of disjoint contours (possibly why the contours name was used instead of polygon originally).

The com.seisw.util.geom.Poly interface is a little weird because I really wanted a single interface for handling the output. By "wierd", I mean that the interface supports two different concepts - a set of inner polygons and a set of points. See the API documentation for more information.

### Code Changes

SEI would appreciate being notified if you are using this code. Also, if you would like to contribute any changes, that would be appreciated too.


[1]: http://web.archive.org/web/20090213122910/http://www.seisw.com/GPCJ/GPCJ.html