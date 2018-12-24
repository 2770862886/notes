% Android Tips

<link id="linkstyle" rel='stylesheet' href='markdown.css'/>

* Read only file system
** mount -o remount rw /system
* DP, PX transform
** Description
|         | scale | density | screen size                                       |   |
|---------+-------+---------+---------------------------------------------------+---|
| ldpi    |  0.75 |     120 | QVGA(320x240),WQVGA400(400x240),WQVGA432(432x240) |   |
| mdpi    |     1 |     160 | HVGA(320x480),WSVGA(1024x600),WXGA800(1280x800)   |   |
| hdpi    |   1.5 |     240 | WVGA(800x480),FWVGA(854x480)                      |   |
| xhdpi   |   2.0 |     320 | WXGA720(1280x720)                                 |   |
| xxhdpi  |   3.0 |     480 | (1920x1080)                                       |   |
| xxxhdpi |   4.0 |     640 |                                                   |   |
** Other
   + px = pixel
   + in = inch
   + mm = milimeter
   + pt = point = 1/72 inch
** Common size
   + small: at least 426dp x 320dp (Android does not currently support screens smaller than this.)
   + normal: at least 470dp x 320dp
   + large: at least 640dp x 480dp
   + xlarge: at least 960dp x 720dp -- Android 2.3 (API Level 9)
** Resource folder
   + res/layout-small : Devices with screens having at least a resolution of 426dp x 320dp will make use the layouts defined in this folder
   + res/layout-normal : Devices with screens having at least a resolution of 470dp x 320dp will make use the layouts defined in this folder
   + res/layout-large : Devices with screens having at least a resolution of 640dp x 480dp will make use the layouts defined in this folder
   + res/layout-xlarge : Devices with screens having at least a resolution of 960dp x 720dp will make use the layouts defined in this folder
   + res/layout-sw320dp : Devices with a smallest screen width which is greater than 320dp will make use the layouts defined in this folder
   + res/layout-sw480dp: Devices with a smallest screen width which is greater than 480dp will make use the layouts defined in this folder
* Calling Screen On Condition
** Dialpad showing && lay on table
** InCallUI not showing && lay on table
** WiredHeadset, Bluetooth, Speaker
** Hardkeyboard

# Touch Event control flow #

*-----------------------------------*
|                 A                 |
|  *-----------------------------*  |
|  |              B              |  |
|  |   *---------------------*   |  |
|  |   |          C          |   |  |
|  |   |    *-----------*    |   |  |
|  |   |    |     D     |    |   |  |
|  |   |    |           |    |   |  |
|  |   |    |           |    |   |  |
|  |   |    |           |    |   |  |
|  |   |    |           |    |   |  |
|  |   |    |           |    |   |  |
|  |   |    *-----------*    |   |  |
|  |   |                     |   |  |
|  |   *---------------------*   |  |
|  |                             |  |
|  *-----------------------------*  |
|                                   |
*-----------------------------------*

> onInterceptTouchEvent负责对touch事件的拦截，最外层的View会首先收到onInterceptTouchEvent，如果返回值为true表示拦截成功。
> 此时，拦截成功的View会收到onTouchEvent事件，内层的View不会再收到onInterceptTouchEvent事件。
> 而onTouchEvent事件的返回值决定父窗口会不会收到onTouchEvent事件。

A.onInterceptTouchEvent -> B.onInterceptTouchEvent -> C.onInterceptTouchEvent -> D.onInterceptTouchEvent
D.onTouchEvent -> C.onTouchEvent -> B.onTouchEvent -> A.onTouchEvent
