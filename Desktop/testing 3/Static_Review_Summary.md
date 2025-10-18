🧪 Static Review Summary
For this assignment, I reviewed the following components:
Documentation (requirements.md): I examined the document for clarity, completeness, and consistency. I checked whether functional and non-functional requirements were clearly defined, measurable, and testable, and identified ambiguities or missing accessibility considerations.

Code (gallery.html and associated JavaScript): I performed a manual static code review to identify runtime errors, unclear logic, and violations of best practices. This included examining the gallery display, filtering functionality, lightbox behavior, and overall maintainability.

Static Analysis (SonarQube): I ran the project through SonarQube to detect code smells, potential bugs, maintainability issues, and best practice violations. This complemented the manual review by identifying hidden problems that may not be obvious by inspection.

2. Types of Issues Found
Documentation Issues

Ambiguous Visual Requirement:
Where: requirements.md
Problem: "All images should look good visually" is subjective and not measurable.
Improvement: Specify minimum resolution or image dimensions.

Incomplete Accessibility Requirements:
Where: requirements.md
Problem: Accessibility is mentioned, but no guidance on ARIA roles or WCAG standards.
Improvement: Include specific accessibility standards to ensure compliance.

Browser Compatibility Not Specific:
Where: requirements.md
Problem: "Modern browsers" is vague and untestable.
Improvement: Specify exact browsers and versions to support.
Manual Code Review Issues

Undeclared Loop Variable (Error):
Where: gallery.html JavaScript, loop over images.
Problem: for (i = 0; i < filteredImages.length; i++) { ... } creates a global variable i.
Improvement: Use let i = 0 to declare the loop variable.

Inline Anonymous Functions (Unclear Logic):
Where: galleryItem.addEventListener('click', function() { openLightbox(img.src); });
Problem: Reduces maintainability and reusability.
Improvement: Use a named function for event handling.

Non-Semantic HTML and Accessibility Issues (Best Practices):
Where: HTML uses <div> and <p> for images/captions. Buttons lack ARIA roles.
Problem: Reduces accessibility and semantic meaning.
Improvement: Use <figure> and <figcaption> for images and add ARIA attributes for interactive elements.

SonarQube Findings
Undeclared Variable i:
Confirmed global variable issue. Matches manual review.
