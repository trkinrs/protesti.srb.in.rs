---
layout: page
title: Peticija za vanredne izbore
---
<h2>Potpiši peticiju putem eUprave i Consent ID mobile aplikacije</h2>

U <b>samo 3 koraka</b> uz pomoć Consent ID mobilne aplikacije potpišite peticiju za manje od 2 minuta.

<h3>1. Napravite zahtev</h3>
Tekst peticije je sa <a href="https://drive.google.com/drive/folders/1EgTIIFL1BIAv3xT2u2bHpQOO_zhzDBa0" target="_blank">Drive</a>.
<iframe id="pdf-iframe" src='{{ 'izbori' | relative_url }}' frameborder="0" style="border=none!important; width: 100%; height: auto;"></iframe>

Popunite ovaj formular da generišete PDF sa vašim podacima (mi ne skupljamo vaše podatke, ali na žalost, obratite pažnju na eUpravu da ne dozvolite slanje
podataka Google).

<h3>2. Potpišite PDF</h3>
Zatim idite na sajt za potpisivanje <a href="https://cloud.eid.gov.rs/" target="_blank" >https://cloud.eid.gov.rs/</a>
<h3>3. Pošaljite mail sa peticijom</h3>
Kada završite potpisivanje, pošaljite potpisani dokument na <a href="mailto:uniplenum@gmail.com?subject=Potpisana%20peticija&body=U%20prilogu">uniplenum@gmail.com</a>

<script>
  const iframe = document.getElementById('pdf-iframe');
  iframe.onload = () => {
    const iframeDoc = iframe.contentDocument || iframe.contentWindow.document;
    iframe.style.height = iframeDoc.body.scrollHeight + "px";
  };
</script>


<iframe style="margin: auto" width="360" height="640"
  src="https://www.youtube.com/embed/1o0i0QAZZUQ"
  frameborder="0"
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
  allowfullscreen>
</iframe>
