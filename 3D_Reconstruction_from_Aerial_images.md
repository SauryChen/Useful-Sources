# Dataset

> Here is a summary of public aerial datasets used for 3D / digital surface model reconstruction. We are grateful to those teams who developed these datasets and open the source data to promote the progress of computer vision in 3D field.

## Overview

### KITTI

Depth maps (annotated and raw Velodyne scans) are saved as **uint16** PNG images. Opened with PIL package, a 0 value indicates an invalid pixel (ie, no ground truth exists, or the estimation algorithm didn't produce an estimate for that pixel). Otherwise, the depth for a pixel can be computed in meters by converting the uint16 value to float and dividing it by 256.0.

`disp(u,v) = ((float)I(u,v))/256.0;`
`valid(u,v) = I(u,v)>0;`

### MVS dataset

### Urban3D

```python
print(np.array(rgb).dtype, np.array(dsm).dtype, np.array(gtl).dtype)
>>> uint8 float32 uint8
```

### CORE3D

### US3D

### WHU MVS/Stereo Dataset (0.1 m ground resolution)

The ground truth depth map is stored in a ``Depths/index.png`` file with **16 bit**, using the same index as image file.

The depth value stored in 16 bit png file is 'STORED_DEPTH_VALUE', while the ground truth depth is 'TRUE_DEPTH_VALUE':

`TRUE_DEPTH_VALUE = STORED_DEPTH_VALUE / 64.0`

### WHU TLC Dataset

The triple-view images were collected from the TLC camera mounted on the Ziyuan-3 (ZY-3) satellite, a professional satellite for surveying and 3D mapping. The ground resolution of the nadir and the two side-looking images is 2.1 m and 2.5 m, respectively



## Dataset introduction

1. **MVS: IAPRA multi-view stereo 3D mapping challenge (2016)**

   + **Dataset contents:** 

     ```bash
     aws s3 ls s3://spacenet-dataset/Hosted-Datasets/MVS_dataset/
                                PRE Challenge_Data_and_Software/
                                PRE JHUAPL_Example_Algorithm/
                                PRE Lidar/
                                PRE Publication/
                                PRE Spectral_Calibration_Software/
                                PRE WV3/
     2019-08-15 04:29:09     103893 Screen Shot 2017-10-20 at 11.04.06 AM.png
     2019-08-15 04:39:37       1102 license.txt
     2019-08-15 04:39:37        518 readme.txt
     2019-08-15 04:39:37        169 test.txt
     ```

     + Issued paper: [Bosch, Marc, et al. "A multiple view stereo benchmark for satellite imagery." *2016 IEEE Applied Imagery Pattern Recognition Workshop (AIPR)*. IEEE, 2016.](https://ieeexplore.ieee.org/abstract/document/8010543)
     + Fifty Digital Globe WorldView-3 panchromatic and multispectral images of a 100 square kilometer area near San Fernando, Argentina.
     + How to download:

   + **Related papers:**

     + [Facciolo, Gabriele, Carlo De Franchis, and Enric Meinhardt-Llopis. "Automatic 3D reconstruction from multi-date satellite images." *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition Workshops*. 2017.](http://gfacciol.github.io/multi-date-stereo) $\rightarrow$ A pipeline that wins the IARPA Multi-View Stereo 3D Mapping Challenge 2016, which consists three stages of pair selection, stereo matching and alignment and fusion.

2. **Urban3D: USSOCOM urban 3D challenge (2017)**

   + **Dataset contents:**

     + 2D orthrorectified RGB + 3D Digitial Surface Models + Digital Terrain Models
     + covering over 360 km, containing 157,000 annotated building footprints, 50 cm ground sample distance
     + [Project website (with demo)](https://github.com/topcoderinc/Urban3d)

     ```bash
     aws s3 ls s3://spacenet-dataset/Hosted-Datasets/Urban_3D_Challenge/
                                PRE 01-Provisional_Train/
                                PRE 02-Provisional_Test/
                                PRE 03-Sequestered_Test/
                                PRE 04-Unused_Data/
                                PRE AOI_polygons/
                                PRE Pretrained_Models/
     2019-08-15 04:30:22        694 Urban3DChallenge_license.md
     ```

3. **CORE3D: IARPA CORE3D public data (2018+2021) [🔗official website](https://spacenet.ai/core3d/)**

   + **Dataset contents:** 

     ```bash
     aws s3 ls s3://spacenet-dataset/Hosted-Datasets/CORE3D-Public-Data/
                                PRE Satellite-Images/
                                PRE Tiled-Examples-for-Urban-3D-Challenge-Comparisons/
     2018-10-16 01:05:25     137438 create_cogs.sh
     ```

     + [CORE3D Open Evaluation Baseline Solution (2021)](https://github.com/pubgeo/core3d-open)
     + multiple DigitalGlobe WorldView-3 satellite images from *Jacksonville (2 sq. km)*, *San Diego (1 sq. km)* and *Omaha (1 sq. km)*.
     + How to download:

   + **Related papers:**

     + [Leotta, Matthew J., et al. "Urban semantic 3D reconstruction from multiview satellite imagery." *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition Workshops*. 2019.](https://openaccess.thecvf.com/content_CVPRW_2019/papers/EarthVision/Leotta_Urban_Semantic_3D_Reconstruction_From_Multiview_Satellite_Imagery_CVPRW_2019_paper.pdf) $\rightarrow$ Propose an end-to-end system for segmenting buildinds and bridges from terrain and estimate simple, low polygon, textured mesh models for the structures based on multiview-stereo satellite imagery.
     + [Hagstrom, Shea, et al. "Cumulative Assessment for Urban 3D Modeling." *2021 IEEE International Geoscience and Remote Sensing Symposium IGARSS*. IEEE, 2021.](https://ieeexplore.ieee.org/abstract/document/9554754) $\rightarrow$ Propose an assessment metric counting the semantic labels, elevation and slope of the building, and evaluate on the [Danesfield pipeline](https://github.com/kitware/danesfield-app) and extended Danesfield pipeline.

4. **(Extended) US3D Dataset [🔗download data 1](https://ieee-dataport.org/open-access/data-fusion-contest-2019-dfc2019) [🔗download data 2](https://ieee-dataport.org/open-access/urban-semantic-3d-dataset)**

   + **Dataset contents**

     ```bash
     s3://ieee-dataport/open/16812/JAX_Metadata_And_Readme.tar
     s3://ieee-dataport/open/16812/OMA_Metadata_And_Readme.tar
     s3://ieee-dataport/open/16812/ATL_Metadata_and_Readme.tar
     s3://ieee-dataport/open/16812/JAX_PointClouds.zip
     s3://ieee-dataport/open/16812/OMA_PointClouds.zip
     s3://ieee-dataport/open/16812/JAX_Val.tar
     s3://ieee-dataport/open/16812/OMA_Val.tar
     s3://ieee-dataport/open/16812/JAX_Train.tar
     s3://ieee-dataport/open/16812/OMA_Train.tar
     s3://ieee-dataport/open/16812/ATL_Train.tar
     s3://ieee-dataport/open/16812/JAX_Extra.tar
     s3://ieee-dataport/open/16812/OMA_Extra.tar
     s3://ieee-dataport/open/16812/geopose_test_rgbs.tar.gz
     s3://ieee-dataport/open/16812/geopose_train.tar.gz
     s3://ieee-dataport/open/16812/geopose-winning-solutions-and-model-files.zip
     ```

     

   + **Extended dataset contents:**[🔗Benchmark website (with demo)](https://drivendata.co/blog/overhead-geopose-benchmark/)[🔗Challenge leaderboard (with demo)](https://www.drivendata.org/competitions/78/overhead-geopose-challenge/leaderboard/)

   > This dataset extends the Urban Semantic 3D (US3D) dataset developed and first released for the 2019 IEEE GRSS Data Fusion Contest (DFC19). We provide additional geographic tiles to supplement the DFC19 training data and also new data for each tile to enable training and validation of models to predict geocentric pose, defined as an object's height above ground and orientation with respect to gravity. We also add to the DFC19 data from Jacksonville, Florida and Omaha, Nebraska with new geographic tiles from Atlanta, Georgia.

   + **Related papers:**
     + [Christie, Gordon, et al. "Learning geocentric object pose in oblique monocular images." *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition*. 2020.](https://github.com/pubgeo/monocular-geocentric-pose)

5. **WHU MVS/Stereo Dataset (CVPR 2020) [🔗download data](http://gpcv.whu.edu.cn/data/WHU_dataset/WHU_MVS_dataset.zip)**

   + **Dataset  contents:**
     + Issued paper: [Liu, Jin, and Shunping Ji. "A novel recurrent encoder-decoder structure for large-scale multi-view stereo reconstruction from an open aerial dataset." *Proceedings of the IEEE/CVF conference on computer vision and pattern recognition*. 2020.](https://openaccess.thecvf.com/content_CVPR_2020/papers/Liu_A_Novel_Recurrent_Encoder-Decoder_Structure_for_Large-Scale_Multi-View_Stereo_Reconstruction_CVPR_2020_paper.pdf)
   + **Related papers:**

6. **WHU TLC Dataset (ISPRS 2023) [🔗download data](http://gpcv.whu.edu.cn/data/whu_tlc.html)**

   + **Dataset  contents:**
     + Issued paper: [Gao, Jian, Jin Liu, and Shunping Ji. "A general deep learning based framework for 3D reconstruction from multi-view stereo satellite images." *ISPRS Journal of Photogrammetry and Remote Sensing* 195 (2023): 446-461.](http://gpcv.whu.edu.cn/data) [Code (11)]
   + **Related papers:**
