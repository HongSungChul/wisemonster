
##  1. 스피커
  $omxplayer -o local /home/pi/Workspace/script/audio.mp3
##  2. 마이크

  - $/home/pi/Workspace/script/door_chirp_test.py 
  - 위의 명령 실행 후 jiipkey mp3 파일 실행 다음 명령어 콘솔 관찰
##  3. gpio
  - 외측:gpio 8 [24], 내측:gpio 7[26]
  
  $gpio read 8
  
##  4. 카메라
  - 외측테스트(화면에 보임)
  $/home/pi/Workspace/script/camerapreview.py 5   
  
  - 내측테스트(화면의 보임)
  $/home/pi/Workspace/script/camerapreview.py 1
  
##  5. USB 모메리 
  - 메모리 스틱을 usb  에 끼운다.
  - $df -h 
  - 마운트 되어 있는 메모리 확인 
  
##  6. WIFI
  - WM10001 이름의 와이파이명이 잡힌다.
  - wifi 계정은 밑은 과정 참고 
  - $ /etc/wpa_supplicant/wpa_supplicant.conf

  '''
  network={
        ssid="Wikibox_Asus_2G"
        psk="wiki1234!"
        key_mgmt=WPA-PSK
        
  }
  '''
