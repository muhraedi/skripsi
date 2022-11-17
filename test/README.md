
### Conda (Recommended)
```bash
# Tensorflow CPU
conda env create -f conda-cpu.yml
conda activate yolov4-cpu

# Tensorflow GPU
conda env create -f conda-gpu.yml
conda activate yolov4-gpu
```

## Menggunakan model yang telah di latih
Copy and paste .weights file ke dalam folder 'data' and copy and paste file .names ke dalam folder 'data/classes/'.
Satu-satunya perubahan dalam kode adalah pada baris 14 dari file 'core/config.py'.

## YOLOv4 menggunakan Tensorflow (tf, .pb model)
Untuk mengimplementasi YOLOv4 menggunakan TensorFlow, pertama-tama kita mengonversi .weights menjadi file model TensorFlow yang sesuai, lalu menjalankan model.

```bash
# Convert darknet weights to tensorflow
## yolov4
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416 --input_size 416 --model yolov4 

# Run yolov4 tensorflow model
python detect.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --images ./data/images/kite.jpg

# Run yolov4 on video
python detect_video.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --video ./data/video/video.mp4 --output ./detections/results.avi

# Run yolov4 on webcam
python detect_video.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --video 0 --output ./detections/results.avi
```
Ganti nama file sesuai dengan nama yang terdapat ./data/

### Hitung Objek (total objek atau per class)

#### Hitung total objek
Untuk menghitung total objek, tambahkan flag "--count" ke command detect.py atau detect_video.py atau detect_realtime.py.
```
# Run yolov4 model while counting total objects detected
python detect.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --images ./data/images/dog.jpg --count
```

## YOLOv4 menggunakan TensorFlow Lite (.tflite model)
Bisa juga mengimplementasikan YOLOv4 menggunakan TensorFlow Lite. TensorFlow Lite adalah model yang jauh lebih kecil dan cocok untuk perangkat seluler atau edge (raspberry pi, dll).
```bash
# Save tf model for tflite converting
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416 --input_size 416 --model yolov4 --framework tflite

# yolov4
python convert_tflite.py --weights ./checkpoints/yolov4-416 --output ./checkpoints/yolov4-416.tflite

# yolov4 quantize float16
python convert_tflite.py --weights ./checkpoints/yolov4-416 --output ./checkpoints/yolov4-416-fp16.tflite --quantize_mode float16

# yolov4 quantize int8
python convert_tflite.py --weights ./checkpoints/yolov4-416 --output ./checkpoints/yolov4-416-int8.tflite --quantize_mode int8 --dataset ./coco_dataset/coco/val207.txt

# Run tflite model
python detect.py --weights ./checkpoints/yolov4-416.tflite --size 416 --model yolov4 --images ./data/images/kite.jpg --framework tflite
```