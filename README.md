# Microsoft-AI-for-humanitarian

This repo is based on the paper below using only Tweet text as input to estimate the winter storm Uri average damage in 7 FEMA categories. Due to the big file sizes, download the missing csv files here (https://drive.google.com/drive/folders/1MnDcO6G4Rni2wgnmsJel16uGM68hA9j4). You need TAMU email address to access. These files are prepared specificly for the winter storm application. 

@article{pi2022rapid,
  title={Rapid Damage Estimation of Texas Winter Storm Uri from Social Media Using Deep Neural Networks},
  author={Pi, Yalong and Ye, Xinyue and Duffield, Nick and others},
  journal={Urban Science},
  volume={6},
  number={3},
  pages={62},
  year={2022},
  publisher={Multidisciplinary Digital Publishing Institute}
}

A Twitter API example using Python is provided by Dr. Yalong Pi named `Grab_Twitter_Data_V3.ipynb`. Please use the academic tokens and keys responsively and do not share with anyone outside of the group. If you have questions/suggestions, please contact piyalong@tamu.edu. 

The `Winter Storm Uri DNN.ipynb` creates and traisn the model saving it as `test2.pth`. Note `HashingVectorizer` from `sklearn` is used to vectorized the text to 1024 dimensional vectors. The vectorization methods will affect the results. As a result, the accuracy graph is slightly different from the figure in the paper but the general features remain the same. 

Other Helpful Message: 
- 1% of the global tweets are archived here. https://archive.org/details/twitterstream. 
- How Tweets are geo-tagged.  https://developer.twitter.com/en/docs/tutorials/advanced-filtering-for-geo-data 
