# PyQt5 Serial Port Communication GUI

## Overview

This project implements a graphical user interface (GUI) for serial port communication using PyQt5. It allows users to connect to a serial port, configure various parameters, send data, and receive data in real-time. The application uses multithreading to handle serial port operations, ensuring a responsive user interface.

## Features

- Select and connect to available serial ports
- Configure serial port parameters:
  - Baud rate
  - Data bits
  - Parity
  - Stop bits
  - Flow control
- Send data to the connected serial port
- Receive and display incoming data in real-time
- Threaded read and write operations for improved performance

## Installation

### Prerequisites

- Python 3.6 or higher
- PyQt5

### Steps

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/pyqt5-serial-communication.git
   cd pyqt5-serial-communication
   ```

2. Create a virtual environment (optional but recommended):
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. Install the required packages:
   ```
   pip install PyQt5 pyserial
   ```

## Usage

To run the application, execute the following command in the project directory:

```
python serial_port_gui.py
```

### Using the GUI

1. **Select Port**: Choose the desired serial port from the dropdown menu.
2. **Configure Settings**: Set the baud rate, data bits, parity, stop bits, and flow control as needed.
3. **Connect**: Click the "Connect" button to establish a connection to the selected port.
4. **Send Data**: Enter the data you want to send in the text box and click "Send".
5. **Receive Data**: Incoming data will be displayed in the large text area at the bottom of the window.
6. **Disconnect**: Click the "Disconnect" button to close the serial port connection.

## Code Structure

The application consists of two main classes:

### SerialThread

This class inherits from `QThread` and handles all serial port operations in a background thread.

Key methods:
- `setup_port`: Configures the serial port with the specified parameters.
- `run`: The main thread loop that handles reading from and writing to the serial port.
- `write_data`: Queues data to be written to the serial port.
- `stop`: Stops the thread and closes the serial port connection.

### SerialPortGUI

This class creates the main window and user interface elements.

Key methods:
- `setup_ui`: Sets up all the UI elements (dropdowns, buttons, text areas).
- `connect_serial`: Establishes a connection to the selected serial port.
- `disconnect_serial`: Closes the serial port connection.
- `send_data`: Sends user-input data to the serial port.
- `update_received_data`: Updates the UI with newly received data.
- `show_error`: Displays error messages in the UI.

## Threading Model

The application uses a separate thread (`SerialThread`) for handling serial port operations. This ensures that long-lasting operations like reading from or writing to the serial port do not block the main UI thread, keeping the interface responsive.

Data to be written is queued in the `SerialThread`, allowing the UI to remain responsive even when sending large amounts of data or when the serial connection is slow.

## Error Handling

Errors that occur during serial port operations are emitted as signals from the `SerialThread` and displayed in the main UI. This includes errors such as failure to open the port or attempting to write when the port is not open.

## Contributing

Contributions to this project are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch for your feature
3. Commit your changes
4. Push to your branch
5. Create a new Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- PyQt5 documentation
- PySerial documentation

---

For any questions or issues, please open an issue on the GitHub repository.
