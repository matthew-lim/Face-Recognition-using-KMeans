# Face-Recognition-using-KMeans

Flow and variables explained in comments

The main idea is 
1. load the image
2. Convert the image array to 2d lab-scale image array
3. Use kmeans to segment the image into number of clusters given
4. Find the cluster with the color closest to the skin color
5. Make that cluster white, and the rest black 
6. Conduct median filtering to remove noise 
7. Put the box around the white space 
8. Save the image

The main difference between kmeans1 and kmeans2 is that
- I implemented two different functions for drawing rectangles
- for the first one, I used mean and std to draw the boxes (mean and std of the pixel locations with white values)
- for the second one, I used a built-in contour function to detect contours and draw the boxes

Some limitations:
- Since we are using color to detect, it also finds objects that have similar color
- for example, if we look at the binary images that has not been filtered, we see noise that are not faces (result from similar colors that were clustered together with the faces)
- I made an improvement by using median filtering to get rid of those noise. However, in this case, we would have a difficulty detecting faces if the noise were bigger than the size of the face (like if the 4 guys had all their hands put together, it would've recognized the hands as a face and put a box around it)
- Maybe moving away from the idea of using colors and implementing a different concept could result in those kind of situations
