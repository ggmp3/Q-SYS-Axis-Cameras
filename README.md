# Q-SYS-Axis-Cameras-VAPIX-Library

## NOTES:
- Tested with the Axis P3224-V Mk II (non-PTZ), P3225-V Mk II (Zoom only), P3245-V (non-PTZ), P3265-V (non-PTZ), M5075 (PTZ), M5525-E (PTZ).
- P3214-V (non-PTZ) - Preview Image only. Possibly not supported by VAPIX Library. Firmware v6.50.5.8.
- P3364 (non-PTZ) - Preview Image only. Possibly not supported by VAPIX Library. Firmware v6.50.5.8.

## 1st August 2024 - Glen Gorton
- Within Result() function, added below code check for unsupported model# to prevent script setting a compromised Status. Preview Image will still be polled with OK status maintained.
- if (code == 404.0) and (string.match(data, "The requested URL was not found on this server")) then
   SetStatus(0, string.format("", code))
   print("Camera model number likely does not support VAPIX Library. eg. P3214-V or P3364")
   -- P3214-V (non-PTZ), P3364 (non-PTZ) - Preview Image only. Possibly not supported by VAPIX Library. Firmware v6.50.5.8.
  return end 

## 30th July 2024 - Glen Gorton
- Within Capture() function, added the camera icon to the button when the 'Preview Image Toggle' is off. Moved this logic to be inside the previewTimer.EventHandler.
- Within Initialize() and Connect() functions, changed the 'Preview Image' to the camera icon.

## 10th July 2024 - Glen Gorton
- Added further detail for the Preset Status text indicator when a response comes back with "PTZ disabled". This is returned when a camera model# does not support PTZ, or PTZ functions are disabled.

## 9th July 2024 - Glen Gorton
- Added Pan/Tilt/Zoom controls.
- Added Autofocus toggle.
- Added Home Position preset select.
- Added Preset (Save & Recall), Preset Active indicators, and Preset Status text indicator.

## 5th July 2024 - Glen Gorton
- Initial script containing Preview Image polling, Preview Image Toggle button, and polling for BasicDeviceInformation and TimeInformation.
