# CAMSAFE Safety Camera 🚨

A browser-based **real-time person detection system** that uses the device camera and **TensorFlow.js with the COCO-SSD object detection model** to detect people.

When a person is detected, the application displays a visual alert, plays an alarm sound, shows a notification and can trigger device vibration on supported mobile devices.

## 📌 Project Overview

**CAMSAFE Safety Camera** is designed as a simple safety-monitoring application that continuously monitors a live camera feed and detects the presence of a person.

The application runs directly in the web browser and uses the device's camera through the browser's MediaDevices API. The **COCO-SSD model** analyzes the video stream and identifies objects in real time.

When the model identifies an object classified as a `person`, the system triggers a safety alert.

## ✨ Features

* 📷 Accesses the device camera through the browser
* 🤖 Real-time person detection using **COCO-SSD**
* 🧠 Uses **TensorFlow.js** for machine-learning inference
* 🚨 Displays a **"Person Detected!"** visual alert
* 🔊 Plays an alarm sound when a person is detected
* 🔔 Displays a browser popup notification
* 📳 Supports vibration alerts on compatible mobile devices
* 🌐 Runs directly in a modern web browser
* ⚡ Performs detection continuously at approximately 1-second intervals

## 🛠️ Technologies Used

| Technology       | Purpose                                     |
| ---------------- | ------------------------------------------- |
| HTML5            | Web page structure and camera video element |
| CSS3             | User interface and alert styling            |
| JavaScript       | Application logic and detection workflow    |
| TensorFlow.js    | Machine-learning inference in the browser   |
| COCO-SSD         | Object detection and person classification  |
| MediaDevices API | Accessing the device camera                 |
| HTML5 Audio      | Playing the alarm sound                     |

## 🏗️ How It Works

The application follows this basic workflow:

```text
             ┌─────────────────┐
             │   Device Camera │
             └────────┬────────┘
                      │
                      ▼
             ┌─────────────────┐
             │  Live Video     │
             │     Stream      │
             └────────┬────────┘
                      │
                      ▼
             ┌─────────────────┐
             │ TensorFlow.js + │
             │    COCO-SSD     │
             └────────┬────────┘
                      │
                Object Detection
                      │
                      ▼
              ┌───────────────┐
              │ Person Found? │
              └───────┬───────┘
                      │
             ┌────────┴────────┐
             │                 │
            YES                NO
             │                 │
             ▼                 ▼
      ┌─────────────┐    ┌─────────────┐
      │ Safety Alert│    │ No Alert    │
      │ Alarm Sound │    │             │
      │ Notification│    │             │
      │ Vibration   │    │             │
      └─────────────┘    └─────────────┘
```

### Detection Process

1. The application requests permission to access the device camera.
2. The live camera stream is displayed on the webpage.
3. TensorFlow.js loads the COCO-SSD object detection model.
4. The application analyzes the camera feed approximately every second.
5. COCO-SSD returns the objects detected in the current video frame.
6. The application checks whether any detected object has the class `person`.
7. If a person is detected:
   * A visual alert is displayed.
   * The alarm sound is played.
   * A browser alert notification is displayed.
   * Device vibration is triggered when supported.
8. If no person is detected, the visual alert is hidden.

## 📂 Project Structure

```text
CAMSAFE_Safety_Camera/
│
├── index.html
├── alarm.mp4
└── README.md
```

### Files

**`index.html`**

Contains the main application code, including:

* Camera initialization
* Video stream
* TensorFlow.js integration
* COCO-SSD model loading
* Person detection
* Alert handling
* Alarm functionality
* Mobile vibration support

**`alarm.mp4`**

Audio file used as the alarm sound when a person is detected.

## 🧠 Machine Learning Model

This project uses **COCO-SSD**, an object detection model that can identify multiple object classes, including:

```text
person
bicycle
car
dog
cat
chair
...
```

For this project, the detection logic specifically checks for:

```javascript
prediction.class === 'person'
```

Therefore, the current application focuses specifically on detecting people.

## ⚙️ Detection Logic

The main detection process is performed using:

```javascript
const predictions = await model.detect(video);
```

The application then checks whether a person exists among the detected objects:

```javascript
const personDetected = predictions.some(
    prediction => prediction.class === 'person'
);
```

If a person is detected, the safety alert is triggered.

## 🚨 Alert Mechanism

When a person is detected, CAMSAFE provides multiple forms of notification:

### Visual Alert

Displays:

```text
Person Detected!
```

### Audio Alert

The application plays the configured alarm sound:

```html
<audio id="alarmSound" src="alarm.mp4"></audio>
```

### Browser Notification

A JavaScript alert is displayed:

```javascript
alert("Person Detected!");
```

### Mobile Vibration

On supported devices, the application triggers:

```javascript
navigator.vibrate([200, 100, 200]);
```

## 📸 Example Use Cases

CAMSAFE can serve as a foundation for applications such as:

* Home safety monitoring
* Basic security monitoring
* Restricted-area monitoring
* Office monitoring
* Classroom or laboratory monitoring
* Entry detection
* Prototype surveillance systems
* Computer-vision learning projects

## 🔮 Future Improvements

The current implementation provides basic person detection. It can be extended with features such as:

* Bounding boxes around detected people
* Detection confidence scores
* Multiple-person counting
* Screenshot capture when a person is detected
* Video recording
* Email or SMS notifications
* Telegram/WhatsApp notifications
* Detection history and event logging
* Timestamped alerts
* Configurable detection intervals
* Adjustable confidence thresholds
* Cloud-based monitoring
* AWS integration
* User authentication
* Dashboard for monitoring detection events

## ⚠️ Limitations

* Detection accuracy depends on lighting, camera quality and the ML model.
* Camera access requires browser permission.
* The current implementation only checks whether a person is detected, it does not display bounding boxes or confidence scores.
* The alarm may repeatedly attempt to play while a person remains in the camera frame.

## 👨‍💻 Author

**Mohd Arshan**
Computer Science & Engineering

---

⭐ If you find this project useful, consider giving the repository a star!
