<html>
  <head>
    <style>
      table {
        border-collapse: collapse;
        width: 95%;
        margin-top: 20px;
        margin-left: auto;
        margin-right: auto;
      }
      thead, tbody, tr {
        width: 98%;
        display: table;
        table-layout: fixed;
      }
      td {
        border: 1px solid #000;
        padding: 4px;
        text-align: left;
        word-wrap: break-word;
      }
    </style>
  </head>
  <body>
    <div style="background: #eeeeee; padding: 5px; text-align: center">
      <div id="pdf-content">
        <h2 style="">Peticija za raspisivanje vanrednih parlamentarnih izbora</h2>

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
      <label>Ime i prezime: <input type="text" id="name" placeholder="Željko Jevtić" style="line-height: 25px"/></label><br>
      <label>Broj lične karte i mesto izdavanja: <input type="text" id="id" placeholder="008204889, Užice" size="18"  style="line-height: 25px"/></label>
      <button onclick="generatePDF()" style="width: 90%; margin: 12px;  background-color: #2563eb; color: white; padding: 12px; border-radius: 6px; border: none; cursor: pointer; font-weight: bold; transition: background-color 0.2s">
        <svg style="display: inline-block; vertical-align: middle; margin-right: 8px" width="20" height="20" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
          <path d="M13 3v12l-5-5m5 5 5-5m2 10H4"></path>
        </svg>
        Preuzmi PDF
      </button>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    <script>

      document.getElementById('name').addEventListener('input', function () {
        const name = this.value;
        document.getElementById('pdf-name').textContent = name;
      });
      document.getElementById('name').addEventListener('keypress', function (e) {
        if (e.keyCode === 13) generatePDF();
      });
      document.getElementById('id').addEventListener('input', function () {
        const name = this.value;
        document.getElementById('pdf-id').textContent = name;
      });
      document.getElementById('id').addEventListener('keypress', function (e) {
        if (e.keyCode === 13) generatePDF();
      });
      const element = document.getElementById("pdf-content");
      function generatePDF() {
        const name = document.getElementById('name').textContent;
        document.getElementById('pdf-name').textContent = name;
        const id = document.getElementById('id').textContent;
        document.getElementById('pdf-id').textContent = id;
        html2pdf().set({
            margin: 10,
            pagebreak: { mode: 'avoid-all' },
          })
          .from(element)
          .save(`Peticija za izbore ${name} ${id}.pdf`);
      }
    </script>
  </body>
</html>
