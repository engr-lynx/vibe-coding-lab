# Vibe code a to-do list app using a minimal prompt. (2 iterations)

- Learning Goals: Demonstrate how there’s a myriad of possibilities.
- Instructions:
    1. Use the following prompt to build a to-do list app.

```
Your goal is to develop a functional to-do list application. This application should be built with a modern web technology stack (you can suggest a suitable one, e.g., React/Next.js for the frontend and Node.js/Express for the backend with a simple database).

The application should include the following typical to-do list features:

**Core Task Management:**

* **Task Creation:** Allow users to add new tasks with a title and optional description.
* **Task Listing:** Display all active tasks in a clear and organized manner.
* **Task Details:** Allow users to view the full details of a task, including its description.
* **Task Completion:** Provide a way to mark tasks as completed. Completed tasks should be visually distinct or moved to a separate view.
* **Task Editing:** Enable users to modify the title and description of existing tasks.
* **Task Deletion:** Allow users to remove tasks from the list.

**Organization and Prioritization:**

* **Due Dates:** Allow users to assign a due date to tasks.
* **Reminders:** (Stretch goal, can be a later addition) Implement a system for setting reminders for tasks with due dates.
* **Prioritization:** Provide a way to set a priority level for tasks (e.g., High, Medium, Low). The task list should be sortable by priority.
* **Categories/Tags:** Allow users to assign categories or tags to tasks for better organization and filtering.

**User Interface and Experience:**

* **Clean and Intuitive UI:** Design a user interface that is easy to navigate and use.
* **Persistence:** Ensure that the to-do list data is saved (e.g., using local storage for a simple client-side app or a database for a full-stack app) so it persists between sessions.

**Technical Considerations:**

* Structure the project with a clear separation of concerns (e.g., frontend, backend if applicable).
* Implement necessary API endpoints for managing tasks if building a full-stack application.
* Include basic error handling and input validation.
* Provide instructions on how to set up and run the application.

**Windsurf Specific Instructions:**

* Utilize Windsurf's capabilities for code generation and completion to speed up development.
* Leverage Windsurf's context awareness to understand the project structure and suggest relevant code modifications.
* If applicable, use Windsurf's multi-file editing features for making consistent changes across the codebase.
* Clearly indicate the chosen technology stack and explain the reasoning.
* Present the generated code and a summary of the implemented features.

Start by outlining the project structure and the main components needed for this application. Then, proceed with implementing the core task management features before adding organization and UI enhancements.
```
  1. Interact with and wait for Cascade to finish building.
  1. Deploy the app in your local dev environment.
  1. Repeat (a)-(c) outputting to a different project.
  1. Inspect both project code. Notice the differences.

# Check an app against a non-functional requirement.
- Learning Goals: Demonstrate trade-offs.
- Instructions:
  1. Setup and run SonarQube against both projects from (1).
```  
Setup and run SonarQube to be used to analyze the security of the code of the to-do list app. Specifically check for safety from cross-origin requests.
```
  1. Notice the differences in the findings.

# Modify an app to improve a non-functional requirement.
- Learning Goals: Demonstrate offloading decision-making.
- Instructions:
  1. Use the following prompt to modify both to-do list app.
```
You will modify the existing to-do list application to enhance its security by implementing Cross-Origin Resource Sharing (CORS).

Assume the to-do list application has a backend API (likely built with a framework like Express.js for Node.js, or similar for another language) that the frontend interacts with. The goal is to configure the backend to accept requests only from the origin(s) where the frontend is hosted.

**Current State:**

* An existing to-do list application with a frontend and a backend API.
* CORS is likely not configured on the backend, which might allow requests from any origin (a security risk).

**Goal:**

Implement CORS on the backend of the to-do list application to restrict access to the API from specified origins.

**Tasks:**

1.  **Identify the Backend Framework:** Determine the programming language and framework used for the backend API (e.g., Node.js with Express, Python with Flask/Django, etc.).
2.  **Install Necessary Libraries:** If the chosen framework requires a specific library for CORS (e.g., `cors` middleware for Express), add it to the project's dependencies.
3.  **Configure CORS Middleware:**
    * Integrate the CORS middleware into the backend application.
    * Configure the middleware to allow requests only from the specific origin(s) where the frontend is or will be hosted. This should ideally be configurable (e.g., via environment variables).
    * Configure allowed HTTP methods (e.g., GET, POST, PUT, DELETE, OPTIONS) that the frontend will use.
    * Configure allowed headers that the frontend might send.
4.  **Verify Implementation:** Briefly explain how to test if CORS is correctly configured, ensuring that requests from allowed origins succeed and requests from disallowed origins are blocked by the browser due to CORS policy.

**Windsurf Specific Instructions:**

* Analyze the existing codebase to identify the backend entry point and API routes.
* Suggest and implement the code changes necessary to add and configure CORS based on the identified backend framework.
* If installing a library is required, provide the necessary command (e.g., `npm install cors`).
* Clearly show the modified code files and explain the changes made to implement CORS.
* Outline any necessary configuration steps the user needs to take (e.g., setting environment variables for allowed origins).
```

  1. Run SonarQube against the updated code base.
