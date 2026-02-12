# TubeStealer

A user-friendly desktop application to batch download YouTube videos as high-quality MP3 files from a list of links.

![App Screenshot](assets/logo.ico)


## Features

- **Batch Downloading**: Process multiple YouTube links from a single `.txt` file.
- **High-Quality Audio**: Converts videos to MP3 files at 320kbps.
- **Simple Interface**: A clean, modern GUI built with PyQt6.
- **Drag & Drop**: Easily select your links file by dragging it onto the application window.
- **Standalone Executable**: Can be packaged into a single executable file for easy distribution.

## Synergy with TubeFile

This project works in perfect harmony with [**TubeFile**](https://github.com/bc1pzzfnxl/TubeFile), my browser extension designed to quickly collect YouTube links.

The workflow is straightforward:

1.  **Collect:** Use **TubeFile** to create your list of video links on YouTube.
2.  **Export:** Export your list to a `links.txt` file.
3.  **Download:** Drag and drop `links.txt` into **TubeStealer** to batch download your selection.

## Who is this for?

This tool is perfect for **amateur DJs** and music enthusiasts building a library for **private practice** or **house parties**.

It’s an ideal solution for:
-   **Bedroom DJs** practicing transitions and sets.
-   **Curating playlists** for offline listening.
-   **Testing tracks** before purchasing high-quality versions for professional gigs.

**⚠️ Legal Disclaimer:** This tool is intended for **private, non-commercial use only**. Please support artists by purchasing their music for public performance or commercial use. Respect copyright laws in your jurisdiction.

## Technical Stack

- **Python 3.8+**
- **yt-dlp**: The core engine for downloading from YouTube.
- **PyQt6**: For the graphical user interface.
- **FFmpeg**: For audio extraction and conversion to MP3.

---

## Prerequisites

1.  **Python 3.8 or newer**:
    - Download from [python.org](https://www.python.org/downloads/).
    - During installation on Windows, ensure "Add Python to PATH" is checked.

2.  **FFmpeg**:
    - **Windows**:
        1.  Download an FFmpeg build (e.g., from [gyan.dev](https://www.gyan.dev/ffmpeg/builds/)).
        2.  Extract the archive.
        3.  From the `bin` folder of the extracted files, copy `ffmpeg.exe` and `ffprobe.exe` into the `ffmpeg/` directory at the root of this project.
    - **Linux (Debian/Ubuntu-based)**:
        - Install it via the system's package manager. The application will use the system-wide installation.
          ```sh
          sudo apt update && sudo apt install ffmpeg
          ```

---

## Development Setup

To run or modify the project in a development environment:

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/bc1pzzfnxl/TubeStealer
    cd python_ytb_mp3_download
    ```

2.  **Create and activate a virtual environment:**
    - **Windows (PowerShell):**
      ```sh
      python -m venv venv
      .\venv\Scripts\Activate.ps1
      ```
    - **macOS/Linux:**
      ```sh
      python -m venv venv
      source venv/bin/activate
      ```

3.  **Install dependencies:**
    ```sh
    pip install -r requirements.txt
    ```

4.  **Run the application:**
    ```sh
    python tubestealer.py
    ```

---

## How to Use the Application

1.  Create a text file (e.g., `links.txt`).
2.  Add one YouTube URL per line in the file.
3.  Launch the application.
4.  Either **drag and drop** the `.txt` file onto the window or click the **"Choose a file..."** button to select it.
5.  Click **"Start Download"**.
6.  The MP3 files will be saved in the `output/` folder, which is created where the application is running.

---

## Compiling the Application (Packaging)

You can package the application into a single standalone executable using **PyInstaller**.

1.  **Install PyInstaller:**
    ```sh
    pip install pyinstaller
    ```

2.  **Prepare the icon (Optional):**
    - For a custom icon on Windows, you need an `.ico` file. Convert the `assets/logo.png` to `assets/logo.ico` using an online converter and place it in the `assets` folder.

3.  **Run the build command:**
    - **For Windows:**
      ```sh
      pyinstaller --onefile --noconsole --name "TubeStealer" --icon "assets/logo.ico" --add-data "ffmpeg;ffmpeg" --add-data "assets;assets" tubestealer.py
      ```
    - **For Linux:**
      ```sh
      pyinstaller --onefile --noconsole --name "TubeStealer" --icon "assets/logo.png" --add-data "ffmpeg:ffmpeg" --add-data "assets:assets" tubestealer.py
      ```

    **Command breakdown:**
    - `--onefile`: Bundles everything into a single `.exe` (or executable file on Linux).
    - `--noconsole`: Hides the background command-line window.
    - `--name "TubeStealer"`: Sets the name of the final executable.
    - `--icon`: Sets the file icon (and default window icon).
    - `--add-data "SOURCE:DEST"`: Bundles additional files/folders. The path separator is `;` for Windows and `:` for Linux/macOS.

4.  **Find the executable:**
    - The final application will be located in the `dist/` directory, named `TubeStealer.exe` (on Windows).

---

## Project Structure

```
├───assets/
│   └───logo.ico      # Application icon (Windows)
│   └───logo.png      # Application icon (Linux/Source)
├───ffmpeg/
│   ├───ffmpeg.exe    # For Windows
│   └───ffprobe.exe   # For Windows
├───tubestealer.py    # Main application script (PyQt6 UI and logic)
├───requirements.txt  # Python dependencies
└───README.md         # This file
```

## Author

-   **@bc1pzzfnxl** ([X/Twitter](https://x.com/bc1pzzfnxl))

## License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**.

You are free to use, modify, and distribute this software, but **all modifications must remain open-source**.
If you use this code in a commercial application, that application must also be open-source under GPLv3.

**Note on Third-Party Libraries:**
This project uses **FFmpeg**, which is licensed under the LGPL v2.1+ (or GPL v2+ depending on build configuration).
The inclusion of FFmpeg binaries or linking against FFmpeg libraries requires compliance with its respective license.
See the [FFmpeg License](https://ffmpeg.org/legal.html) for more details.
