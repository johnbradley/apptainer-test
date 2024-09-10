# Using Other OpenCLIP Models
By default pybioclip uses the bioclip model at [hf-hub:imageomics/bioclip](https://huggingface.co/imageomics/bioclip).

Other OpenCLIP models can be used but only when predicting from a list of custom classes.

The `bioclip` command line tool provides `--model` and `--pretrained` arguments to specify an alternate model to use.

See [open_clip model loading documentation](https://github.com/mlfoundations/open_clip?tab=readme-ov-file#loading-models) for more details about values that can be used for the `--model` and `--pretrained` arguments.

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
Next we will see what pretrained models are available for the `ViT-B-16` model.

```
bioclip list-models --model  ViT-B-16
```
Output:
```
...
laion2b_s34b_b88k
...
```

### Create a prediction 

```
bioclip predict --cls duck,fish,bear --model ViT-B-16 --pretrained laion2b_s34b_b88k Ursus-arctos.jpeg
```


### Using Custom Models with Python Code
```
from bioclip import CustomLabelsClassifier

classifier = CustomLabelsClassifier(
    cls_ary = ["duck","fish","bear"],
    model_str='ViT-B-16',
    pretrained_str='laion2b_s34b_b88k')

print(classifier.predict("Ursus-arctos.jpeg"))
```
  
