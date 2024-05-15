# Repository for UML-English data
This repository contains the data used for "Extraction of UML Class Diagrams from Natural Language Specification" (Yang et al. 2022)

For the implementation, check out https://github.com/songyang-dev/uml-translation-3step.

## Getting the dataset
To get the entire dataset, you must download the release containing `dataset.tar.gz`. 

It is too big to be directly committed to git. Find the most recent version in the Releases section (https://github.com/songyang-dev/uml-classes-and-specs/releases).

## Structure of the dataset

* `dataset.tar.gz`: archive that contains all the following files. Available in the Releases section of this repo.

Important parts of the dataset:
* `fragments.csv`: file that lists UML fragments and their characteristics
* `labels.csv`: file that contains the labels received in the crowdsourcing effort
* `models.csv`: file that lists UML class diagrams and their characteristics
* `zoo/`: folder that contains all the UML data itself, such as pictures and UML encodings. Both labeled and unlabeled data are present. Only 5-10% of the UML are labeled.

## Making use of the dataset
Unzip the tarball first.

### Opening the image of a certain UML model
Open `models.csv` to read the list of available models. Copy its name and search in the `zoo/` folder for `.png` files starting with that name. For example, the ACME model has an image in the `zoo/` folder called `ACME.png`.

```bash
ls zoo/ACME.png
code zoo/ACME.png # any other image visualizer
```

### Opening the image of a certain fragment
Fragment files are named in the following pattern.

Class fragments:
```
(ModelName)_(class)(number).png
```

Relationship fragments:
```
(ModelName)_(rel)(number).png
```

Similarly, you can visualize them.
```bash
code zoo/CFG_class0.png
```

### Finding the image of a fragment starting from a label
1. Browse through `labels.csv` and find the line that has the label of interest.
2. Every label has a `fragment_id`, which can be indexed in `fragments.csv`. Find the ID for the label of interest.
3. Inside `fragments.csv`, search for the line where the column value of `unique_id` equals `fragment_id` from Step 2.
4. Proceed like in the previous [section](#opening-the-image-of-a-certain-fragment).
