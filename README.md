# Admission_fred
<!DOCTYPE html>
<html>
<head>
  <title>Online Admission System</title>
</head>
<body>
  <h1>Online Admission System</h1>
  
  <form id="admission-form">
    <label for="name">Name:</label>
    <input type="text" id="name" required><br><br>
    
    <label for="email">Email:</label>
    <input type="email" id="email" required><br><br>
    
    <label for="degree">Degree:</label>
    <select id="degree">
      <option value="Bachelor's">Bachelor's</option>
      <option value="Master's">Master's</option>
      <option value="Doctorate">Doctorate</option>
    </select><br><br>
    
    <input type="submit" value="Submit">
  </form>
  
  <hr>
  
  <h2>Applicants</h2>
  <table id="applicants-table">
    <thead>
      <tr>
        <th>Name</th>
        <th>Email</th>
        <th>Degree</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody id="applicants-body"></tbody>
  </table>
  
  <script>
    const form = document.querySelector("#admission-form");
    const tableBody = document.querySelector("#applicants-body");
    
    let applicants = [];
    
    form.addEventListener("submit", event => {
      event.preventDefault();
      
      const name = document.querySelector("#name").value;
      const email = document.querySelector("#email").value;
      const degree = document.querySelector("#degree").value;
      
      applicants.push({ name, email, degree });
      renderApplicants();
    });
    
    function renderApplicants() {
      tableBody.innerHTML = "";
      
      for (const applicant of applicants) {
        const { name, email, degree } = applicant;
        const deleteButton = `<button onclick="deleteApplicant('${email}')">Delete</button>`;
        
        const row = `
          <tr>
            <td>${name}</td>
            <td>${email}</td>
            <td>${degree}</td>
            <td>${deleteButton}</td>
          </tr>
        `;
        
        tableBody.innerHTML += row;
      }
    }
    
    function deleteApplicant(email) {
      applicants = applicants.filter(applicant => applicant.email !== email);
      renderApplicants();
    }
  </script>
</body>
</html>
