# OD Sensor
Used simple electronics and 3D printed parts to make an optical density sensor for measuring optical density (OD) of anaerobic bacteria in test tubes. OD Sensor works by shining an LED through a 3D-printed tube holder to a Photosensor on the opposing side. Photosensor returns a voltage value that is proportional to the OD of the sample.
Photosensor functions by acting as variable resistor that responds to amount of light received.  
<div align="center">
Lots of light on sensor = lots of resistance = low voltage = high OD value.  <p></p>
Low light on photosensor = minimal resistance = high voltage = low OD value. <p>
</div>

## Project Libraries
Each versions (K-Bot vs. K-bot Auto) necessary Python libraries can be installed via requirements.txt. 
**<p align="center"> pip install -r requirements.txt </p>**  


## K-Bot
Portable 3D-printed bench top optical density (OD) sensor. Utilizes LabJack U3 data acquisition device (DAQ) to power an LED and collect analog voltage values from K-Bot. Analog voltages converted to OD via species specific calibration curves. DAQ is connected to laptop running terminal based RunPhotosensor application, that uses Export_csv.py file in backend. RunPhotosensor operation consists of user specifying bacteria species to be measured and then collecting as many samples as needed. Avaliable bacterial species to be measured determined by Equations.json file that contains the species specific calibration equations to convert voltage to OD.

## K-Bot Auto
K-Bot Auto is discrete K-bot sensor integrated with oscillating shaker and IR LED panel for autonomous multiday and multisample (up to 4) experiments. K-bot Auto uses Seeed XIAO ESP32S3 microcontroller with built-in wifi and Bluetooth capabilities for modulating component timing and for real time streaming of OD values to online ThingSpeak database. Uses LED panel for photosynthetic growth of bacteria, oscillating shaker to maitain sample homogenity, IoTrealy to modulate timing, and Hall effec sensor to determine osciallator position (Only want to take readings at apex of shaker oscillation for greatest precision). 

Experiment operating conditions specified by setExperimentalParameters.py and uploaded to Thingspeak database. Microcontroller polls a voltage value every tinterval seconds until Max_Time or Max_Num is reached and then will blink LED 4 times to signal experiment termination. Experimental dataset can be downloaded as easy-to-read CSV file via the downloadData.py or ThingSpeak website.

ThingsSpeak Online Database Field Variables:
Field 1 = Uploaded OD values  
Field 2 = Max_Num (number of measurements)  
Field 3 = Max_Time (run time)  
Field 4 = tinterval (measurement time interval)     
