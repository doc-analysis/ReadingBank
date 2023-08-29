# ReadingBank


ReadingBank is a benchmark dataset for reading order detection built with weak supervision from WORD documents, which contains 500K document images with a wide range of document types as well as the corresponding reading order information. 

Our paper "[LayoutReader: Pre-training of Text and Layout for Reading Order Detection](https://arxiv.org/pdf/2108.11591.pdf)" has been accepted by EMNLP 2021.

Our model [LayoutReader](https://github.com/microsoft/unilm/blob/master/layoutreader) captures the text and layout information for reading order prediction using the seq2seq model. For more details of the code, model and results, please refer to [LayoutReader](https://github.com/microsoft/unilm/blob/master/layoutreader).

## Introduction
Reading order detection, aiming to capture the word sequence which can be naturally comprehended by human readers, is a fundamental task for visually-rich document understanding. Although good performance has been achieved, it is time-consuming and labor-intensive to produce an in-house dataset, while they are still not publicly available to compare with other deep learning approaches. Therefore, to facilitate the long-term research of reading order detection, it is inevitable to leverage automated approaches to create a real-world dataset in general domains, not only with high quality but also of larger magnitude than the existing datasets.

To this end, we propose ReadingBank, a benchmark dataset with 500,000 real-world document images for reading order detection. Distinct from the conventional human-labeled data, the proposed method obtains high-quality reading order annotations in a simple but effective way with automated metadata extraction. Inspired by existing document layout annotations, there are a large number of Microsoft WORD documents with a wide variety of templates that are available on the internet. Typically, the WORD documents have two formats: the binary format (Doc files) and the XML format (DocX files). In this work, we exclusively use WORD documents with the XML format as the reading order information is embedded in the XML metadata. Furthermore, we convert the WORD documents into the PDF format so that the 2D bounding box of each word can be easily extracted using any off-the-shelf PDF parser. Finally, we apply a carefully designed coloring scheme to align the text in the XML metadata with the bounding boxes in PDFs.

## Download

Download pre-processed [data](https://layoutlm.blob.core.windows.net/readingbank/dataset/ReadingBank.zip?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D
), which contains text and layout information.

Our data can only be used for research purpose. Please DO NOT re-distribute our data. 

To guarantee there is no potential ethical violation, we publicize a proportion of our dataset (about [100 pages](https://layoutlm.blob.core.windows.net/readingbank/dataset/ReadingBank_images_examples.zip?sv=2022-11-02&ss=b&srt=o&sp=r&se=2033-06-08T16:48:15Z&st=2023-06-08T08:48:15Z&spr=https&sig=a9VXrihTzbWyVfaIDlIT1Z0FoR1073VB0RLQUMuudD4%3D
)) and this subset will be manually checked and redacted while the access of the whole version requires our further permission. All the data in our dataset will be protected by Apache 2.0 license.

We further provide some [examples](examples/images) of them and the [visualization](examples/visual) of their reading orders.

## Statistics
The ReadingBank consists of 500,000 document pages including the image and the sequence of words and coordinates in reading order. We divide  the whole dataset by ratio 8:1:1 for training, validation, and testing. Table 1 shows the details of the three subsets. The average word number, the average sentence-level BLEU score and the sentencelevel BLEU score distribution are reported. The BLEU scores are calculated for the left-to-right and top-to-bottom order using the groundtruth reading order as the reference, so as to measure the difficulty of training samples. To guarantee the data balance, the distribution of word number and BLEU score are consistent as we randomly gather pages into each subset. We assume the ReadingBank will not suffer from the data unbalance during pretraining or fine-tuning.

|            |            |           | BLEU Distribution | BLEU Distribution | BLEU Distribution | BLEU Distribution |
|------------|------------|-----------|-------------------|-------------------|-------------------|-------------------|
| Split      | #Word Avg. | Avg. BLEU | (0.00, 0.25]      | (0.25, 0.50]      | (0.50, 0.75]      | (0.75, 1.00]      |
| Train      | 196.38     | 0.6974    | 9,666 (2.42%)     | 58,785 (14.70 %)  | 155,662 (38.92%)  | 175,884 (43.97%)  |
| Validation | 196.02     | 0.6974    | 1,203 (2.41%)     | 7,351 (14.70%)    | 19,387 (38.78%)   | 22,053 (44.11%)   |
| Test       | 196.55     | 0.6972    | 1,232 (2.46%)     | 7,329 (14.66%)    | 19,555 (39.10%)   | 21,893 (43.78%)   |
| All        | 196.36     | 0.6974    | 12,101 (2.42%)    | 73,465 (14.69%)   | 194,604 (38.92%)  | 219,830 (43.97%)  |

## Citation

If you find ReadingBank helpful, please cite us:
```
@misc{wang2021layoutreader,
      title={LayoutReader: Pre-training of Text and Layout for Reading Order Detection}, 
      author={Zilong Wang and Yiheng Xu and Lei Cui and Jingbo Shang and Furu Wei},
      year={2021},
      eprint={2108.11591},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

## Contact

For help or issues using ReadingBank, please submit a GitHub issue.

For other communications related to LayoutLM, please contact Lei Cui (`lecu@microsoft.com`), Furu Wei (`fuwei@microsoft.com`).
