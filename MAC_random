#!/usr/bin/python
import subprocess
import sys
import threading
import time



class MyThread (threading.Thread):
    die = False
    def __init__(self, name):
        threading.Thread.__init__(self)
        

    def run(self):
        while not self.die:
            print "changing MAC Adress \n\n" + (time.ctime())
            subprocess.call(["sudo","ifconfig","eth0","down"]) # change interface if required
            subprocess.call(["sudo","macchanger","-A","eth0"]) # change interface if required
            subprocess.call(["sudo","ifconfig","eth0","up"]) # change interface if required
            print "MAC Changed\n"
            time.sleep(50) # mac adress will change in 50 seconds. 

    def join(self):
        self.die = True
        print "bye"
        sys.exit(1)

if __name__ == '__main__':
    f = MyThread('first')
    f.start()
    try:
        while True:
            time.sleep(2)
    except KeyboardInterrupt:
           f.join()
