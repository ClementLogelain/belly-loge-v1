<template>
  <div class="app">
    <transition name="fade-slide" mode="out-in" @after-enter="onPageEntered">

      <!-- HOME PAGE -->
      <section v-if="page === 'home'" key="home" class="home-page">

        <!-- Hero -->
        <div class="hero" style="background-image: url('/panorama.jpeg')">
          <div class="hero-overlay"></div>
          <div class="hero-content">
            <h1>BELLY LŌGE</h1>
            <p class="hero-tagline">Parce que la santé, c'est notre liberté.</p>
            <a href="https://calendly.com/bellyloge/30min" target="_blank" class="hero-cta">Prendre rendez-vous</a>
          </div>
        </div>

        <!-- Programmes -->
        <div class="programs-section">
          <div class="programs-grid">
            <div class="prog-card prog-impact" @click="goToProgram('impact')">
              <div class="prog-overlay"></div>
              <div class="prog-meta">
                <strong>Impact</strong>
                <span>3 mois · 6 séances · 299€</span>
              </div>
            </div>
            <div class="prog-card prog-preco" @click="goToProgram('preconception')">
              <div class="prog-overlay"></div>
              <div class="prog-meta">
                <strong>Préconception & Grossesse</strong>
                <span>Sur-mesure</span>
              </div>
            </div>
            <div class="prog-card prog-sport" @click="goToProgram('sportif')">
              <div class="prog-overlay"></div>
              <div class="prog-meta">
                <strong>Sportif</strong>
                <span>3 mois · 6 séances · 299€</span>
              </div>
            </div>
            <div class="prog-card prog-other" @click="goToProgram('a-la-carte')">
              <div class="prog-overlay"></div>
              <div class="prog-meta">
                <strong>À la demande</strong>
                <span>1 séance · 55€</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Biographie -->
        <div class="content-section">
          <div class="card">
            <h2>Bienvenue, je suis Marine – Nutritionniste</h2>
            <p>Très jeune, j'ai commencé à chercher des moyens d'agir pour préserver sa santé et celle de ses proches, sans pour autant renoncer au plaisir ou à la liberté.</p>
            <p>Cette quête a éveillé en moi une grande curiosité, une profonde envie d'en apprendre plus, de comprendre le fonctionnement du corps humain… et surtout d'accompagner les autres à faire des choix éclairés pour eux-mêmes.</p>
            <p>C'est ainsi qu'est née ma vocation : guider chacun vers une alimentation plus consciente, plus respectueuse du corps, de la santé… et de la nature. Je ne propose ni de régime strict ni règles rigides, mais un accompagnement sur mesure, en phase avec votre histoire, vos besoins et vos objectifs.</p>
            <p>Mon approche est simple et humaine : vous aider, à votre rythme, par de petites actions, à adopter des habitudes durables qui font du bien aussi bien au corps qu'à l'esprit.</p>
            <p>Que vous cherchiez à retrouver un équilibre, à mieux comprendre ce que vous mettez dans votre assiette ou à atteindre un objectif précis en donnant au corps ce dont il a vraiment besoin, je suis là pour vous guider avec bienveillance et expertise.</p>
            <p>Parce que la santé, c'est notre liberté. Et celle-ci est entre vos mains.</p>
            <p>C'est avec mon background en nutrithérapie, et mes spécialisations en accompagnement de préconception, de la femme enceinte et du sportif que je peux vous proposer une approche simple et réaliste, pour vous aider, à votre rythme, par de petites actions, à adopter des habitudes durables qui font du bien autant au corps qu'à l'esprit.</p>
          </div>
        </div>

        <!-- Témoignages -->
        <div class="content-section">
          <div class="card">
            <h3 class="section-label">TÉMOIGNAGES</h3>
            <blockquote v-for="(t, i) in testimonials" :key="i">
              "{{ t.quote }}"
              <cite>— {{ t.author }}</cite>
            </blockquote>
          </div>
        </div>

      </section>

      <!-- DETAILS PAGE -->
      <div v-else key="details" class="details-page">
        <button class="back-button" @click="goHome">← Retour</button>

        <div class="offers-list">
          <div
            v-for="(offer, key) in programs"
            :key="key"
            :id="`offer-${key}`"
            class="offer-card"
          >
            <div class="offer-body">
              <h2 class="offer-title">{{ offer.title }}</h2>
              <div class="offer-price">
                <span class="price-main">{{ offer.price }}</span>
                <span v-if="offer.price_info" class="price-sub">{{ offer.price_info }}</span>
              </div>
              <p class="offer-tagline">{{ offer.tagline }}</p>
              <p v-if="offer.taglineExtra" class="offer-tagline">{{ offer.taglineExtra }}</p>
              <ul class="offer-features">
                <li v-for="(item, i) in offer.items" :key="i" v-html="item"></li>
              </ul>
              <a href="https://calendly.com/bellyloge/30min" target="_blank" class="offer-cta">Réserver ce programme</a>
            </div>
            <div class="offer-img" :style="`background-image: url('/${key}.jpeg')`"></div>
          </div>

          <!-- Services inclus -->
          <div class="offer-card services-card">
            <div class="offer-body">
              <h2 class="offer-title">Ce que comprend mes services :</h2>
              <ul class="offer-features">
                <li>Restauration de l'énergie</li>
                <li>Diagnostic et correction des déséquilibres alimentaires et des déficits nutritionnels</li>
                <li>Renforcement du système immunitaire</li>
                <li>Alimentation anti-inflammatoire, anti-toxique</li>
                <li>Protocoles d'assainissement de l'environnement, coscientisation des polluants</li>
                <li>Outils de gestion du stress</li>
                <li>Optimisation du sommeil</li>
                <li>Promotion d'un environnement sain comprenant le mouvement</li>
              </ul>
            </div>
          </div>
        </div>
      </div>

    </transition>

    <!-- Footer contact -->
    <footer class="contact">
      <h3 class="contact-title">CONTACT</h3>
      <div class="contact-links">
        <a href="https://instagram.com/Belly.Loge" target="_blank" aria-label="Instagram">
          <i class="fa-brands fa-instagram"></i>
        </a>
        <a href="tel:+32478252176" aria-label="Téléphone">
          <i class="fa-solid fa-phone"></i>
        </a>
        <a :href="mailtoLink" target="_blank" aria-label="Email">
          <i class="fa-solid fa-envelope"></i>
        </a>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, reactive } from "vue";

