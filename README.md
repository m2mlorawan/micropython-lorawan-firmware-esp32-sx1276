Work with Heltec LoRa V.2 ESP32 SX1276 Only for AS923 Thailand


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
