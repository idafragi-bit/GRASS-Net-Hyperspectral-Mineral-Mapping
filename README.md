# GRASS-Net-Hyperspectral-Mineral-Mapping
GRASS-Net is a novel unsupervised deep learning framework for hyperspectral mineral mapping. It integrates graph regularized spatial–spectral subspace clustering, multi-scale spectral feature extraction, multi-scale spectral–spatial attention module, and cross-attentional spectral–spatial fusion.

Step-by-step explanation of the full pipeline


1. Input hyperspectral cube
You start with an HSI cube:
X∈R^(H×W×B)

where:
	H: height 
	W: width 
	B: number of spectral bands


2. GRSC band selection
The GRSC-inspired module selects informative bands by considering:
	spectral variance 
	graph smoothness 
	structural preservation 
This reduces redundancy and keeps mineral-discriminative information.


3. PCA or MNF preprocessing
After band selection, dimensionality is reduced further using:
	PCA for variance preservation, or 
	MNF-like preprocessing for noise suppression 
This creates a compact spectral representation.


4. Patch extraction
Small spatial neighborhoods are extracted around each pixel:
P_i∈R^(p×p×d)

These patches provide local spectral–spatial context.

5. MS-SFEIDT
Parallel multi-scale convolutions learn fine and coarse spectral patterns:
	3×3 
	5×5 
	7×7 
This helps preserve narrow mineral absorption features.


6. MS-SSAM
Attention is applied over spatial tokens to capture:
	long-range relationships 
	spectral–spatial context 
	global geological structure


7. CA-SSF
Cross-attention fuses:
	local spectral features 
	global attention features 
This creates a more discriminative joint representation.


8. Latent embedding
The model compresses fused features into a latent vector:
z_i∈R^22

This corresponds to your latent representation for clustering.

9. Unsupervised training
A reconstruction objective trains the network without labels.


10. K-means clustering
Latent vectors are clustered into mineral classes.



