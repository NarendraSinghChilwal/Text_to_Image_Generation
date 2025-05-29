# Text\_to\_Image\_Generation

A comprehensive project that **web-scrapes** interior-design images from ArchDaily using Selenium, builds a prompt–image dataset, and leverages a Stable Diffusion model (via Hugging Face’s `diffusers` library) to generate new images from text prompts in a Jupyter notebook.

---

## 🚀 Quickstart

1. **Clone the repository**

   ```bash
   git clone git@github.com:NarendraSinghChilwal/Text_to_Image_Generation.git
   cd Text_to_Image_Generation
   ```

2. **Create a virtual environment & install dependencies**

   ```bash
   python -m venv venv
   source venv/bin/activate        # Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **(Optional) Download full datasets**

   The repository includes a small sample CSV and original ArchDaily images. For full data and model outputs, grab the Release assets:

   * **ArchDaily prompt–image CSV (70 MB)**
     [text\_image\_pairs.csv](https://github.com/NarendraSinghChilwal/Text_to_Image_Generation/releases/download/v1.0/text_image_pairs.csv)
   * **Generated images (ZIP, \~275 MB)**
     [generated\_images.zip](https://github.com/NarendraSinghChilwal/Text_to_Image_Generation/releases/download/v1.0/generated_images.zip)
   * **Original scraped ArchDaily images (ZIP, \~1.7 GB)**
     [original\_images.zip](https://github.com/NarendraSinghChilwal/Text_to_Image_Generation/releases/download/v1.0/original_images.zip)

4. **Launch the notebook**

   ```bash
   jupyter notebook notebooks/interiordesign.ipynb
   ```

   Follow the steps to:

   * **Scrape** interior-design images and metadata from ArchDaily using Selenium
   * **Preprocess** and organize scraped images
   * **Build** prompt–image pairs specific to ArchDaily
   * **Generate** new images with a Stable Diffusion model loaded via Hugging Face `diffusers`
   * **Visualize** before/after comparisons

---

## 📂 Project Structure

```
Text_to_Image_Generation/
├── notebooks/
│   └── interiordesign.ipynb    # ArchDaily scraping & generation workflow
├── data/
│   ├── original_images/        # Raw ArchDaily images (tracked in-repo)
│   └── text_image_pairs_sample.csv  # Sample of prompt–image pairs
├── outputs/                    # (Ignored) Generated images folder
├── .gitignore                  # Whitelist-style ignore
├── requirements.txt            # Python dependencies including Selenium & diffusers
└── README.md                   # Project overview (this file)
```

---

## 🔧 Dependencies

All core dependencies are pinned in `requirements.txt`. Key libraries include:

* `selenium` — automated scraping of ArchDaily content
* `pandas` — data manipulation and CSV handling
* `requests` — HTTP requests for supplemental data
* `Pillow` — image loading & processing
* `transformers`, `diffusers` — Stable Diffusion inference (Hugging Face)

---

## 🧐 How It Works

1. **Web Scraping ArchDaily**

   * Selenium navigates ArchDaily project pages, downloads interior-design images and metadata.
   * Saves raw images under `data/original_images/`.

2. **Dataset Construction & Prompt Clustering**

   * Parses ArchDaily project descriptions (long-form architectural narratives) and extracts key features using NLP heuristics.
   * Breaks detailed descriptions into concise prompt clusters (e.g., "minimalist open-plan living room", "rustic wooden beams") to capture semantics at varying granularity.
   * Associates each image with one or more prompt clusters, producing a rich prompt–image mapping.
   * Outputs `data/text_image_pairs.csv` (full) and `data/text_image_pairs_sample.csv` (sample) for experimentation.

3. **Stable Diffusion Inference**

   * In `interiordesign.ipynb`, loads the clustered prompt–image dataset and initializes a Stable Diffusion pipeline via Hugging Face’s `diffusers`.
   * Iterates over prompt clusters to generate new images, saving them to `outputs/generated_images/`.

4. **Visualization**

   * Presents comparisons of original ArchDaily images and Stable Diffusion–generated visuals side by side, grouped by prompt cluster for qualitative evaluation.

---

## 🎨 Sample Generated Images


Below are two sample generated images based on **Prompt Clusters** :

| Prompt Cluster                                                                                                       | Generated Image                                                                                     |
| --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| *A serene forest-view living room with floor-to-ceiling glass walls, featuring a floating lounge chair and ambient lighting* | ![Generated](https://raw.githubusercontent.com/NarendraSinghChilwal/Text_to_Image_Generation/main/generated_9_1.png) |
| *A minimalist reading nook with a fluffy white fur chair beside a tall black-framed window, soft natural light streaming in* | ![Generated](https://raw.githubusercontent.com/NarendraSinghChilwal/Text_to_Image_Generation/main/generated_9_3.png) |


## 📫 Contact

For questions or collaboration, reach out to:

Email: narensinghchilwal@gmail.com
