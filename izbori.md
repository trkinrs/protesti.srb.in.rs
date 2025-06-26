---
layout: null
---
<html>
  <head>
    <style>

      table {
        border-collapse: collapse;
        margin-top: 20px;
        margin-left: auto;
        margin-right: auto;
      }
      table, td, tr {
        border: 1px solid #000;
      }
      td {
        padding: 4px;
        text-align: left;
        word-wrap: break-word;
        height: 70px; /* Increase the height of table rows */
      }
      tr {
        width: 100%;
        display: table;
        table-layout: fixed;
      }
      @keyframes fadeInOut {
        0% { opacity: 0; }
        10% { opacity: 1; }
        90% { opacity: 1; }
        100% { opacity: 0; }
      }

      #notice {
        animation: fadeInOut 15s forwards;
      }
    </style>
  </head>
  <body>
    <div style="background: #eeeeee; padding: 20px;">
      <div id="pdf-content">
        <h2 style=" text-align: center">Peticija za raspisivanje vanrednih parlamentarnih izbora</h2>

        <p class="font-size">U skladu sa članom 109. Ustava Republike Srbije, zahtevamo:</p>

        <ol class="font-size">
          <li>od Vlade Republike Srbije da predsedniku Republike uputi obrazloženi predlog za raspuštanje Narodne skupštine Republike Srbije;</li>
          <li>od predsednika Republike da odmah nakon prijema predloga iz tačke 1. Ukazom raspusti Narodnu skupštinu i raspiše izbore za narodne poslanike;</li>
          <li>od svih nadležnih institucija Republike Srbije da savesno i odgovorno obavljaju svoj posao i omoguće fer i poštene izbore.</li>
        </ol>

        <table class="font-size">
          <tr>
            <td>Ime i prezime</td>
            <td><span id="pdf-name">Željko Jevtić</span></td>
          </tr>
          <tr>
            <td>Broj lične karte i mesto izdavanja</td>
            <td><span id="pdf-id">008204889, Užice</span></td>
          </tr>
          <tr>
            <td>Elektronski potpis</td>
            <td></td>
          </tr>
        </table>
      </div>
    </div>
    <div style="text-align: center; padding-top: 20px; font-size: 20px; ">
      <label>Ime i prezime: <input type="text" id="name" autofocus placeholder="Željko Jevtić" style="line-height: 20px; font-size: 18px; padding: 8px; border: 2px solid blue; border-radius: 6px; margin-bottom: 10px;"/></label><br>
      <label>Broj lične karte i mesto izdavanja: <input type="text" id="id" placeholder="008204889, Užice" size="18" style="line-height: 20px; font-size: 18px; padding: 8px; border: 2px solid blue; border-radius: 6px;"/></label>
      <button id="download-btn" onclick="generatePDF()" disabled style="width: 90%; margin: 12px; background-color: #2563eb; color: white; padding: 12px; border-radius: 6px; border: none; cursor: pointer; font-weight: bold; transition: background-color 0.2s; background-color: #cccccc;">
        <svg style="display: inline-block; vertical-align: middle; margin-right: 8px" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M13 3v12l-5-5m5 5 5-5m2 10H4"></path>
        </svg>
        Preuzmi PDF
      </button>
      <small id="notice" style="height: 1rem; display: block"></small>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <script>

      const downloadBtn = document.getElementById('download-btn');
      const nameInput = document.getElementById('name');
      const idInput = document.getElementById('id');
      const noticeDiv = document.getElementById('notice');

      function checkInputs() {
        if (nameInput.value.trim() !== '' && idInput.value.trim() !== '') {
          downloadBtn.disabled = false;
          downloadBtn.style.backgroundColor = '#2563eb'; // Blue color when enabled
        } else {
          downloadBtn.style.backgroundColor = '#cccccc'; // Gray color when disabled
          downloadBtn.disabled = true;
        }
      }

      nameInput.addEventListener('input', function () {
        const name = this.value;
        document.getElementById('pdf-name').textContent = name;
        checkInputs();
      });

      nameInput.addEventListener('keypress', function (e) {
        if (e.keyCode === 13) generatePDF();
      });

      idInput.addEventListener('input', function () {
        const id = this.value;
        document.getElementById('pdf-id').textContent = id;
        checkInputs();
      });

      idInput.addEventListener('keypress', function (e) {
        if (e.keyCode === 13) generatePDF();
      });
      const element = document.getElementById("pdf-content");
      function generatePDF() {
        document.getElementById('pdf-name').textContent = nameInput.value;
        document.getElementById('pdf-id').textContent = idInput.value;
        const fileName = `Peticija za izbore ${nameInput.value} ${idInput.value}.pdf`;
        html2pdf().set({
            margin: 10,
            pagebreak: { mode: 'avoid-all' },
          })
          .from(element)
          .save(fileName);
        nameInput.value = "";
        idInput.value = "";
        checkInputs();
        noticeDiv.textContent = `Preuzeto ${fileName}`;
        noticeDiv.style.display = 'block';
        setTimeout(() => {
          noticeDiv.style.display = 'none';
        }, 15000);
      }
    </script>
  </body>
</html>
