# SimRa Dataset

This project is part of the SimRa research project which includes the following subprojects:
- [sirma-android](https://github.com/simra-project/simra-android/): The SimRa app for Android.
- [simra-ios](https://github.com/simra-project/simra-ios): The SimRa app for iOS.
- [backend](https://github.com/simra-project/backend): The SimRa backend software.
- [dataset](https://github.com/simra-project/dataset): Result data from the SimRa project.
- [screenshots](https://github.com/simra-project/screenshots): Screenshots of both the iOS and Android app.
- [SimRa-Visualization](https://github.com/simra-project/SimRa-Visualization): Web application for visualizing the dataset.

In this project, we collect – with a strong focus on data protection and privacy – data on such near crashes to identify when and where bicyclists are especially at risk. We also aim to identify the main routes of bicycle traffic in Berlin. To obtain such data, we have developed a smartphone app that uses GPS information to track routes of bicyclists and the built-in acceleration sensors to pre-categorize near crashes. After their trip, users are asked to annotate and upload the collected data, pseudonymized per trip.
For more information see [our website](https://www.digital-future.berlin/en/research/projects/simra/).

# License
The data collected in the SimRa project and published in this repository is made available under CC BY-NC 4.0 license ([further information](https://creativecommons.org/licenses/by-nc/4.0/)).
While the license denies commercial use, we grant the following additional rights for commercial use:
You are free to use and adapt the data for all journalistic purposes as if it were a non-commercial use.

All usage under the license and the extended rights described above are subject to the terms of use below. Any violation of the terms of use voids your right to use the data set.

# Terms of Use
1. For the purpose of the terms of use, ride data shall refer to the files that include the GPS trace and the incidents; profile data shall refer to the files that include demographic information such as gender and age group.
2. When you use the data you must not engage in any activities designed
   * to identify movement profiles of individual app users,
   * to correlate ride data with profile data, or
   * to engage in other activities that might deanonymize cyclists or otherwise infringe our app users' privacy rights.

   Should you discover any such information accidentally, you are required to delete that information immediately and to not make further use of the information. You are also required to assert that such information cannot be accessed by third parties before you delete it.

3. When you make this data set publicly accessible (either in original or adapted form) you must assert that your data copy also complies with these terms of use. For this, you can either use comparable terms of use or take technical measures such as data aggregation to assert the same outcome.

# Instructions
Each file has the information of app version number and file version number as it's first line. File version number indicates how often a ride has been 
uploaded or edited: <app version>#<file version>

The "Rides" folder contains the rides and the annotations of the incidents, that were detected by the app or added by the user. In a file, first the incident information are listed, followed by an empty line, followed by "=========================", followed by the the ride information.

incidents header: key,lat,lon,ts,bike,childCheckBox,trailerCheckBox,pLoc,incident,i1,i2,i3,i4,i5,i6,i7,i8,i9,scary,desc,i10  
key: number of the incidents (starts at 0)  
lat/lon: latitude and longitude (GPS location)  
ts: timestamp (number of milliseconds from epoch)  
bike: type of bicycle:  
              0 = not chosen  
              1 = City-/Trekking Bike  
              2 = Road Racing Bike  
              3 = E-Bike  
              4 = Recumbent Bicycle  
              5 = Freight Bicycle  
              6 = Tandem Bicycle  
              7 = Mountainbike  
              8 = Other  

childCheckBox: 0, if no child is being transported on the bike, 1 otherwise.  
trailerCheckBox: 0, if no child is attached at the bike,1 otherwise.  
pLoc: Location of the phone during the ride:  
              0 = Pocket (default value)  
              1 = Handlebar  
              2 = Jacket pocket  
              3 = Hand  
              4 = Basket/Pannier  
              5 = Backpack/Bag  
              6 = Other 
incident: Type of incident:
              0 = Nothing (default value)  
              1 = Close Pass  
              2 = Someone pulling in or out  
              3 = Near left or right hook  
              4 = Someone approaching head on  
              5 = Tailgating  
              6 = Near-Dooring  
              7 = Dodging an obstacle (e.g., a dog)  
              8 = Other (Please specify below)  
i1-i10 are other participants involved in the incident. 1, if the according type of participant was involved, 0 otherwise.  
              i1 = Bus/Coach  
              i2 = Cyclist  
              i3 = Pedestrian  
              i4 = Delivery Van  
              i5 = Lorry/Truck  
              i6 = Motorcyclist  
              i7 = Car  
              i8 = Taxi/Cab  
              i9 = Other  
	      i10 = Electric Scooter  
scary: 1, if the incident was scary, 0 otherwise  
desc: text description of the incident.  

========================= (divides incident information and ride information)  

Header: lat,lon,X,Y,Z,timeStamp,acc,a,b,c  
lat/lon: latitude and longitude (GPS location) 
X/Y/Z: accelerometer sensor readings. Further information: https://developer.android.com/guide/topics/sensors/sensors_motion.html#sensors-raw-data  
ts: timestamp (number of milliseconds from epoch)  
acc: the radius of 68% confidence, meaning that there is a 68% chance that the true location is within that radius of the measured point (lat, lon) in meters  
a/b/c: gyroscope sensor readings. Further information: https://developer.android.com/guide/topics/sensors/sensors_motion.html#sensors-motion-gyro  

Profile: Contains demographical data of the user.  
Header: birth,gender,region,experience,numberOfRides,duration,numberOfIncidents,waitedTime,distance,co2,0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,behaviour,numberOfScary  

birth: birth year group  
              0 = Please Choose  
              1 = after 2004  
              2 = 2000–2004  
              3 = 1995–1999  
              4 = 1990–1994  
              5 = 1985–1989  
              6 = 1980–1984  
              7 = 1975–1979  
              8 = 1970–1974  
              9 = 1965–1969  
              10 = 1960–1964  
              11 = 1955–1959  
              12 = 1950–1954  
              13 = before 1950  
gender:  
0 = Please Choose (default value)  
              1 = Male, 2 = Female, 3 = Other  
region:  
              0 = Please Choose (default value)  
              1 = Berlin  
              2 = London  
              3 = Other  
              4 = Bern  
              5 = Pforzheim/Enzkreis  
              6 = Augsburg  
              7 = Ruhr Region  
              8 = Stuttgart  
              9 = Leipzig  
              10 = Wuppertal/Solingen/Remscheid  
              11 = Düsseldorf  
experience: experience as a cyclist (in year groups):  
              0 = Please Choose (default value)  
              1 = More then 10 years  
              2 = 5 to 10 years  
              3 = 2 to 4 years  
              4 = Less then 2 years  
numberOfRides: Number of rides a user has uploaded  
duration: The duration of rides a user has uploaded (unit: milliseconds)  
numberOfIncidents: The number of incidents a user has uploaded  
waitedTime: The duration a user had to wait during his uploaded rides (unit: seconds)  
distance: The distance of rides a user has uploaded (unit: meters)  
co2: The co2 savings of rides a user has uploaded by not driving a car (unit: g)  
0,1,...,23: The distribution of rides through the hours in a day. If a ride is from 2:34pm to 3:10pm, the values at 2 and 3 will be increased by 0.5  
behaviour: How much the user follows the traffic rules. 0 - 5, where 0 is "never" and 5 is "always"
numberOfScary: The number of uploaded incidents that were labeled as scary by the user
