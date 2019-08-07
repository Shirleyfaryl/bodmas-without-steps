# bodmas-without-steps
import cv2
import cv2.aruco as aruco
import numpy as np
cap=cv2.VideoCapture(1)
while(True):
    ret,frame=cap.read()
    img=cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
    arucodict=aruco.Dictionary_get(aruco.DICT_6X6_250)
    parameters=aruco.DetectorParameters_create()
    corners,ids,rejectedImgPoints=aruco.detectMarkers(img,arucodict,parameters=parameters)
    imgcopy=frame.copy()
    font = cv2.FONT_HERSHEY_SIMPLEX
    if len(corners)==4:
        for i in corners:
            cv2.putText(imgcopy,"{}".format(ids),(300,330),font,0.8,(255, 255, 0), 2, cv2.LINE_AA)
            def calc():
                a1=ids[0]/ids[1]+ids[2]*ids[3]-1
                cv2.putText(imgcopy,"my=""{}".format(a1),(300,270),font,0.8,(255, 255, 0), 2, cv2.LINE_AA)
        calc()
    cv2.imshow("image",imgcopy)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
