<template>
  <div style="height: 100vh; width: 100%;">
    <transition name="fade-slide" mode="out-in">
      <section v-if="page === 'home'" key="home" class="content-home">
        <!-- HERO IMAGE -->
        <div class="hero-wrapper" ref="wrapper">
          <section
              :key="index"
              class="hero"
              style="background-image: url('/panorama.jpeg')"
          >
            <div class="overlay"></div>
            <div class="hero-content"><h1>BELLY LŌGE</h1></div>
          </section>
        </div>

        <div ref="contentSection" class="container" style="margin-top: 100px">
          <div class="container">
            <!-- Programmes -->
            <div class="programs-strip">
              <div
                  class="prog-card prog-impact"
                  @click="goToProgram('impact')"
              >
                <div class="overlay-card"></div>
                <div class="meta">
                  <strong>Impact</strong>
                  <div>3 mois · 6 séances<br />250€</div>
                </div>
              </div>
              <div
                  class="prog-card prog-preco"
                  @click="goToProgram('preconception')"
              >
                <div class="overlay-card"></div>
                <div class="meta">
                  <strong>Préconception & Grossesse</strong>
                  <div>Sur-mesure</div>
                </div>
              </div>
              <div
                  class="prog-card prog-sport"
                  @click="goToProgram('sportif')"
              >
                <div class="overlay-card"></div>
                <div class="meta">
                  <strong>Sportif</strong>
                  <div>3 mois · 6 séances<br />250€</div>
                </div>
              </div>
              <div
                  class="prog-card prog-other"
                  @click="goToProgram('a-la-carte')"
              >
                <div class="overlay-card"></div>
                <div class="meta">
                  <strong>À la demande</strong>
                  <div>1 séance<br />50€</div>
                </div>
              </div>
            </div>

            <!-- Bio -->
            <div class="bio">
              <h2>Bienvenue, je suis Marine – Nutritionniste</h2>
              <p>
                Très jeune, j’ai commencé à chercher des moyens d’agir pour préserver sa santé et celle de ses proches, sans pour autant renoncer au plaisir ou à la liberté.
              </p>
              <p>
                Cette quête a éveillé en moi une grande curiosité, une profonde envie d’en apprendre plus, de comprendre le fonctionnement du corps humain… et surtout d’accompagner les autres à faire des choix éclairés pour eux-mêmes.
              </p>
              <p>
                C’est ainsi qu’est née ma vocation : guider chacun vers une alimentation plus consciente, plus respectueuse du corps, de la santé… et de la nature.
                Je ne propose ni de régime strict ni règles rigides, mais un accompagnement sur mesure, en phase avec votre histoire, vos besoins et vos objectifs.
              </p>
              <p>
                Mon approche est simple et humaine : vous aider, à votre rythme, par de petites actions, à adopter des habitudes durables qui font du bien aussi bien au corps qu’à l’esprit.
              </p>
              <p>
                Que vous cherchiez à retrouver un équilibre, à mieux comprendre ce que vous mettez dans votre assiette ou à atteindre un objectif précis en donnant au corps ce dont il a vraiment besoin, je suis là pour vous guider avec bienveillance et expertise.
              </p>
              <p>
                Parce que la santé, c’est notre liberté. Et celle-ci est entre vos mains.
              </p>
              <div>
                C’est avec mon background en nutrithérapie, et mes spécialisations en accompagnement de préconception, de la femme enceinte et du sportif que je peux vous proposer une approche simple et réaliste, pour vous aider, à votre rythme, par de petites actions, à adopter des habitudes durables qui font du bien autant au corps qu’à l’esprit.
              </div>
              <!--<h4 style="padding-top: 15px;">Mon Parcours :</h4>
              <ul class="styled-list">
                <li>CFNA Nutrithérapie — 2021-2022</li>
                <li>2024 — Chi Nei Tsang</li>
                <li>2024 — Precision Nutrition</li>
                <li>2025 — Nutrition préconception et grossesse</li>
              </ul>-->
            </div>

            <!-- Témoignages -->
            <div class="testimonials">
              <h3>TÉMOIGNAGES</h3>
              <blockquote>
                “On voulait mettre toutes les chances de notre côté avant de concevoir notre bébé, et on a bien fait de venir voir Marine. Elle nous a aidés à mieux comprendre l’impact de l’alimentation et de l’environnement sur la fertilité, mais aussi sur la santé future de notre enfant. On a changé beaucoup de choses, en douceur, et aujourd’hui on se sent vraiment prêts. Merci pour ton écoute et ton accompagnement très humain.”<br />
                <cite>— Hélène et Jérem</cite>
              </blockquote>
              <blockquote style="margin-top: 30px;">
                “Grâce au suivi de Marine, j’ai enfin trouvé un équilibre alimentaire qui me correspond vraiment. J’ai gagné en énergie, j’ai perdu de la masse grasse sans sacrifier mes performances, et surtout, je récupère beaucoup mieux. Elle a su adapter ses conseils à ma charge d’entraînement et à mes objectifs. Je recommande à 100 %.”<br />
                <cite>— Clément L.</cite>
              </blockquote>
              <blockquote style="margin-top: 30px;">
                “Ce que je retiens de ce suivi, c’est bien plus qu’un changement physique. J’ai appris à écouter mon corps, à comprendre mes besoins, et à faire la paix avec mon alimentation. Marine m’a donné des clés concrètes, sans jamais me faire culpabiliser. Aujourd’hui, je me sens beaucoup plus sereine, dans mon assiette comme dans ma tête.”<br />
                <cite>— Julie T.</cite>
              </blockquote>
              <blockquote style="margin-top: 30px;">
                “Pendant ma grossesse, je voulais être sûre de bien faire, sans tomber dans l’excès. J’ai adapté mon alimentation, mieux choisi mes compléments, et compris l’impact de tout cela sur mon bébé… et même sur l’accouchement !! Un vrai soulagement de se sentir accompagnée avec bienveillance.”<br />
                <cite>— Sophia L.</cite>
              </blockquote>
              <blockquote style="margin-top: 30px;">
                “On peut dire que je m’y perdais complètement entre tous ces compléments, les conseils contradictoires, etc. Merci d’avoir su m’expliquer simplement ce qui était pertinent pour moi, et ce qui ne l’était pas. On avance bien aussi dans la prise de muscle + 1,5k tout en ayant l’air plus sec! Merci Marine!”<br />
              </blockquote>
            </div>
          </div>
        </div>
      </section>

      <!-- PAGE 2 -->


      <div v-else style="background: linear-gradient(135deg, #f9fafc, #eef1f6); width:100%">
        <button class="back-button" @click="goHome">← Retour</button>
        <section class="offers-section">
          <div class="offers-container">
            <div class="offer-card" v-for="(offer, index) in programs" :key="index">
              <div class="offer-content">
                <h2 class="offer-title">{{ offer.title }}</h2>

                <div class="offer-price">
                  <span class="current-price">{{ offer.price }}</span>
                  <span v-if="offer.old" class="old-price">${{ offer.old }}</span>
                </div>

                <p class="offer-tagline">{{ offer.tagline }}</p>

                <div class="offer-features-box">
                  <ul class="offer-features">
                    <li v-for="(feature, i) in offer.items" :key="i" style="width: 90%">{{ feature }}</li>
                  </ul>
                </div>
              </div>
              <div :class="'offer-img-' + index" :style="`background-image: url(/` + index + `.jpeg);`">
              </div>
            </div>
            <div class="offer-card" style="background-color:  #F5EBE9; width: 80%">
              <div class="offer-content">
                <h2 class="offer-title">Ce que comprend mes services:</h2>

                <div class="offer-features-box" style="width: 80%">
                  <ul class="offer-features">
                    <li>Restauration de l’énergie</li>
                    <li>Diagnostic et correction des déséquilibres alimentaires et des déficits nutritionnels</li>
                    <li>Renforcement du système immunitaire</li>
                    <li>Alimentation anti-inflammatoire, anti-toxique</li>
                    <li>Protocoles d’assainissement de l’environnement, coscientisation des polluants</li>
                    <li>Outils de gestion du stress</li>
                    <li>Optimisation du sommeil</li>
                    <li>Promotion d’un environnement sain comprenant le mouvement</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </section>
      </div>


      <!--<section v-else style="padding-bottom: 20px;" class="content">
        <div class="container">
          <button class="btn-back" @click="goHome">← Retour</button>

          <div style="margin-left: 15%;">
            <h2>ACCOMPAGNEMENTS</h2>
            <div>J’ai développé un programme de nutrition sur mesure.</div>
          </div>

          <div
              class="program-full"
              v-for="(p, key) in programs"
              :key="key"
              :class="{ selected: selected === key }"
              @click="selectProgram(key)"
              style="display: inline-flex; width: 70%;"
          >
            <div style="width: 70%; padding: 30px 10% 30px 5%;">
              <h3>
                {{ p.title }}
                <span class="price">{{ p.price }}</span>
                <span v-if="p.old" class="oldprice">{{ p.old }}</span>
              </h3>
              <p v-if="p.tagline"><em>{{ p.tagline }}</em></p>

              <ul class="styled-list">
                <li v-for="item in p.items" :key="item">{{ item }}</li>
              </ul>

              <div class="actions">
                <a :href="mailtoLink"><button class="btn-primary">Contact</button></a>
              </div>
            </div>
            <div
                style="width: 50%; background-size: 100%; background-repeat: no-repeat;"
                :style="{ backgroundImage: `url('/` + key + `.jpeg')` }"
            >
            </div>
          </div>
        </div>
      </section>-->
    </transition>
    <!-- Contact -->
    <div class="contact">
      <h3 class="contact-title">CONTACT</h3>
      <div class="contact-list">
        <a href="https://instagram.com/Belly.Loge" target="_blank">
          <i class="fa-brands fa-instagram"></i>
        </a>
        <a href="tel:+32478252176" style="margin: 0 50px;">
          <i class="fa-solid fa-phone"></i>
        </a>
        <a :href="mailtoLink" target="_blank">
          <i class="fa-solid fa-envelope"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted, onUnmounted, watch, nextTick } from "vue";

