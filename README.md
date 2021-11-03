# Author #
Adrian Bisberg

# About #
This program provides usage for an application that edits and image and creates and modifies cross stitch patterns out of those images.

The program provides functionality to use two different sets of command line arguments. Usage with: "java -jar project05.jar -scrpit path-to-file"
uses the provided file name to run a batch file through a synchronous controller that reads the commands, executes them, and outputs
their status to the command line. Usage with: "java -jar project05.jar -interactive" begins an interactive GUI that allows for asynchronous
user commands to inputed using interactive components and displays each of their results. 

Both functionalities allows for several different basic forms of editing on 
an image, including color and image filters, creating a mosaic image, a pixelated image, and a color reduced image.
Additionaly, the program allows for the creation of a cross stitch pattern. Finally it allows functionality for loading an image,
saving and reverting it to its original state. 

Functionality: 

1. **load an image** (load image_file.jpg) : before any other commands can be executed, the bath file must specify 
the name of an image file to import for editing. 

2. **blur an image** (blur 2) : with the command "blur" and an optional integer value, apply a blur filter to the image one (or repeated) time(s) 

3. **sharpen an image** (sharpen 3) : with the command "sharpen" and an optional integer value, apply a sharpen filter to the image one (or repeated) time(s) 

4. **greyscale filter an image** (greyscale) : with the command "greyscale", apply a greyscale (black and white colors only) filter to the image

5. **sepia filter an image** (sepia) : with the command "sepia" apply a sepia (brownish and orange colors only) filter to an image

6. **reduce color on an image** (reducecolor 20) : with the command "reducecolor" and a required integer value, reduce the amount of colors with 
dithering in an image to the provided number

7. **pixelate an image** (pixelate 23) : with the command "pixelate" and a required integer value for the number of squares across, create larger super pixels
across the image to give the image a pixelated appearance.

8. **mosaic an image** (mosaic 34) : with the command "mosaic" and a required integer value for the number of seeds, create a mosaic patter from the image

9. **create a crossstitch pattern** (crossstich 30) : with the command "crossstitch" and a required integer value for the number of squares across, use the original
 image to create a crossstich pattern such that each
pixel (or super pixel if the image has been pizelated) is mapped to a DMC thread color and stored with a position and symbol for each color.

10. **save a crossstitch pattern** (savepattern file.txt) : with the command "savepattern" and a required string with the file path for saving, save the 
created cross stitch pattern to a text file. Will not execute if a crossstitch has not yet been made. 

11. **save an image** (save image_finished.jpg) : with the command "save" and a required string with the file path for saving, save the image in its final state.

12. **revert an image** (revert) : with the command "revert", revert an image back to its original state before edits.

Additional functions of the interactive controller:

13. **Modify a cross stitch pattern**: select a square of the cross stitch pattern and replace it with that of another DMC thread.

14. **Create a cross stitch from a custom set of colors**: choose a subset of DMC floss colors to create the cross stitch from.

15. **Add a message to a cross stitch** of ay upper or lowercase letter in a cross stitch friendly font starting in the upper left corner.

16. **Write and execute a batch file** on the image in the UI.

17. **Save the batch file**.



# How to run #

java -jar project05.jar -scrpit path-to-file **OR** java -jar project05.jar -interactive

# How to Use #

**Batch control directions:**

When creating the batch file for usage, use any of the above commands listed in the batch functionality, one per line, with the correct parameters accompanying them.
The first line of the batch file must be "load filename.jpg" in order to load the image data to be edited. 
For each command line in the batch file, the program will output a status message to the console. See example runs for example of proper batch set up.

**Interactive Control Directions:**

- To load an image: select the "File" then "Load" menu item and direct the file chooser to the desired image the select "Okay".

- To greyscale an image or sepia filter an image: select the "Filter Color" menu item and the appropriate sub item.

- To blur an image, sharpen an image, pixelate an image, mosaic an image, or reduce color on an image:
select the appropriate menu item and input the prompted value, then select "Okay".

- To create a regular cross stitch: select the "CrossStitch" menu then "Create default colors". Input the amount for 
desired squares across then select "Okay".

- To modify a cross stitch pattern: select a grid of the pattern of the desired color to be replaced, select a replacement
floss color from the pop up chooser (or select "Blank") then select "Confirm" to complete.

- To add a message to a cross stitch: select the "CrossStitch" menu then select "Add message" and input the string
message to be added then choose the color for the message and select submit.

