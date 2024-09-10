# Using Other OpenCLIP Models
By default pybioclip uses the bioclip model at [hf-hub:imageomics/bioclip](https://huggingface.co/imageomics/bioclip).

Other OpenCLIP models can be used but only with predicting custom classes.

## Tutorial

### Download an example image
Download an image from the [bioclip-demo](https://huggingface.co/spaces/imageomics/bioclip-demo).

```console
wget https://huggingface.co/spaces/imageomics/bioclip-demo/resolve/main/examples/Ursus-arctos.jpeg
```

### List models

```
bioclip list-models
```
Output:
```
...
ViT-B-16
ViT-B-16-plus
...
```

```
bioclip list-models --model ViT-B-16
```
Output:
```
openai
laion400m_e31
laion400m_e32
laion2b_s34b_b88k
datacomp_xl_s13b_b90k
datacomp_l_s1b_b8k
commonpool_l_clip_s1b_b8k
commonpool_l_laion_s1b_b8k
commonpool_l_image_s1b_b8k
commonpool_l_text_s1b_b8k
commonpool_l_basic_s1b_b8k
commonpool_l_s1b_b8k
dfn2b
```

### List models


```
pybioclip predict --cls fox,dog,bird --model 'hf-hub:laion/CLIP-ViT-B-16-laion2B-s34B-b88K'
```

```
 --pretrained
````

```
classifier = CustomLabelsClassifier(
    cls_ary = ['fox','dog','bird'],
    model_str=args.model,
    pretrained_str=args.pretrained)
classifier.predict("Ursus.jpeg");
```
  