const page = ref("home");
const selected = ref(null);
const contentSection = ref(null);

const programs = reactive({
  impact: {
    title: "Programme IMPACT",
    price: "250€ (au lieu de 280€)",
    old: "280€",
    tagline: "3 mois · 6 séances — équilibre, santé & énergie",
    items: [
      "Questionnaire de rencontre",
      "Plan structuré sur mesure pour atteindre les objectifs",
      "Mise en place de nouvelles habitudes saines et durables",
      "Ebook EQUILIBRE avec les informations essentielles et recettes",
      "Conseils à garder pour la vie",
    ],
  },
  preconception: {
    title: "Programme PRÉCONCEPTION ET GROSSESSE",
    price: "Sur-mesure",
    tagline:
        "Accompagnement pour préconception, grossesse et post-partum",
    items: [
      "Questionnaire de pré-rencontre",
      "Mise en place de nouvelles habitudes saines et durables",
      "Ebook avec les informations importantes et recettes",
      "Des conseils pour chacun des parents qui couvrent les différentes phases (préconception, grossesse, post-partum)",
    ],
  },
  sportif: {
    title: "Programme SPORTIF",
    price: "250€ (au lieu de 280€)",
    old: "280€",
    tagline: "3 mois · 6 séances — adapté à l’entraînement",
    items: [
      "Questionnaire de pré-rencontre",
      "Plan structuré sur mesure pour atteindre les objectifs",
      "Mise en place de nouvelles habitudes saines et durables",
      "Ebook du sportif avec les informations essentielles et recettes",
      "Des conseils adaptés en fonction du type d’activité, de la fréquence et des objectifs",
    ],
  },
  "a-la-carte": {
    title: "À la demande",
    price: "Sur demande",
    tagline: "Première rencontre 45min 80€\n" +
        "Séance de suivis 30min 40€",
    items: [
      "Questionnaire de rencontre",
      "Réponse aux différents besoins",
      "Fiches outils",
      "Des conseils personnalisés"
    ],
  },
});

