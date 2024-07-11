<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>University Residence Management System</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            margin: 20px;
        }
        .card {
            border: 1px solid #ddd;
            border-radius: 5px;
            padding: 10px;
            margin-bottom: 10px;
        }
        .card h2 {
            margin-top: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>University Residence Management System</h1>
        <div id="dormRoom" class="card"></div>
        <div id="apartment" class="card"></div>
        <div id="student" class="card"></div>
        <div id="maintenanceRequest" class="card"></div>
    </div>
    <script src="residenceManagement.js"></script>
    <script>
        document.addEventListener("DOMContentLoaded", function() {
            // Create a dorm room
            const dorm = new DormRoom("Dorm A", "123 University St", false, 300);
            const dormDiv = document.getElementById("dormRoom");
            dormDiv.innerHTML = `<h2>Dorm Room</h2>
                <p>Name: ${dorm.name}</p>
                <p>Address: ${dorm.address}</p>
                <p>Size: ${dorm.size} sq ft</p>
                <p>Rent: $${dorm.calculateRent()}</p>
                <p>Occupied: ${dorm.isOccupied ? "Yes" : "No"}</p>`;

            // Create an apartment
            const apartment = new Apartment("Apartment B", "456 University Ave", false, 3);
            const apartmentDiv = document.getElementById("apartment");
            apartmentDiv.innerHTML = `<h2>Apartment</h2>
                <p>Name: ${apartment.name}</p>
                <p>Address: ${apartment.address}</p>
                <p>Number of Bedrooms: ${apartment.numberOfBedrooms}</p>
                <p>Rent: $${apartment.calculateRent()}</p>
                <p>Occupied: ${apartment.isOccupied ? "Yes" : "No"}</p>`;

            // Create a student and assign residence
            const student = new Student("John Doe", "12345", "Male");
            student.assignResidence(dorm);
            const studentDiv = document.getElementById("student");
            studentDiv.innerHTML = `<h2>Student</h2>
                <p>Name: ${student.name}</p>
                <p>Student ID: ${student.studentID}</p>
                <p>Gender: ${student.gender}</p>
                <p>Assigned Residence: ${student.residence.name}</p>`;

            // Create a maintenance request
            const maintenanceRequest = new MaintenanceRequest("Leaky faucet", "submitted", student);
            const maintenanceRequestDiv = document.getElementById("maintenanceRequest");
            maintenanceRequestDiv.innerHTML = `<h2>Maintenance Request</h2>
                <p>Description: ${maintenanceRequest.description}</p>
                <p>Status: ${maintenanceRequest.status}</p>
                <p>Submitted by: ${maintenanceRequest.student.name}</p>`;
        });
    </script>
</body>
</html>
