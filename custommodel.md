# Using Other OpenCLIP Models
By default pybioclip uses the bioclip model at [hf-hub:imageomics/bioclip](https://huggingface.co/imageomics/bioclip).

Other OpenCLIP models can be used but only with predicting custom classes.



```
pybioclip predict --cls fox,dog,bird --model --pretrained 
```

```
classifier = CustomLabelsClassifier(
    cls_ary = ['fox','dog','bird'],
    model_str=args.model,
    pretrained_str=args.pretrained)
classifier.predict("Ursus.jpeg");
```
  
