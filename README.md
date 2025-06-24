# Surveillance Dashboard

A modular, real-time video analytics system for crowd detection, work monitoring, and crime prevention using YOLOv5 and DeepSORT. The project provides a user-friendly Streamlit dashboard to run selected modules on uploaded videos or CCTV streams.

---

## Features

- **Crowd Detection:** Counts and tracks people in real-time using YOLOv5 and DeepSORT.
- **Work Monitoring:** Allows users to define custom zones and monitors worker presence in each zone.
- **Crime Prevention:** (Placeholder for your custom logic or future expansion.)
- **Streamlit UI:** Simple web interface to select modules and input sources (video upload or CCTV stream).

---

## Project Structure

```
combined_UI.py
crime_prevention.py
crowd_detection.py
requirements.txt
work_monitoring.py
yolov5/           # (external, see below)
```

- [`combined_UI.py`](combined_UI.py): Main Streamlit dashboard.
- [`crowd_detection.py`](crowd_detection.py): Crowd detection and tracking logic.
- [`work_monitoring.py`](work_monitoring.py): Zone-based work monitoring logic.
- [`crime_prevention.py`](crime_prevention.py): Streamlit UI (can be extended for crime prevention logic).
- [`requirements.txt`](requirements.txt): Python dependencies.
- `yolov5/`: YOLOv5 codebase (should be cloned from [ultralytics/yolov5](https://github.com/ultralytics/yolov5)).

---

## Setup Instructions

### 1. Clone YOLOv5

Clone the YOLOv5 repository to the path referenced in the code (e.g., `D:/codes/yolov5`):

```sh
git clone https://github.com/ultralytics/yolov5.git D:/codes/yolov5
```

### 2. Install Python Dependencies

It is recommended to use a virtual environment.

```sh
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

**Additional dependencies:**
- `deep_sort_realtime`  
  Install via pip:
  ```sh
  pip install deep_sort_realtime
  ```

### 3. Download YOLOv5 Model Weights

The code will automatically download the `yolov5m` weights on first run.  
Alternatively, you can manually download weights from the [YOLOv5 releases](https://github.com/ultralytics/yolov5/releases).

---

## Usage

### Launch the Streamlit Dashboard

```sh
streamlit run combined_UI.py
```

- Select the modules you want to run (Crowd Detection, Work Monitoring, Crime Prevention).
- Choose input source: upload a video or paste a CCTV stream link.
- Click "Run Selected Modules" to start the selected analytics in separate processes.

### Running Modules Directly

You can also run modules from the command line:

#### Crowd Detection

```sh
python crowd_detection.py <video_path_or_stream_url>
```

#### Work Monitoring

```sh
python work_monitoring.py <video_path_or_stream_url>
```

---

## Module Details

### Crowd Detection ([crowd_detection.py](crowd_detection.py))

- Detects and tracks people using YOLOv5 and DeepSORT.
- Displays live count of people on screen.
- Draws bounding boxes and unique IDs for each person.

### Work Monitoring ([work_monitoring.py](work_monitoring.py))

- Allows drawing custom polygonal zones on the video.
- Tracks which workers are present in each zone.
- Alerts if any zone becomes empty.
- Zones are saved to `saved_polygons.json` for persistence.

### Crime Prevention ([crime_prevention.py](crime_prevention.py))

- Currently acts as a placeholder for future logic.
- Provides the same Streamlit UI as `combined_UI.py`.

---

## Notes

- The YOLOv5 path is hardcoded as `D://codes//yolov5` in the scripts. Update this path if your YOLOv5 clone is elsewhere.
- For best performance, use a machine with a CUDA-capable GPU and install the appropriate PyTorch version.
- The system uses [deep_sort_realtime](https://github.com/levan92/deep_sort_realtime) for multi-object tracking.

---

## Troubleshooting

- **Cannot open video source:** Check the path or stream URL and ensure it is accessible.
- **CUDA not available:** The code will fall back to CPU, but performance will be slower.
- **Polygon file errors:** If `saved_polygons.json` is corrupted, zones will reset.

---

## License

This project uses YOLOv5, which is licensed under the [GNU GPL v3.0](https://github.com/ultralytics/yolov5/blob/master/LICENSE).

---

## Acknowledgements

- [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5)
- [deep_sort_realtime](https://github.com/levan92/deep_sort_realtime)
- [Streamlit](https://streamlit.io/)

---

## Author

*Sukhmanjot Singh Sandhu*
*Karan Kuhar*
