<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>L'élevage des petits félins — Chatterie Familiale en France</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,600;0,700;1,600&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg-cream: #FAF8F5;
      --card-white: #FFFFFF;
      --ink-dark: #231F20;
      --ink-muted: #57534E;
      --accent-amber: #9A5B25;
      --accent-sage: #2E5A44;
      --border-warm: #E6DFD5;
    }
    html { scroll-behavior: smooth; font-size: 16px; }
    html.large-text { font-size: 18.5px; }
    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background-color: var(--bg-cream);
      color: var(--ink-dark);
      line-height: 1.65;
    }
    h1, h2, h3, .font-serif-display {
      font-family: 'Cormorant Garamond', Georgia, serif;
    }
    .nav-btn.active {
      background-color: #231F20;
      color: #FFFFFF;
    }
    .receipt-paper {
      background: #FFFDF9;
      border: 1px dashed #B8AFA6;
      font-family: 'Courier New', Courier, monospace;
      max-width: 390px;
      margin: 0 auto;
    }
    @media print {
      body * { visibility: hidden; }
      #printableDossierArea, #printableDossierArea * { visibility: visible; }
      #printableDossierArea { position: absolute; left: 0; top: 0; width: 100%; }
    }
  </style>
  <script>
    // Optional: set your production keys directly here OR via the "Administration Élevage" panel on the site
    window.APP_CONFIG = {
      SUPABASE_URL: "",       // ex: "https://votre-projet.supabase.co"
      SUPABASE_ANON_KEY: "",  // ex: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
      EMAIL_WEBHOOK_URL: "/api/send-email"
    };
  </script>
