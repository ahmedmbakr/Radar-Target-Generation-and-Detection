# Radar

## Implementation steps for the 2D CFAR process

- Determine the number of Training cells for each dimension. Similarly, pick the number of guard cells. The number of training and guard cells are the same from the lesson and they produce in good results. I had to raise the threshold from 6 (as discussed in the lesson) to 10 to obtain good results as required by the final rubric point to match the output of the 2D CFAR.
- Slide the cell under test across the complete matrix. Make sure the CUT has margin for Training and Guard cells from the edges.
- For every iteration sum the signal level within all the training cells. To sum convert the value from logarithmic to linear using db2pow function.
- Average the summed values for all of the training cells used. After averaging convert it back to logarithmic using pow2db.
- Further add the offset to it to determine the threshold.
- Next, compare the signal under CUT against this threshold.
- If the CUT level > threshold assign it a value of 1, else equate it to 0.
- Loop again through all the cells and for those whose values are not zero or one then the filter does not pass through them because they are on the edges, then let them equal to zero.

To keep the map size same as it was before CFAR, equate all the non-thresholded cells to 0.
