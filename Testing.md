# Login page and register page intergration  
## Description:   
Users can click the login button to successfully jump to the registration page, and fill in the empty email will pop up a reminder, the mailbox password error will pop up an error!  
## Black Box Testing:  
<img width="1512" height="791" alt="testing_login1" src="https://github.com/user-attachments/assets/cf45ea8e-fff8-490f-9de7-a772cd86f399" />   

## White Box Testing:    

### A. Red Test(Fail)   
<img width="574" height="179" alt="截屏2025-07-30 09 49 56" src="https://github.com/user-attachments/assets/ab774957-778e-412a-af63-f39cbc4975fb" />    

### B. Green Test(Passing)  
<img width="1120" height="405" alt="截屏2025-07-30 10 01 13" src="https://github.com/user-attachments/assets/9be9984b-40a9-4ba5-801d-96a6ce7814f8" />   

# Quiz page testing   
## Description:   
1. Question Randomization: No matter how many questions are in the list, it will disrupt the order and will not accidentally lose or duplicate questions.   
2. Week Recognition: It reads the exact week the user wants to work on from the browser's address bar (URL), and also automatically uses the default value if it's not in the address bar   or if it's entered incorrectly, avoiding the program from reporting errors.   
## Black Box Testing:   
<img width="1073" height="696" alt="截屏2025-07-31 15 43 20" src="https://github.com/user-attachments/assets/775adfcb-907b-4ad7-87a2-d78550235375" />     

## White Box Testing: 
shuffleArray method.  
1. Ensure that the number of elements of the array remains unchanged and the contents are not lost after shuffling.  
2. Make sure that the original array will not be modified (not in-place).  
3. can correctly handle empty array input.  
getWeek method.  
1. If the URL has a legal week parameter, return the corresponding value.    
2. If the URL has no week parameter, return 0 (default).   
3. If the week parameter of the URL is not a number, return 0.  
### A. Red Test(Fail)   

<img width="740" height="328" alt="截屏2025-07-31 14 43 57" src="https://github.com/user-attachments/assets/25dc882a-ae2c-43ac-80b8-bba445ea434f" />   
 
### B. Green Test(Passing)    
<img width="830" height="273" alt="截屏2025-07-31 15 45 27" src="https://github.com/user-attachments/assets/33db355d-2529-4138-a207-7e4fcc3a7cbd" />  

# Quiz editor page testing    
## Description:    
1. Query title:     
Verify that when I request a title for week 1, the service sends a “filter by week” query to the backend and returns a list of titles with the correct number and content.  
2. Add Title:   
Verify that when I add a new title, the service will first look up the number of existing titles and then submit a request for adding a new title with the "next ID".  
3. Update Title:   
Verify that when I update the title content for a given document ID, the update operation is initiated for the correct document.  
4. Delete Topic:   
Verify that when I delete a topic with the specified document ID, the delete operation is initiated on the correct document.  
## Black Box Testing:    
<img width="1068" height="736" alt="截屏2025-07-31 17 00 28" src="https://github.com/user-attachments/assets/aee69bc2-2df4-4270-a0c8-d12be2a9d30c" />  
<img width="1081" height="624" alt="截屏2025-07-31 17 01 13" src="https://github.com/user-attachments/assets/33fa4209-9b16-4d3d-b806-42d1bbb4066b" />  
 
## White Box Testing:   
1. every internal function call (collection/where/query/getDocs/addDoc/updateDoc/deleteDoc) is called once as expected and with the correct arguments.   
2. fetchQuestions maps correctly to the docs array (length, content, autocomplete ID).   
3. the automatic nextId calculation logic in addQuestion generates id=2 at size=1.   
4. updateQuestion and deleteQuestion's document reference construction and call chain are correct.   
### A. Red Test(Fail)    
<img width="680" height="300" alt="red" src="https://github.com/user-attachments/assets/a1772bc7-7459-4478-b95d-88cd84359e17" />   

### B. Green Test(Passing)    
<img width="1123" height="306" alt="green" src="https://github.com/user-attachments/assets/a371944d-4db0-4fbe-8fb1-4fa157d58503" />    

# Student record page testing    
## Description:  
There is a “Student Information Management” functional module that allows you to retrieve, add, update, delete and search student records by name.  
## Black Box Testing:  
<img width="1077" height="492" alt="截屏2025-07-31 20 07 37" src="https://github.com/user-attachments/assets/e03863f6-b257-4624-a0a5-0f9a32ed53fe" />  

## White Box Testing:    
1. fetchStudentRecords   
Tests the process of fetching all student information from the database using fetchStudentRecords and ensures that the data structure returned by Firestore is correctly parsed and converted to an array of standard objects.  
2. Data Addition Functionality   
Uses addStudentRecord to test the process of adding a new student record to the database and verifies that Firestore's add interface is called correctly and returns the newly generated document ID.   
3. Data Updating Functionality   
Uses updateStudentRecord to override and update the logic for a given student record, asserting that the update method calls the Firestore with the correct parameters. The update method calls the underlying interface with the correct parameters.     
4. data deletion functionality   
Validates the process of deleting a student record by ID using deleteStudentRecord to ensure that the corresponding Firestore method is triggered correctly. 5. conditional query     functionality fetchStudentRecord is used to retrieve a student record by ID.    
5. Conditional Query Functionality   
Uses fetchStudentByName to check the operation of querying student records by name, and mocks the query conditions and results to ensure that the filtering logic is correct.  
### A. Red Test(Fail)    
<img width="1145" height="274" alt="red" src="https://github.com/user-attachments/assets/156ff0b7-b2f3-4f2c-99ab-e0ec354d80cf" />  

