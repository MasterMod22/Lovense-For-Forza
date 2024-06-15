Lovense Forza
Integrate Lovense toys with Forza games to provide a unique, immersive experience based on telemetry data.

Setup
Prerequisites
Ensure you have the following installed:

Node.js
NPM (Node Package Manager)
1. Clone the Repository
sh
Copy code
git clone https://github.com/yourusername/lovense-forza.git
cd lovense-forza
2. Install Dependencies
sh
Copy code
npm install
3. Enable "Data Out" in Forza Settings
HUD AND GAMEPLAY settings in Forza.
Set IP address to 127.0.0.1.
Set port according to the game:
Forza Motorsport 7: 9917
Forza Horizon 4: 9924
Forza Horizon 5: 9925
4. Network Isolation (for Xbox/Windows Store owners)
Run the appropriate PowerShell command:

Forza Motorsport 7:
sh
Copy code
CheckNetIsolation.exe LoopbackExempt -a -n="microsoft.apollobasegame_1.174.4791.2_x64__8wekyb3d8bbwe"
Forza Horizon 4:
sh
Copy code
CheckNetIsolation.exe LoopbackExempt -a -n="microsoft.sunrisebasegame_8wekyb3d8bbwe"
Forza Horizon 5:
sh
Copy code
CheckNetIsolation.exe LoopbackExempt -a -n="microsoft.624F8B84B80_8wekyb3d8bbwe"
5. Starting the Application
sh
Copy code
npm start
This will execute the start script in your package.json file, which runs node index.js.

6. Getting Toy Data
Enable and connect your Lovense toy.
Visit the Lovense API page available on your LAN by navigating to http://{lovense_ip}:30010/api/lan/getToys.
Look for:
platform: pc, android, ios.
domain: The domain Lovense is on, e.g., 192-168-178-16.lovense.club.
port: Typically 30010.
toyID: Found in the toys section, "status": 1 means the currently active toy.
Configuration
Edit the index.js file to configure the following variables with your Lovense toy details:

javascript
Copy code
const toyID = 'YOUR_TOY_ID'; // Find the ToyId
const platform = 'pc'; // Device platform: pc / android / ios
const domain = '192-168-220-1.lovense.club'; // Domain from Lovense
const port = '30010'; // Port
Usage
Choose the telemetry option for vibration response:

rpm - RPM from the Engine (recommended for best experience).
speed - Current Speed.
rumble-average - Surface Rumble (Average).
power - Power of the vehicle.
torque - Torque of the vehicle.
accel - Acceleration pedal pressure.
brake - Brake pedal pressure.
Troubleshooting
Common Issues
Network Isolation: Ensure you've run the appropriate PowerShell command to disable network isolation.
404 Invalid Parameter: Check that all parameters are correctly set in the request payload.
SSL/TLS Issues: If you encounter SSL certificate verification errors, consider disabling strict SSL checking in your HTTP requests (only for development purposes).
License
This project is licensed under the MIT License - see the LICENSE file for details.
