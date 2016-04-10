#多分辨率融合（Multi-band blending）
Multi-Band Blending把影像分為高頻影像(Laplacian Image)與低頻影像(Gaussian Image)。</br>
##image pyramid
影像金字塔(image pyramid)，是將一張影像分成不同影像大小來分析影像，其中可以分成gaussian pyramid&laplacian pyramid兩種金字塔。
##執行步驟
1. 將兩張Alignment相鄰的影像取出疊合的部分：subA、subB。
2. 對subA與subB做Gaussian blur，產生GA,GB。
3. 利用downsampling方式建立GA與GB的Gaussian Pyramid。(PS.Gaussian Pyramid 的G0是原圖未blur的影像)
4. 對GA與GB兩個pyramid經由EXPAND和SUBTRACT得到Laplacian Pyramid，LA與LB。</br>
Ln=Gn−EXPAND(Gn−1)</br>
