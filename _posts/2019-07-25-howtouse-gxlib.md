---
title: "gxLib을 기본 사용법"
date: 2019-07-26 11:00:00
categories: gxLib Study
---

gxLib의 기본 사용법에 대한 설명입니다.   
gxLib는 Device Context 개념을 적용했기 때문에 그래프출력 대상이 다르더라도 같은 함수 이름을 사용합니다.   
즉, 하드웨어의 화면이나 비트맵, JPEG, PNG에 선을 그린다고 한다면, 출력 대상이 다르더라도 모두 gx_line()을 사용합니다.   
그러므로 출력 대상별로 Device Contect 핸들을 구하는 함수는 따로 있습니다.  

```
화면 : dc_t, gx_get_screen_dc()를 이용하여 구합니다.
bmp : bmp_t, gx_bmp_open()를 이용하여 구합니다.
jpg : jpg_t, gx_jpg_open()를 이용하여 구합니다.
png : png_t, gx_png_open()를 이용하여 구합니다.
```

첫 번째 할 일은 gx_init() 호출
```
gxLib를 사용하려면 gx_init() 함수를 이용하여 라이브러리를 초기화합니다. 
라이브러리 사용을 종료하려면 gx_close()를 호출하여 작업을 완료합니다. 
gx_init() 함수를 호출할 때에는 프레임 버퍼의 장치명을 인수로 넘겨 줍니다.
```

두 번째 할 일은 화면 Device Context 핸들 구하기
```
화면에 선이나 원, BMP나 PNG같은 파일을 출력하기 위해서는 화면에 대한 device Context 핸들을 구합니다.
```
