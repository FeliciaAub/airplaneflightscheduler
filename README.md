# Airplane Flight Scheduler

## Requirements Analysis (RA)
### Chapter 1.   Software Requirements (SR)
 
#### 1.1              Introduction
###### a)      Purpose

The purpose of this document is to ensure that all stakeholders in this program, the Airplane Flight Scheduler, have come to an explicit agreement on the necessary requirements and functionality. This document will lay out the features that the product needs to launch.

Software Engineering Summer 2019 
The Explorers
Felicia Aubert 
Pia Wetzel
Mario Zarco

This document was written in a collaborated effort and any section not explicitly named can be assumed to be the work of the entire team.
Felicia Aubert completed 1.1 a) Document Purpose, 1.1c) Definitions, Acronyms, or Abbreviations, 1.1d) References, and 1.1e) Overview.
Pia Wetzel created the Use-Case Diagram 1.3a)


 
###### b)       Scope of the Problem 
Airplane Flight Scheduler
A graphical user interface that performs reservation tasks at the LAX based airline, Fly’s R US co.  Some functions of the software include: reserve, cancel, review, change and generate a report for managers. The confirmation will be given to the traveler. Also includes ability to pick seating and airplane meal utilizing a database.
This product will not allow for different flight sizes as the client Fly’s R US co. only has Boeing 757s. 

###### c)       Definitions, Acronyms, or Abbreviations

AFS -  Airplane Flight Scheduler
FRU - Client Fly’s R US co.
B757 - Boeing 757
GUI - Graphical user interface
LAX - Los Angeles Airport
PST - Pacific Standard Time
DB - Database
IATA - International Air Transport Association
MS - Microsoft
OS - Operating system
Java SE - Java Standard Edition
JDK - Java Development Kit
VM - Virtual Machine
SQL - Structured Query Language

###### d)      References

[1] Nielsen, J. (2009). *Usability engineering.* Amsterdam: Morgan Kaufmann.

###### e)      Overview
This document contains the product features of the AFS program, the use case diagrams and detailed use cases. It also contains the functional requirements for AFS in terms of behavior as well as interfaces needed for AFS to be run.




#### 1.2 Product Features

FE1: Make a reservation where you can pick from the available seats on the B757 as well as a meal plan determined by the time of day and length of flight. 
FE2: Change current reservation to another time or change in-flight meal or seat.
FE3: Cancel current reservation and retrieve flight number to make seat available
FE4: Generate a report for managers to review flight occupancy and the amount of needed meal plans.
FE5: Select seats for current reservation




#### 1.3     Use-Case Modeling
###### a)Use-case diagrams

![UML Use Case Diagram](figures/UML_use_case_diagram.png?raw=true "UML Use Case Diagram")
 
 
###### b)     Use-case descriptions

![UC-1](figures/use-case-1.png?raw=true "UC-1")
![UC-2](figures/use-case-2.png?raw=true "UC-2")
![UC-3](figures/use-case-3.png?raw=true "UC-3")
![UC-4](figures/use-case-4.png?raw=true "UC-4")
![UC-5](figures/use-case-5.png?raw=true "UC-5")
![UC-6](figures/use-case-6.png?raw=true "UC-6")
 
 
 

#### 1.4  Functional Requirements

**1. Start up Page**
 
a)Functionality: Store reservation input into database - include name, destination, meals, seats, and luggage
b)Realizes : Make a reservation UC-1, Modify a Reservation UC-2, Manager Report Generation UC-6
c)Inputs/Outputs
	Input: None
	Output: Navigate to desired function
d)Processing
	Boot
e)Error Handling
	N/A
 

**2. Make a Reservation**
 
a)Functionality: 
	Store reservation input into database - include name, destination, meals, seats, and luggage
b)Realizes : Make a Reservation UC-1, Seat Selection UC-4, and Meal Selection UC-5
c)Inputs/Outputs
	Input: Selection from start-up page
	Output: Confirmation Number
d)Processing
	Form Handler
		Border Layout - handle to handle west/center/east panel
	West contains:
		A. Text field entry for name
		B. Dropdown menu for destination
		C. Radial Button for luggage Yes/No
	Center Contains:
		ButtonsPanel - Group of buttons one option can be selected for meal
	East Panel:
		Toggle Buttons - 186 for each seat on flight - separated by classes and formed into rows and columns. Blacked out for non-available seats.

