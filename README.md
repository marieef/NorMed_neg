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
        "sent_id": "biomedical_sentence_2326",
        "text": "Resultater som avklarer nytte av dette behandlingsprinsippet foreligger imidlertid ikke .",
        "negations": [
            {
                "Cue": [
                    [
                        "ikke"
                    ],
                    [
                        "83:87"
                    ]
                ],
                "Scope": [
                    [
                        "Resultater som avklarer nytte av dette behandlingsprinsippet foreligger"
                    ],
                    [
                        "0:71"
                    ]
                ],
                "Affixal": false
            }
        ],
        "focus_relations": []
    }

The [NoReC_neg repo](https://github.com/ltgoslo/norec_neg/tree/main#json-format) provides an explanation of the JSON format. In our dataset, each sentence has a list "focus_relations" as well. If non-empty, it has the same structure as the "negations" list, with "Cue" and "Focus" corresponding to "Cue" and "Scope", where "Focus" denotes a term annotated as negated in the original dataset. 