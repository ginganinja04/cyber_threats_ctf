
<body>
  <h1>🕵️‍♀️ Image CTF Challenge</h1>
  <p>We found this suspicious image on a compromised machine. It looks innocent, but we believe something is hidden inside. Can you find the flag?</p>
  <p><strong>Download the challenge file:</strong></p>
  <ul>
    <li><a href="my_vacation.jpg" download>my_vacation.jpg</a></li>
  </ul>
  <p><em>Tools you might find useful: binwalk, steghide, exiftool, unzip...</em></p>

  <h3>Submit Your Flag:</h3>
  <form id="flag-form">
    <input type="text" id="flag-input" placeholder="Enter the flag here..." required>
    <button type="submit">Submit Flag</button>
  </form>

  <p id="result-message"></p>

  <script>
    const correctFlag = "FLAG{d0ubl3_l4y3r_d3c3pt10n}"; // Updated flag

    document.getElementById('flag-form').addEventListener('submit', function(event) {
      event.preventDefault();
      const userFlag = document.getElementById('flag-input').value.trim();
      const resultMessage = document.getElementById('result-message');

      if (userFlag === correctFlag) {
        resultMessage.textContent = "Correct! 🎉 You've found the flag!";
        resultMessage.className = "correct";
      } else {
        resultMessage.textContent = "Incorrect! Try again. ⚠️";
        resultMessage.className = "incorrect";
      }

      document.getElementById('flag-input').value = ''; // Clear input field after submission
    });
  </script>
</body>
</html>
