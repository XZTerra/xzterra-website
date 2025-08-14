# xzterra-website
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>XZ Terra | Landscaping & More</title>
<style>
    * {margin: 0; padding: 0; box-sizing: border-box; font-family: 'Arial', sans-serif;}
    body {background-color: #f4f4f4; color: #333;}
    a {text-decoration: none; color: inherit;}
    header {background: #2c3e50; color: white; padding: 20px 0; text-align: center;}
    header h1 {margin-bottom: 5px;}
    nav {margin-top: 10px;}
    nav a {margin: 0 15px; color: #ecf0f1; font-weight: bold;}
    section {padding: 60px 20px; max-width: 1000px; margin: auto;}
    h2 {margin-bottom: 20px; color: #2c3e50; text-align: center;}
    p {margin-bottom: 15px; line-height: 1.6;}
    .services, .testimonials {display: flex; flex-wrap: wrap; justify-content: space-around;}
    .card {background: white; padding: 20px; margin: 10px; flex: 1 1 250px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);}
    form {background: white; padding: 20px; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);}
    input, textarea, select, button {width: 100%; padding: 10px; margin-bottom: 15px; border-radius: 4px; border: 1px solid #ccc;}
    button {background: #27ae60; color: white; border: none; cursor: pointer;}
    button:hover {background: #2ecc71;}
    footer {background: #2c3e50; color: white; text-align: center; padding: 20px;}
    .social-links a {margin: 0 10px; font-size: 20px;}
</style>
</head>
<body>

<header>
    <h1>XZ Terra</h1>
    <p>Landscaping, Hardscape, Snow Removal & Construction</p>
    <nav>
        <a href="#about">About</a>
        <a href="#services">Services</a>
        <a href="#testimonials">Testimonials</a>
        <a href="#contact">Contact</a>
        <a href="#schedule">Schedule</a>
    </nav>
</header>

<section id="about">
    <h2>About Us</h2>
    <p>Welcome to XZ Terra! With over 10 years of experience in landscaping, hardscape, snow removal, and construction, we bring your residential and commercial projects to life. Our team is dedicated to quality, creativity, and customer satisfaction.</p>
</section>

<section id="services">
    <h2>Our Services</h2>
    <div class="services">
        <div class="card"><h3>Landscaping</h3><p>From lawn care to garden design, we create beautiful outdoor spaces.</p></div>
        <div class="card"><h3>Hardscape</h3><p>Patios, walkways, retaining walls, and more to enhance your property.</p></div>
        <div class="card"><h3>Snow Removal</h3><p>Reliable and fast snow clearing to keep your property safe.</p></div>
        <div class="card"><h3>Construction</h3><p>Residential development projects with experienced manpower.</p></div>
    </div>
</section>

<section id="testimonials">
    <h2>Testimonials</h2>
    <div class="testimonials">
        <div class="card"><p>"XZ Terra transformed our backyard into a paradise! Highly recommend." - Sarah M.</p></div>
        <div class="card"><p>"Professional, on-time, and great results. We love our new patio." - John D.</p></div>
    </div>
</section>

<section id="contact">
    <h2>Contact & Inquiries</h2>
    <form id="contactForm">
        <input type="text" name="name" placeholder="Your Name" required>
        <input type="email" name="email" placeholder="Your Email" required>
        <input type="tel" name="phone" placeholder="Phone Number">
        <textarea name="message" placeholder="Your Message or Inquiry" rows="5" required></textarea>
        <button type="submit">Submit Inquiry</button>
    </form>
</section>

<section id="schedule">
    <h2>Schedule a Service</h2>
    <p>Select an available date and time for your appointment:</p>
    <form id="scheduleForm">
        <select id="serviceDate" required>
            <option value="">Select a Date</option>
        </select>
        <select id="serviceTime" required>
            <option value="">Select a Time</option>
        </select>
        <button type="submit">Book Appointment</button>
    </form>
    <p><em>Note: Update availability by editing the "availability" section in the HTML.</em></p>
</section>

<footer>
    <p>Contact: <a href="mailto:juandvazquez24@gmail.com">juandvazquez24@gmail.com</a> | Phone: (708)-897-6357</p>
    <div class="social-links">
        <a href="#" target="_blank">Facebook</a>
        <a href="#" target="_blank">Instagram</a>
        <a href="#" target="_blank">LinkedIn</a>
    </div>
    <p>&copy; 2025 XZ Terra. All rights reserved.</p>
</footer>

<script>
    // ================================
    // CONTACT FORM
    // ================================
    document.getElementById('contactForm').addEventListener('submit', function(e){
        e.preventDefault();
        alert('Thank you! Your inquiry has been submitted.');
        this.reset();
    });

    // ================================
    // AVAILABILITY - EDIT HERE
    // ================================
    // Format: "YYYY-MM-DD": ["Time1","Time2",...]
    const availability = {
        "2025-08-16": ["08:00 AM", "10:00 AM", "02:00 PM"],
        "2025-08-17": ["09:00 AM", "12:00 PM", "04:00 PM"],
        "2025-08-18": ["08:00 AM", "11:00 AM", "01:00 PM", "03:00 PM"]
    };
    // To update availability: Add/remove dates or times here.
    // Example: "2025-08-19": ["10:00 AM", "01:00 PM"]

    // ================================
    // POPULATE DATE & TIME DROPDOWNS
    // ================================
    const dateSelect = document.getElementById('serviceDate');
    const timeSelect = document.getElementById('serviceTime');

    // Populate available dates
    Object.keys(availability).forEach(date => {
        const option = document.createElement('option');
        option.value = date;
        option.textContent = new Date(date).toDateString();
        dateSelect.appendChild(option);
    });

    // Update time slots when date changes
    dateSelect.addEventListener('change', function() {
        timeSelect.innerHTML = '<option value="">Select a Time</option>';
        if(this.value && availability[this.value]){
            availability[this.value].forEach(time => {
                const option = document.createElement('option');
                option.value = time;
                option.textContent = time;
                timeSelect.appendChild(option);
            });
        }
    });

    // Schedule form submission
    document.getElementById('scheduleForm').addEventListener('submit', function(e){
        e.preventDefault();
        const date = dateSelect.value;
        const time = timeSelect.value;
        if(date && time){
            alert(`Your appointment is booked for ${new Date(date).toDateString()} at ${time}. We will contact you to confirm.`);
            this.reset();
            timeSelect.innerHTML = '<option value="">Select a Time</option>';
        } else {
            alert('Please select both date and time.');
        }
    });
</script>

</body>
</html>
