<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Advanced Age Calculator</title>
    <style>
      body {
        font-family: "Arial", sans-serif;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        height: 100vh;
        background-color: #e0f7fa; /* Light cyan background */
        color: #333;
      }
      h1 {
        color: #00796b; /* Teal color for the heading */
      }
      input {
        margin: 5px;
        padding: 10px;
        width: 200px;
        border: 1px solid #00796b; /* Teal border */
        border-radius: 4px;
        transition: border-color 0.3s;
      }
      input:focus {
        border-color: #004d40; /* Darker teal on focus */
        outline: none; /* Remove default outline */
      }
      button {
        padding: 10px 15px;
        margin-top: 10px;
        background-color: #00796b; /* Teal button */
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        transition: background-color 0.3s;
      }
      button:hover {
        background-color: #004d40; /* Darker teal on hover */
      }
      /* Modal styles */
      #modal {
        display: none; /* Hidden by default */
        position: fixed;
        z-index: 1000;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        overflow: auto;
        background-color: rgba(
          0,
          0,
          0,
          0.5
        ); /* Black background with opacity */
        justify-content: center;
        align-items: center;
      }
      .modal-content {
        background-color: #fff;
        padding: 20px;
        border-radius: 5px;
        width: 300px;
        text-align: center;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      }
      .close {
        color: #aaa;
        float: right;
        font-size: 28px;
        font-weight: bold;
      }
      .close:hover,
      .close:focus {
        color: black;
        text-decoration: none;
        cursor: pointer;
      }
    </style>
  </head>
  <body>
    <h1>Advanced Age Calculator</h1>
    <label for="day">Day:</label>
    <input type="number" id="day" min="1" max="31" required />

    <label for="month">Month:</label>
    <input type="number" id="month" min="1" max="12" required />

    <label for="year">Year:</label>
    <input type="number" id="year" min="1900" max="2100" required />

    <button onclick="calculateAge()">Calculate Age</button>

    <!-- Modal for displaying results -->
    <div id="modal">
      <div class="modal-content">
        <span class="close" onclick="closeModal()">&times;</span>
        <p id="resultMessage"></p>
      </div>
    </div>

    <script>
  function calculateAge() {
    const day = parseInt(document.getElementById("day").value);
    const month = parseInt(document.getElementById("month").value) - 1; // Months are 0-indexed
    const year = parseInt(document.getElementById("year").value);

    if (!day day < 1 !month month < 0 month > 11 !year year < 1900) {
      alert("Please enter a valid date of birth.");
      return;
    }

    const today = new Date();
    const birthDate = new Date(year, month, day);

    if (birthDate > today) {
      alert("Date of birth cannot be in the future.");
      return;
    }

    let age = today.getFullYear() - birthDate.getFullYear();
    const monthDiff = today.getMonth() - birthDate.getMonth();
    const dayDiff = today.getDate() - birthDate.getDate();

    if (monthDiff < 0 || (monthDiff === 0 && dayDiff < 0)) {
      age--;
    }

    alert(Your age is ${age} years old.);
  }

  function closeModal() {
    document.getElementById("modal").style.display = "none";
  }

  window.onclick = function(event) {
    if (event.target == document.getElementById("modal")) {
      closeModal();
    }
  };
</script>
    </script>
  </body>
</html>
