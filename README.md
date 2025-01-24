# LinearDeblurAnalytic

This is a Pixinsight script for implementing different machine learning and analytic linear deblurring algorithms.

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

This is a nonlinear image of a stack of images on the Iris nebula with an autoSTF applied (top left), the results from algorithm A (top right), algorithm B (bottom left), and algorithm C (bottom right).

<img src="./figs/DenoiserSuite no mask on Iris.png" text='DenoiserSuite script' align=left />

This is a linear image from the Leo triplet using algorithm B. It shows the improvement in detail preservation with a stretched lightness mask applied. Top left - original linear stacked image; top right - stretched lightness mask; bottom left - algorithm B with no mask; bottom right - algorithm B with lightness mask applied to preserve high signal details.

<img src="./figs/DenoiserSuite algorithm B mask.png" text='DenoiserSuite algorithm B with and without mask' align=left />

## Script

This is the script interface for the DenoiserSuite script.

<img src="./figs/DenoiserSuite script.png" text='SyntheticStars script' align=left />

This can be found here: ChickadeeScripts > SyntheticStars after installation.

## Manage repository location

In order to automatically install and subsequently refresh script updates in Pixinsight, add the following URL to Resources > Updates > Manage repositories

https://raw.githubusercontent.com/chickadeebird/DenoiserSuite/main/

After this has been added to the repositories, Resources > Updates > Check for updates should place the new DenoiserSuite script in Scripts > ChickadeeScripts

## Machine learning files location

The Denoising Suite script calls an executable file that is a machine learning program trained for the denoising functions for the script. The executable can be downloaded via the following link:

https://drive.google.com/file/d/1rXwK82pragUTp7axTCL6sYaObKHMgKcf/view?usp=sharing

Place the zip file in a location on your computer and unzip the contents. Start the DenoiserSuite script in Pixinsight under the Scripts > ChickadeeScripts location. Click on the wrench at the bottom left of the DenoiserSuite dialog box and then move to the location where the executable files have been unzippped. The enables the DenoiserSuite script to find the executable in the correct location.
