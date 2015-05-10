# Training NFT to a New Surface 

## About surfaces we can use with ARToolKit NFT

ARToolKit NFT tracks from natural features of planar textured surfaces. The current implementation of the tracking algorithm requires that the visual appearance of the surface is known in advance. Thus, in advance we have to **"train"** the system to the appearance of a particular surface which we want to use for tracking. The output of this training is a set of data which can be used for realtime tracking in our application.

The following constraints apply to surfaces which can be used with ARToolKit NFT.

-   The surfaces to be tracked must be supplied as a rectangular image. Currently only jpeg images are supported.
-   The surface must be textured and have a reasonable amount of fine detail (i.e. it must have a low degree of self-similarity and high spatial-frequency). Images with large areas of single flat color will not track well (if at all) since no unique features will be able to be identified in the interior of the areas of flat colour, and images that are blurred or have soft detail will similarly not track well.
-   Larger or higher resolution images (more pixels) will allow the extraction of feature points at higher levels of detail, and thus will track better when the camera is closer to the image, or when a higher resolution camera is used.

The ARToolKit NFT 2.0 tracker does not impose any additional constraints.

## Producing a digital image to be supplied to the training tools

The inputs to the NFT tracking process are

1.  a live image stream from a camera
2.  data (produced by the training tools) about the features of the tracked surface
3.  a digital image of the tracked surface itself

This section will help you in producing the third of these, the digital image.

Summary: A typical workflow for producing NFT markers proceeds thus:

1.  A high-resolution image which is to form the basis of the marker is obtained. If the source texture is on paper, it must be scanned. The image is saved in jpeg format.
2.  The resulting image is fed into the NFT training applications.
3.  If the image is to be printed, print on a good-quality colour printer, on low-gloss paper, to produce the final image which will be tracked.

### Beginning with a pre-existing physical print

In many cases, it may is simplest to start with a physical print of the tracked surface. This might be also be best if

-   you are augmenting the pages of a book, magazine, or other printed material for which you do not have the design artwork
-   you have digital artwork, but the physical print differs considerably in brightness, colour or tone.

**How big, and what resolution?** During photography or scanning of pre-existing artwork, a natural question arises: what settings (scanner resolution or camera image size) to use? To answer this question, we must first ask two other questions:

