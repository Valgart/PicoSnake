# Snake Game on MicroPython

A simple Snake game that runs on a MicroPython-enabled board (e.g., ESP8266/ESP32) and is played in your web browser.

## Features

* Control via **Arrow Keys** (↑ ↓ ← →) and **W A S D**
* **Dark/Light Mode** toggle
* **Modern Mode** (wrap-around edges) and **Classic Mode** (hitting walls ends the game)
* Speed increases every 10 points
* Theme toggles every 5 points
* **Restart** button to start a new game after Game Over

## Prerequisites

* MicroPython-enabled board (ESP8266, ESP32, etc.)
* MicroPython firmware installed on the board
* Python 3.x on your host machine
* `ampy` or similar tool for uploading files to the board
* Wi-Fi network credentials (SSID & password)

## Installation

1. **Flash MicroPython**

   * If not already done, install MicroPython on your board. See: [https://micropython.org/download/](https://micropython.org/download/)

2. **Clone this repository**

   ```bash
   git clone https://github.com/Valgart/PicoSnake.git
   cd PicoSnakeroPython
   ```

3. **Create `secrets.py`**
   In the project folder, create a file named `secrets.py` with the following content:

   ```python
   SSID = 'YourWiFiName'
   PASSWORD = 'YourWiFiPassword'
   ```

4. **Upload files to the board**
   Using `ampy` (adjust the serial port as needed):

   ```bash
   ampy --port /dev/ttyUSB0 put secrets.py
   ampy --port /dev/ttyUSB0 put main.py
   ```

5. **Run the game server**

   * Open a serial REPL (e.g., `screen /dev/ttyUSB0 115200`).
   * At the prompt, enter:

     ```python
     import main
     ```
   * You should see a message like:

     ```text
     Server running at http://192.168.x.y:80
     ```

6. **Open in browser**

   * Enter the shown IP address in your browser, for example:

     ```url
     http://192.168.x.y:80
     ```

## Controls

* **Arrow Keys** or **W A S D** to steer the snake
* **Dark/Light Mode**: toggle switch (sun/moon icons)
* **Modern/Classic Mode**: toggle switch
* **Restart**: button below the game canvas

## Game Rules

1. **Goal**: Eat as many apples as possible.
2. **Growth**: Snake length increases by one segment per apple.
3. **Game Over**:

   * **Classic Mode**: Hitting the wall ends the game.
   * Both modes: Colliding with the snake's own body ends the game.
4. **Speed**: Increases by 10% every 10 apples (minimum 50ms interval).
5. **Theme**: Dark/Light mode toggles automatically every 5 apples.


Enjoy playing and tinkering! 🚀
