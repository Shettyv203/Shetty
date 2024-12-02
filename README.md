# Shetty
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lucky Dip Ticket Booking</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <header>
    <h1>Lucky Dip Ticket Booking</h1>
    <p>Select a ticket number and fill your details!</p>
  </header>

  <main>
    <div class="ticket-selection">
      <label for="ticketNumber">Select Ticket Number (1-300):</label>
      <input type="number" id="ticketNumber" name="ticketNumber" min="1" max="300">
    </div>

    <div class="user-details">
      <label for="name">Your Name:</label>
      <input type="text" id="name" name="name" required>

      <label for="phone">Phone Number:</label>
      <input type="tel" id="phone" name="phone" required>

      <label for="payment">Payment Method:</label>
      <select id="payment" name="payment">
        <option value="cash">Cash</option>
        <option value="upi">UPI</option>
      </select>
    </div>

    <div class="submit">
      <button onclick="bookTicket()">Book Ticket</button>
    </div>

    <div id="confirmationMessage" class="confirmation"></div>
  </main>

  <footer>
    <p>&copy; 2024 Lucky Dip. All rights reserved.</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>

/* styles.css */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f9;
  color: #333;
}

header {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 20px;
}

h1 {
  margin: 0;
}

main {
  padding: 20px;
}

.ticket-selection, .user-details {
  margin-bottom: 20px;
}

input[type="text"], input[type="tel"], input[type="number"], select {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  background-color: #28a745;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #218838;
}

footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 10px;
  position: fixed;
  bottom: 0;
  width: 100%;
}

@media (max-width: 600px) {
  body {
    padding: 10px;
  }
  main {
    padding: 10px;
  }
}

// script.js
function bookTicket() {
  const ticketNumber = document.getElementById('ticketNumber').value;
  const name = document.getElementById('name').value;
  const phone = document.getElementById('phone').value;
  const payment = document.getElementById('payment').value;

  if (!ticketNumber || !name || !phone) {
    alert('Please fill in all the details!');
    return;
  }

  // Simple validation for ticket number
  if (ticketNumber < 1 || ticketNumber > 300) {
    alert('Please select a ticket number between 1 and 300.');
    return;
  }

  // Show confirmation message
  const confirmationMessage = `Ticket Number ${ticketNumber} booked by ${name}. 
    Payment Method: ${payment === 'upi' ? 'Paid via UPI' : 'Cash'}. 
    Confirmation will be sent to ${phone}.`;

  document.getElementById('confirmationMessage').innerText = confirmationMessage;
}