```
Setup and run SonarQube to be used to analyze the security of the code of the to-do list app. Specifically check for safety from cross-origin requests.
```
  1. Notice the differences in the findings between this and (2).

# Vibe code a to-do list app using a detailed prompt.
- Learning Goals: Demonstrate the value of prompt engineering.
- Instructions:
  1. Use the following prompt to build a to-do list app.
```
Your task is to develop a secure to-do list web application with typical features. Security is a primary concern for this project, so Cross-Origin Resource Sharing (CORS) and robust input sanitization must be implemented from the initial development phase.

Choose a suitable modern web technology stack for both the frontend and backend (e.g., a framework like React/Vue/Angular for the frontend and Node.js/Express, Python/Flask/Django, or similar for the backend, with a relevant database technology). Clearly state the chosen stack and the reasoning behind its selection for a secure application.

The application should include the following typical to-do list features:

**Core Task Management:**

* **Task Creation:** Allow users to add new tasks with a title and optional description. **Input for both title and description must be sanitized on the backend before processing or storage.**
* **Task Listing:** Display all active tasks.
* **Task Details:** Allow users to view the full details of a task, including its description. **Ensure displayed data is properly escaped to prevent rendering malicious scripts.**
* **Task Completion:** Provide a way to mark tasks as completed.
* **Task Editing:** Enable users to modify the title and description of existing tasks. **Edited input must also be sanitized on the backend.**
* **Task Deletion:** Allow users to remove tasks from the list.

**Organization and Prioritization:**

* **Due Dates:** Allow users to assign a due date to tasks. **Validate and sanitize due date input.**
* **Prioritization:** Provide a way to set a priority level for tasks (e.g., High, Medium, Low). **Validate and sanitize priority input.**
* **Categories/Tags:** Allow users to assign categories or tags to tasks. **Sanitize tag/category input.**

**Security Measures (Integral to Development):**

* **Cross-Origin Resource Sharing (CORS):**
    * Implement CORS on the backend API from the start.
    * Configure CORS to *only* allow requests from the specific origin(s) where the frontend application is or will be hosted. Avoid using wildcard origins (`*`) in production.
    * Explicitly define the allowed HTTP methods (GET, POST, PUT, DELETE, OPTIONS) and headers required by the frontend.
    * Include necessary handling for CORS preflight requests (OPTIONS method).
* **Input Sanitization:**
    * Implement comprehensive input sanitization on the **backend** for all user-provided data before it is processed, stored in the database, or used in queries.
    * Sanitization should aim to neutralize potential injection attacks (e.g., XSS, SQL injection) by escaping or removing malicious characters or patterns.
    * Mention the specific sanitization library or techniques used for the chosen backend stack.
    * Implement input validation on the backend to ensure data conforms to expected types and formats, rejecting invalid input. While client-side validation is good for user experience, server-side validation and sanitization are critical for security.
* **Output Encoding:** Ensure that any user-generated content displayed on the frontend is properly encoded to prevent XSS vulnerabilities.

**Technical Implementation:**

* Structure the project with a clear separation of concerns (frontend and backend).
* Define and implement secure API endpoints for all to-do list operations, incorporating CORS and input handling.
* Set up a basic database or use local storage with proper data handling considerations for security.
* Include basic error handling and return appropriate error responses for invalid or unauthorized requests.
* Provide clear instructions on how to set up and run the application, including any necessary environment variables for CORS configuration.

**Windsurf Specific Instructions:**

* Utilize Windsurf's code generation, completion, and multi-file editing capabilities to build the application with the specified features and security measures.
* Leverage Windsurf's context awareness to ensure CORS and sanitization logic are correctly integrated into the relevant parts of the codebase (especially backend routes and data processing functions).
* Clearly present the generated code, highlighting the implementation of CORS configuration and input sanitization/validation.
* Explain the security considerations addressed by the implemented CORS and sanitization measures.
* Suggest how the user can further enhance the security of the application (e.g., authentication, more granular access control) as potential future steps.

Begin by outlining the project structure, defining the API endpoints with their expected inputs and outputs, and specifying how CORS and input sanitization will be integrated into these endpoints. Then, proceed with code generation and implementation, focusing on building a secure foundation for the to-do list functionality.
```
  1. Notice the difference between this prompt and the one from (1).
  1. Run SonarQube against the updated code base.
  1. Notice the differences in the findings between this and (2).

