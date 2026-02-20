## Project Structure:

This projet is organized into three parts:
- **Part 1**: Impemented in `P2.ipynb`
- **Part 2**: Implemented in `219pset2part2.ipynb`
- **Part 3**: Implemented in `P2_part3.ipynb`


## Notes:

- All notebooks are designed to run in **Google Colab**.
- Please enable GPU in Colab:
  Runtime → Change runtime type → Hardware accelerator → GPU.
- Required datasets will be automatically downloaded within each notebook.vPlease refer to the setup instructions in Part 3 for additional configuration details.


## Part 1 Setup instructions (P2_Part1.ipynb):

### 1. Dataset Download:
- This notebook uses the curated Steam reviews dataset provided on BruinLearn.
- Download the two CSV files (https://drive.google.com/drive/folders/1h1OAEjEz3qqvk_3uQ20Epeq917bKJRnK):
  - `steam_reviews_main.csv`
  - `steam_reviews_heldout.csv`
- No automatic download is included for Part 1. Please place both files inside a `data/` folder in your project directory.

- Before running Part 1, make sure the dataset paths are set correctly.
  - In the notebook, verify:
    ```python
    DATA_PATH = "./data/steam_reviews_main.csv"
    HELDOUT_PATH = "./data/steam_reviews_heldout.csv"
    ```
  - Update the paths if your files are stored elsewhere.

---

### 2. MiniLM Embedding Model Download
- Part 1 uses the MiniLM model:
  `sentence-transformers/all-MiniLM-L6-v2`
- The model will be downloaded automatically the first time it is loaded.
- Example:
    ```python
    from sentence_transformers import SentenceTransformer
    model = SentenceTransformer("sentence-transformers/all-MiniLM-L6-v2")
    ```


## Part 2 Setup instructions (219pset2part2.ipynb):

### 1. GPU Requirement:
- This notebook uses a pretrained VGG network for feature extraction.
- It is strongly recommended to use Google Colab with GPU runtime.
  Runtime → Change runtime type → Hardware accelerator → GPU
- Verify GPU is enabled:
    ```python
    import torch
    torch.cuda.is_available()
    ```

### 2. Dataset Download:
- This notebook uses the tf_flowers dataset (https://www.tensorflow.org/datasets/catalog/tf_flowers).
- The dataset will be automatically downloaded when running the helper code.
- No manual download is required.

### 3. Pretrained VGG Model:
- The pretrained VGG16 model (ImageNet) will be downloaded automatically.
- Example:
    ```python
    import torchvision.models as models

    vgg = models.vgg16(pretrained=True)
    vgg.classifier = vgg.classifier[:-1]
    vgg.eval()
    ```


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
  
