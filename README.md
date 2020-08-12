# BL@Scale Notebook Contributions
## Project: Energy Detection and Deep Learning on Breakthrough Listen Data in the Cloud
#### Mentors: Andrew Siemion and Steve Croft

### Project Description
Working as a team under the
mentorship of Listen’s senior leadership, in collaboration with others from the Listen group and with experts from industry, interns will implement an ML-powered processing pipeline using Google Cloud Platform. The system will ingest radio spectrograms from the Breakthrough Listen instrument at the Green Bank Telescope, allocate processing resources using Kubernetes to deploy and manage containerized instances of flexible and modifiable algorithms, and report and aggregate results to a database. Coordination of the processing pipeline, and reporting and visualization of results, will be managed by a web front-end.

The goal of this ambitious project is to develop a production-ready tool that can be used for new science by the conclusion of the internship, and more broadly will serve as the prototype for the next generation of radio technosignature search pipelines.The first step is to producea "minimum viable product" using GBT data currently stored in the BL archives, processing them on a Kubernetes cluster, and returning results to a database. The initial signal detection will be based on an energy detection algorithm that looks for regions of the spectrograms that deviate from the assumption of Gaussian noise. Next, additional detection
algorithms will be explored, including relevant algorithms from computer vision such as object localization, and benchmarked against existing techniques. 

Finally, the system will be scaled to run efficiently on several petabytes of data that have been generated by the BL system at GBT to date.In parallel with these
efforts, the team will replicate some of the existing deep learning processing algorithms in the GCP environment, refactoring them to take advantage of the
availability of TPUs on GCP. Additional promising deep learning algorithms for anomaly detection will be explored.

### My Internship Experience
Link to my personal code at branch shirley-dev for the BL-Reservoir (used for preprocessing and energy detection):https://github.com/UCBerkeleySETI/BL-Reservoir.git <br />

Link to my personal code at branch shirley-dev for the BL@Scale Project (webapp and more):https://github.com/UCBerkeleySETI/BL-Scale.git <br />

Note: This repo only contains Jupyter Notebook codes, find web development progress above! Files are from our GCP and include dockerfiles

Green Bank Telescope observation data could be found https://console.cloud.google.com/storage/browser/bl-scale (this data is public)
```info_df.pkl``` contains the rows where the s-values are greater than the statistic threshold value of 2048. ```all_info_df.pkl``` contains all the rows (no s-value filtering). However, keep in mind that using the BAT threshold will also output as ```all_info_df.pkl``` (unless it has been changed). ```filtered.npy``` is a 3-dimensional numpy array of images with shape (pixel width, pixel length, number of images). This array contains all the rows where the s-values are greater than the threshold value of 2048. ```best_hits.npy```is a 3-dimensional numpy array of images with shape (pixel width, pixel length, 12). This contains only the 12 most unusual images based on the statistic value.

Observation_Freq_Urls_Histogram.ipynb is the very first starting point for the BL@Scale website. This notebook contains 10 GBT observation analysis, where I created a histogram of the frequencies per observation and saved them as a base64 string to be passed to the frontend (you can check it out on the BL-Scale repo main.py). Although our methods of producing the images on the front-end are no longer through passing in the image url (we store images in npy arrays now and convert it to base64 string, you can check it out on BL-Scale repo and how we do it on BL-Reservoir) I extracted the image urls for each observation as a starting point as I was learning web developing.

PSNR.ipynb is the notebook where I experimented with finding the signal to noise ratio (SNR) for our energy detection images. This was done to find the best SNR in respect to various test window sizes (number of fine channels or size of the postage stamp I am using to extract energy detection). The first step was to sigma clip the images to remove any outliers, then subract the clipped image from the original image to produce the noiseless signal image. I also show the end results in a graph depicting the relationship between the average SNR and test window size.

BAT_Threshold.ipynb is the work I've done for updating our s-value threshold and upgrading it to Bayesian Adaptive Threshold. This includes both code and several visualizations. Here is the paper the work is based on
https://pubmed.ncbi.nlm.nih.gov/15651566/

ResNet50_Testing.ipynb is just some testing as a first time learner of ResNet50. Find the full model at https://www.kaggle.com/petterma/seti-resnet50
