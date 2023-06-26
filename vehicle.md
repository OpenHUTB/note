

tensorflow实现mask-rcnn:
https://github.com/matterport/Mask_RCNN

本地安装
python2 tools/infer_simple.py \
    --cfg configs/12_2017_baselines/e2e_faster_rcnn_X-101-64x4d-FPN_1x.yaml \
    --output-dir /data/whd/tmp/X-101-64x4d-FPN_local \
    --image-ext jpg \
    --wts /data/whd/model/model_final_X-101-64x4d-FPN.pkl \
    --output-ext jpg \
    /data/whd/image


训练bdd100k数据
python2 /detectron/tools/train_net.py \
    --cfg /detectron/configs/12_2017_baselines/e2e_faster_rcnn_X-101-64x4d-FPN_1x.yaml \
    OUTPUT_DIR /data/whd/output/bdd100k
ln -s /data/whd/bdd100k/bdd100k/images/100k/train /detectron/detectron/datasets/data/coco/coco_train2014
ln -s /data/whd/bdd100k/trainData.json /detectron/detectron/datasets/data/coco/annotations/instances_train2014.json
ln -s /data/whd/bdd100k/bdd100k/images/100k/val /detectron/detectron/datasets/data/coco/coco_val2014
ln -s /data/whd/bdd100k/valData.json /detectron/detectron/datasets/data/coco/annotations/instances_valminusminival2014.json



远程ssh，并且使用共享目录/data/whd/image进行推断
python2 tools/infer_simple.py \
    --cfg configs/12_2017_baselines/e2e_faster_rcnn_X-101-64x4d-FPN_1x.yaml \
    --output-dir /data/whd/tmp/X-101-64x4d-FPN_red_only_vehicle_1 \
    --image-ext jpg \
    --wts /data/whd/model/model_final_X-101-64x4d-FPN.pkl \
    --output-ext jpg \
    /data/whd/image

python2 /detectron/tools/train_net.py \
    --cfg /detectron/configs/12_2017_baselines/e2e_faster_rcnn_X-101-64x4d-FPN_1x.yaml \
    OUTPUT_DIR /data/whd/detectron-output




训练：
python2 tools/train_net.py \
    --cfg configs/getting_started/tutorial_1/gpu_e2e_faster_rcnn_R-50-FPN.yaml \
    OUTPUT_DIR /tmp/detectron-output
coco
|_ coco_train2014
|  |_ <im-1-name>.jpg
|  |_ ...
|  |_ <im-N-name>.jpg
|_ coco_val2014
|_ ...
|_ annotations
   |_ instances_train2014.json
   |_ ...
图片目录：/detectron/detectron/datasets/data/coco/coco_train2014
ln -s /data/whd/data_2014/train2014 /detectron/detectron/datasets/data/coco/coco_train2014
标注结果：/detectron/detectron/datasets/data/coco/annotations/instances_train2014.json
ln -s /data/whd/data_2014/annotations/instances_train2014.json /detectron/detectron/datasets/data/coco/annotations/instances_train2014.json
验证图片：/detectron/detectron/datasets/data/coco/coco_val2014
ln -s /data/whd/data_2014/val2014 /detectron/detectron/datasets/data/coco/coco_val2014
最小验证集
ln -s /data/whd/data_2014/annotations/instances_val2014.json /detectron/detectron/datasets/data/coco/annotations/instances_valminusminival2014.json

验证结果
INFO task_evaluation.py: 181: copypaste: Dataset: coco_2014_minival
INFO task_evaluation.py: 183: copypaste: Task: box
INFO task_evaluation.py: 186: copypaste: AP,AP50,AP75,APs,APm,APl
INFO task_evaluation.py: 187: copypaste: 0.2202,0.4126,0.2117,0.0907,0.2280,0.3021



讲解：https://blog.csdn.net/WZZ18191171661/article/details/79453780

合并结果：把当前目录下所有的 pdf 文件全部合并到 detectron-vehicle.pdf 中。
pdftk detectron-vehicle/*.pdf cat output detectron-vehicle.pdf

将pdf转成jpg
convert 20180505102607869_002282.jpg.pdf 20180505102607869_002282.jpg

修改detectron/util/vis.py
vehicle_list = ['__background__', 'car', 'bus', 'truck']
if get_class_string(classes[i], score, dataset) not in vehicle_list:
    continue
# show box (off by default)
ax.add_patch(
    plt.Rectangle((bbox[0], bbox[1]),
                  bbox[2] - bbox[0],
                  bbox[3] - bbox[1],
                  fill=False, edgecolor='r',
                  linewidth=2.0, alpha=box_alpha))

利用自己高速公路山上的图片
仅仅是box，没有mask: X-101-64x4d-FPN (41.5)  成功
python2 tools/infer_simple.py \
    --cfg configs/12_2017_baselines/e2e_faster_rcnn_X-101-64x4d-FPN_1x.yaml \
    --output-dir /tmp/X-101-64x4d-FPN_red_only_vehicle \
    --image-ext jpg \
    --wts /data/model_final_X-101-64x4d-FPN.pkl \
    --output-ext jpg \
    image


48.1(box AP)
python2 tools/infer_simple.py \
    --cfg configs/12_2017_baselines/e2e_mask_rcnn_X-152-32x8d-FPN-IN5k_1.44x.yaml \
    --output-dir /tmp/detectron-vehicle_e2e_mask_rcnn_X-152-32x8d-FPN-IN5k \
    --image-ext jpg \
    --wts /data/model_final_e2e_mask_rcnn_X-152-32x8d-FPN-IN5k_1.44x.pkl \
    image

40.9(box AP)
python2 tools/infer_simple.py \
    --cfg configs/12_2017_baselines/e2e_mask_rcnn_R-101-FPN_2x.yaml \
    --output-dir /tmp/detectron-vehicle \
    --image-ext jpg \
    --wts /data/model_final.pkl \
    image

利用下载的权重(40.9)  成功
python2 tools/infer_simple.py \
    --cfg configs/12_2017_baselines/e2e_mask_rcnn_R-101-FPN_2x.yaml \
    --output-dir /tmp/detectron-visualizations \
    --image-ext jpg \
    --wts /data/model_final.pkl \
    demo
    
sudo docker run -itv /data/whd:/data detectron:c2-cuda9-cudnn7 /bin/bash
sudo docker cp  7c2b998a3aa9:/detectron/demo .


原始命令
python2 tools/infer_simple.py \
    --cfg configs/12_2017_baselines/e2e_mask_rcnn_R-101-FPN_2x.yaml \
    --output-dir /tmp/detectron-visualizations \
    --image-ext jpg \
    --wts https://s3-us-west-2.amazonaws.com/detectron/35861858/12_2017_baselines/e2e_mask_rcnn_R-101-FPN_2x.yaml.02_32_51.SgT4y1cO/output/train/coco_2014_train:coco_2014_valminusminival/generalized_rcnn/model_final.pkl \
    demo
    
性能：
第一张图：
Inference time: 1.525s
im_detect_bbox: 1.523s
misc_bbox: 0.002s