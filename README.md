# AutoTyper

**AutoTyper** is a simple macOS automation tool built using Automator and AppleScript. It retrieves text from the clipboard and automatically types it into the active application. The tool includes a user-friendly delay, allowing you to switch to the desired window before the typing begins.

## Features

- **Retrieve text from the clipboard**: No need to manually paste, just copy the text and let AutoTyper do the rest.
- **Simulates typing**: Automatically types the clipboard content into the active window.
- **User notification with delay**: Displays a message and gives a 5-second window to switch to the correct input field.

## Prerequisites

- macOS with **Automator** installed.
- Access to **System Preferences** to adjust security settings.

## Installation

1. Open **Automator** and create a new **Program**.
2. Add the following actions:
   - **Run AppleScript** for displaying a delay message:
     ```applescript
     display dialog "The text will be typed. Click 'OK' and you have 5 seconds to switch to the desired window." buttons {"OK"} default button "OK"
     delay 5
     ```
   - **Get Clipboard Content** component.
   - **Run AppleScript** to simulate typing:
     ```applescript
     on run {input, parameters}
         tell application "System Events"
             keystroke input as text
         end tell
         return input
     end run
     ```
3. Save the program as `AutoTyper`.

## Usage

1. Copy the desired text to your clipboard.
2. Launch `AutoTyper`.
3. A dialog box will appear. Click **OK**.
4. Switch to the desired window within 5 seconds.
5. AutoTyper will type the clipboard content automatically.

## Security Settings

To allow AutoTyper to simulate keystrokes, macOS requires specific permissions:

1. Go to **System Preferences > Privacy & Security > Accessibility**.
2. Click the lock icon to make changes.
3. Add **Automator** and/or the saved `AutoTyper` program to the list.
4. If prompted, also enable permissions under **Input Monitoring**.

## Troubleshooting

- **Permission Error**: If you encounter an error like _“AutoTyper is not allowed to send keystrokes”_, ensure that AutoTyper has proper accessibility and input monitoring permissions as outlined above.
- **Typing Not Occurring**: Ensure the clipboard contains text before running AutoTyper.

## License

This project is licensed under the GPLv3 License. See the [LICENSE](LICENSE) file for details.