const mailtoLink = "mailto:lemensmarine12@gmail.com?subject=Demande%20d%27infos%20-%20Belly%20LŌGE";

const wrapper = ref(null);
const currentIndex = ref(0);

function updateIndex() {
  if (wrapper.value) {
    currentIndex.value = Math.round(wrapper.value.scrollLeft / window.innerWidth);
  }
}

function goToProgram(key) {
  selected.value = key;
  page.value = "details";
}
function goHome() {
  page.value = "home";
  currentIndex.value = 0;

  nextTick(() => {
    if (wrapper.value) {
      wrapper.value.scrollTo({ left: 0, behavior: "auto" });
    }
    wrapper.value.addEventListener("scroll", updateIndex);
  });
}

onUnmounted(() => {
  document.title = "Belly LŌGE";
  window.removeEventListener("wheel", handleWheel);
});


watch(page, (newPage) => {
  if (selected) {
    if (selected.value === 'impact') {
      window.scrollTo({ top: 0, behavior: "auto" });
    }
    if (selected.value === 'preconception') {
      window.scrollTo({ top: 400, behavior: "auto" });
    }
    if (selected.value === 'sportif') {
      window.scrollTo({ top: 800, behavior: "auto" });
    }
    if (selected.value === 'a-la-carte') {
      window.scrollTo({ top: 1200, behavior: "auto" });
    }
  }
});
</script>

