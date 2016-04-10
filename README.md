# OpenCV介紹
OpenCV（Open Source Computer Vision）是一個包含許多電腦視覺相關演算處理的開放原始碼Library，並且OpenCV可以在Android、ios上開發，支援的程式語言也有C/C++，Java，Python</br></br>
電腦視覺這門領域主要研究如何讓機器「看」這個世界，了解這個世界能夠解讀影像的涵義與訊息。</br></br>
學習電腦視覺會需要其他領域的知識，如：影像處理、機器學習、資訊檢索、模式識別、統計學、線性代數等許多領域的知識。</br></br>
另外在電腦視覺的領域中包含以下幾項分支：場景重建，事件監測，目標跟蹤，目標識別，機器學習，索引建立，圖像恢復</br>
場景重建（Scene Reconstruction）：試著透過多張場景畫面或影片片段來重建目標的場景，場景重建主要是針對建立三維空間場景為主（立體場景）
事件偵測（Detection）：針對目標物是否在畫面中做偵測，並回應告知
識別（Recognition）：從影像中透過影像的處理與擷取影像特徵，做統計分析識別出目標物體
目標追蹤（ Tracking）：偵測影片中的目標移動物並追蹤此物體目標
影像恢復（Image restoration）：把一些不清晰的影像或模糊影像試著還原成原圖或是使影像清晰</br></br>
除此之外，像是Photoshop中的影像處理也可以透過OpenCV完成。</br>
所以如果需要處理到跟影像相關的技術就可透過OpenCV完協助。

##在OpenCV中包含了許多不同的模組
core：包含儲存影像的資料結構、影像明亮、繪圖、檔案處理，擷取攝像頭等</br>
imgproc：影像的處理如：翻轉縮放、灰階、二值化、邊緣偵測、值方圖等操作</br>
video：有關影片分析的部分、影片中的物件追蹤、影片中前後影像的背景相減</br>
calib3d：影像校正</br>
features2d：影像特徵點擷取（也又是影像中最特別最有特色的地方如：邊緣、顏色變化明顯等），描述子表示</br>
objdetect：物件偵測</br>
highgui：簡單的一些視窗介面或是鍵盤輸入操作功能提供</br>
gpu：透過gpu去處理影像</br>
flann：高維度的特徵處理等演算法如：LSH（局部敏感雜湊）</br>
ml：機器學習相關演算法，如分類KNN、貝式機率分類器、SVM(是SMV 筆誤 感謝網友告知)，如分群Kmean</br>
等多樣化的模組，其中也包含了其他領域的一些演算法在其中。

##在VC++目錄－＞include目錄中加入之後要include的openCV檔案路徑
C:\opencv\build\include\opencv</br>
C:\opencv\build\include\opencv2</br>
C:\opencv\build\include</br></br>
opencv與opencv2幾本上裡面都有包含相同的模組</br>
唯一的差別在於說opencv是早期Opencv1.x API的檔案裡面是以C語言的函式所編寫成，opencv2在後來2.0後才擁有，以類別的方式去編寫，有著新的呼叫與操作方式</br>
opencv2中的檔案是使用.hpp檔案去編寫header檔，所以使用時要記得include .hpp檔</br></br>
撰寫include時區分出是使用哪個版本（opencv or opencv2），你也可以在這邊的include目錄只有打"C:\opencv\build\include"</br>
```
之後在程式中在如下要使用opencv2就打#include <opencv2/highgui/highgui.hpp>
要使用opencv就打#include <opencv/highgui.h>
```
###加入函式庫
C:\opencv\build\x86\vc11\lib
##在連結器(Linker)－＞輸入－＞加入相依性的檔案
依照你要使用什麼library而引入想要使用lib檔，例如core與highgui是我等下會使用到的所以便加入進去使用</br>
C:\opencv\build\x86\vc11\lib\opencv_core246d.lib</br>
C:\opencv\build\x86\vc11\lib\opencv_highgui246d.lib</br>
做一些影像處理便可加入C:\opencv\build\x86\vc11\lib\opencv_imgproc246d.lib</br></br>
看到lib檔的前面名稱尾部都帶有d這個字（如：246d），代表是使用debug時使用，如果哪天你的專案要release請記得換掉（沒有d的是release版本喔！）

##程式碼測試－開啟攝影機為例
```
#include <stdio.h>
#include <opencv2/core/core.hpp>
#include <opencv2/highgui/highgui.hpp>

using namespace cv;
using namespace std;

int main(){

    //抓取攝影機
    VideoCapture cap(0);
    //嘗試開啟攝影機
    if(!cap.isOpened()) return -1;

    //用矩陣紀錄抓取的每張frame
    Mat frame;
    //建立一個視窗,名稱為camera
    namedWindow("camera",1);
    for(;;)
    {
        //把取得的影像放置到矩陣中
        cap >> frame;
        //顯示frame到camera名稱的視窗
        imshow("frame", frame);
        if(waitKey(30) >= 0) break;
    }
    system("PAUSE");
    return 0;
}
```

##參考資料
https://dotblogs.com.tw/v6610688/2013/10/25/image_process_intro_opencv
http://ccw1986.blogspot.tw/2013/09/learningopencv.html

