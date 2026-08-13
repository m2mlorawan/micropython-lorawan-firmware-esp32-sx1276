micropython-lorawan-ESP32+SX1276.bin for EU868, US915, AU915, AS923 work with ESP32 and SX1276. 
Download this file and flash at address 0x0

https://esptool.spacehuhn.com/

If want to flash 3 files, use these address:

bootloader.bin at 0x1000

partition-table.bin at 0x8000

micropython.bin at 0x10000



```python
import lorawan, time

lw = lorawan.LoRaWAN(region=lorawan.AS923)
if not lw.joined():
    lw.join_otaa(
        dev_eui=bytes.fromhex("70B3D57ED00683AA"),
        join_eui=bytes.fromhex("0000000000000000"),
        app_key=bytes.fromhex("78164A6458CF125EFCD4BE75EB6E00AA"),
        timeout=60,
    )
while True:
    lw.send(b"Hello", port=1)
    print("Sent!")
    time.sleep(5)
```
