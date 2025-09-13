# Bug Report - Jira Cloud API

**Detection Date:** September 11, 2025  
**Environment:** Jira Cloud (liudmylal000b.atlassian.net)  
**Detected by:** Postman Automated Tests  
**Test Status:** 115/117 passed (98.3% success rate)  

---

## Bug #1: Silent Modification of Future Dates

### Description
The API automatically and silently modifies future dates entered by users, compromising data integrity.

### Reproduction Steps
1. Create a task via API with `duedate: "2048-12-31"`  
2. Execute GET on the created task  
3. Check the `duedate` field in the response  

### Expected Result
- The API should preserve the original date `2048-12-31`  
- OR return a validation error during request creation if the date is invalid  

### Actual Result
The API silently changes the date from `2048-12-31` to `1948-12-31` without notifying the user.  

### Evidence
- **Test name:** "Verify Far Future Due Date Task" – FAILED  
- **Test URL:** GET `/rest/api/3/issue/JQL1389-20`  

### Manual Confirmation
The bug was confirmed manually: the date `12/31/2048` was automatically changed to `12/31/1948` during manual entry as well.  

**Attachment:**  
- [01_manual_due_date_issue.mp4](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/attachments/01_manual_due_date_issue.mp4)

### Impact
- **Priority:** Medium  
- **Category:** Data Integrity  
- **Consequences:** Users may lose control over entered dates, which could lead to project planning errors  

---

## Bug #2: Orphaned Subtasks After Task-to-Epic Conversion

### Description
During Task-to-Epic conversion, subtasks may become orphaned (without proper parent reference), breaking data hierarchy.  

### Reproduction Steps
1. Create a Task with at least one Subtask  
2. Change the Task type to Epic via PUT API  
3. Check Subtask status – verify if it maintains a proper parent reference  

### Expected Result
- The conversion should be blocked (400 error)  
- OR the Subtask should be automatically converted to a Task  
- OR the Subtask should maintain the correct reference to the new Epic  

### Actual Result
The Subtask remains in the system without a proper parent reference after the Task-to-Epic conversion.  

### Evidence
- **Test name:** "Check Subtask After Parent Epic Conversion" – FAILED  
- **Test URL:** GET `/rest/api/3/issue/JQL1389-10`  
- **Response details:** Subtask exists but has an incorrect parent field  

**Attachments:**  
- [02_api_response_missing_parent.png](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/attachments/02_api_response_missing_parent.png)  
- [03_jira_gui_missing_parent.png](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/attachments/03_jira_gui_missing_parent.png)

### Additional Observations
A business logic inconsistency was detected:  
- DELETE Task with subtasks requires the `deleteSubtasks` parameter (400 error)  
- UPDATE Task with subtasks → Epic succeeds without warning (204 success), leaving orphaned subtasks  

### Impact
- **Priority:** Medium  
- **Category:** Hierarchy Integrity  
- **Consequences:** Loss of hierarchical data integrity, potential issues with reporting and navigation  

---

## Technical Findings & Observations
- Labels are case-sensitive (Test ≠ test ≠ TEST) – behavior requires further analysis  
- Up to 1000 labels can be created on a task without error  
- Cannot directly create Epic → Subtask hierarchy (proper validation required)  
- Deleted project keys cannot be immediately reused (400 error)  

---

## Attachments Summary
1. [01_manual_due_date_issue.mp4](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/attachments/01_manual_due_date_issue.mp4) – Manual date change recording  
2. [02_api_response_missing_parent.png](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/attachments/02_api_response_missing_parent.png) – API response showing missing parent for subtask  
3. [03_jira_gui_missing_parent.png](https://github.com/LiudmylaBondarchuk/Portfolio/blob/master/api-tests/jira-tests/collection/results/bug-report/attachments/03_jira_gui_missing_parent.png) – Jira GUI screenshot showing subtask without parent
