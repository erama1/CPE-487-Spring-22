# Lab 6: Video Game PONG

* Extend the FPGA code developed in Lab 3 (Bouncing Ball) to build a PONG game using a 5k&Omega; potentiometer with a 12-bit [analog-to-digital converter](https://en.wikipedia.org/wiki/Analog-to-digital_converter) (ADC) called [Pmod AD1](https://store.digilentinc.com/pmod-ad1-two-12-bit-a-d-inputs/) connected to the top pins of the Pmod port JA (See Section 10 of the [Reference Manual](https://reference.digilentinc.com/_media/reference/programmable-logic/nexys-a7/nexys-a7_rm.pdf))
  * The Digilent Nexys A7-100T board has a female [VGA connector](https://en.wikipedia.org/wiki/VGA_connector) that can be connected to a VGA monitor via a VGA cable or a [High-Definition Multimedia Interface](https://en.wikipedia.org/wiki/HDMI) (HDMI) monitor via a [VGA-to-HDMI converter](https://www.ventioncable.com/product/vga-to-hdmi-converter/) with a [micro-B USB](https://en.wikipedia.org/wiki/USB_hardware) power supply
  * 2019-11-15 pull request by Peter Ho with the 800x600@60Hz support for 100MHz clock
  * In 2020 Fall, [Zikang Sheng](https://github.com/karlsheng99/CPE487_dsd/tree/master/lab/lab%206) made an [alternative design](https://github.com/kevinwlu/dsd/tree/master/Nexys-A7/Lab-6/Alternative) that used onboard BTNL and BTNR buttons to control the motion of the bat without Pmod AD1 and potentiometer

![ad1.jpg](https://github.com/kevinwlu/dsd/blob/master/Nexys-A7/Lab-6/ad1.jpg)

![knob.jpg](https://github.com/kevinwlu/dsd/blob/master/Nexys-A7/Lab-6/knob.jpg)

![potentiometer.jpg](https://github.com/kevinwlu/dsd/blob/master/Nexys-A7/Lab-6/potentiometer.jpg)

![adc.png](https://github.com/kevinwlu/dsd/blob/master/Nexys-A7/Lab-6/adc.png)

* The **_bat_n_ball_** module draws the bat and ball on the screen and also causes the ball to bounce (by reversing its speed) when it collides with the bat or one of the walls.
  * It also uses a variable game_on to indicate whether the ball is currently in play.
  * When game_on = ‘1’, the ball is visible and bounces off the bat and/or the top, left and right walls.
  * If the ball hits the bottom wall, game_on is set to ‘0’. When game_on = ‘0’, the ball is not visible and waits to be served.
  * When the serve input goes high, game_on is set to ‘1’ and the ball becomes visible again.

* The **_adc_if_** module converts the serial data from both channels of the ADC into 12-bit parallel format.
  * When the CS line of the ADC is taken low, it begins a conversion and serially outputs a 16-bit quantity on the next 16 falling edges of the ADC serial clock.
  * The data consists of 4 leading zeros followed by the 12-bit converted value.
  * These 16 bits are loaded into a 12-bit shift register from the least significant end.
  * The top 4 zeros fall off the most significant end of the shift register leaving the 12-bit data in place after 16 clock cycles.
  * When CS goes high, this data is synchronously loaded into the two 12-bit parallel outputs of the module.

* The **_pong_** module is the top level.
  * BTN0 on the Nexys2 board is used to initiate a serve.
  * The process ckp is used to generate timing signals for the VGA and ADC modules.
  * The output of the adc_if module drives bat_x of the bat_n_ball module.
