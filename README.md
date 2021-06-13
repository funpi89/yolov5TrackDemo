# 氣機車追蹤
*  reference: https://github.com/ultralytics/yolov5

比較1.使用opencv進行去背的影像處理與findContours來找到物件位置與2.使用yolov5預訓練模型預測出的物件位置這兩種方法來進行物件追蹤  
追蹤演算法為拿到車子的座標後先計算中心點，然後下一秒的畫面一樣計算車子的中心點，再去算跟上一秒畫面車子的中心點計算距離，小於25個畫素即為同一台車 
結論:無論是傳統演算法或是使用yolov5模型,並不是每一偵都可以準確預測到車子所以會有計算上的誤差,而可以從結果影片的後半段發現yolov5的表現已經比直接使用影像處理好很多了

* usage:

git clone https://github.com/ultralytics/yolov5
git clone https://github.com/funpi89/yolov5TrackDemo.git
sudo mv yolov5TrackDemo/moto_car_tracker.py yolov5/
sudo mv yolov5TrackDemo/opencv_track.py yolov5/
sudo mv yolov5TrackDemo/tracker.py yolov5/
cd yolov5
sh weights/download_weights.sh

使用yolov5: python moto_car_tracker.py --weights yolov5x.pt --img 1280 --conf 0.4 --source highway.mp4  --view-img

result video: https://www.youtube.com/watch?v=DgIJF_rXBnk

使用opencv進行影像處理: python opencv_track.py

result video: https://www.youtube.com/watch?v=Qn18tIOPMUg