<style scoped>
/* HERO */
html, body, #app {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}
body {
  overflow: hidden;
}

.hero-wrapper {
  display: flex;
  overflow-x: hidden; /* no ugly scrollbar */
  scroll-snap-type: x mandatory;
  scroll-behavior: smooth;
}

.hero {
  min-width: 100%;
  height: 100vh;
  position: relative;
  scroll-snap-align: start;
  background-size: cover;
  background-position: center;
  color: white;
  text-align: center;
}

.overlay {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.4);
}

.hero-content {
  position: relative;
  top: 40%;
  transform: translateY(-40%);
}
.hero h1 {
  font-style: italic;
  font-family: fangsong;
  font-size: 60px;
  margin: 0;
}

@keyframes bounce {
  0%, 100% {
    transform: translate(-50%, 0);
  }
  50% {
    transform: translate(-50%, -10px);
  }
}

.container {
  width: 100%;
  margin: auto;
  font-family: fantasy;
}

/* PROGRAMS */
.programs-strip {
  padding-left: 10%;
  width: 80%;
  display: flex;
  flex-wrap: wrap;
  gap: 40px;
  justify-content: center;
  margin-bottom: 50px;
}
.prog-card {
  width: 350px;
  height: 140px;
  border-radius: 12px;
  position: relative;
  color: white;
  cursor: pointer;
  display: flex;
  align-items: flex-end;
  padding: 15px;
  background-size: cover;
  background-position: center;
  transition: transform 0.3s ease;
}
.prog-card:hover {
  transform: scale(1.10);
}
.prog-impact {
  background-image: url('/impact.jpeg');
}
.prog-preco {
  background-image: url('/preconception.jpeg');
}
.prog-sport {
  background-image: url('/sportif.jpeg');}
.prog-other {
  background-image: url('/a-la-carte.jpeg');}
.overlay-card {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.4);
  border-radius: 12px;
}
.meta {
  position: relative;
  z-index: 2;
}

.styled-list li {
  margin: 6px 0;
  padding-left: 20px;
  position: relative;
}
.styled-list li::before {
  content: "✔";
  position: absolute;
  left: 0;
  color: #2b5d4d;
}

