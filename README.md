# ATM System

A Python desktop ATM simulator built with Tkinter and CustomTkinter. The project demonstrates object-oriented ATM workflows, CSV-backed account data, and optional face-recognition login.

## Features

- PIN-based account login
- Face-recognition login using OpenCV
- Saving and current account selection
- Cash withdrawal
- Cash deposit
- Money transfer between accounts
- Balance inquiry
- CSV persistence for account balances

## Project structure

| File | Purpose |
| --- | --- |
| `project1.py` | Main CustomTkinter ATM application |
| `project.csv` | Sample account data used by the application |
| `face_recog.py` | Captures face samples for a user ID |
| `train_model.py` | Trains the OpenCV LBPH face-recognition model |
| `recogniser.py` | Performs face-recognition login |
| `haarcascade_frontalface_default.xml` | OpenCV face-detection classifier |
| `Atm system/` | Earlier/alternate versions of the ATM and face-recognition scripts |

The root-level `project1.py` is the recommended entry point. The other root-level scripts are earlier experiments or smaller prototypes.

## Requirements

- Python 3.9+
- A working webcam for face capture and biometric login
- Tkinter support for your Python installation

Install the Python packages:

```bash
pip install pandas opencv-contrib-python numpy pillow customtkinter
```

`opencv-contrib-python` is required because the project uses `cv2.face.LBPHFaceRecognizer_create`.

## Running the application

From the repository root:

```bash
python project1.py
```

The application reads and updates `project.csv`, so run it from the repository root.

## Setting up face recognition

Face recognition requires a `dataset/` directory containing captured face images and a generated `training.yml` model.

1. Create the dataset directory:

   ```bash
   mkdir dataset
   ```

2. Capture samples for a user ID:

   ```bash
   python face_recog.py
   ```

   Enter the numeric ID used in `project.csv` when prompted. Press **Enter** to stop capture, or let the script collect three samples.

3. Train the model:

   ```bash
   python train_model.py
   ```

4. Start the ATM application and choose **Biometric** login.

For biometric login to work, the IDs in the captured dataset and the names configured in `recogniser.py` must match the intended users.

## Account data

`project.csv` contains the sample accounts used by the application:

```text
Acc. No,Name,Balance,Password
```

This is a learning project and stores passwords in plain text. Do not use real credentials or financial data.

## Notes

- The application uses a webcam for face recognition.
- Transactions directly modify the CSV file.
- The account and transaction logic is intended for demonstration and is not suitable for production banking use.
