---
---

# The Fourth Project: Cognate Detection

Cognates are pairs of words that are descended from the same word in an language directly ancestral to the two languages from which the pairs are drawn. These are to be distinguished from loanwords (or *borrowings*), which are “borrowed” into one language from a another language. Borrowing is like adoption and the relationship between cognates is like tha between blood siblings.

Im this project, you will build a model to automatically identify cognates. You will be given data from four closely-related languages:

- Ukhrul (Tankghul)
- Kachai
- Huishu
- Tusom

These are Tibeto-Burman languages spoken in the northeast corner of Manipur State, in Northeast India. They diverged around 500–1000 years ago, and their phonologies are quite different, but it is still possible to identify cognates if you know what you're looking for.

## The Datasets

Each dataset will contain a list of Ukhrul words tha have cognates in the other language (form and gloss [=translation]) and a list of all of the words in the other language that I have collected (form and gloss).

Sets will be provided as tab-delimited files. Each set will have at least two files (one for Ukrhul and one for the other language) with two columns (form and gloss). The gold labels will be provided as a single-column file with the same number of rows as the Ukrhul file in which there is the form cognate to the Ukhrul form.

You will be provided with the following sets:

- Ukhrul–Huishu (development data with gold cognacy judgements)
- Ukhrul–Tusom
- Ukrhul–Kachai

## The Task

The task will be to generate a tab-separated file with five columns correspoding to the top five most likely cognates in the other langugae to the corresponding Ukhrul word (the nth row consists of the top-five best cognate candidates for the nth Ukhrul word). The best candidate should be in the first column, the second best candidate should be in the second column, and so on.

## Baseline

The baseline system takes only the phonological similarity of the candidate cognates into account. It uses a simple method of producing phonological embeddings that is based upon the tf-idf of IPA character 1-, 2-, and 3-grams. The algorithm simply ranks words according to the cosine similarity of their embeddings.

## Evaluation

Results will be evaluated with [Mean Reciprocal Rank](https://en.wikipedia.org/wiki/Mean_reciprocal_rank). The reciprocal rank of a query response (candidate cognates) is the multiplicative inverse of the first correct answer. If the first answer is correct, is 1; if the second answer is correct, it is 1/2, if the third is correct, it is 1/2. If none of the answers is correct, it is 0. The formula is as follows:

![The formula for Mean Reciprocal Rank](/assets/images/mrr.svg)

You will upload your outputs to Gradescope with the names:

- `ukhrul-tusom_candidates.tsv`
- `ukhrul-kachai_candidates.tsv`