e)Error Handling
	If user does not fill out any field - inform the user of mistake
	If the user picks a destination - the flight is full - let user know 
 
 
**3.·Modify Reservation**
 
a)Functionality 
	Allows user to modify existing reservation
b)Realizes : UC-2
c)Inputs/Outputs
	Inputs: From start-up - choose modify reservation
	Confirmation # generated from making a reservation
	Outputs: New Confirmation #
d)Processing
	Search Database for confirmation #
	Cancel Flight - Remove from database
	Redirect user to make a reservation
e) Error Handling
	Incorrect confirmation # - let user know no confirmation number is in the system
	Systems error - cannot connect to database - ask user to try again later
	
 
 
 
**4.Cancel a reservation**
 
 
a)Functionality 
	Allows user to cancel reservation
b)Realizes : Cancel a Reservation UC-3
c)Inputs/Outputs
	Input: From start-up - choose modify reservation
		 Confirmation # generated from making a reservation
	Output: Inform user on canceled reservation
			Issue refund - store credit
d)Processing
	Search Database for confirmation #
	Cancel Flight - Remove from database
e)Error Handling
	Incorrect confirmation # - let user know no confirmation number is in the system
	Systems error - cannot connect to database - ask user to try again later

        	
**5.Select a seat**


a)Functionality 
	Allows users to custom choose from available in-flight seats
b)Realizes : Seat Selection UC-4
c)Inputs/Outputs
	Input: Selecting from toggle buttons
	Output: Seat selection
d)Processing
	Visual seat representation created using a matrix
	Seats that are unavailable are retrieved from database for-loop
	Seats selected before confirmation are greyed out with the togglebutton	  

e)Error Handling
	Double-Booking not allowed - seat may only be able to selected once visually represented error handling by disabling the toggle button

**7.Select a meal plan**
 
a)Functionality 
	Allows for in-flight meal selection
b)Realizes : Meal Selection UC-5
c)Inputs/Outputs
	Input: Selection from buttons panel
	Output: Meal selected
d)Processing
	Allow for meal to be selected based on time of flight
	Only allow for selection of one meal plan - everyone eats the same 
		-Low Priority
e)Error Handling
	Only one meal may be selected at a time- once a meal is chosen other meals options are disabled
 
 
**8.Report Generation**

a)Functionality 
	Generates a report for managers
b)Realizes : UC-6
c)Inputs/Outputs
	Input: Through startup - select that they are managers then they enter their manager pin pad.
	Output:  Report generation
d)Processing
	System confirms manager pin number
	Report generated from database organized by destination		
e)Error Handling
	Incorrect Pin - Let manager know they inputted the pin incorrectly


**8.Select Destination and determine distance**

a)Functionality 
	After confirmation distance and price are determined
b)Realizes : Make a reservation UC-1
c)Inputs/Outputs
	Input: Destination
	Output: Price
d)Processing
	Array of Destinations with hardcoded distance/time from LAX
	Determine price based on distance and number of seats in reservation
e)Error Handling
	Systems error - cannot connect to database - inform user


 
 
 
 
#### 1.5  External Interfaces

**a)User Interfaces**
Startup page
 ![Start Up](figures/startup.png?raw=true "Example")

Manager pinpad
 
 
![Manager Pinpad](figures/manager.png?raw=true "Example")
![Manager Pinpad](figures/manager-2.png?raw=true "Example") 
 
Reservation

![Reservation](figures/reserve-ui-original.png?raw=true "Example")

Shown in the images above depicts an initial prototype of the Graphical user interface that the user will interact with to navigate the AFS application. 
Family Font Standard is Aerial.
Screen layout is 800x600.
The standard button are the back button. Which will be included on each interface.
There are no available keyboard shortcuts for this program, it is intended to be used with a standard mouse.
Error messages will be displayed in cases of incorrect input for pin, or confirmation number. Also, error messages will be displayed in the case of a database connection failure.