- To create a custom colored cross stitch: select the "CrossStitch" menu then "Create custom colors". Input the amount 
for desired squares across, then select "Okay". Then select the desired colors to create from from the color chooser
that pops up. Select "Confirm" when finished.

- To run batch commands on your image, direct to the "Batch Editing" tab and write commands in the top
text box according the the batch commands instruction. Select "Run Batch" when complete.

- To save an image: while on the Image Editing workspace tab, select save and direct to the desired filename.

- To save a cross stitch: while on the CrossStitch Editing workspace tab, select save and direct to desired filename.

- To save a batch file: while of the Batch Editing workspace tab, select save and direct to the desired filename.

# Example Runs #

**1 java -jar project05.jar -script basicEditing.txt**

text file contents:
<p>load basicImage.png<br>
blur 2<br>
save blurryImage.png<br>
greyscale<br>
mosaic 50<br>
save manyEdits.png<br>
revert<br>
reducecolor 10<br>
save reducedImage.png</p>

Description: 
1. loads the basicImage.png file
2. applies a blur filter twice
3. saves the image
4. applies a greyscale filter
5. creates a mosaic with 50 seeds
6. saves the image with all edits so far
7. reverts the image to original
8. reduces the color to 10
9. saves the reduced color image

Console output: 
<p>Loaded image from basicImage.png<br>
Applied Blur to image 2 times<br>
Image saved as blurryImage.png<br>
Applied greyscale<br>
Applied Mosaic with 50 seeds<br>
Image saved as manyEdits.png<br>
Reverted image<br>
Applied Reduce color to 10 colors<br>
Image saved as reducedImage.png</p>

**2 java -jar project05.jar -scrpit cossStitchEditing.txt**

text file contents:
<p>load basicImage.png<br>
crossstitch 20<br>
save pixelImage.jpg<br>
savepattern pattern.txt</p>

Description: 
1. loads the basicImage.png file
2. generates a crossstitch pattern with 20 squares across
4. saves the image
5. saves the crossstitch pattern 

Output to console:
<p>Loaded image from res/goat.png<br>
Created cross stitch with 20 squares across<br>
Image saved as pixelImage.jpg<br>
Pattern saved as pattern.txt</p>

**3 java -jar project05.jar -interactive**

Output: Open the interactive GUI application for the program.
No image data is present and must be loaded before any other commands taken.


# Assumptions # 

If a user does not input a repeat number for "blur" or "sharpen", it will be applied 1 time. 

No commands can be performed before an image is loaded. A batch file can still be run though.


# Limitations #

Commands are restricted to those provided in this documentation.

Available floss colors are restricted to those provided by the DMC online documentation
of floss names and RGB values as of April 2021.

There is no zoom or resize feature for the image or cross stitch displayed by the application, 
though they can both be scrolled to see the entirety of the image.

A cross stitch pattern can only be created in reference to an image that has been loaded.

# Changes made from previous versions #

- Added a setImage() to the model function to allow for images to be loaded over for new ones to be opened.

- Added a modifyPattern() method in the CrossStitchInterface to allow for the replacement of a CrossStitchSquare with a new value.

- Made a custom immutable object to represent a CrossStitchSquare that includes the DMC floss name, rgb values, and the symbol so the
values can all be stored and used in unison. 

- Added an additional CrossStitch constructor that allows for the creation of a CrossStitch from a custom list of colors rather than 
the entire DMC floss library. 

- Added an enum to act as a Singleton object that contains the list of all CrossStitchSquares that represent all possible floss values 
for secure and immutable use across the program.

- Added an additional controller for asynchrous control using specific features in conjunction with an ImageEditingView.

- Modified the main method to allow for either synchronous batch file control or asycnhronous interactive control.

#Image Attributions#

Licensing information: Unsplash grants you an irrevocable, nonexclusive, worldwide copyright license to download, copy, modify, distribute, perform, and use photos 
from Unsplash for free, including for commercial purposes, without permission from or attributing the photographer or Unsplash. This license does not include the 
right to compile photos from Unsplash to replicate a similar or competing service.

bread.jpg is: Photo by <a href="https://unsplash.com/@moniqa?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">
Monika Grabkowska</a> on <a href="https://unsplash.com/s/photos/bread?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  
flowers.jpg is Photo by <a href="https://unsplash.com/@corina?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">corina ardeleanu</a> 
on <a href="https://unsplash.com/s/photos/flowers?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  
