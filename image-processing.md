## Structure of point locations in OpenCV functions

The input points need to be an array with the shape (n_points, 1, n_dimensions). So if you have 2D coordinates, they should be in the shape (n_points, 1, 2). Or for 3D coordinates they should be in the shape (n_points, 1, 3). This is true for most OpenCV functions. AFAIK, this format will work for all OpenCV functions, while some few OpenCV functions will also accept points in the shape (n_points, n_dimensions). I find it best to just keep everything consistent and in the format (n_points, 1, n_dimensions).
