# healthcare-hackatho
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Emergency Bed & Doctor Tracker</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <!-- HEADER -->
  <header>
    <h1>Emergency Bed & Doctor Availability Tracker</h1>
    <p>Find nearby hospitals with available beds and on-call doctors</p>
    <button id="emergencyBtn">Emergency! Find Nearby Hospitals</button>
  </header>

  <!-- LOCATION & HOSPITAL LIST -->
  <section id="hospitalSection" style="display:none;">
    <h2>Nearby Hospitals</h2>
    <div id="hospitalList">
      <!-- Hospital Cards Injected Here -->
    </div>
  </section>

  <!-- HOW IT WORKS -->
  <section>
    <h2>How It Works</h2>
    <ol>
      <li>Click Emergency Button</li>
      <li>System detects your location</li>
      <li>Displays nearby hospitals</li>
      <li>Shows bed availability & doctors on call</li>
      <li>Select hospital and call ambulance / visit</li>
    </ol>
  </section>

  <!-- FEATURES -->
  <section>
    <h2>Features</h2>
    <ul>
      <li>Real-time bed availability</li>
      <li>Doctor on-call information</li>
      <li>Emergency priority view</li>
      <li>User-friendly interface</li>
    </ul>
  </section>

  <!-- FOOTER -->
  <footer>
    <p>© 2026 Cyberthon | Healthcare Technology</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
/* GENERAL STYLING */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0 20px;
  line-height: 1.6;
  background-color: #f5f5f5;
  color: #333;
}

/* HEADER */
header {
  text-align: center;
  background-color: #4CAF50;
  color: white;
  padding: 30px 20px;
  margin-bottom: 20px;
}

header h1 {
  margin: 0 0 10px 0;
}

header p {
  font-size: 18px;
  margin: 0 0 20px 0;
}

header button {
  padding: 15px 25px;
  font-size: 16px;
  background-color: #ff4b5c;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

header button:hover {
  background-color: #e33b4e;
}

/* HOSPITAL CARDS */
#hospitalList {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  margin: 20px 0;
}

.hospital-card {
  background-color: white;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  padding: 15px;
  width: 300px;
}

.hospital-card h3 {
  margin-top: 0;
}

.hospital-card p {
  margin: 5px 0;
}

.hospital-card button {
  margin-top: 10px;
  padding: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.hospital-card button:hover {
  background-color: #45a049;
}

/* SECTIONS */
section {
  margin-bottom: 30px;
  padding: 20px;
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0,0,0,0.05);
}

h2 {
  color: #4CAF50;
}

/* FOOTER */
footer {
  text-align: center;
  padding: 20px;
  color: gray;
}
// Dummy hospital data
const hospitals = [
  {
    name: "Suresh Gyan Vihar Hospital",
    bedsAvailable: 5,
    doctorsOnCall: 3,
    contact: "+91 9876543210"
  },
  {
    name: "Jaipur City Hospital",
    bedsAvailable: 2,
    doctorsOnCall: 1,
    contact: "+91 9123456789"
  },
  {
    name: "Sunshine Medical Center",
    bedsAvailable: 0,
    doctorsOnCall: 2,
    contact: "+91 9988776655"
  }
];

// Elements
const emergencyBtn = document.getElementById("emergencyBtn");
const hospitalSection = document.getElementById("hospitalSection");
const hospitalList = document.getElementById("hospitalList");

// Show hospital list on button click
emergencyBtn.addEventListener("click", () => {
  hospitalSection.style.display = "block";
  hospitalList.innerHTML = ""; // Clear previous

  hospitals.forEach(hospital => {
    const card = document.createElement("div");
    card.className = "hospital-card";
    card.innerHTML = `
      <h3>${hospital.name}</h3>
      <p>Beds Available: ${hospital.bedsAvailable}</p>
      <p>Doctors On Call: ${hospital.doctorsOnCall}</p>
      <p>Contact: ${hospital.contact}</p>
      <button onclick="alert('Calling ${hospital.contact}')">Call Hospital</button>
    `;
    hospitalList.appendChild(card);
  });
});
