
The following are some components of the project that i reviewed:

Documentation: requirements.md for clarity, completeness, and unambiguous specifications.
Code: gallery.html and associated JavaScript for functionality, maintainability, accessibility, and adherence to best practices.
Static Analysis: Ran the project through SonarQube to identify code smells, potential bugs, and maintainability issues.

Scope:
Checked that requirements are complete, clear, and testable.
Verified that the gallery displays images correctly, filtering works, lightbox opens/closes properly, and UI is accessible.
Used SonarQube to detect undeclared variables, inline function issues, and semantic/HTML best practice violations.

2. Types of Issues Found
A. Documentation Issues
Issue	Description	Location / Reference
Ambiguous visual requirement	FR1.3 “All images should look good visually” is subjective.	requirements.md
Missing accessibility specifics	NFR3.3 only states “accessible to all users,” no WCAG guidance.	requirements.md
Browser compatibility not precise	“Modern browsers” is vague.	requirements.md

B. Code Issues – Manual Review
Issue	Category	Description	Location	Recommendation
Undeclared loop variable	Error	i used without let, creating global variable	gallery.html JS, line ~120	Declare: for (let i = 0; i < filteredImages.length; i++) {...}
Inline function handlers	Unclear Logic	Inline anonymous functions for each gallery item click	gallery.html JS, line ~130	Use named functions for maintainability and reusability
Non-semantic HTML / Accessibility	Best Practice Violation	<div> and <p> used for captions instead of <figure> + <figcaption>; filter buttons lack ARIA roles	gallery.html HTML, line ~105	Use semantic elements and ARIA attributes

C. Code Issues – SonarQube Findings
Issue	Category	Description	Significance	Agree?
Undeclared variable	Maintainability	Loop variable i is global	Can cause runtime conflicts and bugs	Yes
Inline anonymous functions	Maintainability	Reduces code clarity and reusability	Makes testing and maintenance harder Partially
Accessibility / Semantic HTML	Best Practice	<div> instead of <figure>; missing ARIA roles	Impacts screen readers and accessibility	Yes


Notes:
SonarQube confirmed several issues found manually and flagged additional maintainability concerns.
The automated tool was particularly useful for global variable detection and highlighting semantic violations.


3. Reflection on Your Static Testing Process
What worked well:
Manual review effectively identified logic issues, UI functionality, and accessibility gaps.
SonarQube complemented this by catching maintainability issues and code smells automatically.
Combining manual and automated review provided a thorough assessment.


What was difficult or challenging:
Evaluating accessibility manually required understanding ARIA roles and semantic HTML.
Differentiating between critical issues and minor code smells in SonarQube needed judgment.
Some vague requirements in requirements.md made traceability harder.


Comparison of Manual Review vs. SonarQube:
Manual review was better at assessing UI, UX, and context-specific logic.
SonarQube excelled at detecting undeclared variables, inline function issues, and potential maintainability problems.
Some warnings (e.g., small style issues) were less critical and could be considered false positives in the context of this small project.
