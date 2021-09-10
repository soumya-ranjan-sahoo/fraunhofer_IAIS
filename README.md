# fraunhofer_IAIS
## Description - Evaluation test by Fraunhofer-IAIS

#### Task - Given a user question Q, context of the dialogue C (previous utterances or dialogue turns) and a knowledge graph (KG) as input, pick the KG triples that are relevant for Q. There might be multiple triples possible, so this is a multi-label classification task. The task is divided into 2 subtasks. 

### General instructions to run the code and reproduce the results : 
1. Create a new virtual environment (recommended) - `conda create -n myenv python=3.7`
2. Install all the dependencies using the provided `requirements.txt` file
3. Follow the subsequent subtasks in order 

### Subtasks

#### Subtask#1 - Dataset creation using the given json files
Instruction to run :
1. Run the `Subtask1.ipynb` notebook

#### Subtask#2 - Building the triple extractor model using the current utterance, context and KG. This subtask also involves creating an evaluation metric (loosely being termed as average accuracy) for evaluating the predicted labels against the ground truth labels. 
Instruction to run :
[Note - I have implemented two versions for this subtask namely - `Subtask2-v1.0.ipynb` and `Subtask2-v2.0.ipynb`]
1. __v1.0__- Run the `Subtask2-v1.0.ipynb` notebook. This implementation involves directly extracting tripels using spacy to find possible combination for [subj,pred,obj] triples and using the KG as a look up dictionary to further filter and extract the relevant triples. But unfortunately, the spacy extractor performs very poorly on our dataset given the irregularies and noise. Also, it consumes a very large memory footprint and time to extract the tripels (processes 100 instances in 3 minutes). Possible imrpovement could be seen by using coreference resolver before using the custom spacy's tripels extractor.
2.  __v2.0__- Run the `Subtask2-v2.0.ipynb` notebook. This implementation is rather a very straightforward and quick approach to extract the tripels where we use spacy's NER to look for entities that could be candidate subjects. We then look up for these entities in the KG and if there is a match, we extract the triple from the KG. This approach is computationally very efficient but logically might not be the right approach. (This processes 100 instances in 30 seconds) 



