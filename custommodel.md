# Using Other OpenCLIP Models
By default pybioclip uses the bioclip model at [hf-hub:imageomics/bioclip](https://huggingface.co/imageomics/bioclip).

Other OpenCLIP models can be used but only with predicting custom classes.



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
  
