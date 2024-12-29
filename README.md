🛡️ AntiInjection Function (TypeScript)
A simple and lightweight function to sanitize user input by removing suspicious content and escaping special characters. This helps mitigate basic security risks like SQL Injection and Cross-Site Scripting (XSS).

🚀 Features
Removes extra spaces from the input.
Strips HTML and script tags.
Escapes special characters (e.g., single quotes, double quotes, and backslashes).
Lightweight and easy to integrate.
📦 Installation
You can copy the function directly or add it to your project manually. If you prefer, you can also convert it into a reusable module.

🛠 Usage
typescript
Copiar código
import { antiInjection } from './path-to-your-function';

// Example Input
const userInput = `<script>alert('injection')</script> SELECT * FROM users WHERE id='1'`;
const sanitizedInput = antiInjection(userInput);

console.log(sanitizedInput);
// Output: SELECT * FROM users WHERE id=\'1\'
📄 Function Description
The antiInjection function performs the following steps:

Trim Extra Spaces: Removes leading and trailing spaces using trim().
Remove Tags: Strips HTML and script tags with a regular expression.
Escape Special Characters: Escapes special characters such as quotes and backslashes.
Function Code
typescript
Copiar código
function antiInjection(str: string): string {
    // Remove possible spaces at the start and end
    str = str.trim();

    // Remove HTML and script tags
    str = str.replace(/<\/?[^>]+(>|$)/g, "");

    // Escape special characters (similar to addslashes in PHP)
    str = str.replace(/['"\\]/g, '\\$&');

    return str;
}
⚠️ Security Disclaimer
This function is a basic sanitization tool and does not replace robust security practices, such as:

Using prepared statements for database queries.
Employing secure frameworks or ORM libraries for handling database communication.
Implementing a Content Security Policy (CSP) for web applications.
Always ensure you follow best practices to secure your application.

🏗 Applications
Sanitizing user input before logging or displaying it in the UI.
Pre-processing data before storing it in a database (additional measures recommended).
Mitigating risks from potentially malicious user inputs.
🧑‍💻 Contributions
Feel free to fork this repository and contribute by submitting a pull request. Suggestions and improvements are always welcome!
