# TensorFlow Object Detection API 사용법


## Step 9 train한 파일로 pb파일 만들기

학습이 끝나면

``` cmd
> cd model\research\object_detection

> python3 export_inference_graph.py --input_type image_tensor \
--pipeline_config_path training\faster_rcnn_resnet101_coco_2018_01_28.config \
--trained_checkpoint_prefix training\save_model\model.ckpt-2000000 \
--output_directory obj_test
```

를 하자

export_inference_graph.py 에 자세한 내용이 있으니 참고하길 바란다.

--input_type 은 input data의 type에 대해 말한다.  
jpg 파일은 uint8 4-d tensor of shape 이므로 image_tensor를 사용한다.

--pipeline_config_path 는 training시 config 파일을 넣어주면 된다.

--trained_checkpoint_prefix 는 training시 자동으로 저장되는 ckpt 의 경로를 적어주면 된다.  
저장되는 파일은 data-00000-of-00001 과 index, meta 파일 3가지가 저장된다.  
본인은 model.ckpt-2000000.data-00000-of-00001, model.ckpt-2000000.index, model.ckpt-2000000.meta 파일이 생성되었다.  
명령어에 적어줄 인자는 model.ckpt-2000000 까지만 적어주면 된다.

--output_detectory pb파일이 저장될 폴더를 적어주자. (없을 시 생성된다.)


## Step 10 생성된 pb파일로 test 해보기 ( jupyter notebook )

위 명령어를 실행하면 obj_test directory에 여러 파일들이 저장되는데 이것을 가지고 test를 해본다.

``` cmd
> cd model\research\object_detection
> jupyter notebook
```

을 하여 여기에 업로드 되어 있는 파일을 실행하면 된다.

cam으로도 test 가능하며, image 도 test 가능하다.
