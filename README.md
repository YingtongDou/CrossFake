# CrossFake
An English-Chinese COVID-19 fake&real news dataset from the [ICDMW 2021](https://www.cikm2020.org/) paper below:  
**[Cross-lingual COVID-19 Fake News Detection](https://arxiv.org/pdf/2110.06495.pdf)**.  
Jiangshu Du, [Yingtong Dou](http://ytongdou.com/), [Congying Xia](), [Limeng Cui](), [Jing Ma](https://penghao-buaa.github.io/), [Philip S. Yu](https://www.cs.uic.edu/PSYu/).  


## Introduction
The COVID-19 pandemic poses a significant threat to global public health. Meanwhile, there is massive misinformation associated with the pandemic, which advocates unfounded or unscientific claims. Even major social media and news outlets have made an extra effort in debunking COVID-19 misinformation, most of the fact-checking information is in English, whereas some unmoderated COVID-19 misinformation is still circulating in other languages, threatening the health of less informed people in immigrant communities and developing countries ([The Vox](https://www.vox.com/identities/21579752/asian-american-misinformation-after-2020), [New York Times](https://www.nytimes.com/2020/12/20/opinion/fake-news-disinformation-immigrants.html?smid=url-share)).

In the above paper, we make the first attempt to detect COVID-19 misinformation in a low-resource language (Chinese) only using the fact-checked news in a high-resource language (English).

This repo contains a Chinese-English real & fake news dataset according to existing English fact-checking information. Details on this dataset are described in [Dataset Stats](#dataset-stats).

The highlights of our dataset are as follows:

- Bilingual news pieces for the same event (fact).
- Multiple Chinese news pieces for the same event (fact).
- Comprehensive metadata for each news (see below).

## Dataset Detail

The table below shows the number of annotated news in each language:
| Lang. | Fake | Real | Total |
|:-----:|:----:|:----:|:-----:|
|  ENG  |  55  |  82  |  137  |
|  CHN  |  101 |  118 |  219  |

The metadata of our dataset can be found at [`CrossFake_metadata.xlsx`](https://github.com/YingtongDou/CrossFake/blob/main/CrossFake_metadata.xlsx), which includes two sheets (`news_fake` and `news_real`). Given the news id, you can find the corresponding news body text in the [`body_text`](https://github.com/YingtongDou/CrossFake/tree/main/body_text) directory. The meanings of each column of the metadata are shown below:

- **Column A (id):**

    News id. Chinese real & fake news is annotated according to existing English fact-checking information. Thus, each piece of English news may correspond to multiple pieces of Chinese news from different sources. For example, in the `news_fake` sheet, the ids 1_1 and 1_2 indicate one piece of English news, corresponding to two pieces of Chinese news.

- **Column B (fact_check_url):**

    The fact-checking source of the corresponding English news. 

- **Column C (type):**

    The news type. `Post` and `Article` represent the news is from a social media post or an online article, respectively. Note that we also annotated some `clickbait` news whose title and body text present contradictory information.

- **Column D (source):**

    The news source. `Personal` and `Professional` represent the news is from a personal account or professional source (WHO, NIH, etc.), respectively.

- **Column E (mixed?):**

    Whether the news include mixed content? If a news body text only has the content related to the checked fact, the piece of news is annotated as not mixed.  Accordingly, the news whose content includes events/facts besides the checked fact is regarded as mixed news.
    
- **Column F (platform):**

    The platform where the news is published.

- **Column G (news_url):**

    The news source URL. Note that some of the links are invalid due to the deletion/removal of the news. We have archived the accessible news (see Column H) during we curate the dataset.

- **Column H (archive):**

    The archived news link. To permanently store the original news, we archived the news source URL.
    
- **Column I (newstitle):**

    The news title. 

- **Column J (publish_date):**

    The news publishing date. 

- **Columns K to R have the same meanings as Columns C to J, but they indicate the information of Chinese news.**


## Case Study

Besides the findings and conclusions presented in our [paper](https://arxiv.org/pdf/2110.06495.pdf). We have extra interesting findings during collecting the data:

1. Mixed Fact.
For some fake news, their corresponding Chinese news articles presented them in the form of a news digest with other news events. It brings an extra hurdle to fact-check those news pieces since only partial content of the news contains misinformation. A typical example is news_id `8_3` in the `news_fake` sheet. You can check out other news whose `mixed?` annotated as `Yes`.

2. Misused Fact.
For `news_real` id `9_2`, we find a Chinese social post leveraging the fact that "coronavirus can live for up to 4 hours on copper" to promote their copper-made pot. In this case, even the title and most of the news content seem legit, but the connection between "the copper kills coronavirus" and "copper pot is good" is still questionable.

3. Fake News Type.
During we annotate the Chinese news based on the fact-checked English news. We find that most of the fact-checked fake news from [Politifact](https://www.politifact.com/coronavirus/) have no corresponding Chinese news. Those news pieces usually are local news in the United States. 

4. Cross-lingual Fact-checking.
For the `news_real` id `9_1`, we find a Chinese news piece from a professional news outlet published five days earlier than the fact-checked English Facebook post. It suggests that we could leverage fact information from another language to help fact-check the news. Note that most of the Chinese news in our datasets are published later than the source English news since most of the checked news events are originated in English media. 

## Future Directions

Given the current dataset, some future research directions include:
- The writing style/sentiment/stance differences between fake news and real news.
- The writing style/sentiment/stance differences between professional news outlets and personal accounts.
- The information distortion/loss from English news to Chinese news.
- The temporal patterns of cross-lingual news migration.
- The title patterns of different news.



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
