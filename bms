<!DOCTYPE html>
<html>
<head>
    <title>Student Result Portal</title>
    <style>
        body {
            font-family: Arial;
            background: #eef2f5;
            text-align: center;
        }

        .login-box {
            width: 350px;
            margin: 60px auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
        }

        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
        }

        button {
            width: 95%;
            padding: 10px;
            background: #3498db;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background: #2980b9;
        }

        #result {
            display: none;
            width: 75%;
            margin: 20px auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            text-align: left;
            box-shadow: 0 0 10px rgba(0,0,0,0.2);
        }

        img {
            width: 120px;
            height: 140px;
            border-radius: 8px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }

        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: center;
        }

        th {
            background: #3498db;
            color: white;
        }

        .pass {
            color: green;
            font-size: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<h2>🎓 Student Result Portal</h2>

<div class="login-box">
    <h3>Login</h3>
    <input type="text" id="usn" placeholder="Enter USN">
    <input type="text" id="id" placeholder="Enter ID Card Number">
    <button onclick="login()">Get Result</button>
</div>

<div id="result">

    <h2>Student Details</h2>

    <p><strong>Name:</strong> <span id="name"></span></p>
    <p><strong>USN:</strong> <span id="r_usn"></span></p>
    <p><strong>ID:</strong> <span id="r_id"></span></p>

    <img id="photo">

    <h3>Marks</h3>

    <table>
        <tr>
            <th>Subject</th>
            <th>Marks</th>
            <th>Grade</th>
        </tr>
        <tbody id="marksTable"></tbody>
    </table>

    <h3 id="sgpa"></h3>
    <h3 id="cgpa"></h3>

    <div class="pass" id="status"></div>

</div>

<script>
/* ------------------ DATABASE ------------------ */
const students = {
    "1RV21CS001": {
        id: "ENG1001",
        name: "John Doe",
        photo: "student.jpg",
        marks: [
            {sub: "DS", mark: 85},
            {sub: "DBMS", mark: 78},
            {sub: "OS", mark: 82},
            {sub: "CN", mark: 74}
        ],
        previousSGPA: [8.2, 8.5, 8.1]
    },

    "1RV21CS002": {
        id: "ENG1002",
        name: "Asha Kumar",
        photo: "student.jpg",
        marks: [
            {sub: "DS", mark: 92},
            {sub: "DBMS", mark: 88},
            {sub: "OS", mark: 81},
            {sub: "CN", mark: 90}
        ],
        previousSGPA: [9.0, 8.8, 9.1]
    }
};

/* ------------------ GRADE FUNCTION ------------------ */
function grade(m) {
    if (m >= 90) return 10;
    if (m >= 80) return 9;
    if (m >= 70) return 8;
    if (m >= 60) return 7;
    if (m >= 50) return 6;
    return 0;
}

/* ------------------ LOGIN ------------------ */
function login() {
    let usn = document.getElementById("usn").value;
    let id = document.getElementById("id").value;

    let student = students[usn];

    if (!student || student.id !== id) {
        alert("Invalid USN or ID");
        return;
    }

    document.getElementById("result").style.display = "block";

    document.getElementById("name").innerText = student.name;
    document.getElementById("r_usn").innerText = usn;
    document.getElementById("r_id").innerText = id;
    document.getElementById("photo").src = student.photo;

    /* -------- MARKS TABLE -------- */
    let total = 0;
    let tbody = "";

    student.marks.forEach(m => {
        let g = grade(m.mark);
        total += g;
        tbody += `<tr>
                    <td>${m.sub}</td>
                    <td>${m.mark}</td>
                    <td>${g}</td>
                  </tr>`;
    });

    document.getElementById("marksTable").innerHTML = tbody;

    /* -------- SGPA -------- */
    let sgpa = (total / student.marks.length).toFixed(2);
    document.getElementById("sgpa").innerText = "SGPA: " + sgpa;

    /* -------- CGPA -------- */
    let prev = student.previousSGPA;
    let cgpa = ((prev.reduce((a,b)=>a+b,0) + parseFloat(sgpa)) / (prev.length + 1)).toFixed(2);

    document.getElementById("cgpa").innerText = "CGPA: " + cgpa;

    /* -------- RESULT STATUS -------- */
    document.getElementById("status").innerText = sgpa >= 5 ? "PASS ✅" : "FAIL ❌";
}
</script>

</body>
</html>
