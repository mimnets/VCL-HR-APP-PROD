# OpenHR Smart Attendance User Guide

OpenHR uses a verified attendance system that combines a live selfie, GPS location, and precise time tracking to ensure accurate records.

---

### Prerequisites
Before you begin, ensure your device meets these requirements:
* **Camera Access:** Grant permission in your browser when prompted.
* **Location Services:** Enable GPS on your device and allow the app to access your location.
* **Secure Connection:** You must access the app via **HTTPS** for the camera and GPS to function.

---

### Step 1: Access the Attendance Module
You can start your session from the dashboard in two ways:
1.  Click the **Office Check-In** or **Factory Check-In** quick action buttons.
2.  Select **Attendance** from the sidebar menu.

### Step 2: Select Your Work Mode
* **Office Mode:** Used for standard office locations. The system matches your GPS against pre-configured office coordinates.
* **Factory Mode:** Used for field or site work. You are required to enter remarks (such as the specific site or factory name) before clocking in.

### Step 3: Verify Camera and GPS Status
Wait for the attendance screen to initialize the following:
* **Live Feed:** A circular frame will display your front-facing camera by default.
* **Face Ready Indicator:** A pulsing green light at the top confirms the camera is active.
* **GPS Tag:** Your location will appear below the camera. It will display a specific office name (e.g., "Head Office") or "Remote Area" if you are off-site.

> **Note for mobile users:** You can use the toggle button to switch between front and back cameras or enable the flashlight if needed.

### Step 4: Clocking In
Once the camera and GPS are ready:
1.  Check that your location tag is correct.
2.  If in **Factory Mode**, type your site details in the remarks field.
3.  Click **Begin Session**.

The system automatically captures your selfie and displays a "Verified" animation to confirm your check-in. The following data is recorded:
* Selfie photo and GPS coordinates.
* Location name, date, and check-in time.
* Duty type (Office/Factory).
* Attendance status (Present or Late).

### Step 5: Clocking Out
At the end of your shift:
1.  Return to the **Attendance** page or click **Finish Session** on the dashboard.
2.  The button will now display **Complete Session**.
3.  Wait for the camera and GPS to reactivate.
4.  Add optional end-of-day remarks and click **Complete Session**.

---

### Understanding Attendance Status
Your status is determined by your shift start time plus a set grace period (e.g., 15 minutes):
* **Present:** Clocked in before the grace period ends.
* **Late:** Clocked in after the grace period ends.

### Automatic Session Closure
If you forget to clock out, the system manages the session automatically:
* **Past-Date Sessions:** Closed when you next log in with the remark `[System: Auto-Closed Past Date]`.
* **Same-Day Sessions:** Closed at the end of the day (usually 11:59 PM) with the remark `[System: Max Time Reached]`.

---

### Quick Tips
* **GPS Sync:** If the location shows "Locating...", wait a moment or tap the indicator to refresh the signal.
* **Factory Details:** Be specific in your factory mode remarks to help HR identify your work site.
* **Privacy:** Your selfie is stored securely and used strictly for identity verification.
