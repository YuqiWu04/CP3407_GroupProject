
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