**b)     Hardware Interfaces**
This product is intended for use on terminals located inside the airport.
Hardware devices required are monitor with at least 800x600p aspect ratio.
A mouse is necessary for input to the application.
The terminal requires LAN for connection to local DB that.

**c)      Software Interfaces**
MySQL Version 8.0
Windows Operating System Version 8+
Java JDK Version 12.0.1
Java SE Runtime Environment 8
Json-simple Version 1.1.1
AFS application uses MySQL for it’s DB to store flight information. Information that is stored into the DB is Name, luggage(yes/no), destination, departure time, arrival time, meal selection, seat selection, and confirmation number during passenger reservation at the make a reservation page. The DB stores this information and retrieves it during change or cancel a reservation. Both of these functions delete the initial reservation, and change a reservation redirects to the make a reservation page.

AFS is intended to run on MS Windows OS versions 8 and up, though Java VM can run on additional OS because it is the most used OS in the business world and testing on additional OS will not be conducted.

Java JDK is the development tool that was used to build the application and Java SE is the VM that runs the application. Java programs require Java SE in order to run.

Json-simple is a program that allows for easy and fast reading of JSON files the Json-simple program reads a list of airports into the AFS application and populates the DestinationList class to provide a dynamic array list of airport destinations.
**d) 	Communications Interfaces**
N/A




#### 1.6  Performance Requirements 
	a)  Reliability 
		AFS application is expected to be a reliable resource for FRU. Managing and maintaining an accurate database of flight information will improve customer experience and save manager time.
	b)  Response Time
		AFS application response time is not a critical need at this time. Response time is expected to be around 10 second as that is approximately the amount of time before the user becomes distracted or impatient. [1]




#### 1.7  Other Requirements
 
  	a) Time:
		5 weeks
  	b) Cost:
		Free
  	c) Site Adaptation
		LAX
  	d) Security
		Personal data not stored, encryption not necessary at this time.
  	e)  any other
		N/A
		
		
		
		
		
		
		
		
	


	
		
## Specification/Analysis Modeling	         

 



### Chapter 2. Specification/Analysis Modeling
 
 
 
#### 2.1           Introduction
 
###### a)Purpose

The purpose of this document is to highlight necessary information which could not be obtained in the requirements gathering. This document is intended to precisely describe what the program with do and its constraints.

Software Engineering Summer 2019 
The Explorers
Felicia Aubert 
Pia Wetzel
Mario Zarco

Felicia completed the 2.1) Introduction sections of this document.
Pia Wetzel completed all of the 2.2) Data Flow diagrams and 2.3) Class Modeling diagrams.

 
###### b) 	Definitions, Acronyms, or Abbreviations
	ID - Identification
	GUI - Graphical User Interface
	PIN - Personal Identification Number
	SQL - Structured Query Language
 
###### c)  	 References
[1] Alder, Gaudenz, and David Benson. “Free Flowchart Maker and Diagrams Online.” Flowchart Maker & Online Diagram Software, JGraph Ltd., www.draw.io/.
 
###### d)      Overview
This document contains Data flow diagrams for each use case detailed in the Requirement Analysis documentation. It also contains the converted class modeling diagrams.


 
 
#### 2.2  Data Flow Diagrams
 



###### a)  	Level 0 (Context Diagram)

 ![Context Diagram](figures/level-0.png?raw=true "Context Diagram")
 



###### b) 	Level 1 diagrams
 ![Level 1](figures/level-1.png?raw=true "Level 1")

###### c)  	Level 2 diagrams

**Level 2 DFD for Make Reservation:**

![Level 2 DFD Make Reservation](figures/level-2-reserve.png?raw=true "Make Reservation")  


**Level 2 DFD for Modify Reservation:**

![Level 2 DFD Modify Reservation](figures/level-2-mod.png?raw=true "Modify Reservation")



**Level 2 DFD for Cancel Reservation**

![Level 2 DFD Cancel Reservation](figures/level-2-cancel.png?raw=true "Cancel Reservation")
 


**Level 2 DFD for Select a Seat**

![Level 2 DFD Seat Selection](figures/level-2-seat.png?raw=true "Select a Seat")
 


**Level 2 DFD for Select a Meal**

 ![Level 2 DFD Meal Selection](figures/level-2-meal.png?raw=true "Select a Meal")
 
 
 
