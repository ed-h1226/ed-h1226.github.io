---
title: "gxLib을 사용해 문자 출력"
date: 2019-07-26 22:00:00
categories: gxLib Study
---


{% highlight cpp linenos %}

#include    <stdio.h>
#include    <gx.h>
#include    <gxbdf.h>

int   main( void)
{
    dc_t    *dc_screen;                             // 화면 Device Context

    if  ( gx_init( "/dev/fb"))                      // gxLib 초기화
        gx_print_error( "");                        // 실행 중 에러 내용을 출력
    else
    {
        if  ( !( dc_screen = gx_get_screen_dc()))   // 화면 출력을 위한 스크린 DC 구함
            gx_print_error( "");                    // 실행 중 에러 내용을 출력
        else
        {
            if  ( gx_set_font( "gulim.bdf"))        // 폰트 설정
                gx_print_error("gulim.bdf");
            else
            {
                gx_clear( dc_screen, gx_color( 0, 0, 0, 255));
                dc_screen->pen_color = gx_color( 255, 255, 255, 255);
                gx_text_out( dc_screen, 20 , 40, "안녕하세요. FALINUX 포럼 입니다.");
            }
            gx_release_dc( dc_screen);
        }
        gx_close();
    }
    return   0;
}

{% endhighlight %}
