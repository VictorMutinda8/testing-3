I reviewed the following components of the project:

Documentation (requirements.md): I examined the file for clarity, completeness, and consistency. My goal was to ensure that all functional and non-functional requirements were clearly defined, measurable, and testable. I also looked for ambiguities, missing details, and accessibility considerations.

Code (gallery.html and associated JavaScript): I performed a manual static code review of the HTML and JavaScript to identify runtime errors, unclear logic, and violations of best practices. This included examining the gallery display, filtering functionality, lightbox behavior, and overall maintainability of the code.

Static Analysis (SonarQube): I ran the project through SonarQube to automatically detect code smells, potential bugs, maintainability issues, and best practice violations. This helped to complement the manual review by identifying hidden problems that may not be obvious through visual inspection.

2. Types of Issues Found
Documentation Issues
During the review of requirements.md, I identified several issues:

Ambiguous Visual Requirement: The functional requirement stating that “All images should look good visually” is subjective. It does not specify measurable criteria, such as resolution, size, or aspect ratio. This ambiguity makes it difficult to test whether the requirement is met. A better approach would be to define precise image dimensions or minimum resolution.

Incomplete Accessibility Requirements: The non-functional requirements mention that the gallery should be accessible, but there is no reference to WCAG standards or guidance for ARIA roles. Accessibility considerations are critical for users with disabilities, and the requirements should explicitly state how accessibility will be achieved.

Browser Compatibility Not Specific: The requirement stating that the gallery must work on “modern browsers” is vague. Modern browsers change frequently, and without specifying versions or platforms, it’s unclear what should be supported. Clarifying this with specific browser versions would make the requirement testable.

Manual Code Review Issues
Through a line-by-line review of gallery.html, I found the following issues:

Undeclared Loop Variable (Error):
In the JavaScript code, the loop iterating over images uses for (i = 0; i < filteredImages.length; i++) { ... } without declaring i with let or var. This makes i a global variable, which can lead to conflicts with other parts of the code or cause unexpected behavior.
Improvement: Declare the loop variable explicitly: for (let i = 0; i < filteredImages.length; i++) { ... }.

Inline Anonymous Functions (Unclear Logic):
Each gallery item has an inline function attached to its click event: galleryItem.addEventListener('click', function() { openLightbox(img.src); });. While this works, it reduces code maintainability and makes testing or reusing the code difficult.
Improvement: Use a named function and attach it to all items, improving readability and maintainability.

Non-Semantic HTML and Accessibility Issues (Best Practices):
The gallery uses <div> and <p> for image captions instead of semantic <figure> and <figcaption> elements. Additionally, filter buttons do not have ARIA roles or proper labels, which makes the gallery less accessible to screen readers.
Improvement: Use semantic HTML by wrapping each image in a <figure> element with a <figcaption> for the caption and add ARIA attributes to interactive elements like buttons.

SonarQube Findings

After running SonarQube static analysis on gallery.html, the following key issues were flagged:

Undeclared Variable i: SonarQube highlighted that i is used without declaration, creating a global scope issue. This matches the manual review finding and is a critical maintainability and reliability concern.

Inline Anonymous Functions: The tool flagged inline event handlers as a maintainability issue. Repeated anonymous functions increase code duplication and reduce clarity, making the code harder to test and modify.

Accessibility and Semantic HTML Violations: SonarQube detected non-semantic markup for captions and missing ARIA attributes on interactive elements. This aligns with best practice violations found during manual review and can negatively impact users relying on assistive technologies.

Reflection on SonarQube Findings:
I agree with all the assessments made by SonarQube. It helped highlight issues like the global variable and inline functions that could easily be overlooked during a manual review. SonarQube is especially useful for detecting maintainability issues and potential hidden bugs, complementing the manual review which is better at assessing UI and user experience.

3. Reflection on the Static Testing Process

What worked well:
Manual review was effective in identifying UI/UX issues, logic errors, and accessibility gaps, while SonarQube was invaluable for uncovering undeclared variables, inline function maintainability issues, and code smells. Using both approaches provided a thorough understanding of the project’s strengths and weaknesses.

Challenges faced:
Evaluating accessibility compliance manually was challenging because it required knowledge of ARIA roles and semantic HTML. Additionally, some requirements in requirements.md were vague, making it difficult to determine if they were testable. Distinguishing critical issues from minor warnings in SonarQube required judgment.

Comparison of Manual Review and SonarQube:

Manual review excelled at finding context-specific UI and functionality problems.
SonarQube effectively flagged hidden maintainability issues and potential bugs that may not break functionality immediately but could cause future problems.
Some SonarQube warnings, such as minor style issues, were less critical and could be considered false positives in this small project context.

4. Conclusion

The combination of manual code review, documentation review, and SonarQube analysis provided a comprehensive evaluation of the project. Key areas for improvement include:

Declaring loop variables and avoiding implicit globals

Replacing inline anonymous functions with named functions for maintainability

Using semantic HTML and adding proper ARIA roles to improve accessibility

Clarifying ambiguous requirements and defining measurable non-functional specifications

By addressing these issues, the gallery will become more maintainable, accessible, and reliable, while the requirements will become clearer and testable.