**Level 2 DFD for Generate Report:**

 ![Level 2 DFD Report Generation](figures/level-2-report.png?raw=true "Generate Report")
 

 
 
#### 2.3  Class Modeling

###### a)  Initial Class Diagram

![Class Diagram](figures/class-diagram.png?raw=true "Class Diagram")[1]
 
 
 
###### b) simplified/modified Class Diagram

![Modified Class Diagram](figures/class-diagram-2.png?raw=true "Class Diagram")[1]














## Design Modeling




### Chapter 3.  Design Modeling
 
 
 
#### 3.1 Introduction
###### a)  Purpose

 
The purpose of this document is to show the design models the software engineers of the team “The Explorers” derived from the previously completed specification and analysis part. The implementation of the Airplane Flight Scheduler software is expected to be based on the models and diagrams listed in this document. 

This document was written in a collaborated effort and any section not explicitly named can be assumed to be the work of the entire team.

Software Engineering Summer 2019 
The Explorers
Felicia Aubert 
Pia Wetzel
Mario Zarco

Felicia Aubert Completed 3.1b) Definitions, Acronyms or Abbreviations, 3.1c) References, and 3.3b)  Detailed Class Diagrams
Pia Wetzel completed: PSD Diagram (part 3.2) and Sequence Diagrams (part 3.3 a)

###### b) Definitions, Acronyms or Abbreviations
	UC - Use Case
	PIN - Personal Identification Number
###### c)  References
	
	[1] Alder, Gaudenz, and David Benson. “Free Flowchart Maker and Diagrams Online.” Flowchart Maker & Online Diagram Software, JGraph Ltd., www.draw.io/.
	All diagrams in this document were created using draw.io
###### d) Overview

 
 
 
 
#### 3.2. Functional Modeling
**Program Structure Diagram**

 ![PSD](figures/PSD.png?raw=true "Program Structure Diagram")


 
 
 
 
#### 3.3 OO modeling


###### a)  Sequence Diagrams
 
**For Use Case “Make a Reservation” UC-1**

![Sequence Diagram](figures/sd-reserve.png?raw=true "UC-1 Make a Reservation")



**For Use Case “Modify a Reservation” UC-2**

![Sequence Diagram](figures/sd-mod.png?raw=true "UC-2 Modify a Reservation")
 


**For Use Case “Cancel a Reservation” UC-3**

![Sequence Diagram](figures/sd-cancel.png?raw=true "UC-3 Cancel a Reservation")

 

**For Use Case “Select Seats” UC-4**

![Sequence Diagram](figures/sd-seat.png?raw=true "UC-4 Select Seats")



**For Use Case “Select a Meal Plan” UC-5 **

![Sequence Diagram](figures/sd-meal.png?raw=true "UC-5 Select a Meal")



**For Use Case “Report Generation” UC-6**

![Sequence Diagram](figures/sd-report.png?raw=true "UC-6 Report Generation")



 
###### b)  Detailed Class Diagrams

 
**For Use Case “Make a Reservation” UC-1**

![Detailed Class Diagram](figures/cd-reserve.png?raw=true "UC-1 Make a Reservation")



**For Use Case “Modify a Reservation” UC-2**

![Detailed Class Diagram](figures/cd-mod.png?raw=true "UC-2 Modify a Reservation")
 


**For Use Case “Cancel a Reservation” UC-3**

![Detailed Class Diagram](figures/cd-cancel.png?raw=true "UC-3 Cancel a Reservation")

 

**For Use Case “Select Seats” UC-4**

![Detailed Class Diagram](figures/cd-seat.png?raw=true "UC-4 Select Seats")



**For Use Case “Select a Meal Plan” UC-5 **

![Detailed Class Diagram](figures/cd-meal.png?raw=true "UC-5 Select a Meal")



**For Use Case “Report Generation” UC-6**

![Detailed Class Diagram](figures/cd-report.png?raw=true "UC-6 Report Generation")











## Phase 4: Implementation


 
### Chapter 4.  Implementation




 
#### 4.1 Introduction

