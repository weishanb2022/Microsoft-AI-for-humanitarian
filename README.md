# Intro

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

# Collect Data
A Twitter API example using Python is provided by Dr. Yalong Pi named `Grab_Twitter_Data_V3.ipynb`. Please use the academic tokens and keys responsively and do not share with anyone outside of the group. If you have questions/suggestions, please contact piyalong@tamu.edu. 

# Building Model
The `Winter Storm Uri DNN.ipynb` creates and trains the model saving it and the model architecture follows the description in the paper. Note `HashingVectorizer` from `sklearn` is used to vectorized the text to 1024 dimensional vectors. The vectorization methods will affect the results. As a result, the accuracy graph is slightly different from the figure in the paper but the general features remain the same. 

# Other Helpful Message: 
- 1% of the global tweets are archived here. https://archive.org/details/twitterstream. 
- How Tweets are geo-tagged.  https://developer.twitter.com/en/docs/tutorials/advanced-filtering-for-geo-data 

# Visulization 
Figure below illustrates the ihpAmount from FEMA and the DNN model. In this map, the gray area represents that there are no data from both social media and FEMA. The 338 paired data points in the dataset Uri, i.e., zip codes with both FEMA and social media data, are marked with green color representing the FEMA evaluated amount in USD. The intensity of the color shows the value variation in each legend. There are zip codes with only social media but no FEMA evaluation, and the DNN can estimate the damage for these neglected regions. The DNN-estimated ihpAmount is color-coded with red, indicating the USD values in five bins: 0–105, 105–208, 209–319, 319–429, and 429–533. Similarly, the zip codes that only have FEMA damage data are marked with blue and are visualized with different color intensity.From this map, it is observed that many zip codes in rural West Texas do not have FEMA survey data, whereas metropolitan areas such as Houston and Dallas are fully covered (blue and green). In comparison, the DNN-estimated damage has less variation (0–522) than the FEMA damage data (0–10,070). Still, some zip codes in rural West Texas miss both social media and FEMA data.
![Map4](https://user-images.githubusercontent.com/89216739/205318162-27fc4c89-bb61-40b6-8990-349460871747.png)
- Geojson


```geojson
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "properties": {},
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [
              106.58472061157227,
              29.57106827738255
            ],
            [
              106.58025741577148,
              29.567335671068733
            ],
            [
              106.57304763793945,
              29.5653946612635
            ],
            [
              106.56137466430664,
              29.566738441255648
            ],
            [
              106.5538215637207,
              29.569873858372727
            ],
            [
              106.54541015625,
              29.569724555003123
            ],
            [
              106.53871536254883,
              29.565842589914105
            ],
            [
              106.53751373291016,
              29.562259105087506
            ],
            [
              106.53064727783203,
              29.554942428835226
            ],
            [
              106.53545379638672,
              29.54568383423715
            ],
            [
              106.55193328857422,
              29.551955878093022
            ],
            [
              106.5596580505371,
              29.55091056448027
            ],
            [
              106.57115936279295,
              29.54986524005526
            ],
            [
              106.57888412475586,
              29.55329983685018
            ],
            [
              106.58557891845703,
              29.561960475613336
            ],
            [
              106.58472061157227,
              29.57106827738255
            ]
          ]
        ]
      }
    }
  ]
}
```

Figure below displays the ihpAmount prediction error for each paired zip code, i.e., green in the figure above. The lower the error (coded with lighter color), the closer the prediction is to the FEMA survey, and the darker the color, the less accurate for the DNN estimation. The color intensity is divided into 10 equal bins by data size, with the remaining marked in light blue. It is worth noting that this map only shows the overlapping (FEMA survey and DNN estimation) ihpAmount to show the accuracy as an example; the other categories can be analyzed the same way. In this map, 7 out of 10 bins have an estimation error below 43%, which is consistent with the average ihpAmount 68.42% accuracy. The more accurate estimations appear close to the cities (Houston, Dallas, and San Antonio) compared to rural regions. The map distribution also suggests more data collection in the centers of Houston and Dallas areas, as they are voids. Altogether, the DNN only trained on text data is capable of predicting average damage with up to 70% accuracy and is able to estimate damage for the communities that are often neglected.
https://experience.arcgis.com/experience/66ce0416adaa4f8fb78a895f06ed4511/



