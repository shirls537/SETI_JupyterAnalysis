# BL@Scale Notebook Contributions
Link to my personal code at branch shirley-dev for the BL-Reservoir (used for preprocessing and energy detection):https://github.com/UCBerkeleySETI/BL-Reservoir.git <br />

Link to my personal code at branch shirley-dev for the BL@Scale Project:https://github.com/UCBerkeleySETI/BL-Scale.git <br />

Observation_Freq_Urls_Histogram.ipynb is the very first starting point for the BL@Scale website. This notebook contains 10 GBT observation analysis, where I created a histogram of the frequencies per observation and saved them as a base64 string to be passed to the frontend (you can check it out on the BL-Scale repo main.py). Although our methods of producing the images on the front-end are no longer through passing in the image url (we store images in npy arrays now and convert it to base64 string, you can check it out on BL-Scale repo and how we do it on BL-Reservoir) I extracted the image urls for each observation as a starting point as I was learning web developing.

PSNR.ipynb is the notebook where I experimented with finding the signal to noise ratio (SNR) for our energy detection images. This was done to find the best SNR in respect to various test window sizes (number of fine channels or size of the postage stamp I am using to extract energy detection). The first step was to sigma clip the images to remove any outliers, then subract the clipped image from the original image to produce the noiseless signal image. I also show the end results in a graph depicting the relationship between the average SNR and test window size.

BAT_Threshold.ipynb is the work I've done for updating our s-value threshold and upgrading it to Bayesian Adaptive Threshold. Here is the paper the work is based on
https://pubmed.ncbi.nlm.nih.gov/15651566/

ResNet50_Testing.ipynb is just some testing as a first time learner of ResNet50. Find the full model at https://www.kaggle.com/petterma/seti-resnet50
