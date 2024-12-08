<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Device Information</title>
</head>
<body>

<h1>Device Information</h1>

<label for="categorySelect">Select Category:</label>
<select id="categorySelect">
    <option value="">Select Category</option>
    <option value="camera">Camera</option>
    <option value="lock">Lock</option>
    <option value="doorbell">Doorbell</option>
    <option value="alarm">Alarm</option>
    <option value="sensor">Sensor</option>
</select>

<br><br>

<label for="deviceSelect">Select Device:</label>
<select id="deviceSelect">
    <option value="">Select Device</option>
</select>

<br><br>

<label for="deviceDetails">Device Details:</label>
<textarea id="deviceDetails" rows="10" cols="50" readonly></textarea>

<script>
    // app.js

    // Device Data (simulating the Java code objects)
    const deviceData = {
        camera: [
            { name: "Pet Monitoring Camera", details: "Device: Pet Monitoring Camera\nPrice: ₱100.00\nStatus: Active\nLocation: Living Room\nBattery Level: 85%\nPower Source: Battery\nConnectivity: Wi-Fi\nCamera Type: Indoor\nModel Type: Pet Monitoring" },
            { name: "Baby Monitor", details: "Device: Baby Monitor\nPrice: ₱120.00\nStatus: Active\nLocation: Baby's Room\nBattery Level: 80%\nPower Source: Battery\nConnectivity: Wi-Fi\nCamera Type: Indoor\nModel Type: Baby Monitoring" },
        ],
        lock: [
            { name: "Biometric Fingerprint Lock", details: "Device: Biometric Fingerprint Lock\nPrice: ₱200.00\nStatus: Active\nLocation: Front Door\nBattery Level: 90%\nPower Source: Battery\nConnectivity: Wi-Fi\nLock Type: Fingerprint\nLock Model: Biometric" },
            { name: "Smart Deadbolt Lock", details: "Device: Smart Deadbolt Lock\nPrice: ₱300.00\nStatus: Active\nLocation: Back Door\nBattery Level: 95%\nPower Source: Battery\nConnectivity: Wi-Fi\nLock Type: Deadbolt\nLock Model: Smart" },
        ],
        doorbell: [
            { name: "HD Video Doorbell", details: "Device: HD Video Doorbell\nPrice: ₱80.00\nStatus: Active\nLocation: Front Door\nBattery Level: 95%\nPower Source: Battery\nConnectivity: Wi-Fi\nDoorbell Type: Video\nDoorbell Model: HD" },
            { name: "Audio Only Doorbell", details: "Device: Audio Only Doorbell\nPrice: ₱50.00\nStatus: Active\nLocation: Back Door\nBattery Level: 85%\nPower Source: Battery\nConnectivity: Wi-Fi\nDoorbell Type: Audio\nDoorbell Model: No Video" },
        ],
        alarm: [
            { name: "Wired Burglar Alarm", details: "Device: Wired Burglar Alarm\nPrice: ₱300.00\nStatus: Active\nLocation: Living Room\nBattery Level: 100%\nPower Source: Wired\nConnectivity: Wired\nAlarm Type: Wired\nAlarm Model: SMA-201" },
            { name: "Wireless Burglar Alarm", details: "Device: Wireless Burglar Alarm\nPrice: ₱350.00\nStatus: Active\nLocation: Main Door\nBattery Level: 95%\nPower Source: Battery\nConnectivity: Wi-Fi\nAlarm Type: Wireless\nAlarm Model: SMA-202" },
        ],
        sensor: [
            { name: "PIR Motion Sensor", details: "Device: PIR Motion Sensor\nPrice: ₱80.00\nStatus: Active\nLocation: Living Room\nBattery Level: 100%\nPower Source: Battery\nConnectivity: Wi-Fi\nSensor Type: PIR\nSensor Model: SMS-301" },
            { name: "Glass Break Sensor", details: "Device: Glass Break Sensor\nPrice: ₱60.00\nStatus: Active\nLocation: Living Room\nBattery Level: 85%\nPower Source: Battery\nConnectivity: Wi-Fi\nSensor Type: Glass Break\nSensor Model: SMS-304" },
        ]
    };

    // Event listener for category selection
    document.getElementById("categorySelect").addEventListener("change", function() {
        const category = this.value;
        const deviceSelect = document.getElementById("deviceSelect");
        const detailsTextArea = document.getElementById("deviceDetails");

        // Clear existing device options and details
        deviceSelect.innerHTML = "<option value=''>Select Device</option>";
        detailsTextArea.value = "";

        if (category && deviceData[category]) {
            deviceData[category].forEach(device => {
                const option = document.createElement("option");
                option.value = device.name;
                option.textContent = device.name;
                deviceSelect.appendChild(option);
            });
        }
    });

    // Event listener for device selection
    document.getElementById("deviceSelect").addEventListener("change", function() {
        const selectedDevice = this.value;
        const category = document.getElementById("categorySelect").value;
        const detailsTextArea = document.getElementById("deviceDetails");

        if (selectedDevice) {
            const device = deviceData[category].find(d => d.name === selectedDevice);
            detailsTextArea.value = device ? device.details : "Details not available";
        } else {
            detailsTextArea.value = "";
        }
    });
</script>

</body>
</html>
