const express = require("express");

const app = express();
const PORT = 3000;

// Middleware to read form data
app.use(express.urlencoded({ extended: true }));

// Home page with HTML form
app.get("/", (req, res) => {
    res.send(`
        <!DOCTYPE html>
        <html>
        <head>
            <title>Student Registration</title>
        </head>

        <body>
            <h1>Student Registration Form</h1>

            <form action="/submit" method="POST">

                <label>Name:</label>
                <input type="text" name="name" required>
                <br><br>

                <label>Email:</label>
                <input type="email" name="email" required>
                <br><br>

                <label>Age:</label>
                <input type="number" name="age" required>
                <br><br>

                <label>Course:</label>
                <select name="course">
                    <option value="FSD">Full Stack Development</option>
                    <option value="Java">Java</option>
                    <option value="Python">Python</option>
                    <option value="MERN">MERN Stack</option>
                </select>
                <br><br>

                <button type="submit">Submit</button>

            </form>
        </body>
        </html>
    `);
});

// Handle form submission
app.post("/submit", (req, res) => {

    const name = req.body.name;
    const email = req.body.email;
    const age = req.body.age;
    const course = req.body.course;

    res.send(`
        <!DOCTYPE html>
        <html>
        <head>
            <title>Registration Result</title>
        </head>

        <body>
            <h1>Registration Successful!</h1>

            <h3>Student Details</h3>

            <p><b>Name:</b> ${name}</p>
            <p><b>Email:</b> ${email}</p>
            <p><b>Age:</b> ${age}</p>
            <p><b>Course:</b> ${course}</p>

            <br>
            <a href="/">Go Back</a>
        </body>
        </html>
    `);
});

// Start server
app.listen(PORT, () => {
    console.log(`Server running at http://localhost:${PORT}`);
});
