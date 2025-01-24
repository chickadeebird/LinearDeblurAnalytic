# Linear Deblur Analytic

This is a Pixinsight script for implementing different analytic linear deblurring algorithms.

This script attempts to deal with the problem of elongated stars, such as one might get with cable drag. It applies a PSF to stars detected with Pixinsight's Star Detector in the center of the image. The median rotation angle is calculated and the stars are removed from the image using StarNet2 and then rotated so that the elongated stars are parallel with the horizontal plane. An analytic algorithm (either erosion or deconvolution) is applied to the horizontal blurring with a number of prespecified iterations and a mask length. The stars are then rotated back and then replaced on the starless image.

For this set of algorithms, the background is not deblurred as the stars are isolated and deblurred separately from the background.

The scripts should work on both mono and RGB nonlinear images.

The algorithms should all work both with and without a GPU, although GPU acceleration greatly enhances the speed of the StarNet2 process.

# Erosion Algorithm

This algorithm works relative quickly compared with the deconvolution algorithm and is better suited to sparser starfields.

# Deconvolution Algorithm

This algorithm uses the innate Deconvolution Richardson-Lucy algorithm.

# Usage

These algorithms should work on mono and multi-channel/RGB images.

Select Linear data if you wish the algorithm to treat the data as linear, otherwise significant star removal artifacts may be seen.

## Images

This is a linear RGB image stack with a blurring artifact at about 61 degrees, as detected by the script star detector algorithm. The image on the left is the original image and the image on the right is the deblurred image using the deconvolution algorithm with a length of 6 and 16 iterations.

<img src="./figs/LinearDeblurAnalytic deblurred stars.png" text='LinearDeblurAnalytic script' align=left />

## Script

This is the script interface for the LinearDeblurAnalytic script.

<img src="./figs/LinearDeblurAnalytic script.png" text='LinearDeblurAnalytic script' align=left />

This can be found here: ChickadeeScripts > LinearDeblurAnalytic after installation.

## Manage repository location

In order to automatically install and subsequently refresh script updates in Pixinsight, add the following URL to Resources > Updates > Manage repositories

https://raw.githubusercontent.com/chickadeebird/LinearDeblurAnalytic/main/

After this has been added to the repositories, Resources > Updates > Check for updates should place the new LinearDeblurAnalytic script in Scripts > ChickadeeScripts

