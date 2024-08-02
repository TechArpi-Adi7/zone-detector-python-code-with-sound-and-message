# zone-detector-python-code-with-sound-and-message
from txt import Txt
from playsound import playsound
import time

# Initialize the TXT controller
txt = Txt()

# Set the speed limit for the zone
zone_speed_limit = 20  # in km/h

# Load sound file (ensure the path is correct)
sound_file = 'path/to/sound.mp3'

# Continuously monitor the vehicle's speed
while True:
    vehicle_speed = txt.get_speed()
    
    if vehicle_speed > zone_speed_limit:
        for speed in range(vehicle_speed, zone_speed_limit, -1):
            txt.set_speed(speed)
            time.sleep(0.1)
        
        txt.set_speed(zone_speed_limit)
        playsound(sound_file)  # Play sound when speed is decreased
        print(f"Vehicle speed decreased to {zone_speed_limit} km/h in the zone.")
    
    time.sleep(0.5)
