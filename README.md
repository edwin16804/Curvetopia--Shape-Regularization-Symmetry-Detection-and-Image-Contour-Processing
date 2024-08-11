# Curvetopia--Shape-Regularization-Symmetry-Detection-and-Image-Contour-Processing

# Project Description: Shape Regularization, Symmetry Detection, and Contour-Based Image Processing

This project involves developing a comprehensive Python-based tool for processing geometric shapes, both from CSV files and images. The tool reads path data from CSV files or processes shapes directly from images, visualizes the paths, regularizes the shapes to conform to ideal geometric forms (such as straight lines, circles, and rectangles), and then detects and reports symmetry within these shapes. Additionally, it includes functionality for contour detection and shape filling in images. The output includes visual plots of the original and regularized shapes, files saved in SVG and PNG formats, and processed images with filled contours.

# Overview

Shapes represented as sequences of points or within images may not always perfectly align with ideal geometric forms due to noise, imperfections in data collection, or other factors. This project aims to regularize these shapes, meaning it transforms them into their ideal forms while maintaining their general structure. The tool then analyzes these regularized shapes to detect any inherent symmetries, such as symmetry along the x-axis, y-axis, or diagonal lines. For image data, the project includes an additional step of detecting and filling contours, which can be useful for visualizing and analyzing the structural components of the shapes.

# Functionality

1. **CSV File Reading**: The tool reads a CSV file where each row represents a point in a path, with paths grouped by a unique identifier in the first column. The `read_csv` function organizes these points into paths based on the unique identifiers, making it easier to process them as distinct shapes.

2. **Image Processing with OpenCV**: For images, the tool includes a process that uses OpenCV to detect and fill shapes:
    - **Loading and Grayscaling**: The image is loaded from a PNG file and converted to grayscale to simplify the analysis.
    - **Edge Detection**: Gaussian blur is applied to reduce noise, followed by Canny edge detection to identify the edges within the image.
    - **Contour Detection and Filling**: The contours of the shapes are detected from the edges, and these contours are filled with a color (e.g., green) to highlight the shapes in the image. The processed image is then saved and displayed.

3. **Visualization**: The `plot` function provides a visual representation of the shapes as they are initially read from the CSV, while `cv2_imshow` displays the original and processed images, allowing for a direct comparison of the before and after states.

4. **Shape Regularization**: The `regularize_shape` function applies geometric rules to convert irregular point sequences into idealized shapes.
    - **Straight Line Detection**: If a shape is identified as nearly straight, it is reduced to a line segment between the first and last points.
    - **Circle Detection**: For shapes approximating a circle, the tool calculates the average radius and repositions the points evenly around the center.
    - **Rectangle Detection**: Shapes resembling rectangles are adjusted to form a perfect rectangle with aligned edges.

5. **Symmetry Detection**: The tool checks for symmetry in regularized shapes using the `find_symmetry` function. It assesses symmetry across various axes and diagonal lines and outputs whether the shape is symmetric about the x-axis, y-axis, or along lines such as y=x or y=-x.

6. **SVG and PNG Output**: The `polylines2svg` function converts the regularized shapes into SVG format, a vector graphics format that allows for scalable and detailed visualization. Additionally, the tool saves the output as a PNG image, ensuring compatibility with a wide range of applications.

7. **Complete Workflow**: The `process_file` function integrates all these steps, from reading the CSV to producing the final outputs. It also prints the detected symmetries to the console, providing immediate feedback on the analysis.

# Applications

This tool is versatile and can be used in various fields requiring geometric analysis, such as computer graphics, architectural design, and pattern recognition. The inclusion of image processing capabilities extends its utility to scenarios where shapes are embedded within images, allowing for contour detection and filling, which are essential in image segmentation tasks.

# Conclusion

This project offers a robust solution for reading, regularizing, visualizing, analyzing geometric shapes from CSV files, and processing shapes directly from images. Through its multifaceted functionality, it ensures that even imperfectly defined shapes can be regularized, analyzed for symmetry, and visualized in both vector and raster formats, providing clear and accurate geometric insights.
