# APPA WinDMM 100 Python driver

[![Build Status](https://travis-ci.com/ezhov-evgeny/appa-windmm-python.svg?branch=develop)](https://travis-ci.com/ezhov-evgeny/appa-windmm-python)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=ezhov-evgeny_appa-windmm-python&metric=alert_status)](https://sonarcloud.io/dashboard?id=ezhov-evgeny_appa-windmm-python)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=ezhov-evgeny_appa-windmm-python&metric=coverage)](https://sonarcloud.io/dashboard?id=ezhov-evgeny_appa-windmm-python)

Python driver for APPA WinDMM 100 protocol for multimeters. 
Based on Python Serial Port Extension and compatible with Win32, OSX, Linux, BSD, Jythona and IronPython.  
Tested with APPA 109N but should be compatible with APPA 107n and other models.

Installation
------------
```bash
$ pip install appa-windmm-python
```

Example
-------
```python
from windmm.driver import WinDmmDriver

if __name__ == '__main__':
    # Initialize WinDMM driver with specified RS-232 port name as string.
    # For Windows it can be 'COM1' or 'COM4' 
    # For Unix or MacOS it can be '/dev/tty.xx'
    driver = WinDmmDriver('/dev/tty.usbserial-14130')

    # Check is serial port opened
    if not driver.is_open():
        print("Port is not opened")
        exit(-1)
        
    # Reading data 1000 times
    n = 0
    while n < 1000:
        data = driver.read_data()
        if data:
            print(data.get_raw())
            print(data)
        n = n + 1
    
    # Close serial port
    driver.close()
```