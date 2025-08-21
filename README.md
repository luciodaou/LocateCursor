# LocateCursor

LocateCursor is a lightweight, customizable visual aid for macOS that helps you find your cursor. It's especially useful when working with multiple monitors or large screens. When activated, it dims the screen and highlights the cursor's position with a customizable circle.

<p align="center">
  <img src="media/LocateCursor_defaultmode.gif" alt="LocateCursor Normal Mode" width="400"/>
</p>

## Features

*   **Customizable Presets:** Comes with `default`, `presentation`, and `simple` modes, each with its own settings.
*   **On-the-Fly Configuration:** Change the appearance and behavior of the cursor highlighter without restarting the app.
*   **Command-Line Control:** Activate different modes and even create custom configurations directly from the terminal.
*   **Multi-Monitor Support:** The highlighter appears on the correct screen where your cursor is located.
*   **Lightweight:** It's a simple app with minimal resource usage.

## How to Use

You can activate LocateCursor from the command line with various options:

*   **Default Mode:**
    ```bash
    ./LocateCursor
    ```
    This activates the default mode, which dims the screen and shows a clear circle around the cursor for a short duration.

*   **Presentation Mode:**
    ```bash
    ./LocateCursor -p presentation
    ```
    This mode is designed for presentations, showing a persistent, semi-transparent yellow circle around the cursor.

*   **Simple Mode:**
    ```bash
    ./LocateCursor -p simple
    ```
    A simple red circle with a yellow border.

*   **Custom Configuration:**
    You can pass a JSON string with a custom configuration:
    ```bash
    ./LocateCursor -c '{"duration":5,"screenOpacity":0.1,"circle":{"radius":50,"opacity":0.8,"color":"blue","border":{"width":2,"color":"white"}}}'
    ```

*   **Turn Off:**
    To turn off a persistent mode (like presentation mode), you can use the `off` command:
    ```bash
    ./LocateCursor off
    ```
    You can also simply press the `Esc` key to close the highlighter at any time.

## Configuration

LocateCursor uses a `locatecursor.json` file for configuration. You can customize the existing presets or add your own.

Here's a breakdown of the configuration options:

```json
{
  "default": {
    "duration": 1,
    "screenOpacity": 0.5,
    "circle": {
      "radius": 80,
      "opacity": 0.0,
      "color": "clear",
      "border": {
        "width": 2,
        "color": "white"
      }
    }
  },
  "presentation": {
    "duration": 0,
    "screenOpacity": 0.3,
    "circle": {
      "radius": 80,
      "opacity": 0.3,
      "color": "yellow",
      "border": {
        "width": 2,
        "color": "white"
      }
    }
  },
  "simple": {
    "duration": 5,
    "screenOpacity": 0,
    "circle": {
      "radius": 100,
      "opacity": 0.5,
      "color": "red",
      "border": {
        "width": 5,
        "color": "yellow"
      }
    }
  }
}
```

*   `duration`: The time in seconds the highlighter stays visible. A value of `0` means it's persistent until you turn it off.
*   `screenOpacity`: The opacity of the screen dimming effect (from `0.0` to `1.0`).
*   `circle`: An object that defines the appearance of the circle around the cursor.
    *   `radius`: The radius of the circle in pixels.
    *   `opacity`: The opacity of the circle's fill color (from `0.0` to `1.0`).
    *   `color`: The fill color of the circle. Can be a named color (e.g., "red", "blue", "clear") or a hex code (e.g., "#FF5733").
    *   `border`: An optional object that defines the circle's border.
        *   `width`: The width of the border in pixels.
        *   `color`: The color of the border.

## Building from Source

You can build this project using Xcode or from the command line.

### With Xcode

1.  Clone the repository:
    ```bash
    git clone https://github.com/luciodaou/LocateCursor.git
    ```
2.  Open the project in Xcode.
3.  Build the project. The executable will be in the `Products` directory.

### From the Command Line

You can also compile the application from the command line using the Swift compiler:

```bash
swiftc src/LocateCursor.swift -o LocateCursor -F /System/Library/Frameworks -framework Cocoa
```
This will create the `LocateCursor` executable in the root directory of the project.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Support

If you find this app useful, please consider supporting its development. Thank you!

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/luciodaou)

---
Icon from <a href="https://www.flaticon.com/free-icons/helper" title="helper icons">Helper icons created by Fathema Khanom - Flaticon</a>