###### a) Purpose
   	The purpose of this diagram is to translate the design from the Class Modeling and generating the code for the program.

	Software Engineering Summer 2019 
	The Explorers
	Felicia Aubert 
	•	Wrote the 4.1) introduction, 4.2) Environment Choice and as well as detailed DestinationList, and airports. 
	Pia Wetzel 
	•	Documented 4.2 Implementation Environment for personally implemented classes Customer, SchedulerStart, Manager, SQLConnectionManager
	Mario Zarco
	•	Documented 4.2 Implementation Environment for personally implemented classes Reservation, Scheduler, schedulerPanel, centerPanels, easternPanels, and westernPanels
	
	

###### b)  Definitions, Acronyms or Abbreviations
   	IDE - Integrated Design Element
	VM - Virtual Machine
	Java SE - Java Standard Edition
	UI - User Interface
	
###### c) References
	[1] Sun Microsystems, Inc (6/14/2019) Java2sAutoComboBox *[source code]* http://java.sun.com/docs/books/tutorial/index.html

	[2] Brooks, J (6/05/2019) JSON-Airports *[raw data]*. https://github.com/jbrooksuk/JSON-Airports

	[3] Fang, Y (6/07/2019) JSON-simple *[source code]*. https://github.com/fangyidong/json-simple
	[4] Fly?, H. (2019). *How Fast Do Commercial Aeroplanes Fly?* | FlightDeckFriend.com. Retrieved from https://www.flightdeckfriend.com/how-fast-do-commercial-aeroplanes-fly

		*Note: References are to source code or information pertaining to source code found in Appendix B.*

###### d)  Overview
	This document outlines the decision behind our programing environment and contains the translated implementation of the class diagrams detailed in SECTION 3.




 
#### 4.2. Implementation Environment

Environment: Eclipse
Language: Java
We chose to build our application in Java using the Eclipse IDE because of the available automatic programming for both WindowBuilder for our UI and for the simplicity of correcting simple syntax errors. 
Java also is relatively easy to use cross-platform the system needs to have Java SE install to run Java applications and acts as a VM so it can interface with multiple systems.

 


**a) DestinationList**
b) June 20, 2019
c) Felicia Aubert
d) This class manages the Destinations available by reading in a list of airports from a JSON file and creating an Array List or airports that 
e)  Any important data structure in class/functions
•	ArrayList holding an airport structure data
•	Function distance that utilizes the information in airports to determine the time it takes to get from LAX to the selected destination
•	getAByeTime that utilizes the time given to add it to the departure time.
f)  choice of a specific algorithm within service/function
            N/A
 
**a) Java2sAutoComboBox [1]**
**a) Java2sAutoTextField [1]**
**a) Reservation**
b) June 27,2019
c) Mario Zarco 
d) Reservation encapsulates the information entered in such as:
private String passenger;
	private boolean luggage;
	private String confirmation;
	private String departureTime;
	private String destination;
	private String arrivalTime;
e)  Any important data structure in class/functions
•	The Reservation data structure is created and prompted with setters and getters.
f)  choice of a specific algorithm within service/function
•	N/A
**a) Scheduler**
b) June 27,2019 
c) Mario Zarco 
d) Scheduler is considered our main to initialize schedulerPanel
	private String iata;
	private String name;
	private double longitude;
	private double latitude;
e)  Any important data structure in class/functions
•	N/A
f)  choice of a specific algorithm within service/function
•	N/A
**a) airports**
b) June 20,2019 
c) Felicia Aubert
d) airport structure maintained by DestinationList
	
e)  Any important data structure in class/functions
•	Holds
f)  choice of a specific algorithm within service/function
•	N/A
**a) centerPanels**
b) June 27, 2018
c) Mario Zarco
d) centerPanels just establishes a boundary class for the meal plan buttons.
e)  Any important data structure in class/functions
•	N/A
f)  choice of a specific algorithm within service/function
•	N/A
**a) easternPanels**
b) June 27, 2018
c) Mario Zarco
d) In easternPanels, the seat button boundary class is created and and algorithm for the claimed seat to turn black is implemented with the gui message if selected. Each button is given an itemlistener to be enabled and disabled for the desired effect of adding and deducting seats. 
e)  Any important data structure in class/functions
•	N/A
f)  choice of a specific algorithm within service/function
•	e.g. Implementing this method with the seats already listed in database would work. I wanted an approach that could manage the data self-sufficiently.
**a) schedulerPanel**
b) June 27,2018
c) Mario Zarco
d) schedulerPanel is initialized in our main which is scheduler and is responsible for the sequences of method instructions to manage our Airplane Flight Scheduler. 
e)  Any important data structure in class/functions
•	N/A
f)  choice of a specific algorithm within service/function
•	N/A
**a) westernPanels**
b) June 27, 2018
c) Mario Zarco
d) westernPanels creates a boundary class that displays:
	private JTextField for Name entry
