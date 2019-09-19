## centraul_figure
The data for "Identifying the Central Figure of a Scientific Paper"

## Data Download Link

https://drive.google.com/file/d/1ggsSXcUy5TayGbGNkxBjZZ8sDnBpEtUn/view?usp=sharing


## Requirements

Python
Pickle


## Data Stats

The dataset includes 7,295 papers. We split the whole set into training (train), validation (dev), and test set. The distribution across the three sets:

| Train         | Dev           | Test  |
| ------------- |:-------------:| -----:|
| 5841          | 721           | 733   |



# Data Feature

Please use following command to load the data


```python
import pickle as pkl
with open('central_figure.pkl', 'rb') as f:
	data = pkl.load(f)
```

Data structure is as following:

```
central_figure
│      
└───4099215: str, pmcid
│   │   abstract: str, the abstract of the paper
│   │   abs-elmo: (1024,) numpy array, elmo [1] embedding of the abstract
│   │   abs-tfidf: (1, 1024) numpy array, tfidf feature of the abstract
│   │   type: str, (train, dev, test)
│   │   
│   └───imgs
│       │   PMC4099215_1475-2875-13-264-1.jpg
│       │      │   imgName: str, image file name
│       │      │   caption: str, caption of the image
│       │      │   mention: str, the inline description of the image in the body of the paper
│       │      │   layout: 12-d array, it includes normalized section index, image order, and a 10-d vector boolean  indicating if the section ,where the image is at, includes following unigrams: results, discussion, method, case, material, implementation, design, content, model, experiment.
│       │      │   isKey: bool, True indicates that the image is selected as central figure by one of the authors
│       │      │   figure_order: str, figure type of image plus the appearance order in the paper
│       │      │   res: (2048,) numpy array, image embedding extracted from pre-trained ResNet-50 [2]
│       │      │   imgClass: one hot vector, [visualization, diagram, photo, table, equation]
│       │      │   cap-elmo: (1024,) numpy array, elmo embedding of the caption
│       │      │   cap-tfidf: (1, 1024) numpy array, tfidf of the caption
│       │      │   sim_tfidf: float, the tfidf cosine similarity between the image caption and the paper abstrat 
│       │      │   sim_elmo: float, the elmo cosine similarity between the image caption and the paper abstract
│       │      │   sim_dynamax-elmo float, the dynamax similarity [3] between the image caption and the paper abstract
│       │   PMC4099215_1475-2875-13-264-2.jpg
│       │   ...
└───3843525
    │   
    │   ...
```



## References
[1] Peters, M.E., Neumann, M., Iyyer, M., Gardner, M., Clark, C., Lee, K. and Zettlemoyer, L., 2018. Deep contextualized word representations. NAACL 2018.

[2] He, K., Zhang, X., Ren, S. and Sun, J., 2016. Deep residual learning for image recognition. In Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 770-778).

[3] Zhelezniak, V., Savkov, A., Shen, A., Moramarco, F., Flann, J. and Hammerla, N.Y., 2018. Don't Settle for Average, Go for the Max: Fuzzy Sets and Max-Pooled Word Vectors. ICLR 2019