1.  What is the physical size of the printed material? I.e., what is the width and height in inches or millimetres? Measure this accurately with a ruler. Common paper sizes include A4 (210 mm x 297 mm) and US Letter (8.5 inches x 11 inches, or 215.9 mm x 279.4mm). ![Measuring the size with a millimetre rule. Measure the part which corresponds exactly to your source image. Don't include the border.][NFT_example_KPM_measuring_image_with_rule]
2.  How close to the camera will the printed image be when in use? This relates to the required *resolution*, commonly expressed as pixels or dots per inch (DPI). To help answer this, use the "checkResolution" tool supplied with ARToolKit NFT. [Click here for the checkResolution tutorial][1], then once you have determined the maximum resolution required, return to this page.
3.  -   If using a scanner or camera which needs a "resolution" setting, you can just directly use the maximum resolution calculated by the checkResolution tool.
    -   If using a scanner or camera which calculates in terms of image width and height, multiply the resolution calculated by the physical width and height:

<pre>
width in pixels = width in inches x dots per inch
height in pixels = height in inches x dots per inch
</pre>

If you have the measurements in millimetres, you can convert to inches by dividing by 25.4 (i.e. there are 25.4 millimetres in one inch).

<pre>
inches = millimetres / 25.4
</pre>

1.  If using a scanner or camera which requires a "megapixels" setting, calculate the required width and height in pixels (above) and then multiply these together and divide by 1 000 000. E.g. 640x480 = 0.3 megapixels.

**Checking the result** After scanning or photography is completed, check that the resulting digital image is not blurred and has sufficient contrast. Washed-out blurry images work very poorly in the NFT training process.

### Beginning with digital artwork

Producing the digital image for tracking from pre-existing digital artwork is simple. Care must be taken however to ensure that the image supplied to the training tools is not too big (wasteful of memory, disk and CPU during tracking) and not too small (of insufficient detail to allow tracking when the camera is close to the image.)

**How big, and what resolution?** Similarly to beginning from printed artwork, answering the question of what size image to use must take into account the output factors:

1.  What is the physical size of the printed material? I.e., what is the width and height in inches or millimetres? If the image is to be a page in a book, then the size of the pages might determine this factor. Common sizes include A4 (210 mm x 297 mm) and US Letter (8.5 inches x 11 inches, or 215.9 mm x 279.4mm), although you might choose to track only a portion of the page.
2.  How close to the camera will the printed image be when in use? This relates to the required *resolution*, commonly expressed as pixels or dots per inch (DPI). Consider also the physical limit of your printer, as this imposes an upper limit on the required resolution. Most laser printers produce 300dpi black and white images, while colour printers usually use a dot-screen at 150 dpi (although they may advertise higher resolutions, almost all use a 150dpi resolution). To help answer the resolution question, use the "checkResolution" tool supplied with ARToolKit NFT. [Click here for the checkResolution tutorial][2], then once you have determined the maximum resolution required, return to this page.
3.  Multiply the required maximum printed resolution by the physical width and height of the printed image to calculate the width and height in pixels (the "pixel size" of an image as reported in your image editing application).

<pre>
width in pixels = width in inches x dots per inch
height in pixels = height in inches x dots per inch
</pre>

If you have the measurements in millimetres, you can convert to inches by dividing by 25.4 (i.e. there are 25.4 millimetres in one inch).

<pre>
inches = millimetres / 25.4
</pre>

For example, borderless A4 at 150dpi is 1240 pixels wide and 1754 pixels tall. Borderless US Letter at 150dpi is 1275 pixels wide and 1650 pixels tall. ![If producing from digital artwork at 1:1 scale, you can use image size from that artwork. Example here is from Adobe Photoshop.][NFT_example_KPM_image_size_photoshop]

**Checking the print** After printing your digital artwork, check that the print is the correct size. A scaled print will still track, but will give scaled (and potentially misleading) tracking results (distance from camera etc.). Also, check that the print matches the artwork in terms of contrast, absence of print defects etc. Differences between the digital artwork and the physical print will reduce the robustness of the tracking, as some of the trained features may not be present on the print.

*You can download the sample image "pinball.jpg" used in this tutorial [here][3].*

## Physical print properties

Whether working from supplied printed material or a print from digital artwork, eventually the user needs an actual surface to hold in front of the camera.

It is important that the physical print is kept as flat as possible. Small amounts of curvature can be coped with by the tracker to some degree, but flat is best. Where possible, the print should be on or affixed to a physical prop that keeps it flat.

- If you were (for example) printing a label to be attached to a product, the label should be applied to a flat area of the product. The curved surface of a bottle or can would not be suitable, and alternatives could include the packaging holding the bottle or can, or on a flat label or tag attached to the product. If mounting in a book, surfaces should be printed on heavy card and bound with board-book, ring or spiral binding. If used as an unbound card, affix to the card with a dry glue (e.g. a glue stick or an industrial dry adhesive).

![Glue printed pages to a flat surface using a dry glue. Take care not to distort the printed paper when affixing.][Glueing_marker_to_backing_board]

## Decide on the image set resolutions

Most of the operation of the training utility programs procedure proceeds without much input from the user, but there is one important decision required prior to starting the training utility, which is selecting the resolutions at which features of the image will be extracted. (Generally, features are extracted at three or more resolutions to cope with the fact that dots in the image will appear at different resolution to the software depending on how close or far away the camera is from the image.)

For a typical webcam operating at VGA (640x480) resolution and tracking at handheld-distance from the surface, a range of resolutions between 20 dpi and 120 dpi is a good starting point. If using a higher-resolution webcam or tracking much closer to the surface, higher resolutions will be required. **Note that there is no point in using resolutions higher than the actual resolution of the final printed surface.**

The utility program "checkResolution" can help with the decision of what values to use as minimum and maximum resolutions. [Click here to see the usage instructions for checkResolution][4].

After completing a training pass, it will pay to come back to the choice of image set resolutions and experiment with different minimum and maximum resolutions. The choice depends greatly on the way in which you intend to use ARToolKit NFT for tracking, and your source images.

If you have further questions, it would pay to ask questions of the ARToolworks support staff, and/or other users of ARToolKit NFT, on the [support forum][5].

## Generating an ARToolKit NFT dataset from the digital image

As mentioned above, the inputs to the NFT tracking process are

1.  a live image stream from a camera
2.  data (produced by the training tools) about the features of the tracked surface
3.  a digital image of the tracked surface itself

This section will help you in producing the second of these, the trained data sets.

Surface training uses utilities included in the ARToolKit NFT package. These utilities must be run from the command line. On windows, this means you must open a “cmd” console and cd to the ARToolKitNFT\\bin directory. On Unix systems (Linux and Mac OS X) open a terminal window and cd to the ARToolKitNFT/bin directory.

As of ARToolKit Professional version 4.6, the same NFT dataset generation tools are shared between all supported ARToolKit desktop and mobile platforms, greatly simplifying the previous procedure for generating data sets. Dataset generation is performed using a single integrated tool **genTexData**.

After setting any required video configuration, launch the genTexData tool:

![Launch the program from a terminal window, supplying the name of the input JPEG file as the parameter.][NFT_example_genTexData_010]

![You can specify how selective the training algorithms should be in rejecting candidate tracking features.][NFT_example_genTexData_020]

In the first step, the source image is resampled at multiple resolutions, generating an image set (.iset) file. This contains raw image data which will be loaded into the app at runtime for tracking.

You may be prompted for the source image resolution, as well as the range of resolutions you wish to use for tracking. (See the preceding section for advice on how to choose a good set of resolutions to use.) Enter the minimum and maximum resolutions at the terminal prompt. You can enter decimal values (numbers with a '.'). These values can also be manually specified on the command line. (See the list of command line options below.)

![The utility will load the JPEG and read its size and expected printed resolution. If no resolution value is embedded, you will be prompted to supply the resolution.][NFT_example_genTexData_030]

![Specify the minimum and maximum resolution values for tracking. A suitable image set will then be automatically generated from this range, and saved to disk with the suffix".iset".][NFT_example_genTexData_040]

![The utility begins to generate tracking data. This procedure may take some time, even on a fast CPU.][NFT_example_genTexData_050]

![When generation of tracking data is complete, the utility will save the ".fset" and ".fset2" files to disk alongside the .jpeg. Training is then complete.][NFT_example_genTexData_060]

## Testing the completed dataset

Once the image set and feature sets have been generated, you can use the [[/ARToolKit_NFT_Utilities:_dispImageSet|dispImageSet''' and [dispFeatureSet](ARToolKit NFT Utilities: dispFeatureSet "wikilink") utilities to examine the output of the training process.

By examining the output of dispFeatureSet, you can immediately see a number of things about the image used:

-   Flat areas with no texture provide no features to track. You should use source material with plenty of edges and fine surface detail.
-   Blurry areas (such as the blurry face at the bottom of the printed image) are also poor areas for tracking.
-   Some areas with fine detail but low contrast will be quite "noisy", with a slight adjustment of the image size or other training parameters resulting in these features not being chosen.

The easiest means of testing NFT datasets you have trained in live tracking is to run them using the **nftSimple** example program. See [Running the nftSimple example][6]

## Moving on

Once you have generated a few marker sets, and seen the tracking response, you're ready to gain a deeper understanding of NFT tracking. You can read the reference documentation for more information.

[1]: /ARToolKit_NFT-_Using_checkResolution
[2]: /ARToolKit_NFT-_Using_checkResolution
[3]: http://www.artoolworks.com/support/library/images/f/f8/pinball.jpg
[4]: /ARToolKit_NFT_Utilities:_checkResolution
[5]: http://www.artoolworks.com/support/forum/
[6]: /Running_the_nftSimple_example

[NFT_example_KPM_measuring_image_with_rule]: /NFT_example_KPM_measuring_image_with_rule.jpg
[NFT_example_KPM_image_size_photoshop]: /NFT_example_KPM_image_size_photoshop.jpg
[Glueing_marker_to_backing_board]: /Glueing_marker_to_backing_board.jpg
[NFT_example_genTexData_010]: /NFT_example_genTexData_010.png
[NFT_example_genTexData_020]: /NFT_example_genTexData_020.png
[NFT_example_genTexData_030]: /NFT_example_genTexData_030.png
[NFT_example_genTexData_040]: /NFT_example_genTexData_040.png
[NFT_example_genTexData_050]: /NFT_example_genTexData_050.png
[NFT_example_genTexData_060]: /NFT_example_genTexData_060.png