/* BOXES */
.bio,
.testimonials{
  transition: transform 0.3s, color 0.3s;
  background: white;
  margin: 20px 15%;
  border: 1px solid lightgray;
  border-radius: 6px;
}
.bio,
.testimonials{
  background-color: #FFF9F5;
  padding: 15px 30px;
}
button:hover{
  cursor: pointer;
}
/* BUTTONS */
button {
  padding: 10px 16px;
  border-radius: 8px;
  border: none;
  cursor: pointer;
  font-size: 14px;
}
blockquote {
  margin: 12px 0;
  padding-left: 20px;
  border-left: 4px solid #2b5d4d;
  font-style: italic;
}
cite {
  display: block;
  margin-top: 4px;
  font-size: 0.9em;
  color: #333;
}
.contact {
  padding-top: 20px;
  padding-bottom: 30px;
  background-color: lightgrey;
  color: white;
}
.contact-title {
  display: flex;
  flex-direction: row;
  gap: 20px;
  flex-wrap: wrap;
  margin-bottom: 20px;
  justify-content: center;
  align-items: center;
}
.contact-list {
  display: flex;
  flex-direction: row;      /* desktop: in a row */
  gap: 20px;                /* spacing between links */
  flex-wrap: wrap;           /* wrap if needed */
  justify-content: center;   /* center horizontally on desktop */
  align-items: center;       /* center vertically if needed */
}


.contact-list a {
  color: grey;
  text-decoration: none;
  font-size: 28px;          /* make icons large enough */
  transition: transform 0.2s, color 0.3s;
}

.contact-list a:hover {
  color: black;             /* hover color */
  transform: scale(1.2);    /* small zoom on hover */
}


.offer-content {
  width: 120%
}

.offer-img-impact {
  width: 70%;
  height: 500px; /* or your preferred block height */
  background-repeat: no-repeat;
  background-size: 100% 100%; /* fills the entire div exactly */
  background-position: right center; /* 👈 align image fully to the right */
  background-color: #F5EBE9;
}
.offer-img-preconception {
  width: 60%;
  height: 500px; /* or your preferred block height */
  background-repeat: no-repeat;
  background-size: 100% 100%; /* fills the entire div exactly */
  background-position: right center; /* 👈 align image fully to the right */
  background-color: #F5EBE9;
}
.offer-img-sportif {
  width: 60%;
  height: 500px; /* or your preferred block height */
  background-repeat: no-repeat;
  background-size: 100% 100%; /* fills the entire div exactly */
  background-position: right center; /* 👈 align image fully to the right */
  background-color: #F5EBE9;
}
.offer-img-a-la-carte {
  width: 65%;
  height: 500px; /* or your preferred block height */
  background-repeat: no-repeat;
  background-size: 100% 100%; /* fills the entire div exactly */
  background-position: right center; /* 👈 align image fully to the right */
  background-color: #F5EBE9;
}

.offers-section {
  width: 80%;
  background: linear-gradient(135deg, #f9fafc, #eef1f6);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow-y: auto;
  padding-top: 10px;
  color: white;
}

.offers-container {
  display: grid;
  grid-template-columns: auto;
  gap: 20px;
  max-width: 1200px;
  width: 100%;
  overflow: hidden;
  padding-top: 10px;
  padding-right: 10%;
}

/* Card */
.offer-card {
  display: flex;
  justify-content: center;
  border: 1px solid lightgray;
  border-radius: 6px;
  font-weight: bold;
  margin-bottom: 100px;
}


.offer-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.12);
}

/* Tag */
.offer-tag {
  position: absolute;
  top: 16px;
  right: 16px;
  background: #e5ecff;
  color: #2f46ff;
  font-size: 12px;
  font-weight: 600;
  padding: 4px 10px;
  border-radius: 999px;
}

/* Title */
.offer-title {
  padding-left: 10%;
  font-size: 27px;
  font-weight: 700;
  color: #333;
  margin-bottom: 10px;
  justify-content: center;
  overflow-wrap: break-word;
  word-wrap: break-word;
  word-break: break-word; /* optional, aggressive breaking */
}