private JRadioButton luggageButton1
	private JRadioButton luggageButton2
	private Java2sAutoComboBox destination
	private JComboBox departures
	JButton confirmButton;
e)  Any important data structure in class/functions
•	N/A
f)  choice of a specific algorithm within service/function
•	e.g. The departures and  arrivals JComboBox and confirmation JButton are displayed to the screen after a destination Java2sAutoComboBox state change for aesthetics.

**a) Customer**
b) Date of the code: 06-22-2019
c) Programmer's name: Pia Wetzel
d) Brief  description of the class/service/function
This class allows for the creation of Customer objects and contains attributes relevant to passengers/customers of an airline
e)  Any important data structure in class/functions 
N/A
f)  choice of a specific algorithm within service/function
            e.g. choosing quick sort rather than bubble sort etc.
N/A

**a) Manager**
b) Date of the code: 06-22-2019
c) Programmer's name: Pia Wetzel
d) Brief  description of the class/service/function
This class allows for the creation of Manager objects and contains a 
Method performing manager pin verification
e)  Any important data structure in class/functions 
N/A
f)  choice of a specific algorithm within service/function
            e.g. choosing quick sort rather than bubble sort etc.
N/A

**a) SQLConnectionManager**
b) Date of the code: 06-22-2019
c) Programmer's name: Pia Wetzel
d) Brief  description of the class/service/function
This class centralizes mySQL database connections and queries needed to generate reports
e)  Any important data structure in class/functions 
Vectors of type customer (Vector<Customer> someName)
f)  choice of a specific algorithm within service/function
            e.g. choosing quick sort rather than bubble sort etc.
N/A


**a) SchedulerStart**
b) Date of the code: 06-23-2019
c) Programmer's name: Pia Wetzel (and auto-generated Window-Builder code)
d) Brief  description of the class/service/function
Class that contains UI elements and methods that directly interact with UI
e)  Any important data structure in class/functions 
Vectors of type customer (Vector<Customer> someName, 
Maps of type <String, Manager> (Map <String, Manager> someName)
f)  choice of a specific algorithm within service/function
            e.g. choosing quick sort rather than bubble sort etc.
N/A











## Validation





### Chapter 5.  Testing


 
#### 5.1 Introduction


###### a)  Purpose 
The purpose of this document is to discover defects in the application  and to provide a quality product with a maintained and rigorous detailed report of any defects found during development.

Software Engineering Summer 2019 
The Explorers
Felicia Aubert 
Pia Wetzel
Mario Zarco
This document was created entirely by Felicia Aubert.

###### b)  Definitions, Acronyms or Abbreviations
	LIP’s - Linearly Independent Paths
	
###### c) References
	[1] Alder, Gaudenz, and David Benson. “Free Flowchart Maker and Diagrams Online.” Flowchart Maker & Online Diagram Software, JGraph Ltd., www.draw.io/.

###### d) Overview 
 This document shows the white box test of getAByeTime in the Class DestinationList. It contains the source code, flow chart, and the LIPS. Six test cases were performed and of the six half of them failed. Validation of parameters will be required in this code segment.





#### 5.2  Module Testing

###### a) Module name: getAByeTime 
**in Class DestinationList**
![Code Segment](figures/code-segment.png?raw=true "Code Segment")[1]


###### b) Independent Path Testing
 **Flow Graph**
![Flow Graph](figures/flow-graph.png?raw=true "Flow Graph")[1]

Edges = 15 Nodes = 11 15-11+2 = 6


###### c) LIPS
![Linearly Independent Paths](figures/LIPS.png?raw=true "Linearly Independent Paths")[1]


###### d) TestCases