### B. Green Test(Passing)   
<img width="855" height="375" alt="green" src="https://github.com/user-attachments/assets/7ba9ae2f-ab63-4fb3-985d-f23fd9f6e3f9" />    


# Teacher record page testing 
## Description:  
As a user on the teacher's end, I'm concerned about automatically loading the corresponding student's data and grades upon login.  
	1. View students' quiz results by weekly period (including weekly scores, number of answers, accuracy, time spent, etc.).  
	2. Switch between different weeks through the drop-down menu to filter the data for the time period you want to focus on.  
	3. charts to visualize performance trends, such as line graphs to show changes in accuracy, bar graphs to show average time spent, etc.  
	4. View students' weekly activity (number of questions done, etc.) and total number of questions done.  
	5. view the class leaderboard to know the student's position among his/her classmates (top 5).  
	6. view the student's basic information (name, class, etc.).  
	7. Calendar function can display current date or active day, which enhances the information richness and interface beauty.  
	8. Support one-click logout, login authentication, exception handling and other common operations (e.g. there will be a friendly prompt if the student is not found).  
 ## Black Box Testing:  
<img width="851" height="496" alt="截屏2025-07-31 21 01 54" src="https://github.com/user-attachments/assets/cfa9b95c-90fa-4d1f-9f05-d4f98b3be425" />  
<img width="1255" height="731" alt="截屏2025-07-31 21 02 21" src="https://github.com/user-attachments/assets/3a3d88fb-53d9-4b0b-b408-5c715dbe3fd6" />  
<img width="371" height="306" alt="截屏2025-07-31 21 02 36" src="https://github.com/user-attachments/assets/d65e5bba-1834-4ace-8342-26a2e6e3aff5" />  
<img width="1025" height="358" alt="截屏2025-07-31 21 02 49" src="https://github.com/user-attachments/assets/a8640d72-2c8e-4c66-a35a-d8ad18d7567b" />  
 
## White Box Testing:      
	1. Data pulling and processing: Use Firebase Firestore to pull students' quiz scores, question weeks, user information, all students' quiz data, etc., and locate the current students according to the mailbox parameters, and automatically organize all weekly data.  
	2. state and data management: page state is maintained by multiple variables (questionWeeks, allAttempts, userMap, studentUid, studentQuizzes, filteredQuizzes, etc.), which supports efficient data filtering and page refreshing.  
	3. Event-driven Refresh: Automatically refreshes the content of each module by listening to events such as weekly selection, page loading, logout, etc. to ensure that the page is always synchronized with the data.  
	4. Visual rendering: Based on Chart.js and its plug-ins, it realizes a variety of charts (accuracy line, time-use bar, efficiency mix, activity line), and automatically destroys and rebuilds the charts for each data change, avoiding memory leakage and chart overlapping.  
	5. Modular page rendering: each functional area (weekly dropdown, calendar, results overview, active table, leaderboard) are independently encapsulated rendering method, high reusability and maintainability.  
	6. Exception and Boundary Handling: UI pockets are provided for cases such as no data, no student found, no available quiz, etc. to ensure that users will not see errors or dead pages.  
	7. authentication and security: onAuthStateChanged ensures secure access to the page and supports one-click logout.  
	8. Performance and Interaction Optimization: Re-render the functional areas only when needed to reduce useless DOM operations.    
 ### A. Red Test(Fail)    
<img width="872" height="352" alt="red" src="https://github.com/user-attachments/assets/5898bfba-b02b-4459-a04c-282ceab6623c" />  

 ### B. Green Test(Passing)    
<img width="813" height="377" alt="green" src="https://github.com/user-attachments/assets/ca9bb5f9-8599-48d6-a91f-e0b6393b20ad" />  

# Main AR function page testing  
## Description:  
Functions to be tested:  
	1.camera.test.ts:Launch the camera to capture a frame of the picture to segment  
	2.segmentation.test.ts and segmentationService.test.ts:Launch a segmentation request and get the result by segmentationService and segment  
 	3.legoBoardAnalyzer.test.ts:Utilize the segmentation result to analyze color, position and corresponding component of internet concepts of the lego blocks and return an array conclude all the information  
  	4.legoColors.test.ts and colorMap.test.ts:These two modules are used by the analyzer to match the corresponding lego color and internet concepts componets  
   	5.ui.test.ts:Test the ui modules  
    	6.vision.test.ts:Test the visualization workflow  

## Black Box Testing:  
<img width="1512" height="982" alt="cb378ab9c6a8226413b1e5c1ab44565" src="https://github.com/user-attachments/assets/bb386f10-b52f-4633-9a7d-bcc48c889bec" />
## White Box Testing:  
### Red Test(Fail):  
<img width="1294" height="2618" alt="image" src="https://github.com/user-attachments/assets/a1fb6598-af30-4d35-9e7e-72431c3fa27b" />  
### Green Test(Passed):  
<img width="513" height="670" alt="image" src="https://github.com/user-attachments/assets/036cd966-1399-4953-b344-b7557bb7be10" />  