/* Price */
.offer-price {
  padding-left: 10%;
  margin-bottom: 16px;
}

.current-price {
  font-size: 32px;
  font-weight: 800;
  color: #000000;
}

.old-price {
  font-size: 16px;
  color: #999;
  text-decoration: line-through;
  margin-left: 8px;
}

/* Tagline */
.offer-tagline {
  font-size: 14px;
  color: #555;padding-left: 10%;
  margin-bottom: 20px;
}

.offer-features-box {
  width:100%;
}
.offer-features {
  position: relative;;
  list-style: none;
  padding: 0;
  margin: 0 0 30px 0;
  width: 100%;
}

.offer-features li {
  width: 100%;
  margin-left: 5%;
  height: 10%;
  font-size: 16px;
  color: #444;
  padding: 15px 0;
  text-align: left;
}

.offer-features-img img {
  width: 300px;
}

/* Button */
.offer-button {
  background: #2f46ff;
  color: #fff;
  border: none;
  border-radius: 8px;
  padding: 12px 20px;
  font-size: 15px;
  font-weight: 600;
  cursor: pointer;
  margin-left: 20%;
  width: 20%;
  transition: background 0.3s ease;
}

.offer-button:hover {
  background: #1f34d1;
}

.back-button {
  margin-top: 3%;
  margin-left: 2%;
  align-self: flex-start;
  background: none;
  border: none;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  margin-bottom: 30px;
  transition: color 0.3s ease;
}

.back-button:hover {
  color: #4a4848;
}

@media (min-width: 800px) {
  .offers-section {
    padding-left: 10%;
  }
}

@media (max-width: 650px) {
  .offers-section {
    width: 90%;
  }
}

@media (max-width: 400px) {
  .offer-card {
    margin-left: 5%;
  }
}

@media (max-width: 800px) {
  .offer-card {
    width: 80%;
  }
  .offer-card:nth-child(1) {
    display: grid;
  }
  .offer-card:nth-child(2) {
    display: inline;
  }
  .offer-card:nth-child(3) {
    display: inline;
  }
  .offer-card:nth-child(4) {
    display: inline;
  }

  .offer-img-impact {
    width: 100%;
    height: 350px; /* or your preferred block height */
    background-repeat: no-repeat;
    background-size: 100% 100%; /* fills the entire div exactly */
    background-position: center; /* 👈 align image fully to the right */
    background-color: #F5EBE9;
  }
  .offer-img-preconception {
    width: 100%;
    height: 350px; /* or your preferred block height */
    background-repeat: no-repeat;
    background-size: 100% 100%; /* fills the entire div exactly */
    background-position: center; /* 👈 align image fully to the right */
    background-color: #F5EBE9;
  }
  .offer-img-sportif {
    width: 100%;
    height: 350px; /* or your preferred block height */
    background-repeat: no-repeat;
    background-size: 100% 100%; /* fills the entire div exactly */
    background-position: center; /* 👈 align image fully to the right */
    background-color: #F5EBE9;
  }
  .offer-img-a-la-carte {
    width: 100%;
    height: 350px; /* or your preferred block height */
    background-repeat: no-repeat;
    background-size: 100% 100%; /* fills the entire div exactly */
    background-position: center; /* 👈 align image fully to the right */
    background-color: #F5EBE9;
  }

  .offer-content {
    width: 100%;
  }

}

@media (max-width: 765px) {
  .bio,
  .testimonials {
    margin: 20px 5%;
  }
}

@media (min-width: 600px) and (max-width: 800px) {
  .offer-card {
    margin-left: 25%;
    width: 370px;
  }
}

@media (min-width: 550px) and (max-width: 600px) {
  .offer-card {
    margin-left: 25%;
    width: 370px;
  }
}

@media (max-width: 550px) {
  .offer-card {
    margin-left: 20%;
  }

  .offer-title {
    width: 90%;
  }

  .offer-tagline {
    width: 90%;
    padding-left: 5%;
  }
}
</style>