**Test Case Path 1:**
1-3-4-10-11
Parameter String[] times contains no elements
Parameter double time is >= 10/60 ~.167

Inputs:
1.	times = {}
time = .167

Expected Value;
1.	{}

Test Results:
1.	{}

Conclusion:
Pass


**Test Case Path 2:**
1-2-3-4-10-11
Parameter String[] times contains no elements
Parameter double time is <= 10/60 ~.167

Inputs:
1.	times = {}
	time = 0.0
2.	times = {“00:00}
time = 0.0
3.	times = {“00:00}
time = 0.166
4.	times = {“00:00}
time = 0.1666666666666666
5.	times = {“00:00}
time = 0.16666666666666666
6.	times = {“00:00}
time = -0.1


Expected Value;
1.	{}
2.	{“00:00”}
3.	{“00:09”}
4.	{“00:09”}
5.	{“00:09”}
6.	{“00:0-6”}

Test Results:
1.	{}
2.	{“00:00”}
3.	{“00:09”}
4.	{“00:09”}
5.	{“00:10”}   //This is a precision error. 
6.	{“00:0-6”}

Conclusion:
Fail - 
The precision is ‘close enough’ for our purposes.
Need validation for positive input on parameter time




**Test Case Path 3:**
1-3-4-5-6-8-10-11
Parameter String[] times contains 1 element
Parameter double time has a decimal value >= 10/60 ~.167 
The whole number part of time plus the integer value of the first two characters in the element in string when added are x and 10 < x < 23

Inputs:
1.	times = {“10:00”}
time = .167
2.	times = {“0:00”}
	Time = .167
3.	times = {“:00”}
time = .167
4.	times = {“”}
time = .167
   

Expected Value;
1.	{“10:10”}
2.	Program Crash - Undetermined Behavior
3.	Program Crash - Undetermined Behavior
4.	Program Crash - Undetermined Behavior

Test Results:
1.	{“10:10”}
2.	{“10:10”}
3.	{“04:10:}
4.	Program Crash

Conclusion:
Fail - needs to have input validation for each string - we expect the format “00:00”, and need to make sure that our input matches our expected format.



**Test Case Path 4:**
1-3-4-5-6-8-9-10-11
Parameter String[] times contains 1 element
Parameter double time has a decimal value >= 10/60 ~.167 
The whole number part of time plus the integer value of the first two characters in the element in string when added are x and x < 10

Inputs:
1.	times = {“00:00”}
time = 0.167
2.	times = {“09:00”}
time = 0.167
3.	times = {“9:00”}
time = 0.999
4.	times = {“00:00”}
time = 9.9999
5.	times = {“09:00”}
time = 0.99999999999999999
6.	times = {“00:00”}
time = 9.99999999999999999


Expected Value;
1.	{“00:10”}
2.	{“09:10”}
3.	{“09:59”}
4.	{“09:59”}
5.	{“09:59”}
6.	{“09:59”}

Test Results:
1.	{“00:10”}
2.	{“09:10”}
3.	{“09:59”}
4.	{“09:59”}
5.	{“10:00”}
6.	{“10:00”}

Conclusion:
Pass
Despite Expected behavior != Results
Function is rounding up properly during conversion to int for minutes and the value is reasonable



**Test Case Path 5:**
1-3-4-5-6-7-6-8-10-11
Parameter String[] times contains 1 element
Parameter double time has a decimal value >= 10/60 ~.167 
The whole number part of time plus the integer value of the first two characters in the element in string when added are x and x > 23

Inputs:
1.	times = {“23:00”}
time = 1.167
2.	times = {“01:00”}
time = 23.167
3.	times = {“12:00”}
time = 12.167
4.	times = {“23:00”}
time = 97.167
5.	times = {“1:00”}
time = 23.167

Expected Value;
1.	{“00:10”}
2.	{“00:10”}
3.	{“00:10”}
4.	{“00:10”}
5.	Program Crash - Unexpected Behavior

Test Results:
1.	{“00:10”}
2.	{“00:10”}
3.	{“00:10”}
4.	{“00:10”}
5.	{“19:10”}

Conclusion:
Pass
Validation issue discovered in previous Test Case (5)



