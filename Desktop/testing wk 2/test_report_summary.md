Functional Testing Report — Note-Taking App
👤 Student Information

Full Name: Victor Mutinda
Cohort: July 2025
Date: October 10, 2025

🧪 What I Tested
Test Type	Description
Unit Test	Tested the saveNote() function for correct behavior and input validation.
Integration Test	Verified that saving a note updates the UI and that the note appears correctly in the notes list.
System Test	Simulated full note lifecycle: create edit  delete, checking data consistency and UI updates.
🐛 Bugs / Issues Identified
Type	Description
Unit	Notes are saved even when the title field is empty.
Integration	After saving, the note sometimes does not appear in the UI immediately.
System	The edit function removes the note instead of updating its content.
UI / UX	There is no visual confirmation or success message after saving or deleting a note.
Accessibility	Input fields for note title and content have no accessible labels for screen readers.

GitHub Issues Filed:

Issue #1 – Empty Title Still Saves Note
 (https://github.com/PLP-Database-Design/wk-2-VictorMutinda8-1/issues/1#issue-3502139917)

Issue #2 – Edit Button Deletes Note Instead of Updating
 (https://github.com/PLP-Database-Design/wk-2-VictorMutinda8-1/issues/2#issue-3502145964)

Issue #3 – No Confirmation Message After Save/Delete
(https://github.com/PLP-Database-Design/wk-2-VictorMutinda8-1/issues/3#issue-3502152425)

💬 Reflection

1. What did you learn from testing this app?
I learned how to break down app functionality into smaller testable parts and how to apply unit, integration, and system testing together to verify overall performance. I also gained practical experience using Jest to simulate DOM events and validate UI behavior.

2. Which part of the app had the most bugs or problems?
The edit function had the most issues—it often deleted the note instead of updating it. There were also problems with input validation and feedback for users.

3. What testing strategy worked best for you?
Starting with manual exploratory testing helped identify visible problems quickly. Then, writing Jest tests for functions like saveNote() confirmed where the code logic was failing.

4. What was challenging during this lab?
Setting up Jest for DOM-based tests was tricky, especially mocking HTML elements and handling event listeners. Once configured, running automated tests became much smoother.