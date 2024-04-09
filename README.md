# Corner-Detection-and-Image-Stitching-to-create-Panorama-View
The First Part of the code consists of a pipeline to detect the page corners in a video frame. The Second Part of the code is  stitching an image taken from different perspectives using Homography Calculation and Warp Perspective

For Corner Detection the Video can be found at [here](https://drive.google.com/file/d/1wV4QV3OzrNAsK4ObwwsJTZAD2TzmSsRr/view)

1) Read the video and extract individual frames using OpenCV.
2) Skip blurry frames (use Variance of the Laplacian and decide a suitable threshold)
  Note: Any value below 150 for the Variance of the Laplacian, suggests that it’s a blurry image.
3) Segment out the unwanted background area (example: convert to gray scale and keep white regions)
4) Detect edges pixels in each frame using Canny Edge Detector
   
<div style="text-align:center;">
 <img width="265" alt="image" src="https://github.com/robosac333/Corner-Detection-and-Image-Stitching-to-create-Panorama-View/assets/143353582/88f9c69c-02b9-4a0a-afda-5031aa5a53cc">
</div>
   
5) Use the detected edge pixels to extract straight lines in each frame (hint: use Hough Transform)
6) Filter out “short” lines and only keep a few dominant lines.
7) Compute the intersections of the Hough Lines – these are the putative corners of the paper.
8) Verify the existence of those corners with Harris corner detector. (use OpenCV built-in function)
   
<div style="text-align:center;">
 <img width="245" alt="image" src="https://github.com/robosac333/Corner-Detection-and-Image-Stitching-to-create-Panorama-View/assets/143353582/f3a89c65-4286-4e77-b784-9688535cba43">
</div>
   
9) Filter out remaining extraneous corners that are not the 4 corners of the paper.

<div style="text-align:center;">
  <img width="277" alt="image" src="https://github.com/robosac333/Corner-Detection-and-Image-Stitching-to-create-Panorama-View/assets/143353582/a16b2a18-5c52-48c3-bf89-b017c231fbe3">
</div>

10) Generate the output video in which you have to overlay the 4 blue boundary lines and 4 red corners of the paperin each frame (excluding the blurry frames)

For Image Stitching the Images can be found [here](https://drive.google.com/drive/folders/11iuYdIaysz6fyV0gIO-v6VST5daBm9Sn)

1) Load the images
   
   <img width="826" alt="image" src="https://github.com/robosac333/Corner-Detection-and-Image-Stitching-to-create-Panorama-View/assets/143353582/ebb73e51-5d29-4ad0-b13e-e27df0ec9dac">
   
2) Obtain the best best Matches between conscutive images using FLANN based KNN matches

   <img width="824" alt="image" src="https://github.com/robosac333/Corner-Detection-and-Image-Stitching-to-create-Panorama-View/assets/143353582/bb0816c8-fc52-4658-8d60-88dd92acef96">

3) Obtaining Homographies between adjacent images and Warping perspective.
4) Attching the warped perspective along the destination image.

   <img width="824" alt="image" src="https://github.com/robosac333/Corner-Detection-and-Image-Stitching-to-create-Panorama-View/assets/143353582/5a012aef-e005-46da-81a5-568b83ce8a94">

