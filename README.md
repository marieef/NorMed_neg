# NorMed_neg
This is the repository for the NorMed_neg dataset: a Norwegian dataset of biomedical articles annotated with negation.


## Original dataset
The original dataset is [The Norwegian GastroSurgery Biomedical Negation Corpus](https://github.com/DebaratiSJ/NegEx-on-Norwegian-biomedical-text/blob/main/Gold%20standard%20biomedical%20corpus/Norwegian%20GastroSurgery%20Biomedical%20Negation%20Corpus.txt). It was created as part of a master's thesis at Stockholm University: [Building and evaluating the NegEx negation detection system for Norwegian biomedical text](https://daisy.dsv.su.se/fil/visa?id=233579) (Sadhukhan, 2021).

English sentences and duplicate sentences have been removed from the original dataset, and sentence splitting errors in negated sentences have been corrected manually. We have annotated the dataset according to a different annotation scheme. This is described below.

## Annotation guidelines
The annotation is based on [these guidelines](https://github.com/ltgoslo/norec_neg/blob/main/annotation_guidelines/guidelines_neg.md), which were used in the annotation of the NoReC_neg dataset, see [Negation in Norwegian: an annotated dataset](https://aclanthology.org/2021.nodalida-main.30) (Mæhlum et al., NoDaLiDa 2021).

Some additional assumptions have been made. These are described in Chapter 5 of my master's thesis. (The link will be posted when my thesis is made publicly accessible.)

## Data format
The dataset is provided in JSON format:

    {
        "sent_id": "biomedical_sentence_1601",
        "text": "Forskjellen i bruk av keisersnitt mellom gruppene vedvarte da førstegangsfødende ble analysert separat , mens forskjellene i bruk av tang- og vakuumforløsning forsvant .",
        "negations": [
            {
                "Cue": [
                    [
                        "forsvant"
                    ],
                    [
                        "159:167"
                    ]
                ],
                "Scope": [
                    [
                        "forskjellene i bruk av tang- og vakuumforløsning"
                    ],
                    [
                        "110:158"
                    ]
                ],
                "Affixal": false
            }
        ],
        "focus_relations": []
    }

We render the description of the JSON format provided in the [NoReC_neg repo](https://github.com/ltgoslo/norec_neg/tree/main#json-format):

"Each sentence has a dictionary with the following keys and values:

- 'sent_id': unique NoReC identifier for document + paragraph + sentence which lines up with the identifiers from the document and sentence-level NoReC data
- 'text': raw text
- 'negations': list of all negations (dictionaries) in the sentence

Additionally, each negation in a sentence is a dictionary with the following keys and values:

- 'Cue': a list of text and character offsets for the negation cues
- 'Scope': a list of text and character offsets for the negation scopes
- 'Affixal': (True, False). Indicating whether the cue is affixal (prefix,suffix) or not.

Note that a single sentence may contain several annotated negations. All negations must contain at least one cue, but it is possible for a negation to be without scope. These cases are mostly short comments with references to earlier sentences. Both cues and scopes can be multiword and discontinuous.
"


**Note**: In NorMed_neg, each sentence has a list "focus_relations" as well. If non-empty, it has the same structure as the "negations" list, with "Cue" and "Focus" corresponding to "Cue" and "Scope", where "Focus" denotes a term annotated as negated in the original dataset. 