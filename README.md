# Confidence-Aware Visual Search

A lightweight visual search demo built with Streamlit and OpenAI CLIP.

The app allows users to upload 6–12 images, enter a natural-language query, and retrieve the top 3 most relevant image matches using embedding similarity.

---

## Features

- Natural-language image search
- CLIP image/text embeddings
- Cosine similarity ranking
- Top 3 match retrieval
- Confidence-aware warning system
- Streamlit interface

---

## How It Works

1. Images are converted into CLIP image embeddings.
2. The text query is converted into a CLIP text embedding.
3. Cosine similarity compares image and text embeddings.
4. Images are ranked by similarity score.
5. If the top score falls below the selected threshold, the app warns the user that the query may be ambiguous or unreliable.

---

## Example Queries

### High-confidence examples
- `pizza on a plate`
- `empty beach`

### Low-confidence / ambiguous example
- `dog`

Multiple uploaded images contained dogs in different contexts (dog with pizza, dog on beach, golden retriever outdoors).

The model returned several partially relevant matches with similar confidence scores, demonstrating how broad queries can produce ambiguity even when the object category is detected correctly.

This highlights the importance of confidence-aware ranking and warning systems in semantic visual search applications.

### Additional Failure Case

Query:
`pizza on a plate no dog`

Result:
The system still ranked an image containing both pizza and a dog highly.

Reason:
CLIP understands concepts semantically but does not reliably handle negation terms like “no dog”. The model focuses more strongly on the dominant object (“pizza on a plate”) than excluding secondary objects.

This demonstrates a realistic limitation of embedding-based retrieval systems and why confidence-aware UX is important.

---

## Test Images

The example images used for testing high-confidence and ambiguous retrieval cases are included directly in this repository.
---

## Tech Stack

- Python
- Streamlit
- PyTorch
- OpenAI CLIP
- PIL (Pillow)

---

## Installation

```bash
pip install -r requirements.txt
