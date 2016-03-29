# Examples

GPI was packaged with a few demo networks to illustrate some of the use cases and features that might not be immediately apparent.  This document gives a description of each network and points out some of the key nodes that would be adjusted during a working session.  The example networks (the files with the ‘.net’ extension) can be drag-n-dropped from the file browser to the GPI network canvas.  To locate the example networks, click the ‘Docs’ icon on the left side toolbar, then double-click the ‘Examples’ sub-folder.

## Cross Section Network

![Cross Section Network](./CrossSection.jpg "Reference Screenshot")
<br>A screen-capture of the example network CrossSection.net.<br>

The Cross-Section example network highlights the versatility of the Reduce node.  Reduce can be used to slice through multidimensional arrays and simultaneously crop dimensions.  The three Reduce nodes are making use of  crop and slice operations simultaneously with the ‘Mask’ feature to extract cross-sections of the reconstructed image data.  The slice axis slider (screenshot) is highlighted with a red circle.  This slider can be used to vary the y-axis position of the cropped cross-section shown in the image viewer which is simultaneously updated in the plotter.  The cropping slider, located above the slicing slider, can be adjusted to change the cross-sectional width and x-axis position.

The edge connections between nodes show the dimensionality of the numpy array that is being passed between them.  Hovering over a port shows this dimension information and information about the port connection requirements.  The statistics node can also be used to get the dimensionality and basic information about the data such as the min, max, mean, and standard deviation.

**Download:**<br>
[CrossSection.net >](./CrossSection.net)
[Data t2vol.npy >](./t2vol.npy)


## k-Space Filter

![kSpace Filter Network](./kSpaceFilter.jpg "Reference Screenshot")
<br>A screen-capture of the example network kSpaceFilter.net.  The red arrows indicate the cross-section each reduce is taking.<br>

This network demonstrates how the Shapes node can be used to generate a k-space filter.  As shown in the screen-shot image, the Shapes node has a list of predefined shapes that can be further modified with the hidden widgets further down in the Node Menu.  Shapes takes a chosen dimensionality, the dimension sizes (in this case the size of the image matrix), and other parameters that modify the filter window length, transitions, peak and stop values.  In this example, a 2D filter is generated, as shown in the viewer widget, and its x and y cross-sections are plotted.  The 2D filter array is multiplied by the Fourier transform of the 2D image.  The image is then transformed back into the image domain to reveal a high-pass filter.

The original image and filtered image are concatenated using the numpy.concatenate() function implemented in the Custom node and are then passed to the viewer node.  The Custom node is also used to implement the matplotlib plotter package.  This custom code can be modified to set the title, axis labels, legends, etc...

**Download:**<br>
[kSpaceFilter.net >](./kSpaceFilter.net)
[Data t2vol.npy >](./t2vol.npy)


## File Rosetta Stone

![File Rosetta Stone Network](./FileRosettaStone.jpg "Reference Screenshot")
<br>A screen-capture of the example network FileRosettaStone.net.<br>

GPI can use any python bindable datatype to transmit data between connected nodes.  Most of the time, numpy arrays are used as the common data format for this communication.  When reader and writer nodes are written to support a common format (such as numpy arrays) the GPI framework can be used as a rosetta stone for file formats.  In this way, node developers benefit by only having to write file I/O nodes for their specific needs and can then share data with others in formats available in existing node packages.

**Download:**<br>
[FileRosettaStone.net >](./FileRosettaStone.net)