</head>
<body class="antialiased selection:bg-amber-200/60">

  <!-- TOP HEADER -->
  <header class="sticky top-0 z-40 bg-[#FAF8F5]/95 backdrop-blur border-b border-[#E6DFD5]">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 h-20 flex items-center justify-between gap-3">
      <button type="button" data-nav="home" class="text-left focus:outline-none">
        <span class="block font-serif-display text-2xl sm:text-3xl font-bold tracking-tight text-[#231F20]">
          L'élevage des petits félins
        </span>
        <span class="block text-xs text-[#57534E] tracking-wide">
          Chatterie familiale &bull; Accompagnement personnalisé en France
        </span>
      </button>

      <!-- Desktop Navigation -->
      <nav class="hidden lg:flex items-center gap-1.5" aria-label="Navigation principale">
        <button type="button" data-nav="home" class="nav-btn active px-3.5 py-2 rounded-lg text-sm font-semibold transition-colors">Accueil</button>
        <button type="button" data-nav="inventory" class="nav-btn px-3.5 py-2 rounded-lg text-sm font-semibold text-[#231F20] hover:bg-stone-200/70 transition-colors">Nos chatons</button>
        <button type="button" data-nav="application" class="nav-btn px-3.5 py-2 rounded-lg text-sm font-semibold text-[#231F20] hover:bg-stone-200/70 transition-colors">Candidature</button>
        <button type="button" data-nav="tracking" class="nav-btn px-3.5 py-2 rounded-lg text-sm font-semibold text-[#231F20] hover:bg-stone-200/70 transition-colors">Suivi &amp; Dossier</button>
        <button type="button" data-nav="contact" class="nav-btn px-3.5 py-2 rounded-lg text-sm font-semibold text-[#231F20] hover:bg-stone-200/70 transition-colors">Paiement &amp; Contact</button>
      </nav>

      <!-- Accessibility + Menu Controls -->
      <div class="flex items-center gap-2">
        <button type="button" id="textSizeToggle" class="px-3 py-2 rounded-lg border border-[#D6CEC2] bg-white text-xs sm:text-sm font-semibold text-[#231F20] hover:bg-stone-100" title="Agrandir la taille du texte">
          Grand texte
        </button>
        <button type="button" id="menuToggleBtn" aria-expanded="false" aria-controls="mobileDrawer" class="px-3.5 py-2 rounded-lg bg-[#231F20] text-white text-sm font-semibold flex items-center gap-2 hover:bg-stone-800">
          <span>Menu</span>
          <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16"/></svg>
        </button>
      </div>
    </div>
  </header>

  <!-- SLIDE-OUT NAVIGATION DRAWER -->
  <div id="drawerBackdrop" class="fixed inset-0 bg-black/40 z-50 hidden pointer-events-none"></div>
  <aside id="mobileDrawer" class="fixed top-0 right-0 h-full w-80 max-w-[88vw] bg-white z-50 border-l border-[#E6DFD5] shadow-2xl p-6 flex flex-col justify-between hidden pointer-events-none" aria-label="Menu latéral">
    <div>
      <div class="flex items-center justify-between pb-4 border-b border-[#E6DFD5]">
        <span class="font-serif-display text-xl font-bold">Menu principal</span>
        <button type="button" id="drawerCloseBtn" class="px-3 py-1.5 rounded-lg border border-[#D6CEC2] text-sm font-semibold hover:bg-stone-100">Fermer</button>
      </div>
      <div class="mt-5 flex flex-col gap-2">
        <button type="button" data-nav="home" class="w-full text-left px-4 py-3 rounded-xl font-semibold hover:bg-stone-100">1. Accueil &amp; Présentation</button>
        <button type="button" data-nav="inventory" class="w-full text-left px-4 py-3 rounded-xl font-semibold hover:bg-stone-100">2. Nos chatons</button>
        <button type="button" data-nav="application" class="w-full text-left px-4 py-3 rounded-xl font-semibold hover:bg-stone-100">3. Formulaire de candidature</button>
        <button type="button" data-nav="tracking" class="w-full text-left px-4 py-3 rounded-xl font-semibold hover:bg-stone-100">4. Suivi &amp; Documents DTV</button>
        <button type="button" data-nav="contact" class="w-full text-left px-4 py-3 rounded-xl font-semibold hover:bg-stone-100">5. Paiement &amp; Contact</button>
      </div>
    </div>
    <div class="pt-4 border-t border-[#E6DFD5] space-y-3">
      <button type="button" id="openAdminFromDrawer" class="w-full px-4 py-2.5 rounded-xl border border-stone-300 text-xs font-semibold text-stone-700 hover:bg-stone-100">
        Administration Élevage (Supabase)
      </button>
      <p class="text-xs text-[#57534E]">
        Assistance directe :<br>
        <strong class="text-[#231F20]">+33 7 48 25 85 22</strong><br>
        maisonpourchats@gmail.com
      </p>
    </div>
  </aside>

  <!-- MAIN CONTENT -->
  <main class="max-w-7xl mx-auto px-4 sm:px-6 py-8 sm:py-12 space-y-16">

    <!-- SECTION 1: ACCUEIL -->
    <section id="sec-home" class="page-section space-y-10">
      <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 sm:p-10 lg:p-12 grid lg:grid-cols-12 gap-8 items-center">
        <div class="lg:col-span-7 space-y-5">
          <span class="inline-block px-3 py-1 rounded-full bg-amber-100/80 text-[#9A5B25] text-xs font-bold uppercase tracking-wider">
            Élevage familial agréé &bull; Socialisation douce
          </span>
          <h1 class="text-3xl sm:text-5xl font-bold leading-tight text-[#231F20]">
            Des compagnons équilibrés, élevés au cœur de notre foyer.
          </h1>
          <p class="text-base sm:text-lg text-[#57534E] max-w-2xl">
            Chaque chaton grandit entouré d'attention, habitué aux bruits de la maison et suivi par notre vétérinaire avant de rejoindre sa famille partout en France.
          </p>
          <div class="flex flex-wrap gap-3 pt-2">
            <button type="button" data-nav="inventory" class="px-6 py-3.5 rounded-xl bg-[#231F20] text-white font-semibold text-sm sm:text-base hover:bg-stone-800">
              Découvrir nos chatons
            </button>
            <button type="button" data-nav="tracking" class="px-6 py-3.5 rounded-xl border border-[#231F20] bg-white text-[#231F20] font-semibold text-sm sm:text-base hover:bg-stone-100">
              Suivre mon dossier
            </button>
          </div>
        </div>
        <div class="lg:col-span-5">
          <div class="rounded-2xl overflow-hidden border border-[#E6DFD5] bg-stone-100 aspect-[4/3]">
            <img src="https://images.unsplash.com/photo-1574158622682-e40e69881006?auto=format&fit=crop&w=900&q=80" alt="Chaton de l'élevage des petits félins" class="w-full h-full object-cover" />
          </div>
        </div>
      </div>

      <!-- 3-Step Adoption Process -->
      <div class="grid md:grid-cols-3 gap-6">
        <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 space-y-2">
          <span class="text-xs font-bold uppercase tracking-wider text-[#9A5B25]">Étape 1</span>
          <h2 class="text-2xl font-bold">Choix &amp; Candidature</h2>
          <p class="text-sm text-[#57534E]">Sélectionnez le chaton qui correspond à votre foyer et remplissez le questionnaire d'accueil pour recevoir votre numéro de suivi.</p>
        </div>
        <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 space-y-2">
          <span class="text-xs font-bold uppercase tracking-wider text-[#9A5B25]">Étape 2</span>
          <h2 class="text-2xl font-bold">Validation &amp; Acompte</h2>
          <p class="text-sm text-[#57534E]">Après étude de votre dossier, vous recevez l'e-mail d'approbation. Le règlement de l'acompte débloque vos documents officiels et verrouille la réservation.</p>
        </div>
        <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 space-y-2">
          <span class="text-xs font-bold uppercase tracking-wider text-[#9A5B25]">Étape 3</span>
          <h2 class="text-2xl font-bold">Livraison &amp; Remise</h2>
          <p class="text-sm text-[#57534E]">Les fichiers PDF en ligne servent d'aperçu officiel ; l'ensemble des originaux papier signés vous est remis en main propre lors de la livraison.</p>
        </div>
      </div>
    </section>

    <!-- SECTION 2: NOS CHATONS (INVENTORY) -->
    <section id="sec-inventory" class="page-section hidden space-y-6">
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-4 border-b border-[#E6DFD5] pb-5">
        <div>
          <h2 class="text-3xl sm:text-4xl font-bold">Nos chatons</h2>
          <p class="text-sm sm:text-base text-[#57534E] mt-1">
            Consultez les fiches individuelles, les tempéraments et les tarifs. Un acompte est demandé pour toute réservation définitive.
          </p>
        </div>
        <div class="flex flex-wrap gap-2" role="group" aria-label="Filtrer les chatons">
          <button type="button" data-filter="all" class="filter-btn px-3.5 py-2 rounded-lg bg-[#231F20] text-white text-xs sm:text-sm font-semibold">Tous</button>
          <button type="button" data-filter="available" class="filter-btn px-3.5 py-2 rounded-lg bg-white border border-[#D6CEC2] text-xs sm:text-sm font-semibold">Disponibles</button>
          <button type="button" data-filter="pending" class="filter-btn px-3.5 py-2 rounded-lg bg-white border border-[#D6CEC2] text-xs sm:text-sm font-semibold">Prochainement</button>
          <button type="button" data-filter="adopted" class="filter-btn px-3.5 py-2 rounded-lg bg-white border border-[#D6CEC2] text-xs sm:text-sm font-semibold">Adoptés</button>
        </div>
      </div>

      <div id="kittenGrid" class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6"></div>
    </section>

    <!-- SECTION 3: FORMULAIRE DE CANDIDATURE -->
    <section id="sec-application" class="page-section hidden max-w-3xl mx-auto space-y-6">
      <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 sm:p-8 space-y-6">
        <div class="border-b border-[#E6DFD5] pb-4">
          <span class="text-xs font-bold uppercase tracking-wider text-[#9A5B25]">Dossier d'adoption</span>
          <h2 class="text-3xl font-bold mt-1">Formulaire de candidature</h2>
          <p class="text-sm text-[#57534E] mt-1">
            Ces informations nous permettent de vérifier la bonne adéquation entre votre cadre de vie et les besoins du chaton.
          </p>
        </div>

        <div id="selectedKittenBanner" class="p-4 rounded-xl bg-amber-50 border border-amber-200 flex flex-col sm:flex-row sm:items-center justify-between gap-3">
          <div>
            <span class="text-xs font-bold uppercase text-[#9A5B25]">Chaton sélectionné</span>
            <p id="selectedKittenLabel" class="font-bold text-base text-[#231F20]">Aucun chaton choisi — sélectionnez-en un dans la liste</p>
            <p id="selectedKittenPriceNote" class="text-xs text-[#57534E]"></p>
          </div>
          <button type="button" data-nav="inventory" class="px-3.5 py-2 rounded-lg bg-white border border-amber-300 text-xs font-semibold text-[#231F20] hover:bg-amber-100">
            Changer de chaton
          </button>
        </div>

        <form id="applicationForm" class="space-y-5">
          <input type="hidden" id="appKittenId" name="kittenId" />

          <div class="grid sm:grid-cols-2 gap-4">
            <div>
              <label for="appFirstName" class="block text-sm font-semibold mb-1">Prénom *</label>
              <input id="appFirstName" type="text" required placeholder="Ex. Claire" class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white focus:outline-none focus:border-[#231F20]" />
            </div>
            <div>
              <label for="appLastName" class="block text-sm font-semibold mb-1">Nom de famille *</label>
              <input id="appLastName" type="text" required placeholder="Ex. Moreau" class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white focus:outline-none focus:border-[#231F20]" />
            </div>
          </div>

          <div class="grid sm:grid-cols-2 gap-4">
            <div>
              <label for="appEmail" class="block text-sm font-semibold mb-1">Adresse e-mail *</label>
              <input id="appEmail" type="email" required placeholder="claire.moreau@exemple.fr" class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white focus:outline-none focus:border-[#231F20]" />
            </div>
            <div>
              <label for="appPhone" class="block text-sm font-semibold mb-1">Téléphone (WhatsApp / Mobile) *</label>
              <input id="appPhone" type="tel" required placeholder="+33 6 12 34 56 78" class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white focus:outline-none focus:border-[#231F20]" />
            </div>
          </div>

          <div>
            <label for="appAddress" class="block text-sm font-semibold mb-1">Ville, code postal &amp; adresse de livraison souhaitée *</label>
            <input id="appAddress" type="text" required placeholder="Ex. 14 Rue des Lilas, 69003 Lyon" class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white focus:outline-none focus:border-[#231F20]" />
          </div>

          <div class="grid sm:grid-cols-2 gap-4">
            <div>
              <label for="appHousingType" class="block text-sm font-semibold mb-1">Type de logement *</label>
              <select id="appHousingType" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white">
                <option value="Appartement">Appartement</option>
                <option value="Maison individuelle">Maison individuelle</option>
                <option value="Maison de ville avec cour">Maison de ville avec cour</option>
              </select>
            </div>
            <div>
              <label for="appIndoorOutdoor" class="block text-sm font-semibold mb-1">Mode de vie prévu *</label>
              <select id="appIndoorOutdoor" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white">
                <option value="Intérieur exclusivement">Intérieur exclusivement</option>
                <option value="Intérieur avec balcon / terrasse sécurisée">Intérieur avec balcon / terrasse sécurisée</option>
                <option value="Accès jardin clos et sécurisé">Accès jardin clos et sécurisé</option>
              </select>
            </div>
          </div>

          <div class="grid sm:grid-cols-2 gap-4">
            <div>
              <label for="appChildren" class="block text-sm font-semibold mb-1">Enfants au foyer *</label>
              <select id="appChildren" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white">
                <option value="Aucun enfant">Aucun enfant</option>
                <option value="Enfants de moins de 6 ans">Enfants de moins de 6 ans</option>
                <option value="Enfants de 6 à 14 ans">Enfants de 6 à 14 ans</option>
                <option value="Adolescents (15 ans et plus)">Adolescents (15 ans et plus)</option>
              </select>
            </div>
            <div>
              <label for="appOtherPets" class="block text-sm font-semibold mb-1">Autres animaux à la maison *</label>
              <select id="appOtherPets" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white">
                <option value="Aucun autre animal">Aucun autre animal</option>
                <option value="Un ou plusieurs chats">Un ou plusieurs chats</option>
                <option value="Un chien habitué aux chats">Un chien habitué aux chats</option>
                <option value="Autre petit compagnon">Autre petit compagnon</option>
              </select>
            </div>
          </div>

          <div class="grid sm:grid-cols-2 gap-4">
            <div>
              <label for="appDeliveryMode" class="block text-sm font-semibold mb-1">Mode de remise souhaité *</label>
              <select id="appDeliveryMode" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white">
                <option value="Transporteur animalier agréé DTV à domicile">Transporteur animalier agréé DTV à domicile</option>
                <option value="Retrait sur rendez-vous à la chatterie">Retrait sur rendez-vous à la chatterie</option>
              </select>
            </div>
            <div>
              <label for="appPaymentMethod" class="block text-sm font-semibold mb-1">Mode de règlement privilégié *</label>
              <select id="appPaymentMethod" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white">
                <option value="Virement bancaire SEPA (Acompte + Solde à la livraison)">Virement bancaire SEPA (Acompte + Solde à la livraison)</option>
                <option value="Lien carte sécurisé (Acompte + Solde à la livraison)">Lien carte sécurisé (Acompte + Solde à la livraison)</option>
              </select>
            </div>
          </div>

          <div>
            <label for="appNotes" class="block text-sm font-semibold mb-1">Parlez-nous de votre foyer &amp; de vos disponibilités</label>
            <textarea id="appNotes" rows="3" placeholder="Présence en journée, créneau idéal pour l'accueil..." class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] focus:bg-white focus:outline-none focus:border-[#231F20]"></textarea>
          </div>

          <button type="submit" class="w-full py-3.5 rounded-xl bg-[#231F20] text-white font-semibold text-base hover:bg-stone-800">
            Envoyer ma candidature &amp; générer mon numéro de suivi
          </button>
        </form>

        <!-- Confirmation box after submission -->
        <div id="applicationSuccessBox" class="hidden p-5 rounded-xl bg-emerald-50 border border-emerald-200 space-y-3">
          <div class="flex items-center justify-between">
            <span class="text-xs font-bold uppercase tracking-wider text-emerald-800">Candidature enregistrée &bull; E-mail de bienvenue #1 envoyé</span>
          </div>
          <p class="text-sm text-emerald-950">
            Votre numéro d'identification de suivi est : <strong id="generatedTrackingId" class="text-lg font-mono"></strong>
          </p>
          <p id="welcomeEmailPreview" class="text-xs text-emerald-900 bg-white/80 p-3 rounded-lg border border-emerald-200 whitespace-pre-line"></p>
          <button type="button" id="goToMyTrackingBtn" class="px-4 py-2.5 rounded-lg bg-emerald-800 text-white text-sm font-semibold hover:bg-emerald-900">
            Accéder à mon espace de suivi
          </button>
        </div>
      </div>
    </section>

    <!-- SECTION 4: SUIVI & DOSSIER OFFICIEL -->
    <section id="sec-tracking" class="page-section hidden max-w-4xl mx-auto space-y-6">
      <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 sm:p-8 space-y-6">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 border-b border-[#E6DFD5] pb-4">
          <div>
            <h2 class="text-3xl font-bold">Suivi d'adoption &amp; Documents officiels</h2>
            <p class="text-sm text-[#57534E] mt-1">Saisissez votre numéro de suivi (ex. LPF-8421) pour consulter l'avancement de votre dossier.</p>
          </div>
          <button type="button" id="openAdminFromTracking" class="px-3.5 py-2 rounded-lg border border-stone-300 text-xs font-semibold text-stone-700 hover:bg-stone-100 self-start">
            Administration Élevage
          </button>
        </div>

        <form id="trackingLookupForm" class="flex flex-col sm:flex-row gap-3">
          <input id="trackingInput" type="text" required placeholder="Entrez votre numéro de dossier (ex. LPF-XXXX)" class="flex-1 px-4 py-3 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5] font-mono uppercase focus:bg-white focus:outline-none focus:border-[#231F20]" />
          <button type="submit" class="px-6 py-3 rounded-xl bg-[#231F20] text-white font-semibold hover:bg-stone-800">
            Rechercher mon dossier
          </button>
        </form>

        <div id="trackingError" class="hidden p-4 rounded-xl bg-red-50 border border-red-200 text-sm text-red-800"></div>

        <!-- Result Container -->
        <div id="trackingResult" class="hidden space-y-6">
          <!-- Status Banner -->
          <div id="trackingStatusBanner" class="p-5 rounded-xl border space-y-2"></div>

          <!-- Summary Grid -->
          <div class="grid sm:grid-cols-2 gap-4 bg-[#FAF8F5] p-5 rounded-xl border border-[#E6DFD5] text-sm">
            <div><span class="text-[#57534E]">Adoptant :</span> <strong id="trkAdopter"></strong></div>
            <div><span class="text-[#57534E]">Chaton :</span> <strong id="trkKitten"></strong></div>
            <div><span class="text-[#57534E]">Destination :</span> <strong id="trkAddress"></strong></div>
            <div><span class="text-[#57534E]">Tarif &amp; Acompte :</span> <strong id="trkPricing"></strong></div>
            <div><span class="text-[#57534E]">Date de livraison prévue :</span> <strong id="trkDeliveryDate"></strong></div>
            <div><span class="text-[#57534E]">Mode de transport :</span> <strong id="trkTransport"></strong></div>
          </div>

          <!-- Phone Maps Launcher -->
          <div class="p-4 rounded-xl bg-white border border-[#E6DFD5] flex flex-col sm:flex-row sm:items-center justify-between gap-3">
            <div>
              <p class="font-semibold text-sm">Itinéraire vers votre domicile</p>
              <p class="text-xs text-[#57534E]">Ouvrez directement l'adresse de livraison dans l'application Plans ou Google Maps de votre téléphone.</p>
            </div>
            <a id="openPhoneMapsLink" href="https://maps.google.com" target="_blank" rel="noopener noreferrer" class="px-4 py-2.5 rounded-xl bg-[#2E5A44] text-white text-xs sm:text-sm font-semibold text-center hover:bg-emerald-900">
              Ouvrir dans Plans / Google Maps
            </a>
          </div>

          <!-- GATED DOCUMENTS AREA -->
          <div id="documentsGateNotice" class="p-5 rounded-xl bg-amber-50 border border-amber-300 space-y-3">
            <h3 class="text-xl font-bold text-amber-950">Accès au Bon de livraison, Livret d'accueil &amp; Certificat</h3>
            <p id="documentsGateText" class="text-sm text-amber-900"></p>
            <div class="flex flex-wrap gap-3">
              <button type="button" data-nav="contact" class="px-4 py-2.5 rounded-xl bg-[#9A5B25] text-white text-sm font-semibold hover:bg-amber-800">
                Procéder au règlement de l'acompte
              </button>
            </div>
          </div>

          <!-- UNLOCKED DOCUMENTS (Shown ONLY when confirmed === true AND paid === true) -->
          <div id="unlockedDocumentsSection" class="hidden space-y-6">
            <div class="p-4 rounded-xl bg-emerald-50 border border-emerald-200 flex flex-col sm:flex-row sm:items-center justify-between gap-3">
              <div>
                <p class="font-bold text-sm text-emerald-950">Documents débloqués — Aperçu numérique</p>
                <p class="text-xs text-emerald-900">
                  Ces fichiers PDF constituent votre exemplaire numérique. Les originaux papier signés vous seront remis en main propre le jour de la livraison.
                </p>
              </div>
              <button type="button" id="printReceiptBtn" class="px-4 py-2.5 rounded-xl bg-[#231F20] text-white text-xs sm:text-sm font-semibold hover:bg-stone-800">
                Imprimer / Enregistrer en PDF
              </button>
            </div>

            <div id="printableDossierArea" class="grid lg:grid-cols-12 gap-6 items-start">
              <!-- TALL COURIER RECEIPT PAPER (Bon de livraison) -->
              <div class="lg:col-span-5 receipt-paper p-5 rounded-lg shadow-sm text-xs text-stone-900 space-y-3">
                <div class="text-center border-b border-dashed border-stone-400 pb-3">
                  <p class="font-bold text-sm uppercase tracking-wider">L'ÉLEVAGE DES PETITS FÉLINS</p>
                  <p>BON DE LIVRAISON &amp; TRANSPORT DTV</p>
                  <p class="mt-1 font-bold" id="rcptRef"></p>
                  <p class="tracking-widest text-[10px] mt-1">||||| || |||| ||| ||||| || ||||</p>
                </div>
                <div class="space-y-1 border-b border-dashed border-stone-400 pb-3">
                  <p><strong>EXPÉDITEUR :</strong> Chatterie LPF (France)</p>
                  <p><strong>DESTINATAIRE :</strong> <span id="rcptClient"></span></p>
                  <p><strong>TÉLÉPHONE :</strong> <span id="rcptPhone"></span></p>
                  <p><strong>ADRESSE :</strong> <span id="rcptAddress"></span></p>
                </div>
                <div class="space-y-1 border-b border-dashed border-stone-400 pb-3">
                  <p><strong>CHATON :</strong> <span id="rcptKitten"></span></p>
                  <p><strong>IDENTIFICATION :</strong> Puce électronique + Passeport EU</p>
                  <p><strong>DATE PROGRAMMÉE :</strong> <span id="rcptDate"></span></p>
                  <p><strong>CRÉNEAU :</strong> 09h00 – 13h00 (Appel 30 min avant)</p>
                </div>
                <div class="space-y-1 border-b border-dashed border-stone-400 pb-3">
                  <p><strong>MODE :</strong> <span id="rcptPayMethod"></span></p>
                  <p><strong>PRIX TOTAL :</strong> <span id="rcptTotal"></span></p>
                  <p><strong>ACOMPTE RÉGLÉ :</strong> <span id="rcptDeposit"></span> [PAYÉ]</p>
                  <p><strong>SOLDE À LA LIVRAISON :</strong> <span id="rcptBalance"></span></p>
                </div>
                <div class="space-y-1 border-b border-dashed border-stone-400 pb-3">
                  <p class="font-bold">DOCUMENTS ORIGINAUX REMIS :</p>
                  <p>[X] Certificat vétérinaire de bonne santé</p>
                  <p>[X] Carnet de santé &amp; primo-vaccination</p>
                  <p>[X] Attestation de cession originale</p>
                  <p>[X] Livret d'accueil imprimé</p>
                </div>
                <div class="pt-2 space-y-4">
                  <p class="text-[11px]">Exemplaire numérique. Les originaux papier signés accompagnent le chaton à la livraison.</p>
                  <div class="grid grid-cols-2 gap-3 pt-2">
                    <div>
                      <p class="text-[10px]">Signature Élevage / Convoyeur :</p>
                      <div class="h-10 border-b border-stone-500 italic pt-3">L'élevage LPF</div>
                    </div>
                    <div>
                      <p class="text-[10px]">Signature Adoptant :</p>
                      <div class="h-10 border-b border-stone-500"></div>
                    </div>
                  </div>
                </div>
              </div>

              <!-- LIVRET D'ACCUEIL & CERTIFICAT D'ADOPTION -->
              <div class="lg:col-span-7 space-y-5">
                <div class="bg-white border border-[#E6DFD5] rounded-xl p-5 space-y-2">
                  <span class="text-xs font-bold uppercase text-[#9A5B25]">Document 2 &bull; Aperçu numérique</span>
                  <h3 class="text-2xl font-bold">Certificat de Réservation &amp; d'Adoption</h3>
                  <p class="text-sm text-[#57534E]" id="certBodyText"></p>
                </div>
                <div class="bg-white border border-[#E6DFD5] rounded-xl p-5 space-y-2">
                  <span class="text-xs font-bold uppercase text-[#2E5A44]">Document 3 &bull; Guide pratique</span>
                  <h3 class="text-2xl font-bold">Livret d'accueil du chaton</h3>
                  <ul class="text-sm text-[#57534E] list-disc pl-5 space-y-1.5">
                    <li><strong>Les 48 premières heures :</strong> Installez le chaton dans une pièce calme avec sa litière, son eau fraîche et ses croquettes habituelles (transition progressive sur 10 jours).</li>
                    <li><strong>Suivi vétérinaire :</strong> Rappels de vaccins et vermifuge indiqués dans le carnet original remis lors de la livraison.</li>
                    <li><strong>Assistance à vie :</strong> Notre équipe reste disponible au +33 7 48 25 85 22 pour toute question d'adaptation.</li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- SECTION 5: PAIEMENT & CONTACT -->
    <section id="sec-contact" class="page-section hidden max-w-4xl mx-auto grid md:grid-cols-2 gap-6">
      <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 sm:p-8 space-y-4">
        <span class="text-xs font-bold uppercase tracking-wider text-[#9A5B25]">Règlement sécurisé</span>
        <h2 class="text-3xl font-bold">Acompte &amp; Solde à la livraison</h2>
        <p class="text-sm text-[#57534E]">
          Pour valider définitivement votre réservation et débloquer vos documents officiels en ligne, un acompte est requis après approbation de votre candidature. Le <strong>solde à la livraison</strong> correspond au montant restant dû lors de la remise du chaton.
        </p>
        <div class="p-4 rounded-xl bg-[#FAF8F5] border border-[#E6DFD5] space-y-2 text-sm">
          <p><strong>Titulaire :</strong> L'élevage des petits félins</p>
          <p><strong>Référence à indiquer :</strong> Votre numéro de dossier (ex. LPF-XXXX)</p>
          <p><strong>Contact règlement &amp; RIB :</strong> maisonpourchats@gmail.com</p>
          <p><strong>WhatsApp direct :</strong> +33 7 48 25 85 22</p>
        </div>
      </div>

      <div class="bg-white border border-[#E6DFD5] rounded-2xl p-6 sm:p-8 space-y-4">
        <span class="text-xs font-bold uppercase tracking-wider text-[#2E5A44]">Nous écrire</span>
        <h2 class="text-3xl font-bold">Contacter la chatterie</h2>
        <form id="contactForm" class="space-y-4">
          <div>
            <label for="cntName" class="block text-sm font-semibold mb-1">Votre nom *</label>
            <input id="cntName" type="text" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5]" />
          </div>
          <div>
            <label for="cntRef" class="block text-sm font-semibold mb-1">Numéro de dossier (optionnel)</label>
            <input id="cntRef" type="text" placeholder="LPF-XXXX" class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5]" />
          </div>
          <div>
            <label for="cntMessage" class="block text-sm font-semibold mb-1">Votre message *</label>
            <textarea id="cntMessage" rows="3" required class="w-full px-3.5 py-2.5 rounded-xl border border-[#D6CEC2] bg-[#FAF8F5]"></textarea>
          </div>
          <div class="flex flex-wrap gap-2.5">
            <button type="submit" class="px-5 py-2.5 rounded-xl bg-[#231F20] text-white text-sm font-semibold hover:bg-stone-800">
              Envoyer par e-mail
            </button>
            <button type="button" id="whatsappDirectBtn" class="px-5 py-2.5 rounded-xl bg-[#2E5A44] text-white text-sm font-semibold hover:bg-emerald-900">
              Ouvrir WhatsApp
            </button>
          </div>
        </form>
      </div>
    </section>

  </main>

  <!-- FOOTER -->
  <footer class="border-t border-[#E6DFD5] bg-white mt-16">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 py-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-[#57534E]">
      <p>&copy; 2026 L'élevage des petits félins — Tous droits réservés.</p>
      <div class="flex items-center gap-4">
        <span>maisonpourchats@gmail.com</span>
        <span>+33 7 48 25 85 22</span>
        <button type="button" id="openAdminFromFooter" class="underline hover:text-[#231F20]">Administration</button>
      </div>
    </div>
  </footer>

  <!-- NON-INTRUSIVE BOTTOM-RIGHT LIVE ACTIVITY TOAST -->
  <div id="liveActivityToast" class="fixed bottom-4 right-4 z-30 max-w-xs bg-white border border-[#E6DFD5] shadow-lg rounded-xl p-3.5 text-xs hidden">
    <div class="flex items-start justify-between gap-2">
      <div>
        <span class="inline-block w-2 h-2 rounded-full bg-emerald-600 mr-1.5"></span>
        <span class="font-bold text-[#231F20]">Activité de la chatterie</span>
        <p id="liveActivityText" class="text-[#57534E] mt-1"></p>
      </div>
      <button type="button" id="dismissToastBtn" class="text-stone-400 hover:text-stone-700 font-bold px-1" aria-label="Fermer">&times;</button>
    </div>
  </div>

  <!-- BREEDER ADMINISTRATION MODAL (SUPABASE + VERIFICATION CONTROLS) -->
  <div id="adminModal" class="fixed inset-0 bg-black/50 z-50 flex items-center justify-center p-4 hidden pointer-events-none">
    <div class="bg-white border border-[#E6DFD5] rounded-2xl max-w-3xl w-full max-h-[90vh] overflow-y-auto p-6 space-y-6 shadow-2xl">
      <div class="flex items-center justify-between border-b border-[#E6DFD5] pb-3">
        <h3 class="text-2xl font-bold">Administration Élevage &amp; Supabase</h3>
        <button type="button" id="closeAdminModalBtn" class="px-3 py-1.5 rounded-lg border border-stone-300 text-sm font-semibold hover:bg-stone-100">Fermer</button>
      </div>

      <!-- Supabase & Vercel Credentials Form -->
      <form id="supabaseConfigForm" class="bg-[#FAF8F5] p-4 rounded-xl border border-[#E6DFD5] space-y-3">
        <p class="text-xs font-bold uppercase text-[#9A5B25]">Connexion Base de données Supabase &amp; E-mails Vercel</p>
        <div class="grid sm:grid-cols-2 gap-3">
          <div>
            <label class="block text-xs font-semibold mb-1">Supabase Project URL</label>
            <input id="cfgSupabaseUrl" type="url" placeholder="https://xxxx.supabase.co" class="w-full px-3 py-2 rounded-lg border border-stone-300 bg-white text-xs" />
          </div>
          <div>
            <label class="block text-xs font-semibold mb-1">Supabase Anon Public Key</label>
            <input id="cfgSupabaseKey" type="text" placeholder="eyJhbGciOi..." class="w-full px-3 py-2 rounded-lg border border-stone-300 bg-white text-xs" />
          </div>
        </div>
        <div>
          <label class="block text-xs font-semibold mb-1">Endpoint E-mails Vercel / Edge Function</label>
          <input id="cfgEmailWebhook" type="text" placeholder="/api/send-email" class="w-full px-3 py-2 rounded-lg border border-stone-300 bg-white text-xs" />
        </div>
        <div class="flex items-center justify-between gap-3">
          <span id="supabaseStatusText" class="text-xs text-[#57534E]">Stockage local actif</span>
          <button type="submit" class="px-4 py-2 rounded-lg bg-[#231F20] text-white text-xs font-semibold hover:bg-stone-800">
            Enregistrer &amp; Synchroniser
          </button>
        </div>
      </form>

      <!-- Dossiers Management List -->
      <div class="space-y-3">
        <h4 class="text-lg font-bold">Dossiers enregistrés</h4>
        <div id="adminDossiersList" class="space-y-3 text-sm"></div>
      </div>
    </div>
  </div>

  <script>
    // =========================================================================
    // 1. CATALOGUE DE 30 CHATONS (VARIÉS EN RACES, TEMPÉRAMENTS & TARIFS)
    // =========================================================================
    const KITTENS = [
      { id: "LPF-K01", name: "Noisette", breed: "British Shorthair", age: "12 semaines", sex: "Femelle", price: 1150, status: "available", temperament: "Douce, calme et très câline", img: "https://images.unsplash.com/photo-1592194996308-7b43878e84a6?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K02", name: "Céleste", breed: "Ragdoll", age: "13 semaines", sex: "Femelle", price: 1350, status: "available", temperament: "Pot-de-colle, adore les bras", img: "https://images.unsplash.com/photo-1513245543132-31f507417b26?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K03", name: "Milo", breed: "Maine Coon", age: "14 semaines", sex: "Mâle", price: 1450, status: "available", temperament: "Joueur, sociable avec les enfants", img: "https://images.unsplash.com/photo-1533738363-b7f9aef128ce?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K04", name: "Plume", breed: "Sacré de Birmanie", age: "12 semaines", sex: "Femelle", price: 1250, status: "available", temperament: "Paisible, ronronne au moindre regard", img: "https://images.unsplash.com/photo-1573865526739-10659fec78a5?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K05", name: "Gaspard", breed: "Chartreux", age: "11 semaines", sex: "Mâle", price: 1100, status: "adopted", progress: 85, temperament: "Observateur et fidèle", img: "https://images.unsplash.com/photo-1518791841217-8f162f1e1131?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K06", name: "Ambre", breed: "Sibérien", age: "12 semaines", sex: "Femelle", price: 1300, status: "available", temperament: "Vive, curieuse et très proche de l'humain", img: "https://images.unsplash.com/photo-1495360010541-f48722b34f7d?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K07", name: "Sacha", breed: "Scottish Fold", age: "11 semaines", sex: "Mâle", price: 1200, status: "available", temperament: "Tranquille, apprécie la vie en appartement", img: "https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K08", name: "Iris", breed: "Bleu Russe", age: "13 semaines", sex: "Femelle", price: 1280, status: "available", temperament: "Élégante, discrète et affectueuse", img: "https://images.unsplash.com/photo-1526336024174-e58f5cdd8e13?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K09", name: "Léon", breed: "Européen Tigré", age: "10 semaines", sex: "Mâle", price: 450, status: "available", temperament: "Plein d'entrain et très attachant", img: "https://images.unsplash.com/photo-1543852786-1cf6624b9987?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K10", name: "Perle", breed: "Persan Chinchilla", age: "13 semaines", sex: "Femelle", price: 1380, status: "pending", temperament: "Bilan vétérinaire en cours avant ouverture", img: "https://images.unsplash.com/photo-1574158622682-e40e69881006?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K11", name: "Oscar", breed: "Bengal", age: "14 semaines", sex: "Mâle", price: 1550, status: "available", temperament: "Athlétique, intelligent, aime les jeux", img: "https://images.unsplash.com/photo-1519052537078-e6302a4968d4?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K12", name: "Margot", breed: "British Longhair", age: "12 semaines", sex: "Femelle", price: 1220, status: "available", temperament: "Peluche vivante, très patiente", img: "https://images.unsplash.com/photo-1561948955-570b270e7c36?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K13", name: "Félix", breed: "Norvégien", age: "13 semaines", sex: "Mâle", price: 1320, status: "adopted", progress: 70, temperament: "Aventurier doux, adore grimper", img: "https://images.unsplash.com/photo-1533743983669-94fa5c4338ec?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K14", name: "Capucine", breed: "Exotic Shorthair", age: "12 semaines", sex: "Femelle", price: 1180, status: "available", temperament: "Câline, calme, adore la sieste", img: "https://images.unsplash.com/photo-1571566882372-1598d88abd90?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K15", name: "Roméo", breed: "Ragdoll Bicolore", age: "14 semaines", sex: "Mâle", price: 1400, status: "available", temperament: "D'une grande douceur avec tous", img: "https://images.unsplash.com/photo-1548247416-ec66f4900b2e?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K16", name: "Zélie", breed: "Abyssin", age: "11 semaines", sex: "Femelle", price: 1260, status: "pending", temperament: "Prochainement disponible après primo-vaccination", img: "https://images.unsplash.com/photo-1529778873920-4da4926a72c2?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K17", name: "Simba", breed: "Maine Coon Roux", age: "15 semaines", sex: "Mâle", price: 1500, status: "available", temperament: "Majestueux, joueur et très proche de sa famille", img: "https://images.unsplash.com/photo-1501820488136-72669149e0d4?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K18", name: "Chloé", breed: "Européen Écaille de Tortue", age: "10 semaines", sex: "Femelle", price: 390, status: "available", temperament: "Malicieuse, propre et très sociable", img: "https://images.unsplash.com/photo-1511044568932-338cba0ad803?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K19", name: "Arthur", breed: "Chartreux", age: "12 semaines", sex: "Mâle", price: 1150, status: "available", temperament: "Équilibré, silencieux et fidèle", img: "https://images.unsplash.com/photo-1518791841217-8f162f1e1131?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K20", name: "Louna", breed: "Sacré de Birmanie", age: "13 semaines", sex: "Femelle", price: 1290, status: "adopted", progress: 92, temperament: "Très tendre et bavarde", img: "https://images.unsplash.com/photo-1573865526739-10659fec78a5?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K21", name: "Balthazar", breed: "British Shorthair Lilas", age: "12 semaines", sex: "Mâle", price: 1240, status: "available", temperament: "Nounours paisible et gourmand", img: "https://images.unsplash.com/photo-1592194996308-7b43878e84a6?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K22", name: "Opaline", breed: "Angora Turc", age: "12 semaines", sex: "Femelle", price: 1080, status: "available", temperament: "Agile, gracieuse et affectueuse", img: "https://images.unsplash.com/photo-1513245543132-31f507417b26?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K23", name: "Pablo", breed: "Siamois Thaï", age: "11 semaines", sex: "Mâle", price: 980, status: "available", temperament: "Communicatif, fusionnel et joueur", img: "https://images.unsplash.com/photo-1548247416-ec66f4900b2e?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K24", name: "Mina", breed: "Sibérien Neva Masquerade", age: "13 semaines", sex: "Femelle", price: 1390, status: "pending", temperament: "En cours de sevrage, ouverture prochaine", img: "https://images.unsplash.com/photo-1495360010541-f48722b34f7d?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K25", name: "Hector", breed: "Highland Fold", age: "12 semaines", sex: "Mâle", price: 1210, status: "available", temperament: "Doux, s'entend très bien avec les autres chats", img: "https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K26", name: "Agathe", breed: "Européen Blanc & Gris", age: "10 semaines", sex: "Femelle", price: 420, status: "available", temperament: "Tendresse infinie, idéale premier compagnon", img: "https://images.unsplash.com/photo-1543852786-1cf6624b9987?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K27", name: "Ulysse", breed: "Maine Coon Brown Tabby", age: "14 semaines", sex: "Mâle", price: 1480, status: "adopted", progress: 65, temperament: "Calme et protecteur", img: "https://images.unsplash.com/photo-1533738363-b7f9aef128ce?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K28", name: "Solène", breed: "Ragdoll Blue Point", age: "13 semaines", sex: "Femelle", price: 1360, status: "available", temperament: "Sereine et habituée aux bruits du foyer", img: "https://images.unsplash.com/photo-1574158622682-e40e69881006?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K29", name: "César", breed: "Burmese", age: "12 semaines", sex: "Mâle", price: 1120, status: "available", temperament: "Sociable, curieux et très câlin", img: "https://images.unsplash.com/photo-1526336024174-e58f5cdd8e13?auto=format&fit=crop&w=700&q=80" },
      { id: "LPF-K30", name: "Étoile", breed: "Scottish Straight", age: "11 semaines", sex: "Femelle", price: 1090, status: "available", temperament: "Douceur et élégance au quotidien", img: "https://images.unsplash.com/photo-1561948955-570b270e7c36?auto=format&fit=crop&w=700&q=80" }
    ];

    // =========================================================================
    // 2. CONFIGURATION SUPABASE & ÉTAT LOCAL
    // =========================================================================
    const STORAGE_KEY_DOSSIERS = "lpf_dossiers_v1";
    const STORAGE_KEY_CFG = "lpf_supabase_cfg_v1";

    function getRuntimeConfig() {
      let saved = {};
      try { saved = JSON.parse(localStorage.getItem(STORAGE_KEY_CFG) || "{}"); } catch (_) {}
      return {
        SUPABASE_URL: (saved.SUPABASE_URL || window.APP_CONFIG?.SUPABASE_URL || "").trim().replace(/\/$/, ""),
        SUPABASE_ANON_KEY: (saved.SUPABASE_ANON_KEY || window.APP_CONFIG?.SUPABASE_ANON_KEY || "").trim(),
        EMAIL_WEBHOOK_URL: (saved.EMAIL_WEBHOOK_URL || window.APP_CONFIG?.EMAIL_WEBHOOK_URL || "/api/send-email").trim()
      };
    }

    function getLocalDossiers() {
      try { return JSON.parse(localStorage.getItem(STORAGE_KEY_DOSSIERS) || "[]"); } catch (_) { return []; }
    }

    function saveLocalDossiers(list) {
      localStorage.setItem(STORAGE_KEY_DOSSIERS, JSON.stringify(list));
    }

    function computeDeposit(totalPrice) {
      return Math.round(totalPrice * 0.30);
    }

    // =========================================================================
    // 3. APPELS SUPABASE REST & VERCEL E-MAILS
    // =========================================================================
    async function insertApplicationInSupabase(record) {
      const cfg = getRuntimeConfig();
      if (!cfg.SUPABASE_URL || !cfg.SUPABASE_ANON_KEY) return false;
      try {
        const res = await fetch(`${cfg.SUPABASE_URL}/rest/v1/applications`, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            "apikey": cfg.SUPABASE_ANON_KEY,
            "Authorization": `Bearer ${cfg.SUPABASE_ANON_KEY}`,
            "Prefer": "return=representation"
          },
          body: JSON.stringify(record)
        });
        return res.ok;
      } catch (err) {
        console.warn("Supabase insert fallback:", err);
        return false;
      }
    }

    async function fetchApplicationFromSupabase(trackingId) {
      const cfg = getRuntimeConfig();
      if (!cfg.SUPABASE_URL || !cfg.SUPABASE_ANON_KEY) return null;
      try {
        const res = await fetch(`${cfg.SUPABASE_URL}/rest/v1/applications?tracking_id=eq.${encodeURIComponent(trackingId)}&select=*`, {
          headers: {
            "apikey": cfg.SUPABASE_ANON_KEY,
            "Authorization": `Bearer ${cfg.SUPABASE_ANON_KEY}`
          }
        });
        if (!res.ok) return null;
        const rows = await res.json();
        return rows && rows.length ? rows[0] : null;
      } catch (err) {
        console.warn("Supabase fetch fallback:", err);
        return null;
      }
    }

    async function updateApplicationInSupabase(trackingId, patch) {
      const cfg = getRuntimeConfig();
      if (!cfg.SUPABASE_URL || !cfg.SUPABASE_ANON_KEY) return false;
      try {
        const res = await fetch(`${cfg.SUPABASE_URL}/rest/v1/applications?tracking_id=eq.${encodeURIComponent(trackingId)}`, {
          method: "PATCH",
          headers: {
            "Content-Type": "application/json",
            "apikey": cfg.SUPABASE_ANON_KEY,
            "Authorization": `Bearer ${cfg.SUPABASE_ANON_KEY}`
          },
          body: JSON.stringify(patch)
        });
        return res.ok;
      } catch (err) {
        console.warn("Supabase patch fallback:", err);
        return false;
      }
    }

    async function syncAllDossiersFromSupabase() {
      const cfg = getRuntimeConfig();
      if (!cfg.SUPABASE_URL || !cfg.SUPABASE_ANON_KEY) return;
      try {
        const res = await fetch(`${cfg.SUPABASE_URL}/rest/v1/applications?select=*&order=created_at.desc`, {
          headers: {
            "apikey": cfg.SUPABASE_ANON_KEY,
            "Authorization": `Bearer ${cfg.SUPABASE_ANON_KEY}`
          }
        });
        if (res.ok) {
          const rows = await res.json();
          if (Array.isArray(rows)) saveLocalDossiers(rows);
        }
      } catch (_) {}
    }

    async function triggerTransactionalEmail(type, record) {
      const cfg = getRuntimeConfig();
      if (!cfg.EMAIL_WEBHOOK_URL) return false;
      try {
        const res = await fetch(cfg.EMAIL_WEBHOOK_URL, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({ type, dossier: record })
        });
        return res.ok;
      } catch (_) {
        return false;
      }
    }

    // =========================================================================
    // 4. NAVIGATION & CONTRÔLES UI (MENU, TIROIR, GRAND TEXTE)
    // =========================================================================
    function navigateTo(sectionId) {
      document.querySelectorAll(".page-section").forEach(sec => sec.classList.add("hidden"));
      const target = document.getElementById(`sec-${sectionId}`);
      if (target) target.classList.remove("hidden");

      document.querySelectorAll(".nav-btn").forEach(btn => {
        btn.classList.toggle("active", btn.getAttribute("data-nav") === sectionId);
      });
      closeDrawer();
      window.scrollTo({ top: 0, behavior: "smooth" });
    }

    function openDrawer() {
      const drawer = document.getElementById("mobileDrawer");
      const backdrop = document.getElementById("drawerBackdrop");
      const btn = document.getElementById("menuToggleBtn");
      drawer.classList.remove("hidden", "pointer-events-none");
      backdrop.classList.remove("hidden", "pointer-events-none");
      btn.setAttribute("aria-expanded", "true");
    }

    function closeDrawer() {
      const drawer = document.getElementById("mobileDrawer");
      const backdrop = document.getElementById("drawerBackdrop");
      const btn = document.getElementById("menuToggleBtn");
      drawer.classList.add("hidden", "pointer-events-none");
      backdrop.classList.add("hidden", "pointer-events-none");
      btn.setAttribute("aria-expanded", "false");
    }

    function toggleDrawer() {
      const drawer = document.getElementById("mobileDrawer");
      if (drawer.classList.contains("hidden")) openDrawer();
      else closeDrawer();
    }

    // =========================================================================
    // 5. RENDU DU CATALOGUE DE CHATONS
    // =========================================================================
    let activeFilter = "all";

    function renderInventory() {
      const grid = document.getElementById("kittenGrid");
      const list = activeFilter === "all" ? KITTENS : KITTENS.filter(k => k.status === activeFilter);

      grid.innerHTML = list.map(k => {
        const deposit = computeDeposit(k.price);
        if (k.status === "adopted") {
          return `
            <article class="bg-white border border-[#E6DFD5] rounded-2xl overflow-hidden flex flex-col opacity-90">
              <div class="relative aspect-[4/3] bg-stone-100">
                <img src="${k.img}" alt="${k.name}" class="w-full h-full object-cover grayscale-[35%]" loading="lazy" />
                <span class="absolute top-3 left-3 px-3 py-1 rounded-full bg-stone-800 text-white text-xs font-bold">Adopté</span>
              </div>
              <div class="p-5 flex-1 flex flex-col justify-between space-y-4">
                <div>
                  <div class="flex items-baseline justify-between gap-2">
                    <h3 class="text-2xl font-bold">${k.name}</h3>
                    <span class="text-xs font-mono text-[#57534E]">${k.id}</span>
                  </div>
                  <p class="text-sm font-medium text-[#9A5B25]">${k.breed} &bull; ${k.sex} &bull; ${k.age}</p>
                  <p class="text-sm text-[#57534E] mt-2">${k.temperament}</p>
                </div>
                <div class="space-y-2 pt-2 border-t border-[#E6DFD5]">
                  <div class="flex justify-between text-xs text-[#57534E]">
                    <span>Clôture de la fiche</span>
                    <span>${k.progress || 80}%</span>
                  </div>
                  <div class="w-full h-2 bg-stone-200 rounded-full overflow-hidden">
                    <div class="h-full bg-stone-600" style="width:${k.progress || 80}%"></div>
                  </div>
                  <button type="button" disabled class="w-full py-2.5 rounded-xl bg-stone-200 text-stone-500 text-sm font-semibold cursor-not-allowed">
                    Déjà adopté
                  </button>
                </div>
              </div>
            </article>
          `;
        }

        if (k.status === "pending") {
          return `
            <article class="bg-white border border-[#E6DFD5] rounded-2xl overflow-hidden flex flex-col">
              <div class="relative aspect-[4/3] bg-stone-100">
                <img src="${k.img}" alt="${k.name}" class="w-full h-full object-cover" loading="lazy" />
                <span class="absolute top-3 left-3 px-3 py-1 rounded-full bg-amber-100 text-amber-900 border border-amber-300 text-xs font-bold">Prochainement</span>
              </div>
              <div class="p-5 flex-1 flex flex-col justify-between space-y-4">
                <div>
                  <div class="flex items-baseline justify-between gap-2">
                    <h3 class="text-2xl font-bold">${k.name}</h3>
                    <span class="text-xs font-mono text-[#57534E]">${k.id}</span>
                  </div>
                  <p class="text-sm font-medium text-[#9A5B25]">${k.breed} &bull; ${k.sex} &bull; ${k.age}</p>
                  <p class="text-sm text-[#57534E] mt-2">${k.temperament}</p>
                </div>
                <div class="pt-3 border-t border-[#E6DFD5] space-y-2">
                  <p class="text-sm font-bold">${k.price} € <span class="text-xs font-normal text-[#57534E]">(Acompte : ${deposit} €)</span></p>
                  <button type="button" data-apply-kitten="${k.id}" class="w-full py-2.5 rounded-xl border border-[#231F20] text-[#231F20] text-sm font-semibold hover:bg-stone-100">
                    Pré-réserver ce chaton
                  </button>
                </div>
              </div>
            </article>
          `;
        }

        return `
          <article class="bg-white border border-[#E6DFD5] rounded-2xl overflow-hidden flex flex-col">
            <div class="relative aspect-[4/3] bg-stone-100">
              <img src="${k.img}" alt="${k.name}" class="w-full h-full object-cover" loading="lazy" />
              <span class="absolute top-3 left-3 px-3 py-1 rounded-full bg-emerald-100 text-emerald-900 border border-emerald-300 text-xs font-bold">Disponible</span>
            </div>
            <div class="p-5 flex-1 flex flex-col justify-between space-y-4">
              <div>
                <div class="flex items-baseline justify-between gap-2">
                  <h3 class="text-2xl font-bold">${k.name}</h3>
                  <span class="text-xs font-mono text-[#57534E]">${k.id}</span>
                </div>
                <p class="text-sm font-medium text-[#9A5B25]">${k.breed} &bull; ${k.sex} &bull; ${k.age}</p>
                <p class="text-sm text-[#57534E] mt-2">${k.temperament}</p>
              </div>
              <div class="pt-3 border-t border-[#E6DFD5] space-y-2">
                <div class="flex items-baseline justify-between">
                  <span class="text-lg font-bold">${k.price} €</span>
                  <span class="text-xs text-[#57534E]">Acompte : <strong>${deposit} €</strong></span>
                </div>
                <button type="button" data-apply-kitten="${k.id}" class="w-full py-2.5 rounded-xl bg-[#231F20] text-white text-sm font-semibold hover:bg-stone-800">
                  Postuler pour ce chaton
                </button>
              </div>
            </div>
          </article>
        `;
      }).join("");
    }

    function selectKittenForApplication(kittenId) {
      const k = KITTENS.find(item => item.id === kittenId) || KITTENS[0];
      const deposit = computeDeposit(k.price);
      document.getElementById("appKittenId").value = k.id;
      document.getElementById("selectedKittenLabel").textContent = `${k.name} (${k.breed} — ${k.id})`;
      document.getElementById("selectedKittenPriceNote").textContent = `Tarif total : ${k.price} € • Un acompte de ${deposit} € sera demandé après approbation pour confirmer la réservation.`;
      navigateTo("application");
    }

    // =========================================================================
    // 6. SOUMISSION DE CANDIDATURE & E-MAIL DE BIENVENUE #1
    // =========================================================================
    async function handleApplicationSubmit(e) {
      e.preventDefault();
      const chosenId = document.getElementById("appKittenId").value || KITTENS[0].id;
      const k = KITTENS.find(item => item.id === chosenId) || KITTENS[0];
      const deposit = computeDeposit(k.price);
      const balance = k.price - deposit;
      const trackingId = "LPF-" + Math.floor(1000 + Math.random() * 9000);

      const firstName = document.getElementById("appFirstName").value.trim();
      const lastName = document.getElementById("appLastName").value.trim();
      const email = document.getElementById("appEmail").value.trim();
      const phone = document.getElementById("appPhone").value.trim();
      const address = document.getElementById("appAddress").value.trim();
      const housingType = document.getElementById("appHousingType").value;
      const indoorOutdoor = document.getElementById("appIndoorOutdoor").value;
      const children = document.getElementById("appChildren").value;
      const otherPets = document.getElementById("appOtherPets").value;
      const deliveryMode = document.getElementById("appDeliveryMode").value;
      const paymentMethod = document.getElementById("appPaymentMethod").value;
      const notes = document.getElementById("appNotes").value.trim();

      const scheduledDate = new Date(Date.now() + 7 * 86400000).toLocaleDateString("fr-FR", {
        weekday: "long", day: "numeric", month: "long", year: "numeric"
      });

      const dossier = {
        tracking_id: trackingId,
        kitten_id: k.id,
        kitten_name: `${k.name} (${k.breed})`,
        first_name: firstName,
        last_name: lastName,
        email,
        phone,
        address,
        housing_type: housingType,
        indoor_outdoor: indoorOutdoor,
        children,
        other_pets: otherPets,
        delivery_mode: deliveryMode,
        payment_method: paymentMethod,
        notes,
        total_price: k.price,
        deposit_amount: deposit,
        balance_amount: balance,
        delivery_date: scheduledDate,
        approved: false,
        confirmed: false,
        paid: false,
        created_at: new Date().toISOString()
      };

      const existing = getLocalDossiers();
      existing.unshift(dossier);
      saveLocalDossiers(existing);

      await insertApplicationInSupabase(dossier);
      await triggerTransactionalEmail("welcome_email_1", dossier);

      document.getElementById("generatedTrackingId").textContent = trackingId;
      document.getElementById("welcomeEmailPreview").textContent =
        `Objet : Bienvenue à L'élevage des petits félins — Dossier ${trackingId}\n` +
        `Bonjour ${firstName} ${lastName},\n` +
        `Nous avons bien reçu votre candidature pour ${k.name} (${k.breed}). Votre logement (${housingType}, ${indoorOutdoor}) est en cours d'étude. Vous recevrez un second e-mail dès l'approbation de votre dossier.`;

      const successBox = document.getElementById("applicationSuccessBox");
      successBox.classList.remove("hidden");
      document.getElementById("goToMyTrackingBtn").onclick = () => {
        document.getElementById("trackingInput").value = trackingId;
        navigateTo("tracking");
        lookupTrackingDossier(trackingId);
      };
    }

    // =========================================================================
    // 7. SUIVI DE DOSSIER & LOGIQUE CONFIRMÉ / PAYÉ
    // =========================================================================
    async function lookupTrackingDossier(rawId) {
      const id = (rawId || "").trim().toUpperCase();
      const errBox = document.getElementById("trackingError");
      const resBox = document.getElementById("trackingResult");
      errBox.classList.add("hidden");
      resBox.classList.add("hidden");

      let dossier = await fetchApplicationFromSupabase(id);
      if (!dossier) {
        dossier = getLocalDossiers().find(d => d.tracking_id.toUpperCase() === id) || null;
      } else {
        const list = getLocalDossiers().filter(d => d.tracking_id.toUpperCase() !== id);
        list.unshift(dossier);
        saveLocalDossiers(list);
      }

      if (!dossier) {
        errBox.textContent = `Aucun dossier trouvé pour le numéro "${id}". Vérifiez le code reçu dans votre e-mail de bienvenue.`;
        errBox.classList.remove("hidden");
        return;
      }

      // Fill summary fields
      document.getElementById("trkAdopter").textContent = `${dossier.first_name} ${dossier.last_name}`;
      document.getElementById("trkKitten").textContent = dossier.kitten_name;
      document.getElementById("trkAddress").textContent = dossier.address;
      document.getElementById("trkPricing").textContent = `${dossier.total_price} € (Acompte : ${dossier.deposit_amount} € • Solde à la livraison : ${dossier.balance_amount} €)`;
      document.getElementById("trkDeliveryDate").textContent = dossier.delivery_date || "Programmée après confirmation";
      document.getElementById("trkTransport").textContent = dossier.delivery_mode;

      document.getElementById("openPhoneMapsLink").href = `https://maps.google.com/?q=${encodeURIComponent(dossier.address)}`;

      // Status banner messaging
      const banner = document.getElementById("trackingStatusBanner");
      const gateNotice = document.getElementById("documentsGateNotice");
      const gateText = document.getElementById("documentsGateText");
      const unlockedSec = document.getElementById("unlockedDocumentsSection");

      if (dossier.confirmed && dossier.paid) {
        banner.className = "p-5 rounded-xl border bg-emerald-50 border-emerald-300 text-emerald-950 space-y-1";
        banner.innerHTML = `
          <p class="font-bold text-base">Dossier confirmé &amp; acompte réglé — Livraison programmée</p>
          <p class="text-sm">Tout est prêt pour l'arrivée de <strong>${dossier.kitten_name}</strong> le <strong>${dossier.delivery_date}</strong>. Vos documents officiels sont débloqués ci-dessous.</p>
        `;
        gateNotice.classList.add("hidden");
        unlockedSec.classList.remove("hidden");
        populateReceiptAndCertificates(dossier);
      } else if (dossier.confirmed && !dossier.paid) {
        banner.className = "p-5 rounded-xl border bg-amber-50 border-amber-300 text-amber-950 space-y-1";
        banner.innerHTML = `
          <p class="font-bold text-base">Dossier confirmé — Vos documents sont prêts</p>
          <p class="text-sm">Votre Bon de livraison, votre Certificat d'adoption et votre Livret d'accueil sont finalisés et prêts pour la date du <strong>${dossier.delivery_date}</strong>.</p>
        `;
        gateNotice.classList.remove("hidden");
        gateText.textContent = `Vos documents sont prêts dans notre base de données. Pour ouvrir et télécharger votre Bon de livraison, le Livret d'accueil et le Certificat, veuillez régler l'acompte de ${dossier.deposit_amount} €.`;
        unlockedSec.classList.add("hidden");
      } else if (dossier.approved) {
        banner.className = "p-5 rounded-xl border bg-blue-50 border-blue-200 text-blue-950 space-y-1";
        banner.innerHTML = `
          <p class="font-bold text-base">Candidature approuvée — Préparation en cours</p>
          <p class="text-sm">Votre foyer a été validé pour <strong>${dossier.kitten_name}</strong>. Un e-mail de confirmation vous a été adressé avec les modalités d'acompte (${dossier.deposit_amount} €).</p>
        `;
        gateNotice.classList.remove("hidden");
        gateText.textContent = `Dès confirmation de votre acompte (${dossier.deposit_amount} €), le Bon de livraison, le Certificat et le Livret d'accueil seront débloqués ici.`;
        unlockedSec.classList.add("hidden");
      } else {
        banner.className = "p-5 rounded-xl border bg-stone-100 border-stone-300 text-stone-900 space-y-1";
        banner.innerHTML = `
          <p class="font-bold text-base">Candidature reçue — En cours d'étude</p>
          <p class="text-sm">Notre équipe étudie vos réponses concernant votre logement (${dossier.housing_type}) avant de vous envoyer l'e-mail d'approbation.</p>
        `;
        gateNotice.classList.remove("hidden");
        gateText.textContent = `Les documents officiels seront accessibles dès que votre candidature sera approuvée, confirmée et que l'acompte aura été réglé.`;
        unlockedSec.classList.add("hidden");
      }

      resBox.classList.remove("hidden");
    }

    function populateReceiptAndCertificates(d) {
      document.getElementById("rcptRef").textContent = `DOSSIER N° ${d.tracking_id}`;
      document.getElementById("rcptClient").textContent = `${d.first_name} ${d.last_name}`;
      document.getElementById("rcptPhone").textContent = d.phone;
      document.getElementById("rcptAddress").textContent = d.address;
      document.getElementById("rcptKitten").textContent = d.kitten_name;
      document.getElementById("rcptDate").textContent = d.delivery_date;
      document.getElementById("rcptPayMethod").textContent = d.payment_method;
      document.getElementById("rcptTotal").textContent = `${d.total_price} €`;
      document.getElementById("rcptDeposit").textContent = `${d.deposit_amount} €`;
      document.getElementById("rcptBalance").textContent = `${d.balance_amount} €`;

      document.getElementById("certBodyText").textContent =
        `Par la présente, L'élevage des petits félins certifie la réservation officielle de ${d.kitten_name} au profit de ${d.first_name} ${d.last_name} (${d.address}), dossier ${d.tracking_id}. Livraison prévue le ${d.delivery_date}.`;
    }

    // =========================================================================
    // 8. ADMINISTRATION ÉLEVAGE (APPROUVÉ / CONFIRMÉ / PAYÉ)
    // =========================================================================
    function openAdminModal() {
      const cfg = getRuntimeConfig();
      document.getElementById("cfgSupabaseUrl").value = cfg.SUPABASE_URL;
      document.getElementById("cfgSupabaseKey").value = cfg.SUPABASE_ANON_KEY;
      document.getElementById("cfgEmailWebhook").value = cfg.EMAIL_WEBHOOK_URL;
      document.getElementById("supabaseStatusText").textContent =
        cfg.SUPABASE_URL && cfg.SUPABASE_ANON_KEY ? "Connecté à Supabase" : "Mode stockage local navigateur";

      renderAdminDossiersList();
      const modal = document.getElementById("adminModal");
      modal.classList.remove("hidden", "pointer-events-none");
    }

    function closeAdminModal() {
      const modal = document.getElementById("adminModal");
      modal.classList.add("hidden", "pointer-events-none");
    }

    function renderAdminDossiersList() {
      const container = document.getElementById("adminDossiersList");
      const list = getLocalDossiers();
      if (!list.length) {
        container.innerHTML = `<p class="text-xs text-[#57534E] p-3 bg-stone-50 rounded-lg">Aucun dossier enregistré pour le moment.</p>`;
        return;
      }
      container.innerHTML = list.map(d => `
        <div class="p-4 rounded-xl border border-[#E6DFD5] bg-[#FAF8F5] flex flex-col sm:flex-row sm:items-center justify-between gap-3">
          <div>
            <p class="font-bold">${d.tracking_id} — ${d.first_name} ${d.last_name}</p>
            <p class="text-xs text-[#57534E]">${d.kitten_name} &bull; ${d.email} &bull; Acompte : ${d.deposit_amount} €</p>
            <p class="text-xs mt-1">
              Statut :
              <span class="font-semibold">${d.approved ? "Approuvé" : "En attente"}</span> &bull;
              <span class="font-semibold">${d.confirmed ? "Confirmé" : "Non confirmé"}</span> &bull;
              <span class="font-semibold">${d.paid ? "Payé" : "Acompte dû"}</span>
            </p>
          </div>
          <div class="flex flex-wrap gap-1.5">
            <button type="button" data-admin-action="approve" data-id="${d.tracking_id}" class="px-2.5 py-1.5 rounded-lg bg-blue-700 text-white text-xs font-semibold hover:bg-blue-800">
              Approuver + E-mail #2
            </button>
            <button type="button" data-admin-action="confirm" data-id="${d.tracking_id}" class="px-2.5 py-1.5 rounded-lg bg-amber-700 text-white text-xs font-semibold hover:bg-amber-800">
              Marquer Confirmé
            </button>
            <button type="button" data-admin-action="paid" data-id="${d.tracking_id}" class="px-2.5 py-1.5 rounded-lg bg-emerald-700 text-white text-xs font-semibold hover:bg-emerald-800">
              Marquer Payé
            </button>
          </div>
        </div>
      `).join("");
    }

    async function handleAdminDossierAction(action, trackingId) {
      const list = getLocalDossiers();
      const idx = list.findIndex(d => d.tracking_id === trackingId);
      if (idx === -1) return;

      const patch = {};
      if (action === "approve") {
        patch.approved = true;
      } else if (action === "confirm") {
        patch.approved = true;
        patch.confirmed = true;
      } else if (action === "paid") {
        patch.approved = true;
        patch.confirmed = true;
        patch.paid = true;
      }

      list[idx] = { ...list[idx], ...patch };
      saveLocalDossiers(list);
      await updateApplicationInSupabase(trackingId, patch);

      if (action === "approve") {
        await triggerTransactionalEmail("second_email_approval", list[idx]);
      }

      renderAdminDossiersList();
      if (document.getElementById("trackingInput").value.trim().toUpperCase() === trackingId) {
        lookupTrackingDossier(trackingId);
      }
    }

    // =========================================================================
    // 9. NOTIFICATIONS LATÉRALES DISCRÈTES (ACTIVITÉ EN DIRECT)
    // =========================================================================
    const ACTIVITY_MESSAGES = [
      "Famille Laurent (Lyon) vient de réserver le chaton Céleste (Ragdoll).",
      "Nouvelle candidature validée pour Milo (Maine Coon) à Bordeaux.",
      "Gaspard (Chartreux) a rejoint sa famille à Nantes.",
      "Acompte confirmé pour le chaton Ambre (Sibérien) — livraison programmée.",
      "Louna (Sacré de Birmanie) a bien été remise à sa famille à Toulouse."
    ];
    let activityIndex = 0;

    function startActivityToasts() {
      const box = document.getElementById("liveActivityToast");
      const text = document.getElementById("liveActivityText");
      let dismissed = false;

      document.getElementById("dismissToastBtn").addEventListener("click", () => {
        dismissed = true;
        box.classList.add("hidden");
      });

      function showNext() {
        if (dismissed) return;
        text.textContent = ACTIVITY_MESSAGES[activityIndex % ACTIVITY_MESSAGES.length];
        activityIndex++;
        box.classList.remove("hidden");
        setTimeout(() => {
          box.classList.add("hidden");
        }, 7000);
      }

      setTimeout(showNext, 5000);
      setInterval(showNext, 26000);
    }

    // =========================================================================
    // 10. INITIALISATION & DÉLÉGATION D'ÉVÉNEMENTS
    // =========================================================================
    document.addEventListener("DOMContentLoaded", () => {
      renderInventory();
      syncAllDossiersFromSupabase();
      startActivityToasts();

      document.getElementById("menuToggleBtn").addEventListener("click", toggleDrawer);
      document.getElementById("drawerCloseBtn").addEventListener("click", closeDrawer);
      document.getElementById("drawerBackdrop").addEventListener("click", closeDrawer);

      document.getElementById("textSizeToggle").addEventListener("click", (e) => {
        const isLarge = document.documentElement.classList.toggle("large-text");
        e.currentTarget.textContent = isLarge ? "Texte normal" : "Grand texte";
      });

      document.getElementById("openAdminFromDrawer").addEventListener("click", () => { closeDrawer(); openAdminModal(); });
      document.getElementById("openAdminFromTracking").addEventListener("click", openAdminModal);
      document.getElementById("openAdminFromFooter").addEventListener("click", openAdminModal);
      document.getElementById("closeAdminModalBtn").addEventListener("click", closeAdminModal);

      document.getElementById("supabaseConfigForm").addEventListener("submit", async (e) => {
        e.preventDefault();
        const cfg = {
          SUPABASE_URL: document.getElementById("cfgSupabaseUrl").value.trim(),
          SUPABASE_ANON_KEY: document.getElementById("cfgSupabaseKey").value.trim(),
          EMAIL_WEBHOOK_URL: document.getElementById("cfgEmailWebhook").value.trim() || "/api/send-email"
        };
        localStorage.setItem(STORAGE_KEY_CFG, JSON.stringify(cfg));
        await syncAllDossiersFromSupabase();
        renderAdminDossiersList();
        document.getElementById("supabaseStatusText").textContent = "Configuration enregistrée et synchronisée.";
      });

      document.getElementById("applicationForm").addEventListener("submit", handleApplicationSubmit);

      document.getElementById("trackingLookupForm").addEventListener("submit", (e) => {
        e.preventDefault();
        lookupTrackingDossier(document.getElementById("trackingInput").value);
      });

      document.getElementById("printReceiptBtn").addEventListener("click", () => window.print());

      document.getElementById("contactForm").addEventListener("submit", (e) => {
        e.preventDefault();
        const name = document.getElementById("cntName").value.trim();
        const ref = document.getElementById("cntRef").value.trim();
        const msg = document.getElementById("cntMessage").value.trim();
        const subject = encodeURIComponent(`Contact L'élevage des petits félins ${ref ? "- " + ref : ""}`);
        const body = encodeURIComponent(`Nom : ${name}\nDossier : ${ref || "Non précisé"}\n\n${msg}`);
        window.location.href = `mailto:maisonpourchats@gmail.com?subject=${subject}&body=${body}`;
      });

      document.getElementById("whatsappDirectBtn").addEventListener("click", () => {
        const msg = encodeURIComponent("Bonjour L'élevage des petits félins, je souhaite des renseignements sur une adoption.");
        window.open(`https://wa.me/33748258522?text=${msg}`, "_blank", "noopener,noreferrer");
      });

      // Global delegated click listener for navigation, filters, kitten apply buttons, and admin buttons
      document.body.addEventListener("click", (e) => {
        const navEl = e.target.closest("[data-nav]");
        if (navEl) {
          navigateTo(navEl.getAttribute("data-nav"));
          return;
        }

        const filterEl = e.target.closest("[data-filter]");
        if (filterEl) {
          activeFilter = filterEl.getAttribute("data-filter");
          document.querySelectorAll(".filter-btn").forEach(b => {
            const active = b.getAttribute("data-filter") === activeFilter;
            b.className = active
              ? "filter-btn px-3.5 py-2 rounded-lg bg-[#231F20] text-white text-xs sm:text-sm font-semibold"
              : "filter-btn px-3.5 py-2 rounded-lg bg-white border border-[#D6CEC2] text-xs sm:text-sm font-semibold";
          });
          renderInventory();
          return;
        }

        const applyEl = e.target.closest("[data-apply-kitten]");
        if (applyEl) {
          selectKittenForApplication(applyEl.getAttribute("data-apply-kitten"));
          return;
        }

        const adminActionEl = e.target.closest("[data-admin-action]");
        if (adminActionEl) {
          handleAdminDossierAction(
            adminActionEl.getAttribute("data-admin-action"),
            adminActionEl.getAttribute("data-id")
          );
        }
      });
    });
  </script>
</body>
</html>
