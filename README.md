## Project Structure:

This projet is organized into three parts:
- **Part 1**: Impemented in `P2.ipynb`
- **Part 2**: Implemented in `219pset2part2.ipynb`
- **Part 3**: Implemented in `P2_part3.ipynb`


## Notes:

- All notebooks are designed to run in **Google Colab**.
- Please enable GPU in Colab:
  Runtime → Change runtime type → Hardware accelerator → GPU.
- Required datasets will be automatically downloaded within each notebook. Please refer to the setup instructions in Part 3 for additional configuration details.


## Part 3 Setup instructions (P2_Part3.ipynb):
### 1. Dataset Download:
- This notebook uses the Pokémon image dataset from Kaggle and metadata from GitHub. The Pokemon image dataset will be automatically downloaded via KaggleHub when running Part 3.
No manual download is required.
- Before running Part 3, make sure the dataset path is set correctly.
  - After running the following snippet in the notebook:
    ```python
    path = kagglehub.dataset_download("hlrhegemony/pokemon-image-dataset")
    print("Path to dataset files:", path)
    ```
  - You should something like (actual path might be different):
    ```python
    Path to dataset files: /kaggle/input/pokemon-image-dataset
    ```
  - Then update the image root directory accordingly:
    ```python
    IMAGE_ROOT = "/kaggle/input/pokemon-image-dataset/images"
    ```

### 2. Hugging Face Login (For VLM Reranking)
- For Question 23 (VLM reranking), a Hugging Face access token is required to download the Qwen-VL model.
- **(1)** Generate token
  - Go to `https://huggingface.co/settings/tokens`
  - Create a Read access token
  - Copy the token
- **(2)** Insert token
  - Replace the place holder
  ```python
    HF_TOKEN = "ENTER_YOUR_TOKEN_HERE"
  ```
  - with your actual token and run login: 
  ```python
    HF_TOKEN = "hf_xxxxxxxxxxxxxxxxx"
    login(HF_TOKEN)
  ```
  
