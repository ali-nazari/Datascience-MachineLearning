## Structure of point locations in OpenCV functions([Reference](https://stackoverflow.com/questions/47402445/need-help-in-understanding-error-for-cv2-undistortpoints/47403282#47403282))

The input points need to be an array with the shape (n_points, 1, n_dimensions). So if you have 2D coordinates, they should be in the shape (n_points, 1, 2). Or for 3D coordinates they should be in the shape (n_points, 1, 3). This is true for most OpenCV functions. AFAIK, this format will work for all OpenCV functions, while some few OpenCV functions will also accept points in the shape (n_points, n_dimensions). I find it best to just keep everything consistent and in the format (n_points, 1, n_dimensions).



If you have an array that has the shape (n_points, n_dimensions) you can expand it with 

1. First Solution with **np.newaxis**:

<pre>
>>> points = np.array([[1, 2], [3, 4], [5, 6], [7, 8]])
>>> points.shape
(4, 2)
>>> points = points[:, np.newaxis, :]
>>> points.shape
(4, 1, 2)
</pre>

2. Second Solution with **np.expand_dims()**:

<pre>
>>> points = np.array([[1, 2], [3, 4], [5, 6], [7, 8]])
>>> points.shape
(4, 2)
>>> points = np.expand_dims(points, 1)
>>> points.shape
(4, 1, 2)
</pre>

3. Third Solution with **np.transpose())**:

If your shape is <pre>(1, n_points, n_dimensions)</pre> then you want to swap axis 0 with axis 1 to get <pre>(n_points, 1, n_dimensions)</pre>, 
you must use  <pre>points = np.transpose(points, (1, 0, 2))</pre> 
to put the axes 1 first, then axis 0, then axis 2.