// ── Navigation ────────────────────────────────────────────────────
const page = ref("home");
const selected = ref(null);
const mailtoLink = "mailto:lemensmarine12@gmail.com?subject=Demande%20d%27infos%20-%20Belly%20LŌGE";

function goToProgram(key) {
  selected.value = key;
  page.value = "details";
}

function goHome() {
  page.value = "home";
}

function onPageEntered() {
  if (page.value === "details" && selected.value) {
    document.getElementById(`offer-${selected.value}`)?.scrollIntoView({ behavior: "auto", block: "start" });
  } else {
    window.scrollTo({ top: 0, behavior: "auto" });
  }
}

// ── Data ──────────────────────────────────────────────────────────
const programs = reactive({
  impact: {
    title: "Programme IMPACT",
    price: "299€",
    tagline: "3 mois · 6 séances — équilibre, santé & énergie",
    items: [
      "Questionnaire de pré-rencontre",
      "Plan structuré sur mesure pour atteindre les objectifs",
      "Mise en place de nouvelles habitudes saines et durables",
      "Ebook impact avec les informations essentielles et recettes",
      "Échange illimité entre les séances",
      "Conseils à garder pour la vie",
    ],
  },
  preconception: {
    title: "Programme PRÉCONCEPTION ET GROSSESSE",
    price: "Sur-mesure",
    tagline: "Accompagnement pour préconception, grossesse et post-partum",
    items: [
      "Questionnaire de pré-rencontre",
      "Mise en place de nouvelles habitudes saines et durables",
      "Ebook avec les informations importantes et recettes",
      "Échange illimité entre les séances",
      "Des conseils pour chacun des parents qui couvrent les différentes phases (préconception, grossesse, post-partum)",
    ],
  },
  sportif: {
    title: "Programme SPORTIF",
    price: "299€",
    tagline: "3 mois · 6 séances — adapté à l'entraînement",
    items: [
      "Questionnaire de pré-rencontre",
      "Plan structuré sur mesure pour atteindre les objectifs",
      "Mise en place de nouvelles habitudes saines et durables",
      "Ebook du sportif avec les informations essentielles et recettes",
      "Échange illimité entre les séances",
      "Des conseils adaptés en fonction du type d'activité, de la fréquence et des objectifs",
    ],
  },
  "a-la-carte": {
    title: "À la demande",
    price: "55€",
    price_info: "1 séance - sur mesure",
    tagline: "Première rencontre 45min 80€",
    taglineExtra: "Séance de suivis 30min 40€",
    items: [
      "Questionnaire de rencontre",
      "Réponse aux différents besoins",
      "Fiches outils",
      "Des conseils personnalisés",
    ],
  },
});

