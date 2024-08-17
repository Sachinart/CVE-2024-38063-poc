This should be on to perform the proof of concept and also you need flask in order to test/verify the bug.

Integer Overflow
In the ```process_packet``` function, the vulnerability occurs when calculating the ```total_length```:

```
total_length = packet.main_header_length
for header_length in packet.extension_headers:
    total_length += header_length
```
    
If the sum of these lengths becomes larger than the maximum value an integer can hold (2^31 - 1 for a 32-bit signed integer), it will wrap around to a negative number. This is the integer overflow.
Buffer Overflow
The integer overflow leads to a buffer overflow in this line:
```
for i in range(total_length):
    buffer[i] = 0xFF  # Potential out-of-bounds write
```
If ```total_length``` becomes negative due to integer overflow, it will be interpreted as a very large positive number by ```range()```. This causes the loop to write far beyond the end of the ```buffer```, which only has 64 bytes allocated.

### Real-World Implications
In a real system, this could lead to:

1. Overwriting adjacent memory
2. Crashing the application
3. Potential arbitrary code execution if an attacker can control the overwritten memory

This is written by Chirag Artani and if you have bad intension , you are responsible for any bad/malicious activity.

Enable it => Most probably this is enabled bydefault. 

![Screenshot_1](https://github.com/user-attachments/assets/01d8da94-6dbc-49eb-86b0-6c52d97f5073)

<mark>Check the ```CVE-2024-38063-poc.py``` for more, everything will be perform using flask python, crashing the ipv6 flowing it over passing commands and getting things executed.<mark>

Thank You!
- Chirag Artani
