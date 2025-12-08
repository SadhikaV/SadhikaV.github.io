# Login Flow Documentation

## 1. Overview
The Login Flow allows users to authenticate into the application using their registered email  and password. It manages validation, error handling and secure navigation to the dashboard upon succesful login.

## 2. Purpose
The purpose of the Login Flow is to provide a secure and user-firnedly method for accessing protected areas of the application.

## 3. Scope
This document covers:
- UI components
- Validation rules
- API interaction
- Success and error handling
- Navigation behavior

## 4. User Interface (UI)
The Login screen includes:
- Email input field
- Passowrd input field (masked)
- "Sign In" button
- "Forgot Password?" link
- Inline validation messages
- Loading spinner during authentication
{
  "email": "user@example.com",
  "password": "*******"
}
 ### 5. Workflow
 1. User enters email and password.
 2. User clicks the "Sign In" button.
 3. Frontend validation checks email format and empty fields.
 4. If validation fails, inline error messages appear.
 5. If validation succeeds, a POST request is sent to '/api/auth/login'.
 6. Backend validates credentials.
 7. If authentication succeeds, token is returned and user is redirected to the dashboard.
 8. If authentication fails, an error message is displayed.
{
  "email": "user@example.com",
  "password": "*******"
}
  ### 6. Validation Rules
  - Email is required and must be a valid format.
  - Password is required.
  - Backend validates credentials and returns an error if invalid.
{
  "email": "user@example.com",
  "password": "*******"
}
  ### 7. API Interaction

   ### Endpoint
   `POST /api/auth/login`

   ### Request Body
  ```json```
  {
    "email": "user@example.com",
    "password": "*******"
  }
  
  ### Success Response
  ```json```
  {
    "token": "<jwt-token>",
    "userID": "12345"
  }
  
  ### Error Response
  ```json```
  {
    "error": "Invalid email or password"
  }

  ### 8. Error Handling

  The Login Flow includes both frontend and backend error handling:
  - **Email is required** - shown if the email field is empty.
  - **Password is required** - shown if the password field is empty.
  - **Invalid email format** - shown if the email does not match standard pattern.
  - **Incorrect email or password** - returned by backend authentication.
  - **Network error** - shown if API server fails or timeout.

```json```
{
  "email": "user@example.com",
  "password": "*******"
}
  ### 9. Navigation 
  
  After a succesful login:

  - The user is redirected to `/dashboard` route.
  - The authentication token (JWT) is stored securely in browser storage:
      - `localStorage` for persistent sessions or
      - `sessionStorage` for temporary sessions.
  - All protected routes are accessible only when a valid token exists.
    
    Navigation is handled using React Router's `useNavigate()` hook.
json    
{
  "email": "user@example.com",
  "password": "*******"
}
   
  ### 10. Diagram

  A visual workflow of the Login process will be added here.

   Login Flow Diagram - To be inserted

     



 