**Test Case Path 6:**
1-3-4-5-6-8-10-4-5-6-8-10-11
Parameter String[] times contains 2 elements
Parameter double time has a decimal value >= 10/60 ~.167 
The whole number part of time plus the integer value of the first two characters in the elements in the string when added are x and 10 < x < 23

Inputs:
1.	times = {“10:00”, “11:00”}
time = .167
2.	times = {“10:00”, “11:00”, “12:00”, “13:00”, “14:00”, “15:00”, “16:00”, “17:00”, “18:00”, “19:00”, “20:00”, “21:00”, “22:00”, “23:00”, “24:00”, “25:00” }
time = .167
3.	times = {“10:00”,  {} }
time = .167



Expected Value;
1.	{“10:10”, “11:10”}
2.	{“10:10”, “11:10”, “12:10”, “13:10”, “14:10”, “15:10”, “16:10”, “17:10”, “18:10”, “19:10”, “20:10”, “21:10”, “22:10”, “23:10”, “00:10”, “01:10” }
3.	Uninitialized Value - Program Crash

Test Results:
1.	{“10:10”, “11:10”}
2.	{“10:10”, “11:10”, “12:10”, “13:10”, “14:10”, “15:10”, “16:10”, “17:10”, “18:10”, “19:10”, “20:10”, “21:10”, “22:10”, “23:10”, “00:10”, “01:10” }
3.	Crash

Conclusion:
Fail
Need to check for valid element before dereferencing

###### c) Black Box Testing
 	TBD
 
 
 
 
 
 
#### 5.3 Validation Testing
TBD












## Phase 6: Operation





### Chapter 6 User Manual



#### 6.1. Introduction

###### a) Purpose 
	
	The purpose of this document is to provide a reference for users to install, run, and understand the system.

Software Engineering Summer 2019 
The Explorers
Felicia Aubert 
Pia Wetzel
Mario Zarco 
•	This document was completed in its entirety by Mario Zarco
	
	
###### b)  Definitions, Acronyms or Abbreviations
•	N/A
###### c)  References
•	N/A
###### d)  Overview 
This document shows the performed functionality requirements in images that pertain to interacting with the software.

 
 
 
#### 6.2. Hardware Configuration
•	The software requirements are minimal with the use of either an AMD or Intel CPU. Normal entry devices such as mouse and keyboard.
 
 
 
#### 6.3. System Parameters
•	N/A
 
 
 
#### 6.4. Operation Procedure
•	MySQL database needs to be connected for functionality or else the software connections will return an error.
 
 
 
#### 6.5. Demonstration
  	Show your working system.
  	Select any one requirement (feature) and execute it from start to the end.
  	Attach screen dumps for that requirement.
 


 	**a) Start-up screen to enter the UI**
 
![Start-up](figures/startup.png?raw=true "Start-up")





	**b) After clicking “New Reservation”,	**
	the opening screen should display entry fields for creating the reservation which includes Name, Luggage, Destination, Departure, Arrival, MealPlan, and seats available. 
	The name for this passenger is Tanka Tanner
	Luggage option set to NO or 0 for boolean
	Departure is 17:00 or 5:00P.M.
	Arrival is 5:05 P.M.
	The seats D70 and D71 have been picked with arbitrary meal plan values.
 

![Make a Reservation UI](figures/reserve.png?raw=true "UI")



	**c) After Reservation confirmation**
		The manager can access the data that passengers have entered including Tanka Tanner.
 

![Manager UI](figures/manager.png?raw=true "UI")




	**d) Manager Access **
		The manager can access the information that all passengers have entered from the database.
 

![Data UI](figures/db.png?raw=true "UI")




	**e) To Modify or Cancel**
		The passenger can then enter their own unique confirmation number to cancel or modify an existing reservation.


![Modify UI](figures/mod.png?raw=true "UI")





	**f) Mod or Cancel **
	The confirmation number displays the information saved and can either be canceled or “changed” which is just a cancel and redirect. Tanka has chosen to cancel.
 
![Cancel UI](figures/cancel.png?raw=true "UI")






	**g) Manager Report** 
		The manager’s report should reflect the change that Tanka made to the no longer existing reservation. 
 


![Report UI](figures/report.png?raw=true "UI")