# Add a feature to an existing app.
- Learning Goals: Demonstrate how to make vibe coding part of a bigger SW engineering process.
- Instructions:
  1. Use the following prompt to add a new feature to the to-do list app from (4).
```
The goal is to introduce a separate area or flow within the application where users can quickly record transient thoughts without the immediate need to structure them as full tasks with due dates, priorities, etc. Later, they should be able to review these thoughts and promote them to become tasks in their main to-do list.

**Requirements:**

1.  **Frontend - Thought Input Area:**
    * Design and implement a simple user interface element (e.g., a text area or a dedicated "Jot Down a Thought" section) where users can quickly enter freeform text.
    * This area should be easily accessible but distinct from the main task creation interface.
    * Implement a way to save the entered thought (this will require interaction with the backend).

2.  **Backend - Thought Storage:**
    * Create a new mechanism on the backend to store these thoughts persistently. This might involve a new table in the database or a separate data structure, depending on the chosen backend technology.
    * Implement a new API endpoint (e.g., `/api/thoughts`) to receive and store new thoughts from the frontend.
    * **Apply the existing CORS policies to this new endpoint** to ensure only the frontend can access it.
    * **Implement input sanitization for the thought content** received from the frontend, similar to how task inputs are sanitized, to prevent security vulnerabilities.

3.  **Frontend - Viewing and Converting Thoughts:**
    * Create a new section or page in the frontend to display the saved thoughts.
    * For each displayed thought, provide an option (e.g., a button) to "Convert to Task".

4.  **Backend - Converting Thoughts to Tasks:**
    * Implement a new API endpoint (e.g., `/api/convert-thought-to-task`) that accepts the ID of a thought.
    * When this endpoint is called, retrieve the content of the specified thought.
    * **Sanitize the thought content again** before using it to create a new task entry in the task storage mechanism. This is a crucial second layer of defense.
    * Create a new task with the thought's content as the task title (or description, or both, decide on a sensible mapping). Assign a default status (e.g., not completed) and potentially other default values (e.g., no due date, default priority).
    * After successfully creating the task, remove the original thought from storage.
    * **Apply the existing CORS policies to this new conversion endpoint.**

5.  **Integration and Data Handling:**
    * Ensure seamless data flow between the frontend and the new backend endpoints for saving, retrieving, and converting thoughts.
    * Maintain the separation between thoughts and tasks in storage until conversion.

**Windsurf Specific Instructions:**

* Analyze the existing project structure to determine the best locations for new frontend components, backend routes, and data models/storage logic for the thought feature.
* Generate the necessary frontend code for the thought input area and the thought listing/conversion section, ensuring they integrate with the existing application layout.
* Generate the backend code for the new API endpoints (`/api/thoughts` and `/api/convert-thought-to-task`), including the logic for storing, retrieving, and deleting thoughts, and creating tasks from thoughts.
* **Crucially, automatically apply the established CORS configuration to the new backend endpoints.**
* **Implement input sanitization for all incoming data to the new thought endpoints** by adapting the existing sanitization logic used for tasks.
* Clearly present the new and modified code files, explaining how the thought feature is implemented and how security measures (CORS and sanitization) are applied to it.
* Provide instructions on how to use the new feature in the application.
```
  1. Inspect how project code changed from (4).
