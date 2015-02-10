---
---

Here i'm working on a stabilization system using a Stm32F3Disovery.

Here you can take a look at raw data coming from the board.
upper graph is gyroscope, with a range of +-500°/s
lower is acceleromenter, with a range of 2G
the with of the graph is about 4 seconds. (all point coming from sensors are displyed, and their ODR is sett be 400Hz)
![raw rotation 1](rotazione1.png)
![raw rotation 2](rotazione2.png)
![raw rotation 3](rotazione3.png)

as you can see there is a lot of noise onthe acceleromenter; so i decided to try to average the last 5 reading (please note acceleromenter zero hasn't been calibrated in those graph):
![average 5 value 1](rotazioneMid5valor1.png)
![average 5 value 2](rotazioneMid10valor1.png)

then with the last 10 reading:
![average 10 value](rotazioneMid10valor1.png)

andfinally as a check with the last 50 reading:
![average 50 value](rotazioneMid50valori1.png)