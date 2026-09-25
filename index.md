---
layout: default
---

# Moin - Hier ein Einblick in meine Welt 


<div class="intro-container">
  <img src="/assets/Images/TR.jpeg" class="intro-image">
  <div class="intro-text">
    <h2>In Erinnerung an das was uns die Zeit nimmt.</h2>
    <p>Zeit verfliegt und ich versuche Sie einzufangen, doch scheiter – deswegen schreibe ich. Mit der Zeit werden meine Worte wohl auch vergehen doch noch fangen Sie, was mir immer wieder davon rennt. Mein Auf und Ab durch die Zeit. </p>
  </div>
</div>

<section class="bilderkarussell" aria-label="Meine Empfehlungen">
  <button class="karussell-pfeil karussell-zurueck"
          type="button" aria-label="Vorherige Bilder">
    &#10094;
  </button>

  <div class="karussell-fenster">
    <div class="karussell-reihe">
      <a class="karussell-bild" href="https://youtu.be/c-CsKFTh8e0"
        target="_blank"
        rel="noopener noreferrer">
        <img src="/assets/Images/ZeichnungYT.jpg">
      </a>
      <a class="karussell-bild" href="https://ontjemosambik.wordpress.com/"
       target="_blank"
       rel="noopener noreferrer">
        <img src="/assets/Images/MOZ.jpg">     
      </a> 
      <a class="karussell-bild" href="https://substack.com/@yurf1">
        <img src="/assets/Images/Room.jpeg">
      </a>
<!-- 
      <a class="karussell-bild" href="/OnWiriting/">
        <img src="/assets/Images/bild4.jpg"
             alt="Buchzusammenfassung zu On Writing lesen">
      </a>
      <a class="karussell-bild" href="/2026/">
        <img src="/assets/Images/bild5.jpg"
             alt="Tagebucheinträge lesen">
      </a>
 -->

    </div>
  </div>

  <button class="karussell-pfeil karussell-weiter"
          type="button" aria-label="Nächste Bilder">
    &#10095;
  </button>
</section>

<div style="margin-top: 3rem;"></div>


# Sachen die ich Interessant finde

<div class="tile-container">
  <a href="/Pernambuko/" class="tile tile-meinung">
    <h3>Pernambuco</h3>
    <p>Erinnerungen an ein Auslandssemster</p>
  </a>

  <a href="/PopulistischerOekonom/" class="tile tile-meinung">
    <h3>Einkommensungleichheit</h3>
    <p>Eine extreme Perspektive</p>
  </a>

</div>

<div style="margin-top: 3rem;"></div>

# Buchzusammenfassungen

<div class="tile-container">

  <a href="/OnWiriting/" class="tile tile-buecher">
    <h3>On Writing</h3>
    <p>Stephen King  
    -  
    Biographie und paar Schreibtipps</p>
  </a>

  <a href="/Bleibefreiheit/" class="tile tile-buecher">
    <h3>Bleibefreiheit</h3>
    <p>Eva Redeker  
      -  
    Was ist Freiheit?</p>
  </a>

</div>

<div style="margin-top: 3rem;"></div>

# Tagebucheinträge

<div class="tile-container">
  <a href="/2026/" class="tile tile-tagebuch">
    <h3>2026</h3>
    <p>Tagebucheinträge - Mal täglich mal auch nicht</p>
  </a>

   <a href="/AltesNotizheft.md/" class="tile tile-tagebuch">
    <h3>Erstes Tagebuch</h3>
    <p>Meine erste Sinneskrise und was ich gelernt habe</p>
  </a>

</div>

# Emotionale Beiträge

<div class="tile-container">
  <a href="/Dutschi/" class="tile tile-Emotional">
    <h3>Dutschi</h3>
    <p>Unausgesprochenes Schreiben</p>
  </a>
  <a href="/Flickenteppich/" class="tile tile-Emotional">
    <h3>Flickenteppich</h3>
    <p>Persöhnlichkeitverlust</p>
  </a>
</div>


<!-- Skripte für Website  -->
<script>
(() => {
  document.querySelectorAll(".bilderkarussell").forEach((karussell) => {
    const reihe = karussell.querySelector(".karussell-reihe");
    const bilder = Array.from(reihe.children);
    const zurueck = karussell.querySelector(".karussell-zurueck");
    const weiter = karussell.querySelector(".karussell-weiter");
    let start = 0;

    function anzeigen() {
      const anzahl = Math.min(
        bilder.length,
        parseInt(
          getComputedStyle(karussell)
            .getPropertyValue("--sichtbare-bilder"),
          10
        ) || 3
      );

      bilder.forEach((bild) => {
        bild.hidden = true;
        bild.style.display = "none";
      });

      for (let i = 0; i < anzahl; i++) {
        const bild = bilder[(start + i) % bilder.length];
        bild.hidden = false;
        bild.style.display = "block";
        reihe.appendChild(bild);
      }

      zurueck.disabled = bilder.length <= anzahl;
      weiter.disabled = bilder.length <= anzahl;
    }

    zurueck.addEventListener("click", () => {
      start = (start - 1 + bilder.length) % bilder.length;
      anzeigen();
    });

    weiter.addEventListener("click", () => {
      start = (start + 1) % bilder.length;
      anzeigen();
    });

    window.addEventListener("resize", anzeigen);
    anzeigen();
  });
})();
</script>