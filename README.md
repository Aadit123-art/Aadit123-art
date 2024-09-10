<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aadit Massages - Membership Portal</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1, h2 {
            text-align: center;
        }
        input, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        button {
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Welcome to Aadit Massages</h1>
        <h2>Membership Card Check</h2>
        <form id="membershipForm">
            <label for="membershipID">Enter Membership Card ID:</label>
            <input type="text" id="membershipID" required placeholder="Membership Card ID">
            <button type="button" onclick="checkMembership()">Check Details</button>
        </form>
        <div id="membershipDetails"></div>

        <hr>

        <h2>Staff Access</h2>
        <form id="staffLoginForm">
            <label for="staffCode">Enter Staff Code:</label>
            <input type="password" id="staffCode" required placeholder="Staff Code">
            <button type="button" onclick="staffLogin()">Login</button>
        </form>
        <div id="staffDetails"></div>

        <button type="button" onclick="showAddCardForm()">Add Membership Card</button>
        <div id="addCardForm" style="display:none;">
            <h2>Add New Membership Card</h2>
            <form id="addCard">
                <label for="staffID">Enter Your Staff ID:</label>
                <input type="text" id="staffID" required placeholder="Staff ID">
                <label for="newCardID">Enter New Membership Card ID:</label>
                <input type="text" id="newCardID" required placeholder="New Card ID">
                <button type="button" onclick="addCard()">Add Card</button>
            </form>
        </div>
    </div>

    <script>
        // Sample data for members and staff
        const members = {
            '12345': { name: 'John Doe', dob: '01-01-1985', address: '123 Street, City', debt: '$100' },
            '67890': { name: 'Jane Smith', dob: '05-15-1990', address: '456 Avenue, City', debt: '$50' }
        };

        const staff = {
            'staff001': { name: 'Alice Johnson', dob: '10-20-1980', job: 'Manager' },
            'staff002': { name: 'Bob Lee', dob: '07-11-1985', job: 'Massager' }
        };

        // Check Membership
        function checkMembership() {
            const membershipID = document.getElementById('membershipID').value;
            const details = members[membershipID];

            if (details) {
                document.getElementById('membershipDetails').innerHTML = `
                    <h3>Membership Details</h3>
                    <p><strong>Name:</strong> ${details.name}</p>
                    <p><strong>Date of Birth:</strong> ${details.dob}</p>
                    <p><strong>Address:</strong> ${details.address}</p>
                    <p><strong>Debt:</strong> ${details.debt}</p>
                `;
            } else {
                document.getElementById('membershipDetails').innerHTML = '<p>Membership ID not found.</p>';
            }
        }

        // Staff Login
        function staffLogin() {
            const staffCode = document.getElementById('staffCode').value;
            const staffDetails = staff[staffCode];

            if (staffDetails) {
                document.getElementById('staffDetails').innerHTML = `
                    <h3>Staff Details</h3>
                    <p><strong>Name:</strong> ${staffDetails.name}</p>
                    <p><strong>Date of Birth:</strong> ${staffDetails.dob}</p>
                    <p><strong>Job:</strong> ${staffDetails.job}</p>
                `;
            } else {
                document.getElementById('staffDetails').innerHTML = '<p>Invalid staff code.</p>';
            }
        }

        // Show Add Card Form
        function showAddCardForm() {
            document.getElementById('addCardForm').style.display = 'block';
        }

        // Add Membership Card
        function addCard() {
            const staffID = document.getElementById('staffID').value;
            const newCardID = document.getElementById('newCardID').value;

            if (staff[staffID]) {
                if (!members[newCardID]) {
                    members[newCardID] = { name: 'New Member', dob: 'N/A', address: 'N/A', debt: '$0' };
                    alert('New membership card added successfully.');
                } else {
                    alert('Membership ID already exists.');
                }
            } else {
                alert('Invalid staff ID.');
            }
        }
    </script>
</body>
</html>