const testimonials = [
  {
    quote: "On voulait mettre toutes les chances de notre côté avant de concevoir notre bébé, et on a bien fait de venir voir Marine. Elle nous a aidés à mieux comprendre l'impact de l'alimentation et de l'environnement sur la fertilité, mais aussi sur la santé future de notre enfant. On a changé beaucoup de choses, en douceur, et aujourd'hui on se sent vraiment prêts. Merci pour ton écoute et ton accompagnement très humain.",
    author: "Hélène et Jérem",
  },
  {
    quote: "Grâce au suivi de Marine, j'ai enfin trouvé un équilibre alimentaire qui me correspond vraiment. J'ai gagné en énergie, j'ai perdu de la masse grasse sans sacrifier mes performances, et surtout, je récupère beaucoup mieux. Elle a su adapter ses conseils à ma charge d'entraînement et à mes objectifs. Je recommande à 100 %.",
    author: "Clément L.",
  },
  {
    quote: "Ce que je retiens de ce suivi, c'est bien plus qu'un changement physique. J'ai appris à écouter mon corps, à comprendre mes besoins, et à faire la paix avec mon alimentation. Marine m'a donné des clés concrètes, sans jamais me faire culpabiliser. Aujourd'hui, je me sens beaucoup plus sereine, dans mon assiette comme dans ma tête.",
    author: "Julie T.",
  },
  {
    quote: "Pendant ma grossesse, je voulais être sûre de bien faire, sans tomber dans l'excès. J'ai adapté mon alimentation, mieux choisi mes compléments, et compris l'impact de tout cela sur mon bébé… et même sur l'accouchement !! Un vrai soulagement de se sentir accompagnée avec bienveillance.",
    author: "Sophia L.",
  },
  {
    quote: "On peut dire que je m'y perdais complètement entre tous ces compléments, les conseils contradictoires, etc. Merci d'avoir su m'expliquer simplement ce qui était pertinent pour moi, et ce qui ne l'était pas. On avance bien aussi dans la prise de muscle + 1,5k tout en ayant l'air plus sec! Merci Marine!",
    author: "Raphaël M.",
  },
];
</script>

<style scoped>
/* ── Design tokens ──────────────────────────────────────────────── */
.app {
  --green:     #2b5d4d;
  --cream:     #F5EBE9;
  --warm-bg:   #FFF9F5;
  --border:    #e8e0dc;
  --text:      #1a1a1a;
  --muted:     #666;
  --shadow:    0 4px 16px rgba(0, 0, 0, 0.08);
  --radius:    10px;

  min-height: 100vh;
  background: var(--warm-bg);
  color: var(--text);
}

/* ── Hero ──────────────────────────────────────────────────────── */
.hero {
  height: 100vh;
  position: relative;
  background-size: cover;
  background-position: center;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.42);
}

.hero-content {
  position: relative;
  z-index: 1;
}

.hero-content h1 {
  font-style: italic;
  font-family: fangsong;
  font-size: clamp(40px, 8vw, 72px);
  letter-spacing: 4px;
  margin: 0 0 16px;
}

.hero-tagline {
  font-size: clamp(14px, 2vw, 18px);
  font-style: italic;
  opacity: 0.85;
  margin: 0 0 32px;
  letter-spacing: 1px;
}

.hero-cta {
  display: inline-block;
  padding: 14px 36px;
  background: white;
  color: var(--green);
  font-size: 15px;
  font-weight: 700;
  letter-spacing: 1px;
  border-radius: 50px;
  text-decoration: none;
  transition: background 0.2s, color 0.2s, transform 0.2s;
}

.hero-cta:hover {
  background: var(--green);
  color: white;
  transform: scale(1.04);
}

/* ── Programme cards ───────────────────────────────────────────── */
.programs-section {
  padding: 60px 10% 40px;
}

.programs-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 24px;
  max-width: 900px;
  margin: 0 auto;
}

.prog-card {
  height: 200px;
  border-radius: var(--radius);
  position: relative;
  cursor: pointer;
  display: flex;
  align-items: flex-end;
  padding: 18px;
  background-size: cover;
  background-position: center;
  color: white;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.prog-card:hover {
  transform: scale(1.03);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
}

.prog-overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.38);
  border-radius: var(--radius);
}

.prog-meta {
  position: relative;
  z-index: 1;
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.prog-meta strong { font-size: 16px; }
.prog-meta span   { font-size: 13px; opacity: 0.9; }

.prog-impact { background-image: url('/impact.jpeg'); }
.prog-preco  { background-image: url('/preconception.jpeg'); }
.prog-sport  { background-image: url('/sportif.jpeg'); }
.prog-other  { background-image: url('/a-la-carte.jpeg'); }

/* ── Bio & Testimonials cards ──────────────────────────────────── */
.content-section {
  padding: 0 10% 40px;
}

.card {
  background: white;
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 32px 40px;
  box-shadow: var(--shadow);
}

.card h2 {
  font-size: 20px;
  color: var(--green);
  margin: 0 0 20px;
}

.section-label {
  font-size: 18px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--green);
  margin: 0 0 24px;
}

