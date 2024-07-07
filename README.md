# The Pivot Word
## Naïve Proof of Inference for Autoregressive Models.

Alice wants to run an inference using the Llama-3-8B model on a set of inputs but lacks the necessary computing power.

Bob, equipped with the required computing resources, offers to perform the inference for Alice.

Alice needs a way to verify that Bob used the correct model for the inference, without having to perform the entire computation herself.

To address this, we leverage the autoregressive nature of large language models (LLMs). In these models, each subsequent token is generated based on the sequence of previous tokens and the model's state (previously computed key/value attention pairs).

Here’s how our algorithm works:

- Bob processes the entire input and shares the results with Alice.

- The final word, known as the pivot word, is crucial for Alice’s verification.

- Bob also provides the attention values recorded just before generating the pivot word.

- Alice receives the complete output, including the pivot word, from Bob.

- She loads the model with Bob’s attention values and performs a one-word inference to check if it matches the pivot word.

Alice can either directly compare the words (tokens) or, for a more robust verification, compare the token logits, which are significantly harder to forge.

This approach allows Alice to confidently verify the model’s inference with minimal computational effort.

See the code for implementation details and slides for more explanations.