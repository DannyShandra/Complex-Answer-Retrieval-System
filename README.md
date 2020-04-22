# Complex-Answer-Retrieval-System
While current retrieval systems provide good results for phrase-level retrieval of simple facts, they are less effective in assembling facts into an information package. This project will focus on answering more complex information needs with longer answers through assembling of different information sources. Much like Wikipedia pages that synthesize knowledge that is globally distributed, I am interested in building a retrieval system that collects relevant information from an entire corpus, creating synthetically structured documents by collating retrieved results. I attempt to assemble an information package or the so called complex answer in response to an information need in question answering systems.

There are 4 important python files to note:

- danu_weight_score
- test_gen_rankings
- danu_tfidf_scoring
- eval_framework

The weight_score and tfidf_scoring files compute the weight and score of each passage. The gen_rankings
file uses these scores to rank passages based on their relevance to the query. The gen rankings file also creates 
a run/output file to compare with relevance judgement files using eval_framework.

Heres how the code should be run in the terminal:

1. Navigate to the folder containing the above files

2. Once all files are in the same folder, execute the following command to retrieve 100 passages from the corpus set:
***NOTE: this process may take some time depending on the number of passages retrieved***

`python test_gen_rankings.py train.benchmarkY1train.cbor.outlines train.benchmarkY1train.cbor.paragraphs [output.______.run] RANK1 100 5`
  
The command will attempt to retrieve 100 passages, and out of those 100 passsages, 5 will be used to compute the weight scores of the query  

3. After the run file is created, it must be inputted into the eval_framework file to get the precision metrics:

`python eval_framework.py train.benchmarkY1train.cbor.hierarchical.qrels [output.______.run]`
