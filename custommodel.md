# Using Other OpenCLIP Models
By default pybioclip uses the bioclip model at [hf-hub:imageomics/bioclip](https://huggingface.co/imageomics/bioclip).

Other OpenCLIP models can be used but only when predicting from a list of custom classes.


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
pybioclip predict --cls fox,dog,bird --model ViT-B-16 --predefined laion2b_s34b_b88k Ursus-arctos.jpeg
```


### Using Custom Models with Python Code
```

classifier = CustomLabelsClassifier(
    cls_ary = ['fox','dog','bird'],
    model_str='ViT-B-16',
    pretrained_str='laion2b_s34b_b88k')
print(classifier.predict("Ursus.jpeg"))
```
  
