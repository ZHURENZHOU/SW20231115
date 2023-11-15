# SW20231115
## 그림 경계선 추출 코드 설명

#그림 읽기
img=cv2.imread("/content/drive/MyDrive/computer vision/sample3.jpg")
#각 채널에 대한 임계값 처리
retval,img_0=cv2.threshold(img[:,:,0],110,255,cv2.THRESH_BINARY)
retval,img_1=cv2.threshold(img[:,:,1],205,255,cv2.THRESH_BINARY_INV)
retval,img_2=cv2.threshold(img[:,:,2],200,255,cv2.THRESH_BINARY_INV)
#임계값 처리된 이미지를 조합하여 마스크 만들기
img_0_1=cv2.bitwise_and(img_0,img_1)
msk=cv2.bitwise_and(img_0_1,img_2)
#원본 이미지에 마스크 적용하기
result_img=cv2.bitwise_and(img, img, mask= msk)
#원본 그림 및 중간 결과 보이기
cv2_imshow(img);cv2_imshow(img_0);
cv2_imshow(img_1);cv2_imshow(img_2);
cv2_imshow(msk);cv2_imshow(result_img);
