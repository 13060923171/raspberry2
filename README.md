# raspberry2
树莓派怎么用GPIO控制马达

![4aa579024c4c6ee9cddca4dd982dccb](https://s1.ax1x.com/2020/06/21/N3NzQJ.png)

![72d7ba977fa887cf22a7a90b4bee82e](https://s1.ax1x.com/2020/06/21/N3UJSg.png)![b15c9664e9c2328aa0eb9fb2175345b](https://s1.ax1x.com/2020/06/21/N3Uc6J.png)

它们管脚的对应：

- GPIO 25–Pin 22 > L293D–Pin 1
- GPIO 24–Pin 18 > L293D–Pin 2
- GPIO 23–Pin 16 > L293D–Pin 7
- GND   –Pin 30 > L293D–Pin 5

源代码

```python
import RPi.GPIO as GPIO
from time import sleep
 
GPIO.setmode(GPIO.BOARD)
 
Motor1A = 16
Motor1B = 18
Motor1E = 22
 
GPIO.setup(Motor1A,GPIO.OUT)
GPIO.setup(Motor1B,GPIO.OUT)
GPIO.setup(Motor1E,GPIO.OUT)
 
print "Turning motor on"
GPIO.output(Motor1A,GPIO.HIGH)
GPIO.output(Motor1B,GPIO.LOW)
GPIO.output(Motor1E,GPIO.HIGH)
 
sleep(2)
 
print "Stopping motor"
GPIO.output(Motor1E,GPIO.LOW)
 
GPIO.cleanup()
```

这样就可以控制马达的转动了，扩展可以做出树莓派小车