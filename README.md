# JWT Authentication with Spring Boot

This project demonstrates how to implement **JWT-based authentication** in a Spring Boot application. It includes user login via `/authenticate`, token generation, and access to a secured endpoint `/hello`.

---

## 🔧 Tech Stack

- Java
- Spring Boot
- Spring Security
- JWT (JSON Web Token)
- Hibernate (JPA)
- H2/MySQL (based on your config)
- Postman (for testing)

---

## 🚀 How to Run the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/Gunjan22Sri/jwtproject.git
   cd jwtproject
2. Open in your IDE (like VS Code or IntelliJ).

3. Update application properties:

 - Set your database (H2/MySQL) if not using the default.
 - Configure your UserDetailsService or initial user data.

4. Run the Spring Boot application
   
✅ ## How to Test Using Postman
Step 1: Get the JWT Token
Open Postman.
Create a POST request to:

http://localhost:8080/authenticate

Go to the Body tab → Select raw → Choose JSON.

Paste this:

{
  "username": "admin",
  "password": "password"
}
Click Send.

Copy the value of token from the response.

Step 2: Call the Secured Endpoint /hello
Create a GET request to:

http://localhost:8080/hello

Go to the Authorization tab:

Type: Bearer Token

Token: Paste the token from Step 1

OR

Go to the Headers tab and add:

Key: Authorization
Value: Bearer <paste_your_token_here>
Click Send.

✅ You should get:

Hello, authenticated user!

🔒 ##  Security Configuration
- /authenticate is public (no auth needed).

- All other endpoints require a valid JWT token.

- Stateless session management with JWT.

- Filter chain uses UsernamePasswordAuthenticationFilter.

🧪 Sample User
Username	Password	Role
admin	password	USER

📁 Project Structure Highlights
```bash
jwtproject/
├── controller/
│   └── HelloController.java
├── config/
│   └── SecurityConfig.java
├── filter/
│   └── JwtAuthFilter.java
├── service/
│   └── CustomUserDetailsService.java
├── util/
│   └── JwtUtil.java
├── model/
│   └── User.java
├── AuthRequest.java
├── JwtProjectApplication.java
└── application.properties
🧠 Tip
If you're facing 403 Forbidden when calling /hello, make sure:

The JWT token is valid (not expired).

You passed the token with the correct Bearer prefix.

Your filter is properly registered before the UsernamePasswordAuthenticationFilter.
