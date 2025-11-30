<script setup>
import { ref, watch } from 'vue'
import juliePhoto from './assets/julie.jpg'

const scrollToId = (id) => {
  const el = document.getElementById(id)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}

// État du menu mobile
const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenuAndScroll = (id) => {
  isMenuOpen.value = false
  scrollToId(id)
}

// Bloquer le scroll quand le menu est ouvert (comme ton site)
watch(isMenuOpen, (open) => {
  document.body.style.overflow = open ? 'hidden' : ''
})
</script>

<template>
  <div class="page-root">
    <div class="bg-orb"></div>

    <!-- NAVBAR -->
    <header class="nav">
      <div class="container nav-inner">
        <div class="nav-logo">
          <div class="logo-mark">
            <div class="logo-mark-inner">JS</div>
          </div>
          <div class="nav-title">
            <span>Julie Sion</span>
            <span>Adjointe en magasin – Retail</span>
          </div>
        </div>

        <!-- Liens desktop -->
        <nav class="nav-links nav-links-desktop">
          <a href="#about" @click.prevent="scrollToId('about')">À propos</a>
          <a href="#experience" @click.prevent="scrollToId('experience')">Expérience</a>
          <a href="#skills" @click.prevent="scrollToId('skills')">Compétences</a>
          <a href="#contact" @click.prevent="scrollToId('contact')">Contact</a>
          <button class="btn btn-ghost nav-cta" @click="scrollToId('contact')">
            Me contacter
          </button>
        </nav>

        <!-- Burger mobile -->
        <button
          type="button"
          class="nav-burger"
          :class="{ 'nav-burger-open': isMenuOpen }"
          @click="toggleMenu"
        >
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>

      <!-- Overlay menu mobile -->
      <transition name="nav-overlay">
        <div v-if="isMenuOpen" class="nav-overlay">
          <div class="nav-overlay-inner">
            <div class="nav-overlay-header">
              <div class="nav-logo">
                <div class="logo-mark">
                  <div class="logo-mark-inner">JS</div>
                </div>
                <div class="nav-title">
                  <span>Julie Sion</span>
                  <span>Adjointe en magasin – Retail</span>
                </div>
              </div>
              <button type="button" class="nav-overlay-close" @click="toggleMenu">
                ✕
              </button>
            </div>

            <ul class="nav-overlay-list">
              <li>
                <button type="button" @click="closeMenuAndScroll('top')">
                  Accueil
                </button>
              </li>
              <li>
                <button type="button" @click="closeMenuAndScroll('about')">
                  À propos
                </button>
              </li>
              <li>
                <button type="button" @click="closeMenuAndScroll('experience')">
                  Expérience
                </button>
              </li>
              <li>
                <button type="button" @click="closeMenuAndScroll('skills')">
                  Compétences
                </button>
              </li>
              <li>
                <button type="button" @click="closeMenuAndScroll('contact')">
                  Contact
                </button>
              </li>
            </ul>
          </div>
        </div>
      </transition>
    </header>

    <main class="page">
      <!-- HERO -->
      <section class="hero" id="top">
        <div class="container hero-grid">
          <!-- VISUEL CARTE (en haut sur mobile) -->
          <div class="hero-visual">
            <article class="hero-card">
              <div class="hero-card-inner">
                <div class="avatar-row">
                  <div class="avatar">
                    <div class="avatar-inner">
                      <img :src="juliePhoto" alt="Portrait de Julie Sion" />
                    </div>
                  </div>
                  <div class="avatar-info">
                    <h2>Julie Sion</h2>
                    <span>Adjointe en magasin – Chevalier</span>
                    <span class="muted">Basée à Seynod (74) – Permis B</span>
                  </div>
                </div>
                <div class="hero-pill">
                  <span class="chip-dot"></span>
                  En poste depuis novembre 2025 – Chevalier
                </div>
                <div class="hero-stats">
                  <div class="stat-card">
                    <div class="stat-label">Expérience retail</div>
                    <div class="stat-value">+7 ans</div>
                  </div>
                  <div class="stat-card">
                    <div class="stat-label">Spécialité</div>
                    <div class="stat-value">Gestion d’équipe &amp; client</div>
                  </div>
                </div>
                <p class="hero-note">
                  « Je garde les pieds sur le terrain et les yeux sur les indicateurs. L’un ne va pas sans l’autre. »
                </p>
                <div class="hero-floating-tag">
                  <span class="dot"></span>
                  Shift, ouverture, fermeture, caisse, équipe : tout est sous contrôle.
                </div>
              </div>
              <div class="hero-ring"></div>
            </article>
          </div>

          <!-- TEXTE HERO -->
          <div>
            <div class="hero-badge">
              <span class="chip">
                <span class="chip-dot"></span>
                Disponible pour opportunités retail &amp; management
              </span>
            </div>
            <h1 class="hero-title">
              Adjointe qui fait tourner<br />
              <span class="accent">le magasin et l'équipe.</span>
            </h1>
            <p class="hero-subtitle">
              <strong>7 ans d’expérience terrain</strong> en vente et management, du comptoir à la gestion d’équipe.
              Aujourd’hui adjointe en magasin chez <strong>Chevalier</strong>, Julie pilote le quotidien du point de
              vente, la performance et l’expérience client.
            </p>
            <div class="hero-actions">
              <a href="Julie_Sion_cv.pdf" class="btn btn-primary">
                Télécharger le CV
              </a>
              <button class="btn btn-ghost" @click="scrollToId('experience')">
                Voir le parcours
              </button>
            </div>
            <p class="hero-tagline">
              Management de proximité, organisation millimétrée, priorité au client : une adjointe capable de tenir un
              shift comme de faire monter l’équipe en puissance.
            </p>
          </div>
        </div>
      </section>

      <!-- ABOUT -->
      <section id="about">
        <div class="container">
          <div class="section-header">
            <span class="section-kicker">Profil</span>
            <h2 class="section-title">À propos de Julie</h2>
            <p class="section-desc">
              Une adjointe issue du terrain, passée par la vente, la restauration et la grande distribution
              avant de prendre des responsabilités de management.
            </p>
          </div>

          <div class="about-grid">
            <div class="about-text">
              <p>
                Julie a construit son expérience sur le terrain, au contact direct des clients, des équipes et des contraintes
                opérationnelles. De la boulangerie au second de rayon, jusqu’au rôle de Shift Leader chez Normal A/S,
                elle a appris à gérer un magasin dans le détail comme dans sa globalité.
              </p>
              <p>
                Aujourd’hui adjointe en magasin chez <strong>Chevalier</strong>, elle combine
                <strong>management de proximité</strong>, <strong>organisation du point de vente</strong>
                et <strong>culture du résultat</strong>. Elle sait encadrer une équipe, tenir un shift, sécuriser les
                procédures et maintenir un niveau d’accueil client irréprochable.
              </p>
              <p>
                Son style : claire dans ses consignes, présente sur le terrain, fiable sur l’exécution. Une adjointe capable
                d’être à la fois relais du/de la responsable et repère pour l’équipe.
              </p>
            </div>

            <div class="about-highlights">
              <div class="highlight-card">
                <div class="highlight-label">Années d’expérience</div>
                <div class="highlight-value">7 ans en continu</div>
              </div>
              <div class="highlight-card">
                <div class="highlight-label">Secteurs</div>
                <div class="highlight-value">Retail, alimentaire, service</div>
              </div>
              <div class="highlight-card">
                <div class="highlight-label">Forces</div>
                <div class="highlight-value">Organisation, fiabilité, relation client</div>
              </div>
              <div class="highlight-card">
                <div class="highlight-label">Localisation</div>
                <div class="highlight-value">Seynod (74) – mobile</div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- EXPERIENCE -->
      <section id="experience">
        <div class="container">
          <div class="section-header">
            <span class="section-kicker">Parcours</span>
            <h2 class="section-title">Expériences professionnelles</h2>
            <p class="section-desc">
              Un fil conducteur clair : la relation client, le rythme du magasin et la montée en compétences vers le management.
            </p>
          </div>

          <div class="exp-grid">
            <div>
              <div class="timeline">
                <!-- Chevalier -->
                <div class="timeline-item">
                  <div class="timeline-line">
                    <div class="timeline-dot"></div>
                    <div class="timeline-stem"></div>
                  </div>
                  <div class="timeline-content">
                    <div class="timeline-header">
                      <div>
                        <div class="timeline-role">Adjointe en magasin</div>
                        <div class="timeline-company">Chevalier – [Ville à préciser]</div>
                      </div>
                      <div class="timeline-meta">Depuis nov. 2025</div>
                    </div>
                    <div class="timeline-badges">
                      <span class="badge">Encadrement opérationnel</span>
                      <span class="badge">Organisation magasin</span>
                      <span class="badge">Relation client</span>
                    </div>
                    <ul class="timeline-list">
                      <li>Participation au pilotage quotidien du magasin aux côtés du/de la responsable.</li>
                      <li>Encadrement opérationnel de l’équipe sur le terrain (briefs, priorités, suivi).</li>
                      <li>Contribution à la qualité de l’accueil client et au respect des standards de l’enseigne.</li>
                      <li>Appui sur le suivi des objectifs commerciaux et des indicateurs de performance.</li>
                    </ul>
                  </div>
                </div>

                <!-- Normal A/S -->
                <div class="timeline-item">
                  <div class="timeline-line">
                    <div class="timeline-dot"></div>
                    <div class="timeline-stem"></div>
                  </div>
                  <div class="timeline-content">
                    <div class="timeline-header">
                      <div>
                        <div class="timeline-role">Shift Leader</div>
                        <div class="timeline-company">Normal A/S – Epagny</div>
                      </div>
                      <div class="timeline-meta">2025 – 2025</div>
                    </div>
                    <div class="timeline-badges">
                      <span class="badge">Management</span>
                      <span class="badge">Ouverture / fermeture</span>
                      <span class="badge">Mise en rayon</span>
                    </div>
                    <ul class="timeline-list">
                      <li>Encadrement des équipes en magasin et relais du/de la responsable sur le terrain.</li>
                      <li>Application des procédures et des priorités opérationnelles de l’enseigne.</li>
                      <li>Mise en place des rayons et respect du concept Normal A/S.</li>
                      <li>Contribution à l’atteinte des objectifs magasins et gestion des flux clients.</li>
                      <li>Ouverture, fermeture, supervision des caisses et gestion du coffre.</li>
                    </ul>
                  </div>
                </div>

                <!-- SA Albert Pougnier -->
                <div class="timeline-item">
                  <div class="timeline-line">
                    <div class="timeline-dot"></div>
                    <div class="timeline-stem"></div>
                  </div>
                  <div class="timeline-content">
                    <div class="timeline-header">
                      <div>
                        <div class="timeline-role">Vendeuse / Serveuse</div>
                        <div class="timeline-company">SA Albert Pougnier – Genève</div>
                      </div>
                      <div class="timeline-meta">Oct. 2023 – Janv. 2025</div>
                    </div>
                    <div class="timeline-badges">
                      <span class="badge">Service client</span>
                      <span class="badge">Encaissement</span>
                    </div>
                    <ul class="timeline-list">
                      <li>Accueil, conseil et fidélisation de la clientèle.</li>
                      <li>Service au comptoir et encaissement des commandes.</li>
                      <li>Entretien et mise en valeur de l’espace de vente.</li>
                      <li>Gestion des pics d’affluence avec un bon niveau de service.</li>
                    </ul>
                  </div>
                </div>

                <!-- Fresh Belley -->
                <div class="timeline-item">
                  <div class="timeline-line">
                    <div class="timeline-dot"></div>
                    <div class="timeline-stem"></div>
                  </div>
                  <div class="timeline-content">
                    <div class="timeline-header">
                      <div>
                        <div class="timeline-role">Second de rayon</div>
                        <div class="timeline-company">Fresh – Belley</div>
                      </div>
                      <div class="timeline-meta">Déc. 2022 – Sept. 2023</div>
                    </div>
                    <div class="timeline-badges">
                      <span class="badge">Gestion de stock</span>
                      <span class="badge">Réassort</span>
                    </div>
                    <ul class="timeline-list">
                      <li>Gestion des stocks, du réassort et des commandes sur le rayon.</li>
                      <li>Réception, contrôle des livraisons et mise en rayon.</li>
                      <li>Respect des règles d’hygiène et de sécurité.</li>
                      <li>Participation au développement du chiffre d’affaires du rayon.</li>
                    </ul>
                  </div>
                </div>

                <!-- Boulangerie Bourgeois -->
                <div class="timeline-item">
                  <div class="timeline-line">
                    <div class="timeline-dot"></div>
                  </div>
                  <div class="timeline-content">
                    <div class="timeline-header">
                      <div>
                        <div class="timeline-role">Vendeuse / Serveuse</div>
                        <div class="timeline-company">Boulangerie Pâtisserie Bourgeois – Seyssel</div>
                      </div>
                      <div class="timeline-meta">Juin 2018 – Nov. 2022</div>
                    </div>
                    <div class="timeline-badges">
                      <span class="badge">Vente</span>
                      <span class="badge">Encaissement</span>
                      <span class="badge">Mise en vitrine</span>
                    </div>
                    <ul class="timeline-list">
                      <li>Accueil, vente et encaissement en boulangerie-pâtisserie.</li>
                      <li>Mise en vitrine et valorisation des produits.</li>
                      <li>Préparation des commandes clients et gestion des demandes spécifiques.</li>
                      <li>Maintien de la propreté et de la présentation du point de vente.</li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>

            <div class="exp-side">
              <div class="exp-card">
                <strong>Un parcours cohérent.</strong><br />
                Julie n’a pas « changé de métier » tous les six mois : elle est restée dans le retail, le service
                et la relation client, en gagnant progressivement en responsabilités et en maîtrise du magasin.
              </div>
              <div class="exp-card">
                <strong>Une adjointe issue du terrain.</strong><br />
                Elle sait ce que vivent les équipes parce qu’elle l’a fait, longtemps. Ce passé de vendeuse,
                serveuse et second de rayon fait d’elle une adjointe crédible et légitime auprès de l’équipe.
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- SKILLS -->
      <section id="skills">
        <div class="container">
          <div class="section-header">
            <span class="section-kicker">Compétences</span>
            <h2 class="section-title">Ce que Julie sait faire</h2>
            <p class="section-desc">
              Des compétences concrètes, utiles en magasin immédiatement. Pas de buzzwords inutiles, juste ce qui sert
              au quotidien.
            </p>
          </div>

          <div class="skills-grid">
            <div class="skills-group">
              <h3>Compétences métiers</h3>
              <div class="tag-grid">
                <span class="tag">Management d’équipe</span>
                <span class="tag">Encadrement de shift</span>
                <span class="tag">Ouverture &amp; fermeture</span>
                <span class="tag">Organisation du magasin</span>
                <span class="tag">Relation client</span>
                <span class="tag">Fidélisation</span>
                <span class="tag">Mise en rayon &amp; merchandising</span>
                <span class="tag">Gestion de stock / commandes</span>
                <span class="tag">Réception &amp; contrôle des livraisons</span>
                <span class="tag">Encaissement &amp; caisse</span>
                <span class="tag">Respect des procédures</span>
                <span class="tag">Hygiène &amp; sécurité</span>
              </div>
            </div>

            <div class="skills-group">
              <h3>Savoir-être &amp; façon de travailler</h3>
              <div class="pill-list">
                <div class="pill-item">Adaptable à différents univers (boulangerie, grande distrib, service)</div>
                <div class="pill-item">Efficace en équipe comme en autonomie</div>
                <div class="pill-item">Bonne gestion du rythme et des priorités</div>
                <div class="pill-item">Exigeante sur la qualité du service</div>
                <div class="pill-item">Communication claire avec les collègues</div>
                <div class="pill-item">Présente sur le terrain, pas enfermée en réserve</div>
              </div>
            </div>
          </div>

          <div class="skills-grid mt-md">
            <div class="skills-group">
              <h3>Formation</h3>
              <p class="mt-xs muted">
                <strong>Baccalauréat commerce / marketing</strong> – 2016<br />
                Base solide en vente, communication et techniques commerciales.
              </p>
            </div>
            <div class="skills-group">
              <h3>Centres d’intérêt</h3>
              <div class="tag-grid">
                <span class="tag">Mode</span>
                <span class="tag">Musculation</span>
                <span class="tag">Équitation</span>
                <span class="tag">Lecture</span>
                <span class="tag">Musique</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- CONTACT -->
      <section id="contact">
        <div class="container">
          <div class="section-header">
            <span class="section-kicker">Contact</span>
            <h2 class="section-title">Envie de travailler avec Julie ?</h2>
            <p class="section-desc">
              Pour un poste d’adjointe, de responsable de secteur ou de bras droit en magasin, le plus simple est encore
              de la contacter directement.
            </p>
          </div>

          <div class="contact-card">
            <div class="contact-text">
              <p>
                <strong>Claire dans le discours, fiable dans l’exécution.</strong><br />
                Julie est le profil à l’aise aussi bien en caisse qu’en briefing d’équipe. Elle connaît les contraintes
                terrain et les attentes d’une direction. Si vous cherchez une adjointe capable de prendre le relais sans
                perdre le contact avec le magasin, vous êtes au bon endroit.
              </p>
            </div>
            <div class="contact-details">
              <span><span class="dot"></span> Basée à Annecy</span>
              <span><span class="dot"></span> Email :
                <a href="mailto:julie.sionpro@gmail.com">julie.sionpro@gmail.com</a>
              </span>
              <span><span class="dot"></span> Permis B – véhiculée</span>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      Portfolio réalisé pour présenter le parcours professionnel de Julie Sion. Contenu basé sur son CV et son expérience réelle.
      <br>
      <div id="footerRights"><p class="icon-copyright">2012 PoettaTech. All Rights Reserved |</p><p>Designed &amp; created by <span>Poetta</span>@PoettaTech WSDS</p></div>
    </footer>
  </div>
</template>
