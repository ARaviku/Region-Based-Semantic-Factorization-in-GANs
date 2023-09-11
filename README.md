# Reproducibility Report of "Region-Based Semantic Factorization in GANs"

In the repository, we show our code for our reproducibility report. We include the code for different manipulation with multiple degrees or given degree, extraction of latent code from real images (for manipulation on real images), evaluation with FID, Masked MSE, and ID.

Our implementation includes revision in the manipulate.py, stylespace.ipynb, the whole extract_latent_code.ipynb, fid.ipynb, mse.ipynb, and id.ipynb. The revised lines have been marked in the manipulate.py and stylespace.ipynb.

For random seeds in quantitative evaluation, we use seed=1 for manipulation of lipstick, seed=2 for manipulation of eye size, and seed=4 for manipulation of mouth. In our quantitative evaluation, for every manipulation, we generate 1000 manipulated samples and save the corresponding original images for evaluation. We save our generated results on google drive, therefore, the evaluation files (fid.ipynb, mse.ipynb, and id.ipynb) will ask to mount drive to get access to the folders.

Before you run the code

```bash
  conda create --name env
  conda activate env
  cd code
  pip install -r ./requirements/minimal.txt
  pip install sk-video
  pip install click requests tqdm pyspng ninja imageio-ffmpeg==0.4.3
```
Download the StyleGAN2 checkpoint:

```bash
  gdown 1VkuECjZiW-kO3mpyo0kONymchzrM3Oa_
```

A certain type of manipulation:

- Manipulation: Close Eye

  ```bash
  MODEL_PATH='stylegan2-ffhq-config-f-1024x1024.pth'
  DIRECTION='directions/ffhq/stylegan2/eyesize.npy'
  SAVE_DIR='out'
  python manipulate.py ${MODEL_PATH} ${DIRECTION} --stylegan2 --save_jpg --mani_layers 4,5,6,7 --seed 2 --nums 1000 --save_dir ${SAVE_DIR} --degree 6
  ```

- Manipulation: Close Mouth

  ```bash
  MODEL_PATH='stylegan2-ffhq-config-f-1024x1024.pth'
  DIRECTION='directions/ffhq/stylegan2/mouth.npy'
  SAVE_DIR='out'
  python manipulate.py ${MODEL_PATH} ${DIRECTION} --stylegan2 --save_jpg --mani_layers 4,5,6,7 --seed 4 --nums 1000 --save_dir ${SAVE_DIR} --degree 0
  ```

- Manipulation: Lipstick

  ```bash
  MODEL_PATH='stylegan2-ffhq-config-f-1024x1024.pth'
  DIRECTION='directions/ffhq/stylegan2/lipstick.npy'
  SAVE_DIR='out'
  python manipulate.py ${MODEL_PATH} ${DIRECTION} --stylegan2 --save_jpg --mani_layers 8,9,10,11 --seed 1 --nums 1000 --save_dir ${SAVE_DIR} --degree 0
  ```


For the StyleSpace and evaluation, please follow the instructions in the Jupyter Notebooks. Here we provides a list of google drive links to the manipulated images with corresponding original images on which we conducted evaluation:

- [Close Eyes (after manipulation)](https://drive.google.com/drive/folders/1-34JFnzOGLmWKnR_3rcn-CnKwiEJTM3_?usp=share_link)
- [Close Eyes (before manipulation)](https://drive.google.com/drive/folders/1-14iLpRkU4nmdH1Ap2IFz3SNc1TQmrbl?usp=share_link)
- [Close Mouth (after manipulation)](https://drive.google.com/drive/folders/1-4WX_unKTZ2ERsC8q2mxlG45gfj6e_ER?usp=share_link)
- [Close Mouth (before manipulation)](https://drive.google.com/drive/folders/1-8DnSP-FDQleWFxQHkZ1nzx2YRJbrENn?usp=share_link)
- [Lipstick (after manipulation)](https://drive.google.com/drive/folders/1--ow4RsA2hwd7y5cwnyRjn2s_f19IaeN?usp=share_link)
- [Lipstick (before manipulation)](https://drive.google.com/drive/folders/15j-Aw3yZbfepjdmeWf3LZZqUBi-ebqsQ?usp=share_link)