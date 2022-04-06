/////THIS PROGRAM IS STILL BEING DEVELOPED IF YOU'RE SEEING THIS. CHECK BACK IN A WEEK/////////////////////////////////////////

Here is the proposal if interested

Problem Statement
The emergence of Web 2.0 has enabled frictionless messaging and document sharing. However, this transition to the digital world is still incomplete with the majority of important documents either being both hard-copied and digital or only hard-copied. As such, there’s a point in this file-sharing journey where users have to fetch their hard-copied documents into the digital realm. Companies and Institutions solve this problem by acquiring expensive scanners, however, such an option is not possible for the day-to-day casual user. Therefore, casual users face the challenge between sending non-professional badly cropped images or going out of their way to find a scanner available. To offer an intuitive solution to this type of user, I will develop a document-scanning program developed in C++ that utilizes the OpenCV library. 

Methodology
Inputs: The program will input the image through two possible methods: as a file or through the user’s camera. When the program is run, the user can choose their preferred method through the CLI. The image needs to be A4, upright, clear and all four edges showing, otherwise the program will handle issues such as perspective, distortion, exposure and right-angled edges. 

Preprocessing: The program will then preprocess the image to add clarity and layout the image flat. This instance in our code will perform 3 functions on the image: 
•	Convert image to Grayscale
•	Add gaussian blur, image dilation, and erosion 
•	Find edges of image through Canny Edge Detector

Processing: Once the image is preprocessed and ready to be handled we will perform the following function on the image:
•	Approximate Contours of image and determine shape, assuming the biggest rectangle in the image is our paper.
•	Draw image
•	Warp the image and lay it flat. 

Outputs: The processed image will then be displayed by the program, while also giving the user the possibility of downloading the scanned image as a pdf. The image can then be sent or submitted digitally. 

Testing/ Debugging
 A test set of 100 images will be provided as input to test the functionality of the code throughout different document images. The test set will contain these variations of images:
•	Different image perspectives, from multiple angles. 
•	Colored and black-white images.
•	Different types of backgrounds.
•	Different levels of clarity in the image.






Pseudocode
#include opencv libraries
#include <iostream>
#include <vector>

//Declare global variables 
preProcessing(img){
	grayImg = Grayscale(img)
	blurImg = GaussianBlur(grayImg)
	cannyImg = Canny(blurImg)
	dilateImg = Dilate(cannyImg)
	return dilateImg
}
Contour(img){
	Find contours of image 
	Filtrate area
	Approximate poly count and find vector points
	Find maximum area of points that is rectangular
	drawContours
	return vector of points
}
drawImg(vector points) {
	draw the image using the vector of points received
	return drawnImg
}
getWarp(img, vector points, width, height) {
	initial points = {x1y1, x2y1, x1y2, x2y2}
	wanted points = {(0,0), (width, 0), (0, height), (width, height) }
	imgWarp = warpPerspective(img, initial points, wanted points )
return imgWrap
}

main() {
	image = read image(path)
	pre processed image =  prePocessing(image)
	vector points = Contour(pre processed image)
	imgDrawn = drawImg(vector points)
imgWarp = getWarp(imgDrawn, vector points, A4width, A4height )	
	show imgWarp
	save imgWarp if user presses key	
}
