# CrossFake
A cross-lingual COVID-19 fake news dataset from the [ICDMW 2021](https://www.cikm2020.org/) paper below:  
**Cross-lingual COVID-19 Fake News Detection**.  
Jiangshu Du, [Yingtong Dou](http://ytongdou.com/), [Congying Xia](), [Limeng Cui](), [Jing Ma](https://penghao-buaa.github.io/), [Philip S. Yu](https://www.cs.uic.edu/PSYu/).  
\[[Paper](https://arxiv.org/pdf/2008.08692.pdf)\]\[[Blog](https://github.com/safe-graph/DGFraud)\]


## Introduction

The COVID-19 pandemic poses a great threat to global public health. Meanwhile, there is massive misinformation associated with the pandemic which advocates unfounded or unscientific claims. Even major social media and news outlets have made an extra effort in debunking COVID-19 misinformation, most of the fact-checking information is in English, whereas some unmoderated COVID-19 misinformation is still circulating in other languages, threatening the health of less informed people in immigrant communities and developing countries. In this paper, we make the first attempt to detect COVID-19 misinformation in a low-resource language (Chinese) only using the fact-checked news in a high-resource language (English). This repo contains a Chinese real & fake news dataset according to existing English fact-checking information. Details on this dataset are described in [Dataset Stats](#dataset-stats).

## Dataset Stats

~~a table with data stats~~

The table below shows the dataset stats:
| Lang. | Fake | Real | Total |
|:-----:|:----:|:----:|:-----:|
|  ENG  |  55  |  82  |  137  |
|  CHN  |  101 |  118 |  219  |

introduce the repo structure

~~introduce the meaning of each column~~

The metadata of our dataset can be found at CrossFake_metadata.xlsx, which includes two sheets (news_fake and news_real). Here are explanations of some columns:

- Column A (id):

    News ids. Chinese real & fake news is annotated according to existing English fact-checking information. Thus, each piece of English news may correspond to multiple pieces of Chinese news from different sources. For example, in news_fake sheet, the ids 1_1 and 1_2 indicate one piece of English news and it corresponds two pieces of Chinese news.

- Column B (fact_check_url):

    The fact check url of English news. 

- Column C (type):

    The type of news. “Post” and “article” indicates the news is from social media posts or website articles, respectively.

- Column D (source):

    The source of news. “Personal” and “professional” indicates the news is from personal account or professional source (WHO, NIH, etc.), respectively.

- Column E (mixed?):

- Column F (platform):

    The platform where the news published.

- Column H (archive):

    Links to archived news. To permanently store the original news, we archived the news sites data. 

- Columns K to R has the same meanings to Columns C to J but they indicate the information of Chinese news.


## Potential Usage

1. The news outlet type: professional, personal, more finegrained
2. The news event type
3. The news temporal pattern
4. The portion of misinformation in a news
5. Time difference between news migration
6. For one event, report the different between professional and personal news
7. A case study for a typical event
8. Topic and sentiment
9. Title pattern
10. Separating long text and short text
11. Information loss and information distortion



## Citation
If you use our code, please cite the paper below:
```bibtex
@inproceedings{du2021cross,
  title={Cross-lingual COVID-19 Fake News Detection},
  author={Du, Jiangshu and Dou, Yingtong and Xia, Congying and Cui, Limeng and Ma, Jing and Yu, Philip S},
  booktitle={Proceedings of the 21st IEEE International Conference on Data Mining Workshops (ICDMW'21)},
  year={2021}
}
```
