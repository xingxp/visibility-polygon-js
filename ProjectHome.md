Download latest version: http://www.byronknoll.com/visibility_polygon_1-5.zip

This code is released into the public domain - attribution is appreciated but not required.

Made by Byron Knoll in 2014.

Demo: http://www.byronknoll.com/visibility.html

This library can be used to construct a visibility polygon for a set of line segments.

The time complexity of this implementation is O(N log N) (where N is the total number of line segments). This is the optimal time complexity for this problem.

The following functions should be useful:
  1. compute(position, segments):
    * Computes a visibility polygon. O(N log N) time complexity (where N is the number of line segments).
    * Arguments:
      * position - The location of the observer. Must be completely surrounded by line segments (an easy way to enforce this is to create an outer bounding box).
      * segments - A list of line segments. Each line segment should be a list of two points. Each point should be a list of two coordinates.  Line segments can **not** intersect each other (although overlapping vertices is OK). Use the "breakIntersections" function to fix intersecting line segments.
    * Returns: The visibility polygon (in clockwise vertex order).
  1. inPolygon(position, polygon):
    * Calculates whether a point is within a polygon. O(N) time complexity (where N is the number of points in the polygon).
    * Arguments:
      * position - The point to check: a list of two coordinates.
      * polygon - The polygon to check: a list of points. The polygon can be specified in either clockwise or counterclockwise vertex order.
    * Returns: True if "position" is within the polygon.
  1. convertToSegments(polygons):
    * Converts the given polygons to list of line segments. O(N) time complexity (where N is the number of polygons).
    * Arguments: a list of polygons (in either clockwise or counterclockwise vertex order). Each polygon should be a list of points. Each point should be a list of two coordinates.
    * Returns: a list of line segments.
  1. breakIntersections(segments)
    * Breaks apart line segments so that none of them intersect. O(N^2) time complexity (where N is the number of line segments).
    * Arguments: a list of line segments. Each line segment should be a list of two points. Each point should be a list of two coordinates.
    * Returns: a list of line segments.

Example code:
```
var polygons = [];
polygons.push([[-1,-1],[501,-1],[501,501],[-1,501]]);
polygons.push([[250,100],[260,140],[240,140]]);
var segments = VisibilityPolygon.convertToSegments(polygons);
segments = VisibilityPolygon.breakIntersections(segments);
var position = [10, 10];
if (VisibilityPolygon.inPolygon(position, polygons[0])) {
  var visibility = VisibilityPolygon.compute(position, segments);
}
```