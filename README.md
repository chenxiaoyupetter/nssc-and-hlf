# Non-Semantic-Spurious-Correlations-NSSC-attack-and-High-Low-Frequency-HLF-attack


# Environment
Recover the environment by

`<conda env create -f environment_transformer.yml>`

# Attacked Dataset
The used datasets are sampled from ImageNet. Unzip clean_resized_images.zip to ROOT_PATH of utils.py.

# Models

ViTs models from[timm](https://github.com/rwightman/pytorch-image-models)

CNNs and robustly trained CNNs from [TI](https://github.com/dongyp13/Translation-Invariant-Attacks)  

Note that at this stage, the robustly trained CNNs are based on tensorflow, so if you want to use them, you need to change the image to [3,299, 299] and change the num_classes to 1001 in the code.  I have consulted and confirmed this with the author of  [paper](https://ojs.aaai.org/index.php/AAAI/article/download/20169/19928)  

# Implementation

# attack and evaluate
I wrote both attack and evaluate to the sh file

`sh run_attack and run_evaluate.sh` 

In the sh file, I've added examples that you can change to suit your needs：

`python our_attacks.py --attack OurAlgorithm --gpu 0 --batch_size 1 --model_name vit_base_patch16_224 --filename_prefix paper_results --boundary self.boundary` 

` python our_attacks.py --attack OurAlgorithm --gpu 0 --batch_size 1 --model_name pit_b_224 --filename_prefix paper_results --boundary self.boundary` 

` python our_attacks.py --attack OurAlgorithm --gpu 0 --batch_size 1 --model_name visformer_small --filename_prefix paper_results --boundary self.boundary` 

` python our_attacks.py --attack OurAlgorithm --gpu 0 --batch_size 1 --model_name cait_s24_224 --filename_prefix paper_results --boundary self.boundary` 

` python evaluate.py --boundary self.boundary` 

self.boundary can be used to adjust the parameters of NSSC and HLF

evaluate.py is suitable for ViTs, considering that robustly trained CNNs use TensorFlow, we have recreated evaluate.py for CNNs. 





