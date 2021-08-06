

##  0. 마우스, 키보드 연결 (usb 허브 필요)
  - 명령어 콘솔를 실행한후 모든 명령어 실행

##  1. 스피커
  - wav, mp3 파일을 찾아 플레이 해본다. 소리가 들리면 ok
  <pre>
  $sudo find / -name *.mp3
  $sudo find / -name *.wav
  $omxplayer -o local /home/pi/Workspace/script/audio.mp3
 </pre>
  - 테스트결과=> 성공
##  2. 마이크

  - 명령 실행 후 jiipkey mp3 파일 실행 다음 명령어 콘솔 관찰
  <pre>
  
  $/home/pi/Workspace/script/door_chirp_test.py 
  
  Initializing device.
   0 bcm2835 HDMI 1: - (hw:0,0), ALSA (0 in, 8 out)
   1 bcm2835 Headphones: - (hw:1,0), ALSA (0 in, 8 out)
   2 USB PnP Sound Device: Audio (hw:2,0), ALSA (1 in, 0 out)
   3 sysdefault, ALSA (0 in, 128 out)
   4 lavrate, ALSA (0 in, 128 out)
   5 samplerate, ALSA (0 in, 128 out)
   6 speexrate, ALSA (0 in, 128 out)
   7 pulse, ALSA (32 in, 32 out)
   8 upmix, ALSA (0 in, 8 out)
   9 vdownmix, ALSA (0 in, 6 out)
  10 dmix, ALSA (0 in, 2 out)
* 11 default, ALSA (32 in, 32 out)
State changed from Stopped to Running
  ......................State changed from Running to Receiving
Receiving data [ch0]
...State changed from Receiving to Running
Received: [0, 0, 0, 5, 1, 8, 6, 2, 9] [ch0] String : b'\x00\x00\x00\x05\x01\x08\x06\x02\t'

  </pre>
위와 같이 보이면 리슨 성공 
- 테스트결과=> 성공
##  3. gpio
  - 외측:gpio 8 [24], 내측:gpio 7[26] 22 gpio: 벨버튼
  - 명령어 gpio read gpio번호 형태로 테스트 할 수 있다.
    <pre>
    $/home/pi/Workspace/script/gpiotest.py 7
      </pre>
  - <p style='color:red'>테스트결과=> 실패 </p>
##  4. 카메라
  - 외측테스트(화면에 보임)
  <pre>
  $/home/pi/Workspace/script/camerapreview.py 5   
  </pre>
  
  - 내측테스트(화면의 보임)
  <pre>
  $/home/pi/Workspace/script/camerapreview.py 1
  </pre>
  - <font color='red'>테스트결과=> 실패 </font>
  
  <pre>
  $ls /dev/video*
  /dev/video10  /dev/video11  /dev/video12  /dev/video13  /dev/video14  /dev/video15  /dev/video16
  </pre>
  
  J6 점퍼 2개를 세로로 연결해야함
##  5. USB 모메리 
  - 메모리 스틱을 usb  에 끼운다.
  - $df -h 
  - 마운트 되어 있는 메모리 확인 
  - 테스트결과=> 성공
##  6. WIFI
  - WM10001 이름의 와이파이명이 잡힌다.
  - wifi 계정은 밑은 과정 참고. ui에서도 가능(생략)
  - $ /etc/wpa_supplicant/wpa_supplicant.conf

  <pre>
  - 테스트결과=> 성공
  network={
        ssid="Wikibox_Asus_2G"
        psk="wiki1234!"
        key_mgmt=WPA-PSK
        
  }
  </pre>
##  7. 락커

  - 하이원 문서 https://www.evernote.com/shard/s567/client/snv?noteGuid=95020550-315c-ac5e-2dea-8f2fad826a36&noteKey=38c7e6ca537e7e79487e7b7185bfa3d9&sn=https%3A%2F%2Fwww.evernote.com%2Fshard%2Fs567%2Fsh%2F95020550-315c-ac5e-2dea-8f2fad826a36%2F38c7e6ca537e7e79487e7b7185bfa3d9&title=%25ED%2595%2598%25EC%259D%25B4%25EC%259B%2590%2B%25EC%259D%25BC%25EB%25B0%2598%25EB%258F%2584%25EC%2596%25B4%25EB%259D%25BD%2B%25ED%2594%2584%25EB%25A1%259C%25ED%2586%25A0%25EC%25BD%259C%2B%2528%25EC%259C%2584%25ED%2582%25A4%25EB%25B0%2595%25EC%258A%25A4%2529
  - usb 연결후  테스트 
  - 열기 명령어 
  <pre>
  $/home/pi/Workspace/script/hione.py open
  </pre>
  - 닫기 명령어
  <pre>
  $/home/pi/Workspace/script/hione.py close
  </pre>
  <pre>
  도어락)
19200

/설명/
1:VCC      2:Dead bolt
3:NC       4:Sublatch
5:NC       6:Tx
7:GND    8:RX
<도어락기준> - 핀이 우측에 있음
  </pre>
  
    - 테스튼결과 => 성공
    - 자체 전력으로는 문을 열지 못함
    
### 8. 터치모니터
  - 테스트못함

### 9. 접압이 낮다고 경고가 나옴 (12V 5A)
  - 정품은 12V 3A 에서 작동함
  
### 10. 락커 외부전원 공급 문제 

### 11. led 테스트

    <pre>
    pi@10001:~ $ gpio -g mode 6 output
    pi@10001:~ $ gpio -g write 6 1
    pi@10001:~ $ gpio -g write 6 0
</pre>

