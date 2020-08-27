
import verify_api

image_source='../full_path/'    # create a folder in local folder  where images are to be saved 

image_names=('abc.jpg','bcd.jpg)

Call this function to match/verify sample images or reset threshold

    result=verify_api.match_faces(image_source_path,file_name,fp_limit=0,verify_mode='pair_match',classifier_threshold=0.36,threshold_reset=False)
    The output result seems like this in dictionary format: {'face_result': (True, 0.2804102301597595, 'as1', 'as2', 0.36)}

    if key 'face_result' is the result then everything is ok with input', however if some errors appear to input the a dictionary is returned with key: 'face_input_error'

image_source_path: It is the path of directory from where images are to be verified

file_name=name of the image files to be matched

False positive tolerance: It is used to limit how many false positive is acceptable. If given 3 it accepts 2 false positive.

verify mode: if pair_match is given then it will return matching bool,similarity distance between them,ID1,ID2, threshold to match 
but on multi_match selection it compares images one to many and many to one. It returns a pandas dataframe of comparision among images.

classifier_threshold: It is the threshold value given or default  to verify faces using similarity metrics. 

threshold_reset: if set False it either does pair_match or multi_match, while if set True it processes to determine best threshold from
samples of images. It  creates a threshold.txt file where it is overwritten with new threshold found.For every new applications and requirements we call this function mode.

The function returns like (True, 0.188248872756958, 'IMG_20190418_214739', 'IMG_20200412_224323', 0.36) for pair_match and  returns dataframe for multi_match.
In case of threshold reset=True we will get a list  of tuples of false positive, true positive,thresholds and false negative assciated with number of
false positive,threshold  and index of threshold.

like below format: ((no. of FN/TP/FN,threshold),index) for metrics and (threshold,index) for thresholds.

The best selected threshold of format (selected thres,index in list,no of False Positive acceptable) is:  (0.39, 33, 0.0)

False Negatives [((50.0, 0.06), 0), ((48.0, 0.07), 1), ((46.0, 0.08), 2), ((42.0, 0.09), 3), ((42.0, 0.1), 4), ((40.0, 0.11), 5), ((37.0, 0.12), 6), ((33.0, 0.13), 7), ((31.0, 0.14), 8), ((29.0, 0.15), 9), ((29.0, 0.16), 10), ((29.0, 0.17), 11), ((29.0, 0.18), 12), ((27.0, 0.19), 13), ((27.0, 0.2), 14), ((27.0, 0.21), 15), ((26.0, 0.22), 16), ((26.0, 0.23), 17), ((22.0, 0.24), 18), ((22.0, 0.25), 19), ((20.0, 0.26), 20), ((16.0, 0.27), 21), ((13.0, 0.28), 22), ((11.0, 0.29), 23), ((11.0, 0.3), 24), ((11.0, 0.31), 25), ((11.0, 0.32), 26), ((10.0, 0.33), 27), ((8.0, 0.34), 28), ((8.0, 0.35), 29), ((8.0, 0.36), 30), ((8.0, 0.37), 31), ((8.0, 0.38), 32), ((7.0, 0.39), 33), ((6.0, 0.4), 34)]

False Positives [((0.0, 0.06), 0), ((0.0, 0.07), 1), ((0.0, 0.08), 2), ((0.0, 0.09), 3), ((0.0, 0.1), 4), ((0.0, 0.11), 5), ((0.0, 0.12), 6), ((0.0, 0.13), 7), ((0.0, 0.14), 8), ((0.0, 0.15), 9), ((0.0, 0.16), 10), ((0.0, 0.17), 11), ((0.0, 0.18), 12), ((0.0, 0.19), 13), ((0.0, 0.2), 14), ((0.0, 0.21), 15), ((0.0, 0.22), 16), ((0.0, 0.23), 17), ((0.0, 0.24), 18), ((0.0, 0.25), 19), ((0.0, 0.26), 20), ((0.0, 0.27), 21), ((0.0, 0.28), 22), ((0.0, 0.29), 23), ((0.0, 0.3), 24), ((0.0, 0.31), 25), ((0.0, 0.32), 26), ((0.0, 0.33), 27), ((0.0, 0.34), 28), ((0.0, 0.35), 29), ((0.0, 0.36), 30), ((0.0, 0.37), 31), ((0.0, 0.38), 32), ((0.0, 0.39), 33), ((1.0, 0.4), 34)]

True Positives [((2.0, 0.06), 0), ((4.0, 0.07), 1), ((6.0, 0.08), 2), ((10.0, 0.09), 3), ((10.0, 0.1), 4), ((12.0, 0.11), 5), ((15.0, 0.12), 6), ((19.0, 0.13), 7), ((21.0, 0.14), 8), ((23.0, 0.15), 9), ((23.0, 0.16), 10), ((23.0, 0.17), 11), ((23.0, 0.18), 12), ((25.0, 0.19), 13), ((25.0, 0.2), 14), ((25.0, 0.21), 15), ((26.0, 0.22), 16), ((26.0, 0.23), 17), ((30.0, 0.24), 18), ((30.0, 0.25), 19), ((32.0, 0.26), 20), ((36.0, 0.27), 21), ((39.0, 0.28), 22), ((41.0, 0.29), 23), ((41.0, 0.3), 24), ((41.0, 0.31), 25), ((41.0, 0.32), 26), ((42.0, 0.33), 27), ((44.0, 0.34), 28), ((44.0, 0.35), 29), ((44.0, 0.36), 30), ((44.0, 0.37), 31), ((44.0, 0.38), 32), ((45.0, 0.39), 33), ((46.0, 0.4), 34)]

Thresholds [(0.06, 0), (0.07, 1), (0.08, 2), (0.09, 3), (0.1, 4), (0.11, 5), (0.12, 6), (0.13, 7), (0.14, 8), (0.15, 9), (0.16, 10), (0.17, 11), (0.18, 12), (0.19, 13), (0.2, 14), (0.21, 15), (0.22, 16), (0.23, 17), (0.24, 18), (0.25, 19), (0.26, 20), (0.27, 21), (0.28, 22), (0.29, 23), (0.3, 24), (0.31, 25), (0.32, 26), (0.33, 27), (0.34, 28), (0.35, 29), (0.36, 30), (0.37, 31), (0.38, 32), (0.39, 33), (0.4, 34)]

The optimum recall 0.8654,precision 1.0000,f1 score 0.9278, and accuracy 0.9746 is determined with accepted false positive of 0.