.card p {
  line-height: 1.75;
  color: #444;
  margin: 0 0 14px;
}

.card p:last-child { margin-bottom: 0; }

blockquote {
  margin: 0 0 16px;
  padding: 16px 20px;
  background: var(--warm-bg);
  border-left: 3px solid var(--green);
  border-radius: 0 var(--radius) var(--radius) 0;
  font-style: italic;
  color: #444;
}

blockquote:last-child { margin-bottom: 0; }

cite {
  display: block;
  margin-top: 8px;
  font-size: 0.875em;
  font-style: normal;
  color: var(--muted);
}

/* ── Details page ──────────────────────────────────────────────── */
.details-page {
  min-height: 100vh;
  background: linear-gradient(135deg, #f9fafc, #eef1f6);
  padding-bottom: 40px;
}

.back-button {
  display: inline-block;
  margin: 28px 0 20px 5%;
  background: none;
  border: none;
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  color: var(--text);
  transition: color 0.2s;
}

.back-button:hover { color: var(--green); }

.offers-list {
  display: flex;
  flex-direction: column;
  gap: 24px;
  padding: 0 5%;
  max-width: 1100px;
  margin: 0 auto;
}

.offer-card {
  display: flex;
  background: white;
  border: 1px solid var(--border);
  border-radius: var(--radius);
  overflow: hidden;
  box-shadow: var(--shadow);
  transition: transform 0.2s, box-shadow 0.2s;
}

.offer-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
}

.services-card { background-color: #edf5f0; }

.offer-body {
  flex: 1;
  padding: 36px 40px;
  min-width: 0;
}

.offer-img {
  width: 40%;
  flex-shrink: 0;
  background-size: cover;
  background-position: center;
  background-color: var(--cream);
  min-height: 300px;
}

.offer-title {
  font-size: 22px;
  font-weight: 700;
  color: #333;
  margin: 0 0 12px;
  word-break: break-word;
}

.offer-price { margin-bottom: 8px; }

.price-main {
  font-size: 30px;
  font-weight: 800;
}

.price-sub {
  display: block;
  font-size: 15px;
  color: var(--muted);
  margin-top: 4px;
}

.offer-tagline {
  font-size: 14px;
  color: var(--muted);
}

.offer-features {
  list-style: none;
  padding: 0;
  margin: 0;
}

.offer-features li {
  position: relative;
  padding: 10px 0 10px 28px;
  font-size: 15px;
  color: #444;
  border-bottom: 1px solid var(--border);
}

.offer-features li:last-child { border-bottom: none; }

.offer-cta {
  display: inline-block;
  margin-top: 24px;
  padding: 12px 28px;
  background: var(--green);
  color: white;
  font-size: 14px;
  font-weight: 700;
  letter-spacing: 0.5px;
  border-radius: 50px;
  text-decoration: none;
  transition: background 0.2s, transform 0.2s;
}

.offer-cta:hover {
  background: #1e4035;
  transform: scale(1.03);
}

.offer-features li::before {
  content: "✔";
  position: absolute;
  left: 0;
  top: 12px;
  font-size: 12px;
  color: var(--green);
}

/* ── Contact footer ────────────────────────────────────────────── */
.contact {
  padding: 28px 0 32px;
  background: #1e4035;
  text-align: center;
}

.contact-title {
  font-size: 12px;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.5);
  margin: 0 0 16px;
}

.contact-links {
  display: flex;
  justify-content: center;
  gap: 40px;
}

.contact-links a {
  color: rgba(255, 255, 255, 0.85);
  font-size: 26px;
  text-decoration: none;
  transition: color 0.2s, transform 0.2s;
}

.contact-links a:hover {
  color: white;
  transform: scale(1.2);
}

/* ── Page transition ───────────────────────────────────────────── */
.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
  opacity: 0;
  transform: translateY(10px);
}

/* ── Responsive ────────────────────────────────────────────────── */
@media (max-width: 768px) {
  .programs-section { padding: 40px 5% 30px; }
  .programs-grid    { grid-template-columns: 1fr; }
  .content-section  { padding: 0 5% 30px; }
  .card             { padding: 24px 20px; }
  .offer-card       { flex-direction: column; }
  .offer-img        { width: 100%; min-height: 220px; }
  .offer-body       { padding: 24px 20px; }
}
</style>
