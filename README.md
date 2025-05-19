# Stolen Car Detector

A Python application for detecting stolen cars from video footage using object detection, license plate recognition, and database matching.

---

## Table of Contents
- [Features](#features)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)
- [Dependencies](#dependencies)
- [Key Components](#key-components)
  - [Vehicle Detection & Tracking](#vehicle-detection--tracking)
  - [License Plate Processing](#license-plate-processing)
  - [Database Integration](#database-integration)
- [License](#license)
- [Acknowledgements](#acknowledgements)
- [Contact](#contact)

---

## Features

- Detects vehicles and license plates in video files using YOLO models.
- Reads and matches license plates against a CSV list of stolen vehicles.
- Tracks vehicles across frames using the SORT tracking algorithm.
- Visualizes results by overlaying bounding boxes and license numbers on video.
- Stores and matches results in a MySQL database.

---

## Project Structure

```
Stolen-Car-Detector/
├── src/
│   ├── main.py           # Main application entry point
│   ├── util1.py          # Core utility functions and GUI
│   ├── util2.py          # License plate processing utilities
│   ├── sort/             # SORT tracking algorithm
│   │   ├── sort.py
│   │   └── LICENSE
│   └── data/             # Model weights
│       ├── car_detector.pt
│       └── license_plate_detector.pt
├── output/               # Generated output
│   ├── out.mp4          # Processed video
│   ├── test.csv         # Intermediate results
│   ├── final_data.csv   # Processed tracking data
│   └── stolen_cars.csv  # Matched stolen vehicles
└── requirements.txt      # Dependencies
```

---

## Requirements

- Python 3.8+
- MySQL Server
- CUDA-capable GPU (recommended)

Key Python packages:
- OpenCV
- Ultralytics YOLO
- EasyOCR
- MySQL Connector
- NumPy
- Pandas
- SciPy

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/Stolen-Car-Detector.git
   cd Stolen-Car-Detector
   ```

2. **Install dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

3. Set up MySQL:
- Install MySQL Server
- Create a database named `automaticlicenseplatedetector`
- Update database credentials in `src/util1.py`:
```python
password = 'your_password'
instance = 'automaticlicenseplatedetector'
```

4. Download YOLO models:
- Place model weights in `src/data/`:
  - `car_detector.pt` - Vehicle detection model
  - `license_plate_detector.pt` - License plate detection model

5. **Model Files:**
   - Place your YOLO model weights (`car_detector.pt` and `license_plate_detector.pt`) in the `src/data/` directory.

---

## Usage

1. **Run the Application:**
   ```sh
   python src.py
   ```

2. **GUI Instructions:**
   - Click "Insert CSV" to select a CSV file containing stolen license plates.
   - Click "Insert Video" to select a video file (`.mp4`).
   - Click "Execute" to start the detection and matching process.
   - The application will process the video, detect and recognize license plates, match them against the CSV, and display/save results.

![C2](https://github.com/user-attachments/assets/5a20a834-f0ea-4c88-814c-e40d3116b826)

3. **Database Cleanup:**
   - To clear the database tables, run:
     ```sh
     python src/delete\ table\ records.py
     ```

---

## Output

- Processed video with overlays is saved as `output/out.mp4`.
- Matched license plates are saved in `output/stolen_cars.csv`.

---![C1](https://github.com/user-attachments/assets/a9eb3bbc-80ad-407e-8755-95a400bf1e06)

## Dependencies

See [requirements.txt](requirements.txt) for the full list. Key packages include:
- OpenCV
- Ultralytics YOLO
- EasyOCR
- MySQL Connector
- Numpy, Pandas, Scipy

---

## Key Components

### Vehicle Detection & Tracking

- Uses YOLOv8 for vehicle and license plate detection
- Implements SORT algorithm for real-time object tracking
- Maintains vehicle identity across video frames

### License Plate Processing

- EasyOCR for plate number recognition
- Custom format validation and character correction
- Confidence scoring for OCR results

### Database Integration

- MySQL backend for storing and matching plates
- Real-time comparison against stolen vehicle database
- Result logging and export capabilities

---

## License

- The SORT tracker is licensed under the [GNU GPL v3](src/sort/LICENSE).
- Other code in this repository is provided for educational and research purposes.

---

## Acknowledgements

- [Ultralytics YOLO](https://github.com/ultralytics/ultralytics)
- [EasyOCR](https://github.com/JaidedAI/EasyOCR)
- [SORT](https://github.com/abewley/sort)

---

## Contact
For questions or support:
- Open an issue
- Submit a pull request
- Email: xie19113@gmail.com
- Email: sameerrizwanf23@nutech.edu.pk
