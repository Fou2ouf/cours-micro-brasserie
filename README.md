 [index.html.html](https://github.com/user-attachments/files/24605751/index.html.html)
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <title>Physico-chimie du brassage — Quiz</title>
  <style>
    :root {
      --bg: #0d1117;
      --accent: #58a6ff;
      --text: #e6edf3;
      --correct: #3fb950;
      --incorrect: #f85149;
      --card-bg: #161b22;
      --border: #30363d;
      --muted: #8b949e;
    }
    * { 
      margin: 0; 
      padding: 0; 
      box-sizing: border-box; 
      -webkit-tap-highlight-color: transparent; /* Safari iOS */
    }
    body {
      background: var(--bg);
      color: var(--text);
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      line-height: 1.6;
      -webkit-font-smoothing: antialiased; /* Safari */
      -moz-osx-font-smoothing: grayscale;
    }
    header {
      background: linear-gradient(135deg, #0d1117 0%, #1f6feb 100%);
      padding: 2rem;
      text-align: center;
      border-bottom: 2px solid var(--accent);
    }
    header h1 { font-size: 2em; color: var(--text); }
    #nav {
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
      padding: 1.5rem;
      background: var(--card-bg);
      border-bottom: 1px solid var(--accent);
      min-height: 1px; /* assure une zone visible même vide */
    }
    .category-group {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      align-items: flex-start;
      margin-bottom: 1.5rem;
      padding: 1rem;
      background: linear-gradient(135deg, rgba(37, 99, 235, 0.08) 0%, rgba(59, 130, 246, 0.12) 100%);
      border-radius: 8px;
      border-left: 4px solid var(--accent);
      box-shadow: 0 2px 10px rgba(37, 99, 235, 0.15);
    }
    .category-title {
      font-size: 1.1em;
      color: #fff;
      background: linear-gradient(90deg, #a78bfa, #c4b5fd);
      font-weight: 700;
      margin: 0 0 1rem 0;
      padding: 0.6rem 1rem;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      width: 100%;
      flex-basis: 100%;
      border-radius: 6px;
      box-shadow: 0 2px 8px rgba(167, 139, 250, 0.4);
    }
    .category-group .theme-btn {
      flex: 1;
      min-width: 180px;
    }
    .theme-btn {
      padding: 1rem;
      background: var(--accent);
      color: #000;
      border: none;
      border-radius: 6px;
      font-weight: 600;
      cursor: pointer;
      font-size: 0.9em;
      transition: transform 0.2s;
      margin-right: 0.5rem;
      margin-bottom: 0.5rem;
      position: relative;
    }
    .theme-btn:hover { 
      transform: scale(1.02);
      -webkit-transform: scale(1.02); /* Safari transform */
    }
    .theme-btn.active { background: var(--correct); }
    .theme-btn.started::before {
      content: "▶";
      position: absolute;
      top: 4px;
      right: 8px;
      font-size: 0.7em;
      color: #ff9800;
      font-weight: bold;
    }
    .theme-btn.completed::before {
      content: "✓";
      position: absolute;
      top: 4px;
      right: 8px;
      font-size: 1em;
      color: #4caf50;
      font-weight: bold;
    }
    .theme-container {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      margin-bottom: 0.5rem;
    }
    .theme-container .theme-btn {
      flex: 1;
      margin: 0;
    }
    .reset-btn {
      padding: 0.5rem 0.8rem;
      background: #dc3545;
      color: #fff;
      border: none;
      border-radius: 6px;
      font-weight: 600;
      cursor: pointer;
      font-size: 0.8em;
      transition: background 0.2s;
      white-space: nowrap;
    }
    .reset-btn:hover {
      background: #c82333;
    }
    #controls,
    #nav {
      display: -webkit-flex;
      display: flex;
      -webkit-flex-wrap: wrap;
      flex-wrap: wrap;
      gap: 0.5rem;
      margin-bottom: 1rem;
      border-bottom: 1px solid var(--accent);
    }
    label { font-weight: 600; }
    select {
      padding: 0.6rem;
      background: var(--bg);
      border: 1px solid var(--accent);
      color: var(--text);
      border-radius: 4px;
      cursor: pointer;
      font-weight: 500;
      -webkit-appearance: none; /* Safari select reset */
      appearance: none;
    }
    button {
      padding: 0.7rem 1.5rem;
      background: var(--accent);
      color: #000;
      border: none;
      border-radius: 6px;
      font-weight: 600;
      cursor: pointer;
      -webkit-appearance: none; /* Safari button reset */
      box-sizing: border-box; /* Safari box model */
    }
    button:hover { opacity: 0.8; }
    #resetQuiz {
      background: #dc3545;
      color: #fff;
    }
    #resetQuiz:hover {
      opacity: 1;
      background: #c82333;
    }
    #fiche {
      padding: 2rem;
      background: var(--card-bg);
      margin: 2rem;
      border-radius: 8px;
    }
    #fiche h2 { color: var(--accent); margin-bottom: 1.5rem; }
    .section {
      margin-bottom: 1.5rem;
      padding: 1rem;
      background: var(--bg);
      border-radius: 6px;
    }
    .section h3 { color: #b1baf8; margin-bottom: 0.7rem; }
    .section ul { list-style: none; padding-left: 1rem; }
    .section li { margin-bottom: 0.5rem; color: var(--text); }
    .section li strong { color: var(--accent); }
    #quizContainer {
      padding: 2rem;
    }
    .question {
      background: var(--card-bg);
      padding: 1.5rem;
      margin-bottom: 1.5rem;
      border-radius: 8px;
    }
    .question h3 { margin-bottom: 1rem; }
    .options {
      display: grid;
      gap: 0.7rem;
    }
    .option {
      padding: 1rem;
      background: #1c2128;
      border: 2px solid #30363d;
      text-align: left;
      border-radius: 6px;
      transition: all 0.2s;
      color: #e6edf3;
      font-weight: 500;
    }
    .option:hover { 
      border-color: var(--accent);
      background: #21262d;
      cursor: pointer;
    }
    .option {
      -webkit-appearance: none; /* Safari button fix */
      -webkit-user-select: none; /* Safari text select */
    }
    .option.correct { 
      background: var(--correct);
      color: #000;
      font-weight: 600;
      border-color: var(--correct);
    }
    .option.incorrect { 
      background: var(--incorrect);
      color: #fff;
      font-weight: 600;
      border-color: var(--incorrect);
    }
    .explanation {
      margin-top: 1rem;
      padding: 1rem;
      background: var(--bg);
      border-left: 3px solid var(--accent);
      border-radius: 4px;
      font-size: 0.9em;
    }
    #progress {
      font-weight: 600;
      color: var(--accent);
      margin-left: auto;
    }
  </style>
</head>
<body>
  <header>
    <h1>🍺 Physico-chimie du brassage <span style="float: right; font-size: 0.5em; font-weight: normal; color: rgba(255,255,255,0.7);">Nicolas Lambert</span></h1>
  </header>

  <!-- Barre de recherche -->
  <div style="padding: 1.5rem; background: var(--card-bg); border-bottom: 1px solid var(--accent); display: flex; gap: 1rem; align-items: center;">
    <input type="text" id="searchBar" placeholder="🔍 Rechercher un thème..." style="flex: 1; padding: 0.8rem; background: var(--bg); border: 2px solid var(--accent); color: var(--text); border-radius: 6px; font-size: 1em;">
    <button id="exportAllThemes" style="background: #3fb950; color: #fff; border: none; padding: 0.8rem 1.5rem; border-radius: 6px; cursor: pointer; font-weight: 600; white-space: nowrap; font-size: 1em; transition: all 0.2s;">📦 Exporter tous</button>
    <button id="resetAllData" style="background: #dc3545; color: #fff; border: none; padding: 0.8rem 1.5rem; border-radius: 6px; cursor: pointer; font-weight: 600; white-space: nowrap; font-size: 1em; transition: all 0.2s;">🔄 Tout réinitialiser</button>
  </div>

  <!-- Résultats de recherche -->
  <div id="searchResults" style="display: none; padding: 1.5rem; background: var(--card-bg); border-bottom: 1px solid var(--accent); max-height: 400px; overflow-y: auto;">
    <h3 style="color: var(--accent); margin-bottom: 1rem; font-size: 1.1em;">📋 Résultats de recherche</h3>
    <div id="searchResultsContent"></div>
  </div>

  <!-- Panneau de statistiques globales -->
  <div id="statsPanel" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; padding: 1.5rem; background: var(--card-bg); border-bottom: 1px solid var(--accent);">
    <div class="stat-card" style="background: linear-gradient(135deg, #1f6feb 0%, #0d1117 100%); padding: 1.5rem; border-radius: 8px; text-align: center;">
      <div style="font-size: 2em; font-weight: bold; color: #58a6ff;">0</div>
      <div style="font-size: 0.9em; color: rgba(255,255,255,0.7);">Thèmes démarrés</div>
    </div>
    <div class="stat-card" style="background: linear-gradient(135deg, #3fb950 0%, #0d1117 100%); padding: 1.5rem; border-radius: 8px; text-align: center;">
      <div style="font-size: 2em; font-weight: bold; color: #3fb950;">0</div>
      <div style="font-size: 0.9em; color: rgba(255,255,255,0.7);">Thèmes terminés</div>
    </div>
    <div class="stat-card" style="background: linear-gradient(135deg, #a78bfa 0%, #0d1117 100%); padding: 1.5rem; border-radius: 8px; text-align: center;">
      <div style="font-size: 2em; font-weight: bold; color: #a78bfa;">0%</div>
      <div style="font-size: 0.9em; color: rgba(255,255,255,0.7);">Taux de réussite</div>
    </div>
    <div class="stat-card" style="background: linear-gradient(135deg, #f85149 0%, #0d1117 100%); padding: 1.5rem; border-radius: 8px; text-align: center;">
      <div style="font-size: 2em; font-weight: bold; color: #f85149;">0</div>
      <div style="font-size: 0.9em; color: rgba(255,255,255,0.7);">Questions ratées</div>
    </div>
  </div>

  <!-- Graphiques circulaires de progression -->
  <div id="statsChart" style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 2rem; padding: 2rem; background: var(--card-bg); border-bottom: 1px solid var(--accent);">
    <div style="text-align: center;">
      <canvas id="completedChart" width="150" height="150"></canvas>
      <div style="margin-top: 1rem; color: var(--text); font-weight: 600;">Terminés</div>
    </div>
    <div style="text-align: center;">
      <canvas id="startedChart" width="150" height="150"></canvas>
      <div style="margin-top: 1rem; color: var(--text); font-weight: 600;">Démarrés</div>
    </div>
    <div style="text-align: center;">
      <canvas id="notStartedChart" width="150" height="150"></canvas>
      <div style="margin-top: 1rem; color: var(--text); font-weight: 600;">Non démarrés</div>
    </div>
  </div>
  
  <nav id="nav"></nav>
  
  <div id="controls">
    <label for="questionCount">Questions :</label>
    <select id="questionCount">
      <option value="5">5 questions</option>
      <option value="10">10 questions</option>
      <option value="15">15 questions</option>
      <option value="20">20 questions</option>
      <option value="25">25 questions</option>
      <option value="30" selected>30 questions</option>
    </select>
    <button id="startQuiz">Démarrer</button>
    <button id="toggleFiche">👁️ Masquer la fiche</button>
    <button id="revisionMode" style="background: #a78bfa; color: #000;">🔄 Mode révision</button>
    <button id="fullscreenBtn">🖥️ Plein écran</button>
    <button id="exportThemeBtn" style="background: #3fb950; color: #fff;">📄 Exporter thème</button>
    <button id="resetAllBtn" style="background: #dc3545; color: #fff;">🔄 Réinitialiser tout</button>
    <span id="progress">—</span>
  </div>

  <!-- Barre de recherche dans le thème -->
  <div id="themeSearchContainer" style="padding: 1rem; background: var(--card-bg); border-bottom: 1px solid var(--border); margin-bottom: 0;">
    <input type="text" id="themeSearchBar" placeholder="🔍 Rechercher dans ce thème..." style="width: 100%; padding: 0.8rem; background: var(--bg); border: 2px solid var(--accent); color: var(--text); border-radius: 6px; font-size: 1em;">
    <div id="themeSearchResults" style="display: none; margin-top: 1rem; padding: 1rem; background: var(--bg); border-radius: 6px; max-height: 300px; overflow-y: auto;">
      <div id="themeSearchResultsContent"></div>
    </div>
  </div>

  <div id="fiche">
    <h2 id="ficheTitle"></h2>
    <div id="ficheContent"></div>
  </div>
  
  <div id="quizContainer"></div>

<script>
function q(question, options, correctIndex, explanation) {
  return { question, options, correctIndex, explanation };
}

const THEMES = [
  {
    id: "specificationsMalt",
    category: "MALT",
    title: "1. Spécifications du malt",
    ficheRich: [
      { title: "Humidité du malt", items: ["**Humidité optimale: 4–6%** pour un stockage à long terme stable et prévention des moisissures.", "L'eau > 8% favorise la dégradation enzymatique et le développement microbien (Fusarium, moisissures).", "Stockage optimal: température < 15°C + obscurité améliore la stabilité. À 20°C, perte ~1% qualité/mois.", "Mesurée par **titrage Karl Fischer**, méthode standard analytique avec précision ±0.1%."] },
      { title: "Protéines brutes et FAN", items: ["**FAN (Free Amino Nitrogen): 150–180 mg/L** source d'azotes libres essentiels pour la levure dans le moût final. Insuffisant → fermentation lente, diacétyle.", "**FAN pale malt spécifique: 120–150 mg/L** (valeur typique pour le malt de base lui-même), tandis que le niveau optimal général dans le moût est de 150–180 mg/L pour la fermentation.", "Les protéines structurent le grain et contribuent à la **mousse de bière** (stabilisent les bulles via complexes protéine-polyphénol).", "**Indice de Kolbach (IK) = FAN/Protéines Totales (%)** : 40–50% optimal. IK < 35% = modification insuffisante. IK > 45% = mousse faible.", "Protéines + polyphénols → complexe protéine-tanin → **casse chaude** (70°C clarification) ou **casse froide** (5°C défaut)."] },
      { title: "Couleur EBC et mesure", items: ["**Pale malt: 3–8 EBC** très clair, amidon maximisé pour la conversion enzymatique complète. **Usage: 60–100% de la recette** comme malt de base fournissant l'essentiel des sucres fermentescibles et des enzymes de conversion.", "**Munich: 10–25 EBC** repos prolongé 75–85°C, protéines élevées, mélanoïdines intermédiaires. **Usage typique: 20–50%** dans les Lagers de type Oktoberfest ou Munich Dunkel, apportant une couleur ambrée et des arômes maltés prononcés.", "**Caramel: 20–200 EBC** sucres résiduels figés dans le grain (saccharification in-grain), douceur résiduelle.", "**Chocolat/Noir: 800–1500 EBC** torréfaction > 200°C, sucres brûlés, notes café/cacao, acidité (↓ pH). Usage < 5% (Black) ou < 10% (Chocolat)."] },
      { title: "Densité d'extraction", items: ["Rendement des sucres fermentescibles **80–90%** de la masse du malt. Facteurs : amidon (70%), protéines (11%), β-glucanes (5%).", "Dépend de: type de malt (2RP vs 6RW), finesse du broyage (75–150 microns), température d'empâtage (62–73°C), durée repos enzymatique (45–90 min), pH moût (5.4–5.8)."] },
      { title: "Paramètres Clés de Qualité", items: ["**Extrait Fine Grind (Min 80.5%)**: Potentiel maximum sucres fermentescibles après saccharification complète. Lié à teneur amidon.", "**Différence Fin/Gros (Max 2.0%)**: Indicateur **modification** du grain. Faible différence = endosperme bien dégradé = conversion facile.", "**Friabilité (Min 80.0%)**: Mesure **vitrosité** (dureté). Friabilité élevée = grain tendre = meilleure hydratation, conversion rapide.", "**Viscosité (Max 1.60 mPas)**: Directement liée aux **β-glucanes**. Viscosité élevée → risque colmatage filtre lors filtration."] },
      { title: "Impact sur le Brassage", items: ["**Humidité excessive** → perte rendement financier, développement mycotoxines (DON), conservation médiocre.", "**Extrait faible** → rendement insuffisant, bière moins riche, volume insuffisant pour recette cible.", "**Modification insuffisante** → nécessite palier protéinique long pour convertir amidon, risque colmatage.", "**FAN insuffisant** → fermentation lente, levure sous stress, diacétyle (saveur beurre rancide), alcool incomplet.", "**Kolbach trop élevé** → protéines dégradées excessives → mousse faible ou collapse rapide."] }
    ],
    questions: [
      q("Quelle est l'humidité optimale du malt?", ["2–3%", "4–6%", "10–12%", "15–20%"], 1, "4–6% permet un stockage stable à long terme."),
      q("Que signifie FAN?", ["Fungal Acid Neutralization", "Free Amino Nitrogen source pour la levure", "Fast Acid Number", "Fermentation Amino Acid"], 1, "FAN = azotes libres essentiels pour la fermentation."),
      q("Quel est le niveau optimal de FAN (mg/L)?", ["50–100 mg/L", "150–180 mg/L", "250–300 mg/L", "> 400 mg/L"], 1, "150–180 mg/L optimal pour la fermentation."),
      q("Qu'est-ce que l'indice de Kolbach?", ["Couleur EBC", "Dégradation protéique/solubilité", "Densité d'extraction", "Amertume IBU"], 1, "Mesure le degré d'hydrolyse des protéines."),
      q("Quelle est la couleur EBC du pale malt?", ["1–2 EBC", "3–8 EBC", "20–50 EBC", "200+ EBC"], 1, "3–8 EBC très clair."),
      q("Si l'humidité du malt dépasse 8%, quelle conséquence principale?", ["Conservation meilleure", "Favorise moisissures et dégradation enzymatique", "Augmente les sucres fermentescibles", "Aucun impact"], 1, "L'eau catalyse les réactions de dégradation."),
      q("Quelle est la température idéale de stockage du malt?", ["Température ambiante 20–25°C", "Froid inférieur à 15°C + obscurité", "Chauffé à 40°C", "Congelé à –20°C"], 1, "Le froid ralentit les réactions de dégradation."),
      q("Quel est le rôle principal des protéines dans la mousse de bière?", ["Les lipides la stabilisent", "Les protéines colloïdales stabilisent les bulles de CO₂", "Les sucres la créent", "Les acides gras la renforcent"], 1, "Les protéines viscoélastiques forment l'écume stable."),
      q("Quel est le pourcentage optimal pour l'indice de Kolbach?", ["20–30%", "40–50%", "70–80%", "95–100%"], 1, "40–50% représente une dégradation protéique équilibrée."),
      q("Quel est le rendement typique d'extraction du malt (densité)?", ["50–60%", "70–75%", "80–90%", "95–100%"], 2, "80–90% de rendement en sucres fermentescibles."),
      q("Quelle est la cause principale du brunissement du malt?", ["Oxydation des acides gras", "Réaction de Maillard entre sucres et acides aminés", "Fermentation par la levure", "Humidité de l'eau"], 1, "La réaction de Maillard = polymérisation créant la couleur brune."),
      q("Quelle est la méthode standard de mesure de la couleur EBC?", ["Goût par panel sensoriel", "Spectrophotométrie visible à 430 nm", "Analyse olfactive", "Évaluation visuelle à l'œil"], 1, "Analyse spectrophotométrique standardisée internationalement."),
      q("Quelle est la température de repos pendant le touraillage du malt Munich?", ["50–60°C", "60–65°C prolongé", "75–80°C", "Au-dessus de 90°C"], 2, "Repos prolongé à 75–85°C pour développer les mélanoïdines."),
      q("D'où proviennent les sucres résiduels du malt Caramel?", ["Fermentation par la levure", "Saccharification in-grain figée par chauffage", "Sucre de candi ajouté", "Chauffage seul sans enzyme"], 1, "Saccharification in-grain = sucres figés dans le grain."),
      q("Quelle est la proportion typique de pale malt dans une recette?", ["10–20%", "60–80% comme base", "100% exclusif", "Jamais utilisé"], 1, "60–80% de pale malt constitue la base de la plupart des recettes."),
      q("Qu'est-ce que le titrage Karl Fischer?", ["Protéines", "Dosage de l'humidité avec précision", "Couleur", "IBU"], 1, "Dosage de l'eau avec précision extrême."),
      q("Quelle est la différence entre le FAN et les protéines totales?", ["FAN représente moins de 10% des protéines", "FAN représente environ 20–30% des protéines totales", "FAN et protéines sont identiques", "FAN est supérieur aux protéines"], 1, "FAN est une fraction soluble des azotes libres."),
      q("Quel est l'impact de la lumière sur le stockage du malt?", ["La lumière n'a aucun impact", "La lumière catalyse l'oxydation et dégrade le malt", "La lumière améliore la qualité", "L'obscurité rend le malt inutilisable"], 1, "La lumière = oxydation et dégradation rapide."),
      q("Quelle est l'intensité de la réaction de Maillard dans le malt Caramel?", ["Légère", "Intense car saccharification in-grain à température élevée", "Nulle", "Modérée"], 1, "Réaction intense créant des sucres caramélisés figés."),
      q("À quelle température les protéases sont-elles actives?", ["20–30°C (inactive)", "Environ 50°C (hydrolyse optimale)", "75–80°C", "Au-dessus de 95°C"], 1, "Environ 50°C : les protéases hydrolysent les protéines."),
      q("Quel est le niveau de FAN typique pour le pale malt?", ["80–100 mg/L", "120–150 mg/L", "180–200 mg/L", "Plus de 250 mg/L"], 1, "120–150 mg/L est le niveau standard pour le pale malt."),
      q("Qu'est-ce que mesure l'indice de Kolbach?", ["Amidon conversion", "Hydrolyse protéique/solubilité", "Sucre fermentation", "Activation enzyme"], 1, "Mesure l'hydrolyse protéique."),
      q("À quel usage le malt Munich est-il destiné?", ["Jamais rare", "5–20% complément", "20–50% style Lager", "80–100% exclusive"], 2, "20–50% dans les Lagers Oktoberfest."),
      q("Quelle est la couleur EBC du malt Chocolat?", ["50–100 EBC", "400–600 EBC", "800–1500 EBC", "1500+ EBC"], 2, "800–1500 très sombre noir."),
      q("Quel est l'impact de la température du séchage du malt?", ["Zéro impact", "Basse T° pas de dégradation", "Haute T° réaction de Maillard et couleur", "Indifférent"], 2, "Haute T° = réaction de Maillard."),
      q("Le pale malt est-il obligatoire en base?", ["10–20%", "40–50%", "60–100% fondation", "0% jamais"], 2, "60–100% pour la base de recettes."),
      q("Quelle est la relation protéine/amidon?", ["Amidon source", "Protéine + amidon dans le grain", "Sucre seul", "Enzyme"], 1, "Le grain = protéine + amidon."),
      q("Que se passe-t-il si l'humidité de stockage dépasse 12%?", ["Stockage optimal", "Dégradation accélérée et moisissures", "Aucun effet notable", "Améliore la saveur maltée"], 1, "Dégradation catalysée par l'excès d'eau."),
      q("Quelle est la différence entre l'indice de Kolbach et le FAN?", ["Ils sont identiques", "FAN = azotes libres (mg/L), Kolbach = ratio d'hydrolyse (%)", "Ils sont inversés", "Aucune relation"], 1, "FAN mesure une quantité absolue, Kolbach un ratio en pourcentage."),
      q("Quel est l'impact de la fraîcheur du malt sur la qualité?", ["Le malt reste stable indéfiniment", "La qualité baisse avec le temps par oxydation", "La qualité s'améliore avec le temps", "Aucun changement notable"], 1, "Fraîcheur = meilleure qualité, moins d'oxydation.")
    ]
  },
  {
    id: "turbidite",
    category: "MALT",
    title: "2. Turbidité",
    ficheRich: [
      { title: "Colloïdes et complexes", items: ["**Complexe protéine-polyphénol** macromolécules colloïdales.", "Le chauffage du moût crée des liaisons entre protéines (hordéines) et tannins.", "Casse colloïdale = trouble visible dans la bière."] },
      { title: "NTU - Mesure du trouble", items: ["**Nephelometric Turbidity Unit (NTU)** diffusion à 90°.", "**ISO 7027** spectrophotométrie standard.", "Unité: mg SiO₂/L équivalent.", "Cible brasserie: < 2–5 NTU pour la clarté."] },
      { title: "Casse chaude vs froide", items: ["**Casse chaude**: Précipitation ~70°C (clarification).", "**Casse froide**: Trouble ~5°C (défaut)."] },
      { title: "Impact sensoriel", items: ["Trouble élevé = bière trouble, saveur astringente.", "0–2 NTU = brillant et transparent.", "2–10 NTU = légèrement trouble.", "> 20 NTU = inacceptable."] }
    ],
    questions: [
      q("Quelle est la cause principale de la turbidité dans la bière?", ["Les sucres simples dissous", "Complexes protéine-polyphénol colloïdaux", "Levures viables en suspension", "Pigments de couleur du malt"], 1, "Colloïdes protéine-polyphénol forment le trouble."),
      q("Que signifie l'abréviation NTU?", ["Neutral Turbidity Unit", "Nephelometric Turbidity Unit (mesure à 90°)", "Natural Trouble Unit", "Nitrogen Total Unit"], 1, "NTU mesure la diffusion de la lumière pour quantifier le trouble."),
      q("À quel angle la lumière est-elle mesurée pour déterminer le NTU?", ["45 degrés", "90 degrés", "180 degrés", "0 degré"], 1, "90° est l'angle standard de diffusion nephelométrique."),
      q("À quelle température se produit la casse chaude?", ["40–50°C", "Environ 65–75°C", "85–95°C", "Au-dessus de 100°C"], 1, "Environ 70°C : précipitation protéine-polyphénol bénéfique."),
      q("À quelle température se produit la casse froide?", ["Inférieur à 5°C", "15–20°C", "40–50°C", "80–90°C"], 0, "Environ 5°C lors du refroidissement : trouble indésirable."),
      q("Qu'est-ce qu'un polyphénol dans la bière?", ["Un type de sucre simple", "Des tannins colloïdaux provenant du malt", "Une enzyme de dégradation", "Un lipide du houblon"], 1, "Polyphénols = tannins du malt et houblon."),
      q("Quelle est la cible professionnelle de turbidité (NTU) pour une bière claire?", ["Inférieur à 50 NTU", "Inférieur à 2–5 NTU", "10–20 NTU", "Supérieur à 50 NTU"], 1, "Moins de 5 NTU = bière excellemment claire."),
      q("Dans quel contexte recherche-t-on la casse chaude?", ["C'est un défaut à éviter absolument", "C'est une clarification souhaitable pendant l'ébullition", "Pendant la fermentation", "Pendant le stockage"], 1, "Casse chaude = clarification bénéfique à 70°C."),
      q("Quel niveau de NTU correspond à une turbidité légère?", ["0–2 NTU (transparent)", "10–20 NTU", "Plus de 50 NTU", "Immesurable"], 1, "10-20 NTU représente une turbidité légère visible."),
      q("Quelle est la source principale des protéines causant la turbidité?", ["La levure", "Les hordéines du malt d'orge", "Le houblon", "L'eau de brassage"], 1, "Le malt est la source principale des protéines."),
      q("Quelle est la source de polyphénol?", ["Levure", "Pellicule du malt et résine du houblon", "Sucre", "Enzyme"], 1, "Malt pellicule + houblon."),
      q("La casse froide affecte quelle saveur?", ["Sucré", "Astringent et tannique", "Fruité", "Acide"], 1, "Astringence off-flavour."),
      q("Quel est le standard ISO 7027?", ["Couleur EBC", "Turbidité NTU", "IBU", "Densité"], 1, "Standard trouble international."),
      q("Un trouble > 50 NTU est-il acceptable?", ["Excellent", "Inacceptable", "Bon", "Moyen"], 1, "> 50 NTU rejeté."),
      q("Quel type de liaisons forment le complexe protéine-polyphénol?", ["Hydrogène faible", "Liaisons covalentes fortes", "Électrostatique", "Aucune"], 1, "Liaisons chimiques stables."),
      q("À quelle température la protéase agit?", ["20–30°C", "~50°C hydrolyse", "75–80°C", "> 95°C"], 1, "~50°C les protéases sont actives."),
      q("Les colloïdes ont quelle consistance?", ["Liquide cristallin", "Suspension opaque", "Gaz vapeur", "Solide"], 1, "Suspension colloïdale opaque."),
      q("Quel instrument mesure NTU?", ["Goût par panel", "Spectrophotomètre à 90°", "Odeur", "Œil"], 1, "Spectrophotomètre est l'instrument."),
      q("La casse protéine-tannin est-elle souhaitable?", ["Jamais", "Chauffage ~70°C clarification", "Fermentation", "Froid"], 1, "70°C ébullition clarification."),
      q("Quelle est l'apparence d'une bière sans trouble?", ["Trouble opaque", "Cristallin et transparent", "Blanc laiteux", "Brunâtre"], 1, "Cristallin transparent."),
      q("Qu'est-ce que l'hordéine?", ["Sucre", "Protéine du malt de type gluten", "Enzyme", "Lipide"], 1, "Protéine du grain d'orge."),
      q("Quelle est la taille des macromolécules colloïdales?", ["< 1 nm", "1–100 nm micron", "> 1 mm", "Invisible"], 1, "Taille colloïdale nanoparticules."),
      q("La casse chaude est-elle bénéfique?", ["Non problème", "Oui clarification souhaitable", "Rarement", "Jamais"], 1, "Oui clarification bénéfique."),
      q("La turbidité affecte-t-elle le goût?", ["Zéro impact", "Saveur astringente désagréable", "Améliore", "Indifférent"], 1, "Astringence sensation négative."),
      q("Comment se forment les complexes?", ["Oxydation simple", "Liaisons polyphénol-protéine par chauffage", "Fermentation levure", "Dilution eau"], 1, "Liaisons chimiques formation."),
      q("Les colloïdes légères sont-elles visibles?", ["Très visible trouble", "Invisible cristallin", "Partiellement légèrement", "Blanc opaque"], 1, "Invisible bière claire."),
      q("Pourquoi mesure-t-on à 90°?", ["Angle standard meilleure sensibilité", "Angle arbitraire", "Zéro raison", "Meilleur prix"], 1, "Standard meilleure sensibilité angle."),
      q("Quelle est la source principale de tannin?", ["Levure fermentation", "Pellicule du malt et résine du houblon", "Sucre ajouté", "Minéraux de l'eau"], 1, "Malt et houblon sources tannins."),
      q("Quand se produit la casse froide?", ["Pendant l'ébullition", "Refroidissement ~5°C", "Après fermentation", "Stockage chaud"], 1, "Refroidissement à température basse."),
      q("Comment se stabilisent les colloïdes?", ["Spontanément", "Protéines viscoélastiques stabilisent les bulles", "Sucres seul", "Zéro stabilisation"], 1, "Protéines stabilisent les suspensions.")
    ]
  },
  {
    id: "houblonIBU",
    category: "HOUBLON",
    title: "8. Houblon & IBU",
    ficheRich: [
      { 
        title: "Acides alpha et isomérisation", 
        items: [
          "**Humulones (α-acides)** : Acides de la résine du houblon, 3-18% selon variété",
          "**État initial** : Non solubles dans l'eau, peu amers à l'état brut",
          "**Isomérisation** : Chauffage >60°C convertit α-acides en iso-α-acides solubles et amers",
          "**Rendement** : 25-40% des α-acides deviennent IBU (60+ min ébullition = optimal)",
          "**Cohumulone** : 20-45% des α-acides, taux élevé = amertume plus rude"
        ]
      },
      { 
        title: "IBU - Mesure de l'amertume", 
        items: [
          "**International Bittering Unit** : 1 IBU = 1 mg iso-α-acides/L de bière",
          "**Calcul** : IBU = (AA% × Poids g × Utilisation% × 1000) / Volume L",
          "**Échelle typique** : 10-20 (lagers légères), 30-50 (IPA), 60-100+ (Double IPA)",
          "**Facteurs** : Temps ébullition, température, pH, densité, forme houblon"
        ]
      },
      { 
        title: "Utilisation bittering", 
        items: [
          "**Timing** : 60-90 min avant fin ébullition",
          "**Variétés** : High AA (>10%) : Magnum, Warrior, Columbus, Galena",
          "**Objectif** : Maximiser IBU, huiles aromatiques évaporées",
          "**Rendement** : 60 min = ~28% utilisation, 90 min = ~30%"
        ]
      },
      { 
        title: "Utilisation aromatique", 
        items: [
          "**Timing** : 0-20 min fin ébullition, whirlpool 70-90°C, dry hopping",
          "**Variétés** : Aromatiques : Cascade, Citra, Mosaic, Saaz, Hallertau",
          "**Objectif** : Préserver huiles essentielles volatiles (terpènes)",
          "**Late hopping** : 0-5 min = arôme max, ~5-10% IBU",
          "**Whirlpool (70-90°C)** : **Température optimale 70–90°C** car assez chaude pour dissoudre les huiles essentielles lipophiles et assurer une légère stérilisation du houblon, avec un **rythme d'isomérisation considérablement ralenti** par rapport à l'ébullition (l'isomérisation des α-acides commence dès ~60°C mais s'accélère exponentiellement avec la température). Cette plage préserve les terpènes volatils tout en maximisant leur extraction et solubilité dans le moût, avec un faible ajout d'IBU (5-15 IBU typique en 20-30 min).",
          "**Dry hopping** : Post-fermentation froid, 0 IBU, arôme fruité/floral intense"
        ]
      },
      { 
        title: "Ratio BU:GU et équilibre", 
        items: [
          "**Calcul** : BU:GU = IBU / (OG - 1.000) × 1000",
          "**< 0,5** : Maltée, sucrée (Bock, Scotch Ale)",
          "**0,5-0,7** : Équilibrée (Pale Ale, Amber)",
          "**0,7-1,0** : Houblonnée (IPA, APA)",
          "**> 1,0** : Très houblonnée (Double IPA)"
        ]
      },
      { 
        title: "Houblons nobles vs modernes", 
        items: [
          "**Nobles** : Saaz, Hallertau, Tettnang, Spalt | 3-5% AA, faible cohumulone, arôme délicat",
          "**Américains bittering** : Magnum, Warrior, Columbus | 12-18% AA, efficacité maximale",
          "**Américains aromatiques** : Cascade (agrumes), Citra (tropical), Mosaic (baies), Simcoe (pin)"
        ]
      },
      { 
        title: "Stockage et points clés", 
        items: [
          "**Stockage** : Froid (<5°C), sous vide/azote, obscurité, 6-12 mois optimal",
          "**HSI** : Hop Storage Index, 0,2-0,5 = excellent (faible dégradation)",
          "**Oxydation** : Perte 5-50%/an des α-acides selon conditions",
          "**Température** : Froid ralentit oxydation de 80% vs température ambiante"
        ]
      }
    ],
    questions: [
      q("Qu'est-ce que l'humulone dans le houblon?", ["Un type de sucre", "Les acides α-acides de la résine du houblon (humulones)", "Une protéine structurale", "Un lipide aromatique"], 1, "Humulone = acides alpha, précurseurs de l'amertume."),
      q("Qu'est-ce que l'isomérisation des acides alpha?", ["Conversion par chauffage (>60°C) en iso-α-acides amers", "Fermentation par la levure", "Refroidissement du moût", "Aucune transformation"], 1, "La chaleur convertit les alpha-acides en iso-alpha solubles et amers."),
      q("Que signifie l'abréviation IBU?", ["International Bittering Unit", "Index Brewing Unit"], 1, "IBU = unité internationale de mesure de l'amertume."),
      q("À quoi correspond exactement 1 IBU?", ["1 mg d'humulone par litre", "1 mg d'iso-α-acide par litre de bière", "1 ppm de houblon total", "1 mg de terpènes"], 1, "1 IBU = 1 mg d'iso-alpha-acide par litre."),
      q("À quel moment ajoute-t-on le houblon pour le bittering?", ["Les 5 dernières minutes", "60 minutes ou plus d'ébullition pour extraction maximale", "En fin d'ébullition (whirlpool)", "Jamais pendant l'ébullition"], 1, "60+ minutes d'ébullition pour extraction optimale des IBU."),
      q("À quel moment ajoute-t-on le houblon pour l'aromatique?", ["60 minutes complètes", "15–30 minutes avant la fin", "5 minutes ou whirlpool (70–90°C)", "Jamais pendant l'ébullition"], 1, "Fin d'ébullition ou whirlpool pour préserver les arômes volatiles."),
      q("Les terpènes du houblon sont-ils stables à la chaleur?", ["Très stables au chauffage", "Volatiles et se dégradent au-dessus de 100°C", "Insolubles dans l'eau", "Se polymérisent à la chaleur"], 1, "Les terpènes sont volatiles et s'évaporent avec la chaleur intense."),
      q("Les iso-α-acides créent-ils l'amertume?", ["Non, ils donnent une saveur douce", "Oui, ils créent l'amertume perceptible", "Ils donnent une saveur sucrée", "Ils sont neutres en goût"], 1, "Les iso-alpha-acides sont responsables de l'amertume."),
      q("Quelles variétés de houblon utilise-t-on pour le bittering?", ["Houblons aromatiques ou nobles", "Houblons à haute teneur en AA (>10%)", "Houblons à faible AA (<7%)", "Aucun houblon spécifique"], 1, "High AA pour maximiser l'extraction d'amertume."),
      q("Quelles variétés de houblon utilise-t-on pour l'aromatique?", ["High AA uniquement", "Low AA (<7%)", "Houblons nobles (Hallertau, Saaz)", "Aromatiques et nobles (low AA)"], 1, "Houblons nobles et aromatiques pour leurs huiles essentielles."),
      q("La perception IBU est-elle subjective?", ["Objectif chimique", "Subjectif humain", "Zéro relation", "Variable"], 1, "Objectif mesure chimique."),
      q("Quelle est la source d'amertume?", ["Sucres résiduels", "ISO-α-acides du houblon IBU", "Levure", "Tannins du malt"], 1, "Acides iso-alpha du houblon."),
      q("Différence acides alpha vs beta?", ["Alpha = bittering, Beta = aromatique", "Identique", "Beta bittering", "Alpha nul"], 1, "Alpha bittering, beta aromatique."),
      q("Qu'est-ce que le ratio IBU:OG?", ["BU:GU < 0,5 maltée", "BU:GU 0,5–0,8 équilibre", "BU:GU > 0,8 houblonnée", "BU:GU = IBU/(OG–1000)"], 1, "Tous facteurs BU:GU."),
      q("Quel est le rendement IBU?", ["Toujours 100%", "30–40% modéré", "70–80%", "Variable T°/pH"], 1, "Variable selon conditions."),
      q("Qu'est-ce que le séchage du houblon?", ["Zéro impact", "Concentre les acides alpha", "Augmente", "Détruit"], 1, "Concentration des acides."),
      q("Quelle est la durée de stockage houblon?", ["Indéfini", "6–12 mois optimal", "1 mois", "Heures"], 1, "6–12 mois de stockage."),
      q("Qu'est-ce que l'indice HSI?", ["Densité sucre", "Hop Storage Index qualité", "Humidité", "IBU"], 1, "Hop Storage Index qualité."),
      q("Quel est le rendement en acides alpha?", ["5–10% faible", "25–50% modéré", "100% total", "Variable selon variété"], 1, "Variable selon variété."),
      q("Quel est le seuil de perception amertume?", ["< 10 IBU", "~15–20 IBU", "> 40 IBU", "Zéro"], 1, "~15–20 IBU perceptible."),
      q("Le chauffage isomérises les acides?", ["20–30°C", "60°C+ convertit les iso-alpha", "100°C+ destruction", "Froid seulement"], 1, "60°C+ convertit les iso-alpha."),
      q("Quelle est la température optimale pour le whirlpool aromatique?", ["Moins de 40°C (arômes perdus)", "70–90°C (préserve les terpènes)", "100°C+ (destruction des arômes)", "Température froide"], 1, "70–90°C : température optimale pour whirlpool aromatique."),
      q("Quel houblon est typiquement utilisé pour le style Pilsner?", ["Cascade américain", "Saaz noble tchèque", "Chinook à high AA", "Citra fruité"], 1, "Saaz = houblon noble classique des Pilsners."),
      q("À quoi contribuent principalement les acides bêta du houblon?", ["Amertume directe", "Arôme principalement", "Couleur de la bière", "Densité du moût"], 1, "Les acides bêta contribuent surtout à l'arôme."),
      q("Quelle est la température optimale pour l'isomérisation des acides alpha?", ["40–50°C", "60–70°C", "90–100°C (ébullition)", "120°C et plus"], 2, "Ébullition nécessaire pour isomérisation efficace."),
      q("Quelle est la caractéristique principale du houblon Cascade?", ["Floral noble", "Agrumes et pamplemousse", "Épicé terreux", "Fruité tropical"], 1, "Cascade = profil agrumes typiquement américain."),
      q("Utilisation first wort hopping?", ["Début empâtage", "Avant ébullition dans moût chaud", "Fin ébullition", "Fermentation"], 1, "First wort = avant ébullition."),
      q("Cohumulone élevée donne?", ["Amertume douce", "Amertume astringente rude", "Arôme fruité", "Zéro impact"], 1, "Cohumulone = amertume rude."),
      q("Houblon noble caractéristiques?", ["High AA > 12%", "Low AA 3-5%, arôme délicat", "AA moyen 8%", "Zéro AA"], 1, "Nobles = low AA, arôme fin."),
      q("Lupuline c'est quoi?", ["Tige du houblon", "Glandes jaunes résine", "Feuille verte", "Racine"], 1, "Lupuline = glandes résineuses.")
    ]
  },
  {
    id: "formeHoublon",
    category: "HOUBLON",
    title: "9. Formes de houblon",
    ficheRich: [
      { 
        title: "Cônes entiers (Whole leaf)", 
        items: [
          "**Description** : Cônes de houblon séchés intacts, forme naturelle",
          "**Rendement** : 30-40% extraction des α-acides (moins efficace)",
          "**Avantages** : Qualité aromatique excellente, huiles volatiles préservées",
          "**Inconvénients** : Dosage imprécis, volumineux (10x pellets), oxydation rapide",
          "**Stockage** : Congélation –18°C sous vide essentielle"
        ]
      },
      { 
        title: "Pellets Type 90 (T90) - Standard", 
        items: [
          "**Description** : Houblon broyé et compressé en granulés, 90% de la masse originale",
          "**Rendement** : 50-60% extraction (50% meilleur que cônes)",
          "**Avantages** : Dosage précis, compact, stable, polyvalent (bittering + arôme)",
          "**Perte lupuline** : ~10% lors compression (acceptable)",
          "**Usage** : Standard mondial, 90% du marché"
        ]
      },
      { 
        title: "Pellets Type 45 (T45) et Cryo Hops", 
        items: [
          "**T45** : Lupuline concentrée 45% masse, 2x plus concentré que T90, trub réduit",
          "**Cryo Hops** : Lupuline purifiée par congélation –196°C, poudre jaune concentrée",
          "**Concentration** : 2-3x plus d'huiles et α-acides que T90",
          "**Avantages** : Arômes intenses, réduction trub 50%, biotransformation optimale",
          "**Inconvénients** : Prix élevé (3-4x T90), texture poudreuse",
          "**Usage** : NEIPA, dry hopping intensif"
        ]
      },
      { 
        title: "Extraits CO₂ supercritique", 
        items: [
          "**Description** : Résine extraite par CO₂ supercritique, liquide visqueux",
          "**Pureté** : 90-95% α-acides et β-acides",
          "**Rendement** : 95-100% utilisation (quasi-total)",
          "**Types** : Non-iso (bruts) ou iso-extraits (pré-isomérés pour post-fermentation)",
          "**Avantages** : Dosage ultra-précis (±0,1 IBU), stabilité 5+ ans, zéro trub",
          "**Inconvénients** : Zéro arôme, amertume parfois métallique",
          "**Usage** : Bittering précis, ajustement post-fermentation"
        ]
      },
      { 
        title: "Comparaison efficacité et coût", 
        items: [
          "**Rendement** : Extraits (95-100%) > Cryo (75-85%) > T45 (70-80%) > T90 (50-60%) > Cônes (30-40%)",
          "**Coût relatif** : Cônes (1x) < T90 (1,5x) < T45 (2,5x) < Cryo (4x) < Extraits (10x base poids)",
          "**Volume** : Extraits (0,5%) < Cryo (3%) < T45 (5%) < T90 (10%) < Cônes (100%)",
          "**Stockage** : Extraits très stables, T90/T45 modérés, cônes sensibles"
        ]
      },
      { 
        title: "Recommandations usage", 
        items: [
          "**Bittering (60+ min)** : T90 ou extraits (économique, efficace)",
          "**Aromatique ébullition** : T90 standard",
          "**Whirlpool** : T90 ou cônes",
          "**Dry hopping classique** : T90 (standard)",
          "**Dry hopping NEIPA** : T45, Cryo (arôme intense, trub contrôlé)",
          "**Ajustement final** : Iso-extraits (post-fermentation)",
          "**Polyvalence** : T90 convient 90% des applications"
        ]
      }
    ],
    questions: [
      q("Quel est le rendement en extraction des cônes de houblon frais?", ["Excellent", "Modéré (30–40%)", "Faible", "Nul"], 1, "Rendement modéré de 30–40% pour les cônes frais."),
      q("Que représentent les pellets T90?", ["100% de cônes complets", "90% de résidu de houblon compressé", "70% de concentration", "Poudre fine"], 1, "T90 = 90% de la masse du houblon original après compression."),
      q("Quel est le rendement des pellets T90 comparé aux cônes?", ["Identique", "T90 donne 50–60% vs 30–40% pour cônes", "Cônes meilleurs", "Variable aléatoire"], 1, "T90 offre un bien meilleur rendement d'extraction."),
      q("Le dosage des pellets T90 est-il précis?", ["Très difficile", "Facile et précis au milligramme", "Impossible", "Nécessite balance spécialisée"], 1, "Dosage facile et précis avec les pellets."),
      q("Quelle forme de houblon offre la meilleure stabilité?", ["Cônes frais", "Pellets T90", "Extraits CO₂", "Identique"], 1, "T90 et extraits offrent meilleure stabilité au stockage."),
      q("Les cônes de houblon frais ont-ils une bonne qualité aromatique?", ["Excellente qualité aromatique", "Modérée", "Pauvre", "Aucune"], 1, "Les cônes frais ont une excellente qualité aromatique."),
      q("Que sont les extraits de houblon au CO₂?", ["Cônes entiers séchés", "Résine de houblon pure et concentrée", "Pellets standard", "Poudre de malt"], 1, "Extraits = résine pure extraite au CO₂ supercritique."),
      q("Le dosage des extraits de houblon est-il précis?", ["Difficile à mesurer", "Très précis au milligramme", "Impossible", "Approximatif seulement"], 1, "Dosage très précis grâce à la concentration."),
      q("Les extraits de houblon ont-ils des qualités aromatiques?", ["Excellentes", "Modérées", "Aucune (zéro aromatique)", "Dégradées"], 1, "Extraits ont zéro qualité aromatique, uniquement bittering."),
      q("À quoi servent principalement les extraits de houblon?", ["Arôme uniquement", "Bittering avec contrôle précis des IBU", "Usage généraliste", "Jamais utilisés"], 1, "Extraits = contrôle précis du bittering."),
      q("Les cônes sont-ils volumineux?", ["Compact", "Volumineux", "Minimal", "Énorme"], 1, "Volumineux cônes."),
      q("Qu'est-ce que T90?", ["Teneur 90%", "Total 90%", "Temperature 90°", "Type 90"], 1, "Teneur 90% de résidu."),
      q("Quel ordre d'efficacité?", ["Cônes > T90 > Extraits", "Cônes < T90 < Extraits", "Identique", "Variable"], 1, "Cônes < T90 < Extraits."),
      q("Quel est le coût relatif?", ["Cônes < T90 < Extraits", "Cônes > T90 > Extraits", "Identique", "Variable"], 1, "Cônes moins cher."),
      q("Pour un brasseur débutant?", ["Cônes difficile", "T90 facile dosage", "Extraits concentré", "Indifférent"], 1, "T90 facile."),
      q("L'humidité des cônes a quel impact?", ["Zéro impact", "Élevée dégradation alpha", "Zéro acceptable", "Humide optimal"], 1, "Humidité dégradation."),
      q("Comment conserve-t-on les cônes?", ["Température ambiante", "Congélateur –20°C + vide", "Chauffé", "Humide"], 1, "Froid vide optimal."),
      q("Pellets vs extraits coût?", ["Pellets plus cher", "Extraits plus cher concentré", "Identique", "Variable"], 1, "Extraits plus concentré."),
      q("Les cônes conservent-ils les terpènes?", ["Zéro perdu", "Bien préservés qualité", "Partiellement", "Complètement"], 1, "Bien préservés cônes."),
      q("Rendement vs impact relatif?", ["Cônes meilleur impact", "T90 rendement + impact", "Extraits impact maximal", "Identique"], 1, "Extraits impact maximal."),
      q("T90 permet quelle utilisation?", ["Bittering uniquement", "Bittering + aromatique", "Aromatique uniquement", "Jamais"], 1, "T90 polyvalent bittering + arôme."),
      q("Oxydation des cônes produit?", ["Fromage cheddar", "Fruité tropical", "Floral", "Neutre"], 0, "Oxydation = arôme fromage."),
      q("Pellets T45 c'est quoi?", ["45% résidu standard", "Lupuline concentrée 45% masse", "45°C séchage", "45 jours stockage"], 1, "T45 = lupuline concentrée."),
      q("Cryo hops avantage?", ["Moins cher", "Concentration lupuline, moins matière végétale", "Plus d'amertume", "Conservation zéro"], 1, "Cryo = lupuline pure concentrée."),
      q("Extraits isomérises utilisés pour?", ["Arôme final", "Bittering post-fermentation ajustement", "Whirlpool", "Dry hop"], 1, "Extraits iso = ajustement IBU après."),
      q("Stockage pellets optimal?", ["Température ambiante", "Froid + vide sous azote", "Humide", "Lumière"], 1, "Froid + vide préserve AA."),
      q("Cônes vs pellets biodisponibilité?", ["Cônes meilleur", "Pellets meilleur extraction", "Identique", "Variable"], 1, "Pellets = meilleure extraction."),
      q("Extraits CO₂ supercritique avantage?", ["Moins cher", "Pureté maximale sélective", "Arôme intense", "Conservation longue"], 1, "CO₂ supercritique = extraction sélective pure."),
      q("Utilisation extraits en fermentation?", ["Jamais toxique levure", "Possible post-fermentation", "Début fermentation", "Pendant empâtage"], 1, "Post-fermentation pour ajuster IBU."),
      q("Pellets T90 perte lupuline vs cônes?", ["50% perte", "~10% perte acceptable", "Zéro perte", "90% perte"], 1, "~10% perte lors compression.")
    ]
  },
  {
    id: "orgeVarietes",
    category: "MALT",
    title: "3. Variétés d'orge (2RP/6RW)",
    ficheRich: [
      { title: "Orge à 2 Rangées (2RP - Spring Barley / Printemps)", items: [
        "**Saison de semis**: Semée au **printemps** (mars-avril), récoltée en été. Cycle court de croissance.",
        "**Caractéristiques**: Le grain est plus gros, mieux rempli d'amidon, ce qui se traduit par un **rendement en extrait plus élevé**. La teneur en protéines est naturellement **plus faible** (bas Azote), menant à un meilleur contrôle du IK et une meilleure clarté.",
        "**Usage**: C'est l'orge standard pour le maltage en Europe et la fabrication de bières où la saveur maltée fine et la clarté sont recherchées (Pils, Lager, Pale Ale)."
      ]},
      { title: "Orge à 6 Rangées (6RW - Winter Barley / Hiver)", items: [
        "**Saison de semis**: Semée en **automne/hiver** (octobre-novembre), récoltée au printemps suivant. Cycle plus long.",
        "**Caractéristiques**: Le grain est plus petit, mais la plante produit **davantage d'enzymes** (Diastasique Power très élevé). La teneur en protéines est généralement **plus élevée** (haut Azote). Les enveloppes sont plus épaisses.",
        "**Usage**: Indispensable lors de l'utilisation d'**adjoints non maltés** (riz, maïs, blé cru) dans la recette. Le surplus d'enzymes qu'elle fournit permet de compenser le manque de pouvoir diastasique de ces adjoints. Les pailles plus épaisses sont aussi bénéfiques pour la filtration."
      ]},
      { title: "Relation Modification/Enzymes", items: [
        "Les malts 2RP sont souvent naturellement mieux modifiés que les 6RW, car le grain est plus homogène. L'orge 6RW nécessite souvent des ajustements de palier protéinique pour gérer son taux d'azote plus élevé et sa dégradation protéique."
      ]}
    ],
    questions: [
      q("L'orge 2 rangées (2RP) contient quoi comparé à la 6RW?", ["Plus de protéines", "Moins de protéines + plus d'amidon", "Plus d'enzymes", "Moins d'amidon"], 1, "2RP favorise l'extrait amylacé (plus d'amidon, moins d'azote)."),
      q("L'orge 6 rangées (6RW) est idéale pour quoi?", ["Conversion des adjuvants non maltés", "Fermentation froide", "Bières sans houblon", "Bières acides"], 0, "L'excès d'enzymes de la 6RW permet de convertir riz, maïs, etc."),
      q("Quelle est la caractéristique de l'enveloppe de la 6RW?", ["Fine et mince", "Épaisse (avantage pour filtration)", "Moyenne", "Variable aléatoire"], 1, "Enveloppe épaisse = avantage pour la filtration du moût."),
      q("Quelle est la taille des grains de l'orge 2RP?", ["Petits", "Gros grains", "Moyens", "Variables"], 1, "Grains plus gros = plus d'amidon stocké."),
      q("Quel est le rendement en extrait de l'orge 2RP?", ["Bas", "Moyen", "Élevé", "Variable"], 2, "Grain bien rempli = rendement élevé."),
      q("Quelle est la teneur en azote de la 6RW?", ["Basse", "Moyenne", "Haute", "Ultra-haute"], 2, "Teneur en protéines (azote) élevée dans la 6RW."),
      q("Quelle est la production enzymatique de la 6RW?", ["Basse", "Normale", "Élevée", "Énorme"], 3, "Production enzymatique très élevée, essentielle pour les adjuvants."),
      q("La clarté de la bière avec l'orge 2RP est comment?", ["Faible", "Bonne clarté", "Excellente", "Variable"], 1, "Faible teneur en protéines = meilleure clarté."),
      q("La modification du grain de la 6RW est comment?", ["Rapide", "Lente", "Moyenne", "Inconsistante"], 3, "Grain plus hétérogène = modification variable."),
      q("Le palier protéinique est-il nécessaire avec la 6RW?", ["Pas besoin", "Optionnel", "Recommandé", "Critique"], 2, "Recommandé pour gérer la haute teneur en azote."),
      q("L'orge 2RP est typiquement utilisée pour quel style?", ["IPA uniquement", "Pilsner et Lager principalement", "Stout", "Porter"], 1, "2RP = base traditionnelle des lagers européennes."),
      q("Quels adjuvants sont typiques avec la 6RW?", ["Seigle", "Riz et maïs", "Blé", "Avoine"], 1, "Riz et maïs = céréales non maltées classiques."),
      q("L'indice de Kolbach de la 2RP est comment?", ["Bas", "Idéal", "Haut", "Variable"], 1, "Modification naturelle idéale de la 2RP."),
      q("L'indice de Kolbach de la 6RW est comment?", ["Bas", "Idéal", "Souvent haut", "Variable"], 2, "Protéolyse souvent prononcée."),
      q("L'orge 2RP est semée à quelle saison?", ["Printemps (Spring barley)", "Automne", "Hiver", "Été"], 0, "2-row spring barley = semée au printemps."),
      q("Saison 6RW…", ["Printemps", "Automne", "Hiver", "Été"], 2, "6-row Winter."),
      q("2RP/6RW impact recette…", ["Couleur", "Saveur", "Fermentescibilité/Enzyme", "IBU"], 2, "Profil moût."),
      q("Homogénéité 2RP…", ["Faible", "Bonne", "Excellente", "Très variable"], 1, "Grain uniforme."),
      q("Homogénéité 6RW…", ["Faible", "Bonne", "Excellente", "Très variable"], 0, "Moins uniforme."),
      q("Rendement final 2RP…", ["65%", "70%", "75%", "80%"], 3, "Environ comparatif."),
      q("Densité grain 2RP…", ["Léger", "Moyen", "Lourd", "Ultra-lourd"], 2, "Grain rempli amidon."),
      q("Sélection orge brasseur…", ["Ajustement pH", "Style recette", "Adjoints plan", "Tous"], 2, "Paramètres."),
      q("2RP pour Pale Ale?", ["Non adapté", "Excellent choix", "Moyen", "Jamais"], 1, "2RP idéal Pale Ale."),
      q("6RW coût production?", ["Moins cher", "Plus cher", "Identique", "Variable région"], 0, "Rendement moindre mais enzyme élevée."),
      q("2RP protéines brassage?", ["Nécessite palier long", "Palier court ou skip", "Palier complexe", "Impossible"], 1, "Faible protéines = simple."),
      q("6RW filtration avantage?", ["Enveloppes épaisses lit filtrant", "Plus rapide", "Pas d'avantage", "Plus lent"], 0, "Pailles épaisses aident filtration."),
      q("Usage 2RP moderne?", ["Rare", "Standard mondial", "Obsolète", "Régional"], 1, "2RP = standard actuel."),
      q("6RW adjunct beer type?", ["Light Lager américaine", "IPA", "Stout", "Sour"], 0, "Riz/maïs Light Lager."),
      q("Conversion enzyme 2RP?", ["Suffisante seule", "Besoin supplément", "Faible", "Zéro"], 0, "2RP suffit pour tout-malt."),
      q("Température maltage 2RP vs 6RW?", ["2RP plus basse", "Identique", "6RW plus basse", "Variable"], 1, "Paramètres similaires.")
    ]
  },
  {
    id: "maillardMelanoidines",
    category: "MALT",
    title: "4. Réactions de Maillard et mélanoïdines",
    ficheRich: [
      { title: "Chimie de la Réaction", items: [
        "**Définition**: C'est une réaction de **brunissement non enzymatique** fondamentale. Elle implique la condensation entre le **groupement carbonyle** (C=O) d'un **sucre réducteur** (glucose, maltose, xylose) et le **groupement aminé** (NH2) d'un acide aminé ou d'une protéine.",
        "**Note importante sur les sucres**: Seuls les **sucres réducteurs** (avec carbonyle libre) participent à la réaction. Le **saccharose** (sucre de table) n'est PAS un sucre réducteur car son carbonyle est bloqué dans la liaison glycosidique, donc il ne réagit PAS dans Maillard.",
        "**Conditions**: Accélérée par la **chaleur** (touraillage, ébullition), un **pH élevé** et une faible teneur en eau (faible activité de l'eau).",
        "**Températures de touraillage**: Pale malt 80–85°C (légère réaction), Munich 85–105°C (modérée, mélanoïdines), Malts foncés/torréfiés 120–150°C (réaction intense = couleur sombre et arômes café/cacao prononcés).",
        "**Étapes Clés**: 1) Condensation → 2) Réarrangement d'Amadori → 3) Dégradations (fragmentation des sucres) → 4) Dégradation de Strecker (production d'aldéhydes aromatiques) → 5) Polymérisation."
      ]},
      { title: "Produits et Impacts", items: [
        "**Couleur (EBC)**: La polymérisation finale produit des pigments bruns foncés appelés **Mélanoïdines**.",
        "**Arômes/Saveurs**: La fragmentation et la dégradation de Strecker créent des arômes de **malt, pain grillé, caramel, toffee** et de **cacao/café** (selon l'intensité de la chaleur).",
        "**Mélanoïdines**: Ces polymères de haute masse moléculaire sont essentiels pour le **corps** et la **sensation en bouche** des bières maltées (Bock, Munich Dunkel). Elles agissent aussi comme de puissants **antioxydants**.",
        "**Consommation de FAN**: La réaction consomme des acides aminés libres (FAN), diminuant la quantité de nutriments pour la levure, surtout si la réaction est très intense (longue ébullition ou malts très torréfiés)."
      ]}
    ],
    questions: [
      q("Entre quels composants se produit la réaction de Maillard?", ["Amidon et CO₂", "Sucres réducteurs et acides aminés", "Eau et houblon", "Enzymes et pH"], 1, "Réaction chimique essentielle au développement des saveurs maltées."),
      q("Les mélanoïdines apportent principalement quoi?", ["Amertume", "Couleur brune et corps", "Acidité", "Viscosité uniquement"], 1, "Mélanoïdines = couleur profonde + sensation en bouche."),
      q("Quelle est la première étape de la réaction de Maillard?", ["Condensation C=O + acide aminé", "Réarrangement d'Amadori", "Fragmentation", "Polymérisation"], 0, "Condensation entre carbonyle du sucre et amine."),
      q("Le réarrangement d'Amadori est quelle étape?", ["Étape 1", "Étape 2 du processus", "Étape 3", "Étape 4"], 1, "Deuxième étape après la condensation initiale."),
      q("La réaction de Maillard est accélérée par quoi?", ["Froid", "Humidité élevée", "Chaleur + pH haut + faible humidité", "Alcool élevé"], 2, "Conditions optimales : chaleur, pH basique, faible eau."),
      q("Que produit la fragmentation des sucres dans Maillard?", ["Sucres simples uniquement", "Aldéhydes aromatiques par dégradation de Strecker", "Hydrolyse simple", "Fermentation"], 1, "Dégradation de Strecker crée des aldéhydes aromatiques."),
      q("Quel est le résultat final sur l'échelle EBC de la réaction de Maillard?", ["Couleur pâle", "Couleur ambre", "Couleur brun foncé / noir", "Incolore"], 2, "Pigments polymérisés = brun foncé."),
      q("Quels arômes développe la réaction de Maillard lors du touraillage?", ["Sucré uniquement", "Malt / pain grillé / caramel / cacao", "Acide", "Floral"], 1, "Profil aromatique typique du malt torréfié."),
      q("Quelle est la masse moléculaire des mélanoïdines?", ["Petite", "Grande (polymères)", "Moyenne", "Variable"], 1, "Polymères de haute masse moléculaire."),
      q("Les mélanoïdines agissent comme quoi?", ["Houblons", "Levures", "Antioxydants naturels", "Levains"], 2, "Défense contre le vieillissement oxydatif."),
      q("FAN consommé par Maillard…", ["Aucun", "Peu", "Modéré", "Beaucoup"], 3, "Limite nutriment levure."),
      q("Intensité Maillard…", ["Basse T courte", "Haute T longue", "Dépend sucre", "Dépend eau"], 1, "Paramètres."),
      q("Couleur EBC Pils…", ["5–10", "15–25", "30–40", "50+"], 0, "Pale typical."),
      q("Couleur EBC Munich…", ["5–10", "20–40", "50–70", "80+"], 1, "Foncé mélanoïdines."),
      q("Polymérisation finale…", ["Étape 3", "Étape 4", "Étape 5", "Étape 6"], 2, "Dernier stade."),
      q("Condensation sucre-amino…", ["Hydrose", "Hémiacétal", "Aldéhyde", "Amine"], 2, "Type réaction."),
      q("Perte eau Maillard…", ["Augmente réaction", "Ralentit réaction", "N'affecte pas", "Inverse"], 0, "Eau basse = Maillard ↑"),
      q("Caféine dans Maillard…", ["Produit", "Détruit", "Inchangé", "Variable"], 2, "Non pertinent."),
      q("Saveur toffee/caramel…", ["Sucres simples", "Mélanoïdines", "Hops", "Levain"], 1, "Polymères colorés."),
      q("Bock/Munich Dunkel…", ["Faible Maillard", "Intense Maillard", "Moyen", "Zéro"], 1, "Malt foncé."),
      q("Maillard vs Caramélisation…", ["Même", "Différent", "Pareil résultat", "Inverse"], 1, "Réactions distinctes."),
      q("Température touraillage Maillard?", ["40–60°C faible", "80–100°C modéré", "120–150°C intense", "200°C+ extrême"], 2, "Haute T = Maillard intense."),
      q("pH optimal Maillard?", ["Acide < 5", "Neutre 7", "Basique > 8", "Très acide < 3"], 2, "pH élevé accélère."),
      q("Sucre non réducteur Maillard?", ["Glucose réagit", "Saccharose ne réagit pas", "Maltose réagit", "Fructose réagit"], 1, "Saccharose pas carbonyle libre."),
      q("Acide aminé essentiel Maillard?", ["Tous", "Lysine sensible", "Aucun", "Tryptophane"], 1, "Lysine réactive."),
      q("Temps ébullition impact?", ["Aucun", "Plus long = plus Maillard", "Plus court meilleur", "Indifférent"], 1, "Temps = intensité."),
      q("Mélanoïdines stabilité?", ["Instables", "Stables polymères", "Fragiles", "Réversibles"], 1, "Polymères stables."),
      q("Corps bière mélanoïdines?", ["Léger", "Rond plein", "Aqueux", "Gazeux"], 1, "Sensation bouche."),
      q("Maillard arrêt réaction?", ["Refroidissement", "pH bas", "Dilution", "Tous"], 0, "Froid stoppe."),
      q("Couleur finale dépend?", ["Temps + T° + pH", "Houblon", "Levure", "Eau"], 0, "Paramètres Maillard.")
    ]
  },
  {
    id: "enzymesPalier",
    category: "MALT",
    title: "5. Enzymes et paliers d'empâtage",
    ficheRich: [
      { 
        title: "Bêta-Amylase (β-Amylase)", 
        items: [
          "**Température optimale** : 60-65°C (zone fermentescibilité)",
          "**pH optimal** : 5,4-5,6",
          "**Action** : Coupe l'amidon par les extrémités (exo-enzyme), liaisons α-1,4",
          "**Produit** : Maltose (disaccharide fermentescible), 50-70% des sucres",
          "**Thermolabilité** : Détruite au-dessus de 70°C",
          "**Impact** : Basse température (62-65°C) = bière sèche et alcoolisée"
        ]
      },
      { 
        title: "Alpha-Amylase (α-Amylase)", 
        items: [
          "**Température optimale** : 68-75°C (zone dextrinisation)",
          "**pH optimal** : 5,6-5,8",
          "**Action** : Coupe l'amidon aléatoirement à l'intérieur (endo-enzyme)",
          "**Produit** : Dextrines (non fermentescibles), maltotriose, maltose",
          "**Thermostabilité** : Résiste jusqu'à 75-78°C",
          "**Cofacteur** : Nécessite Ca²⁺ pour stabilité",
          "**Impact** : Haute température (70-73°C) = bière avec corps et douceur"
        ]
      },
      { 
        title: "Paliers de saccharification", 
        items: [
          "**Palier Bêta (62-65°C)** : Favorise maltose → bière sèche, fermentescible (75-85% atténuation)",
          "**Palier Alpha (70-73°C)** : Favorise dextrines → bière douce, corps plein (65-75% atténuation)",
          "**Monopalier (66-68°C)** : Compromis équilibré, standard moderne (70-78% atténuation)",
          "**Durée standard** : 60 min pour conversion complète",
          "**Test d'iode** : Noir-bleu = amidon résiduel, jaune = conversion OK"
        ]
      },
      { 
        title: "Palier protéinique (50-55°C)", 
        items: [
          "**Enzymes** : Protéases et peptidases actives",
          "**Objectif** : Augmenter FAN (nutrition levure), dégrader β-glucanes",
          "**Durée** : 15-30 min (court = ↑FAN, long = ↓mousse)",
          "**Utilité** : Malts sous-modifiés, adjuvants (blé, avoine, seigle)",
          "**Malts modernes** : Souvent inutile (si Kolbach > 42%)",
          "**Risque** : Trop long détruit protéines de mousse"
        ]
      },
      { 
        title: "Autres paliers", 
        items: [
          "**Mash-out (75-78°C)** : Arrêt enzymatique, améliore filtration (5-10 min, optionnel)",
          "**Décoction (méthode traditionnelle allemande)** : Technique où une portion (30-40%) de la maische est retirée, portée à ébullition (100°C) pendant 10-20 min, puis réincorporée pour augmenter la température du reste. **Avantages** : Maximise l'extraction avec malts sous-modifiés, développe arômes maltés intenses par réaction de Maillard pendant l'ébullition. **Usage moderne** : Optionnel avec malts bien modifiés d'aujourd'hui, principalement utilisé pour styles traditionnels (Bock, Doppelbock, Pilsner tchèque) ou pour authenticité historique.",
          "**Palier β-glucanes (40-45°C)** : Réduit viscosité, améliore filtration (rare, malts bien modifiés)",
          "**Palier acide (35-45°C)** : Acidification par phytase (obsolète, remplacé par acide lactique)"
        ]
      },
      { 
        title: "Facteurs clés", 
        items: [
          "**Température** : Principal facteur, chaque enzyme a un optimum étroit",
          "**pH** : 5,2-5,6 optimal, > 6,0 réduit activité drastiquement",
          "**Temps** : 90% conversion en 30 min, 95% en 60 min",
          "**Ratio eau/grain** : Épais (2,5-3 L/kg) = rapide, dilué (3,5-4 L/kg) = lent",
          "**Calcium** : Essentiel pour α-amylase, stabilise enzymes"
        ]
      },
      { 
        title: "Exemples programmes selon styles", 
        items: [
          "**Pilsner/IPA (sèche)** : 63-64°C/60min",
          "**Pale Ale (équilibrée)** : 67°C/60min (monopalier)",
          "**Stout (corps)** : 70°C/60min",
          "**Weizen (blé)** : 45°C/15min → 63°C/40min → 72°C/20min",
          "**Standard moderne** : Monopalier 66-67°C/60min convient 90% des recettes"
        ]
      }
    ],
    questions: [
      q("La bêta-amylase produit majoritairement quel sucre?", ["Dextrines", "Maltose (fermentescible)", "Glucose", "Amidon"], 1, "Le maltose est le principal sucre fermentescible produit."),
      q("La plage de température 68-75°C favorise quelle enzyme?", ["Une bière sèche", "L'alpha-amylase (crée du corps)", "Le palier protéinique", "L'amertume"], 1, "L'alpha-amylase crée des dextrines pour le corps."),
      q("Quelle est la température optimale de la bêta-amylase?", ["50–55°C", "60–65°C", "70–75°C", "80–85°C"], 1, "Température optimale d'activité bêta-amylase."),
      q("Quelle est la température optimale de l'alpha-amylase?", ["50–55°C", "60–65°C", "68–75°C", "80–90°C"], 2, "Température supérieure à la bêta-amylase."),
      q("À quelle température la bêta-amylase est-elle détruite?", ["60°C", "65°C", "70°C et plus", "80°C"], 2, "Thermolabilité : détruite au-dessus de 70°C."),
      q("L'alpha-amylase a quelle thermostabilité?", ["Très fragile", "Fragile", "Résistante (survit plus longtemps)", "Ultra-résistante"], 2, "Elle survit plus longtemps que la bêta-amylase."),
      q("Comment la bêta-amylase coupe-t-elle l'amidon?", ["Coupure interne", "Coupure externe (par les extrémités)", "Coupure aléatoire", "Coupure random"], 1, "Coupure spécifique par les extrémités de la chaîne."),
      q("Les dextrines sont-elles fermentescibles?", ["Totalement fermentescibles", "Non fermentescibles par levures standard", "Partiellement", "Dépend de la levure utilisée"], 1, "Les dextrines apportent le corps et la douceur résiduelle."),
      q("Le palier bêta (62–65°C) donne quel profil de bière?", ["Bière sèche + alcoolisée", "Bière avec corps + douceur", "Bière équilibrée", "Bière acide"], 0, "Beaucoup de maltose = bière sèche et alcoolisée."),
      q("Le palier alpha (70–73°C) donne quel profil?", ["Bière sèche + alcool", "Bière avec corps + douceur résiduelle", "Bière équilibrée", "Bière acide"], 1, "Beaucoup de dextrines = corps et rondeur."),
      q("Un monopalier (66–68°C) donne quel résultat?", ["Bière très sèche", "Bière très douce", "Bière équilibrée (compromis)", "Bière acide"], 2, "Compromis entre corps et fermentescibilité."),
      q("Quelle est la température du palier protéinique?", ["30–40°C", "50–55°C (protéases actives)", "60–65°C", "70–75°C"], 1, "50–55°C pour activer les protéases et peptidases."),
      q("Quel est le rôle des protéases et peptidases?", ["Créent de l'amidon", "Dégradent les protéines en peptides", "Hydrolysent les graisses", "Oxydent les polyphénols"], 1, "Conversion de haut poids moléculaire vers bas poids."),
      q("Les β-glucanes sont dégradés par quelle enzyme?", ["Amylase", "Protéase", "Glucanase spécifique", "Lipase"], 2, "Enzyme spécifique pour les bêta-glucanes."),
      q("Dans quel palier augmente-t-on le FAN?", ["Palier bêta", "Palier alpha", "Palier protéinique (50–55°C)", "Monopalier"], 2, "Libération des acides aminés libres."),
      q("Palier Protéinique long…", ["Augmente mousse", "Réduit mousse", "Neutral", "Améliore clarté"], 1, "Dégrade protéines structures."),
      q("Palier 52°C typique durée…", ["5–10 min", "15–30 min", "45–60 min", "90+ min"], 1, "Standard industrie."),
      q("Saccharification optim pH…", ["5.0–5.2", "5.4–5.6", "6.0–6.2", "6.5–6.8"], 1, "Amylases."),
      q("pH > 6.0 sur amylases…", ["Augmente", "Réduit fortement", "Neutral", "Inactive"], 1, "Enzyme sensibilité."),
      q("Enzyme dénatur T…", ["55°C", "65°C", "75°C", "85°C+"], 3, "Destruction totale."),
      q("Iode test amidon…", ["Sucres", "Amidon résiduel", "Protéines", "Levures"], 1, "Vérification."),
      q("Conversion amidon efficacité…", ["% dépend palier", "% dépend T", "% dépend temps", "Tous"], 3, "Paramètres."),
      q("Limite dextrinisation Alpha-Amylase?", ["20%", "30%", "40% limité par ramifications", "100%"], 2, "Branches alpha-1,6 résistent."),
      q("Mash-out température?", ["70°C", "75–78°C arrêt enzymes", "85°C", "95°C"], 1, "Stop conversion."),
      q("Temps palier Bêta optimal?", ["10–20 min", "30–45 min", "60–90 min complet", "120+ min"], 2, "Extraction maltose."),
      q("Palier acid rest 40–45°C?", ["Augmente pH", "Réduit pH via phytase", "Neutre", "Destroy enzymes"], 1, "Acidification naturelle."),
      q("Ratio eau/grain impact?", ["Aucun", "Plus épais = enzymes concentrées", "Plus dilué meilleur", "Indifférent"], 1, "Concentration enzyme."),
      q("Decoction bénéfice?", ["Extraction maximale sous-modifié", "Plus rapide", "Moins cher", "Optionnel moderne"], 0, "Méthode traditionnelle."),
      q("Enzyme endogène vs exogène?", ["Malt vs ajoutée", "Même", "Levure vs malt", "Bactérie vs levure"], 0, "Source enzyme."),
      q("Paliers multiples nécessité?", ["Toujours", "Malt bien modifié = non", "Jamais", "Optimal"], 1, "Moderne skip possible.")
    ]
  },
  {
    id: "sucres",
    category: "GÉNÉRAL",
    title: "43. Sucres (amidon, candi, miel…)",
    ficheRich: [
      { title: "Sucres Issus du Maltage et Structure", items: [
        "**Amidon**: Polymère de glucose, composé d'**Amylose** (chaînes linéaires) et d'**Amylopectine** (chaînes ramifiées, majoritaires). C'est la source énergétique principale du moût.",
        "**Maltose**: Disaccharide (glucose-glucose) très facilement fermentescible. Il représente 50-70 % des sucres totaux après une saccharification typique.",
        "**Maltotriose**: Trisaccharide, plus long, fermenté plus lentement que le Maltose par Saccharomyces cerevisiae. Sa consommation influence la densité finale.",
        "**Dextrines**: Polysaccharides de plus de 3 molécules de glucose. Non fermentescibles par les levures de bière classiques, elles sont vitales pour le **corps, la viscosité et la douceur** résiduelle."
      ]},
      { title: "Sucres d'Adjonction (Adjuvants)", items: [
        "**Sucre de Candi / Saccharose**: Sucre de table (glucose-fructose). Il est presque 100 % fermentescible. Son ajout est souvent fait à l'ébullition pour **augmenter la densité initiale (DI)** sans ajouter de corps, ce qui conduit à une bière **sèche et alcoolisée** (typique des Dubbel/Tripel belges).",
        "**Dextrose / Glucose**: Sucre simple (monosaccharide), immédiatement fermentescible par la levure. Il est couramment utilisé pour l'**embouteillage** (refermentation en bouteille).",
        "**Lactose**: Disaccharide (galactose-glucose) non fermentescible par Saccharomyces cerevisiae (manque de l'enzyme bêta-galactosidase). Il est utilisé pour apporter une **douceur non alcoolique** et du corps (Sweet Stout, Milk Stout)."
      ]}
    ],
    questions: [
      q("Le sucre de candi sert à…", ["Baisser le pH", "Augmenter l'alcool sans alourdir le corps", "Épaissir la bière", "Clarifier le moût"], 1, "Il est presque totalement fermentescible, allégeant le corps."),
      q("Le lactose est ajouté pour…", ["↑ FAN", "Amertume", "Corps et Douceur", "Couleur"], 2, "Il est non fermentescible et apporte de la douceur."),
      q("Quelle est la composition de l'amidon?", ["Amylose (linéaire) + Amylopectine (ramifiée)", "Glucose seul", "Maltose uniquement", "Dextrine simple"], 0, "Deux composants structuraux de l'amidon."),
      q("Quelle est la structure de l'amylose?", ["Chaîne ramifiée", "Chaîne linéaire de glucose", "Structure cyclique", "Structure aléatoire"], 1, "Chaînes linéaires de glucose."),
      q("Quelle est la structure de l'amylopectine?", ["Chaîne ramifiée (majoritaire dans l'amidon)", "Chaîne linéaire", "Structure cyclique", "Hélice"], 0, "Chaînes ramifiées, composant majoritaire."),
      q("Quelle est la composition du maltose?", ["Glucose-Glucose (disaccharide)", "Glucose-Fructose", "Glucose-Galactose", "Glucose-Mannose"], 0, "Disaccharide formé de deux glucose."),
      q("Le maltotriose est composé de combien d'unités?", ["Deux unités (di-sucre)", "Trois unités de glucose (tri-sucre)", "Polysaccharide long", "Sucre simple"], 1, "Trois unités de glucose."),
      q("Les dextrines sont-elles fermentescibles?", ["100% fermentescibles", "50% fermentescibles", "0% (non fermentescibles)", "Dépend de la levure"], 2, "Les levures typiques ne fermentent pas les dextrines."),
      q("Le saccharose est composé de quoi?", ["Sucre de table complet", "Glucose + Fructose", "Glucose + Galactose", "Maltose"], 1, "Sucre de table classique."),
      q("Quel pourcentage du saccharose est fermentescible?", ["50%", "75%", "100% (complètement fermentescible)", "0%"], 2, "Fermentation complète par la levure."),
      q("Quel est l'impact du saccharose sur la bière?", ["Augmente le corps", "Neutre sur le corps / bière sèche finale", "Diminue le corps", "Astringence"], 1, "Augmente l'alcool sans ajouter de corps."),
      q("Le dextrose est égal à quoi?", ["Fructose", "Glucose (sucre simple)", "Saccharose", "Maltose"], 1, "Dextrose = glucose monosaccharide."),
      q("Dextrose usage…", ["Bouteille carbonatation", "Empâtage", "Refroidissement", "Whirlpool"], 0, "Embouteille standard."),
      q("Lactose source…", ["Maltage", "Levure", "Lait", "Amidon"], 2, "Sucre laitier."),
      q("Lactose enzyme…", ["β-galactosidase", "Sucrase", "Maltase", "Invertase"], 0, "Manquante à levure."),
      q("Lactose % douceur…", ["Léger", "Moyen", "Élevé", "Intense"], 2, "Moût + final."),
      q("Miel composition…", ["Glucose/Fructose", "Sucre pure", "Protéine", "Lipides"], 0, "Sucres majoritaires."),
      q("Miel brassage impact…", ["Stérilisation obligatoire", "Direct OK", "Refroidissement hygiène", "Pasteurisation"], 2, "Microbes naturels."),
      q("Sirop maïs HFCS…", ["Naturel", "Complètement artificiel", "Transformation maïs", "Synthèse chimique"], 2, "Glucose/Fructose."),
      q("Sucres adjoint % total…", ["1–5%", "5–15%", "15–30%", "30–50%"], 2, "Variabilité brasseur."),
      q("Densité finale faible…", ["Sucres non-fermentescibles bas", "Fermentation trop sèche", "Malt faible", "Tous"], 1, "Profil sec."),
      q("Densité finale élevée…", ["Dextrines résiduelles", "Lactose/Sucre non-ferment", "Sucres insuffisant consommés", "Tous"], 3, "Douceur reste."),
      q("Invert sugar avantage?", ["Moins cher", "Fermentation rapide prédigéré", "Plus sucré", "Couleur"], 1, "Glucose+fructose séparés."),
      q("Candi belge couleur?", ["Blanc clair", "Ambre caramélisé", "Noir foncé", "Tous"], 3, "Variétés multiples."),
      q("Turbinado/Demerara?", ["Sucre raffiné", "Sucre brut mélasse résiduelle", "Sucre artificiel", "Édulcorant"], 1, "Moins raffiné."),
      q("Mélasse ajout?", ["Couleur + saveur forte", "Neutre", "Clarification", "Houblon substitute"], 0, "Saveur profonde."),
      q("Honey malt?", ["Malt au miel", "Malt caramel saveur miel", "Miel cristallisé", "Aucun"], 1, "Type spécialité."),
      q("Adjuncts % maximum safe?", ["10%", "20%", "40% fermentescibilité OK", "80%"], 2, "Équilibre important."),
      q("Carapils/Dextrine malt?", ["Fermentescible", "Corps sans fermentation", "Sucré", "Amer"], 1, "Dextrines ajoutées."),
      q("Treacle britannique?", ["Mélasse sombre", "Sucre blanc", "Miel", "Sirop érable"], 0, "Saveur intense stout.")
    ]
  },
  {
    id: "gluten",
    category: "GÉNÉRAL",
    title: "44. Gluten et bières sans gluten",
    ficheRich: [
      { title: "Chimie et Pathologie", items: [
        "**Gluten**: Complexe protéique composé de **gluélinines** (élasticité) et de **prolamines** (viscosité). Dans l'orge, la prolamine est la **Hordéine**.",
        "**Impact Brassicole**: Les protéines du gluten et ses précurseurs (polypeptides) jouent un rôle majeur dans la **formation et la stabilité de la mousse** et le corps de la bière.",
        "**Cœliaque**: La maladie est déclenchée par la réponse immunitaire à certains fragments peptidiques du gluten. Le seuil légal de sécurité pour la certification 'sans gluten' est de **moins de 20 ppm** (20 mg/kg) en Europe et au Canada."
      ]},
      { title: "Méthodes de Production", items: [
        "**Méthode 1: Céréales sans gluten**: Utilisation de céréales alternatives comme le millet, le riz, le maïs, le sorgho, ou le sarrasin (qui est une pseudocéréale). Ces bières ont un profil de saveur différent et une tenue de mousse souvent inférieure.",
        "**Méthode 2: Dé-glutéinisation**: Brassage avec du malt d'orge conventionnel, puis ajout d'une enzyme, souvent la **Prolyl Endopeptidase (PE)** (nom commercial **Brewers Clarex®**), en début de fermentation.",
        "**Rôle de l'enzyme**: La PE coupe spécifiquement les liaisons peptidiques contenant des prolines. Elle fragmente les grosses protéines de gluten en très petits fragments qui ne sont plus reconnus par le système immunitaire des cœliaques (sous le seuil de 20 ppm).",
        "**Vérification**: La conformité au < 20 ppm doit être confirmée par la méthode d'analyse **ELISA** R5 (Enzyme-Linked Immunosorbent Assay) validée."
      ]}
    ],
    questions: [
      q("Le seuil de certification 'sans gluten' est de…", ["100 ppm", "20 ppm", "5 ppm", "50 ppm"], 1, "20 ppm est le seuil légal en Europe."),
      q("L'enzyme Brewers Clarex® sert à…", ["Augmenter l'IBU", "Dégrader le gluten", "Réduire la couleur", "Augmenter la viscosité"], 1, "C'est une enzyme utilisée pour réduire la teneur en gluten."),
      q("Quelle est la différence entre gluélines et prolamines?", ["Ce sont identiques", "Élasticité vs Viscosité (composants du gluten)", "Sucre vs Protéine", "Enzyme vs Inhibiteur"], 1, "Deux composants complémentaires du gluten."),
      q("L'hordéine est quoi exactement?", ["Gluten du blé", "Prolamine spécifique de l'orge", "Gluten du seigle", "Protéine de l'avoine"], 1, "Protéine clé de l'orge responsable du gluten."),
      q("Quel est l'impact du gluten sur la mousse?", ["Réduit la mousse", "Amplifie la stabilité de la mousse", "Effet neutre", "Détruit la mousse"], 1, "Protéines structurelles stabilisent les bulles."),
      q("Quelle est la cause de la maladie cœliaque?", ["Infection par levure sauvage", "Réaction immunitaire aux fragments peptidiques du gluten", "Mycotoxines", "Alcool trop élevé"], 1, "Réponse immunitaire anormale au gluten."),
      q("Quelles céréales pour bière sans gluten?", ["Orge modifiée", "Riz / Maïs / Sorgho / Millet", "Blé à gluten réduit", "Extrait de malt"], 1, "Céréales alternatives naturellement sans gluten."),
      q("Pseudocéréales sans gluten…", ["Riz", "Maïs", "Sarrasin", "Avoine"], 2, "Pas vraies céréales."),
      q("Bière sans gluten saveur…", ["Identique", "Différente/Mousse faible", "Sucrée", "Amère"], 1, "Profil distinct."),
      q("Prolyl Endopeptidase (PE) cible…", ["Amidon", "Protéines prolines", "Lipides", "Minéraux"], 1, "Liaisons spécifiques."),
      q("PE coupe liaison…", ["N-N", "Proline-spécifique", "C-C", "S-S"], 1, "Peptidique proline."),
      q("Fragment peptide après PE…", ["Gros > 20ppm", "Petit < 20ppm", "Amidon", "Sucre"], 1, "Sous seuil."),
      q("PE activation…", ["Avant empâtage", "Début fermentation", "Après ébullition", "Fin maturation"], 1, "Fermentation active."),
      q("ELISA R5 test…", ["Goût", "Détecte gluten immunologique", "Coloration", "Densité"], 1, "Analyse validation."),
      q("Température PE optimale…", ["15-20°C (fermentation)", "37°C", "55°C", "80°C"], 0, "Température de fermentation, pas corporelle."),
      q("Céréales alternatives mousse…", ["Bonne", "Faible/Instable", "Excellente", "Variable"], 1, "Protéines moins."),
      q("Riz gluten…", ["Contient", "Zéro gluten naturel", "Trace only", "Élevé"], 1, "Naturellement sans."),
      q("Maïs gluten…", ["Contient trace", "Aucun", "Peu", "Élevé"], 1, "Naturellement sans."),
      q("Certification sans gluten…", ["Test simple", "ELISA R5 obligatoire", "Visuel", "Goût"], 1, "Analyse pointue."),
      q("Hordéine structure…", ["Chaîne linéaire", "Polymère complexe", "Sucre", "Lipide"], 1, "Protéine gluten."),
      q("Bière sans gluten brasserie…", ["Procédé identique", "Séparation ligne production", "Même équipement", "Sans précaution"], 1, "Contamination risque."),
      q("Dé-glutéinisation efficacité…", ["Partielle", "Complète < 20ppm", "Nulle", "80–90%"], 1, "Enzymatique."),
      q("Avoine gluten contenu?", ["Aucun naturel", "Trace pure non contaminée", "Élevé", "Modéré"], 1, "Contamination croisée risque."),
      q("Quinoa bière?", ["Céréale", "Pseudocéréale sans gluten", "Contient traces", "Impossible brasser"], 1, "Alternative valide."),
      q("Gluten extraction maltage?", ["Complet", "Partiel résidus", "Aucun", "Augmente"], 1, "Protéines persistent."),
      q("Bière gluten-reduced vs gluten-free?", ["Même", "Reduced > 20ppm, Free < 20ppm", "Inverse", "Marketing"], 1, "Distinction légale."),
      q("Brewers Clarex dosage?", ["1–3 g/hL", "5–10 g/hL", "15–20 g/hL", "Selon fabricant protocole"], 3, "Instructions spécifiques."),
      q("Ligne production contamination?", ["Négligeable", "Critique séparation absolue", "Rinçage suffit", "Optionnel"], 1, "Traces suffisent cœliaque."),
      q("PE origine enzyme?", ["Bactérie Aspergillus", "Levure", "Plante", "Synthèse"], 0, "Enzyme microbienne."),
      q("Test terrain gluten?", ["Kits rapides < fiables", "ELISA seul certifié", "Goût suffit", "Visuel"], 1, "Laboratoire requis.")
    ]
  },
  {
    id: "histoire",
    category: "GÉNÉRAL",
    title: "45. Histoire de la bière",
    ficheRich: [
      { title: "Antiquité : Bière Aliment et Fermentation Spontanée", items: [
        "**Mésopotamie (Sumer)**: Les plus anciennes preuves de brassage (4000 av. J.-C.) montrent une boisson épaisse, riche en nutriments, fermentée à partir de galettes d'orge. La bière était un aliment de base, souvent consommée à la paille pour éviter les résidus.",
        "**Égypte ancienne**: La bière (bouza) était cruciale. Le processus reposait entièrement sur le **microbiote ambiant** (levures sauvages et bactéries), d'où une qualité très variable et un goût souvent acide.",
        "**Innovation**: Le processus d'empâtage (mash) est une étape clé de l'histoire, permettant l'extraction des sucres fermentescibles."
      ]},
      { title: "Moyen Âge : Monastères et Houblon", items: [
        "**Gruit**: Le **Gruit** était le mélange d'herbes aromatiques utilisé avant le houblon (*Myrica gale*, Armoise, etc.). Il servait à masquer les défauts et à conférer de faibles propriétés de conservation.",
        "**Adoption du Houblon (XIIe - XIVe siècles)**: L'utilisation du *Humulus lupulus* s'est généralisée depuis les monastères allemands (Bavière). Le houblon a révolutionné la bière grâce à ses qualités aromatiques supérieures et, surtout, à ses propriétés **antibactériennes** (défense contre les bactéries lactiques et acétiques) et **antioxydantes**, améliorant la conservation."
      ]},
      { title: "L'Ère Moderne : Science et Industrie", items: [
        "**Reinheitsgebot (Édit de Pureté Bavarois, 1516)**: Décrété par le Duc Guillaume IV de Bavière, il stipulait que la bière ne devait être faite qu'avec l'**eau, le malt d'orge et le houblon**. Le but initial était d'assurer l'approvisionnement en blé pour le pain et de garantir une qualité minimale.",
        "**Louis Pasteur (XIXe siècle)**: Ses travaux (Théorie des germes) ont prouvé le rôle des levures (*Saccharomyces*) dans la fermentation. Il a permis d'isoler des souches pures, conduisant à la **pasteurisation** et au contrôle microbiologique.",
        "**Carlsberg (Emil Christian Hansen)**: Isola la première souche de levure de lager pure (*Saccharomyces carlsbergensis*) au Danemark en 1883."
      ]}
    ],
    questions: [
      q("Le Reinheitsgebot date de…", ["1857", "1516", "1200", "4000 av. J.-C."], 1, "L'édit de pureté bavarois."),
      q("Le houblon a remplacé quel ingrédient principal ?", ["Le blé", "Le gruit", "L'orge", "Le sucre"], 1, "Le gruit était un mélange d'herbes aromatiques."),
      q("Quand date le brassage de Sumer (Mésopotamie)?", ["Moderne", "Environ 4000 av. J.-C.", "Époque médiévale", "Époque Renaissance"], 1, "Plus anciennes preuves archéologiques de brassage."),
      q("Quel était le statut de la bière en Mésopotamie?", ["Boisson de luxe rare", "Aliment de base nutritif", "Médicament uniquement", "Boisson rituelle"], 1, "Aliment crucial et nutritif pour la population."),
      q("Pourquoi buvait-on la bière à la paille en Antiquité?", ["Question d'hygiène", "Éviter les résidus de grains", "Mode époque", "Tradition religieuse"], 1, "Éviter les impuretés et résidus solides."),
      q("Comment était la qualité de la bière égyptienne (bouza)?", ["Consistante et stable", "Variable avec goût souvent acide", "Très sucrée", "Forte en alcool"], 1, "Fermentation sauvage = qualité variable."),
      q("Quels étaient les composants du gruit médiéval?", ["Orge uniquement", "Mélange d'herbes (Myrica gale, Armoise)", "Levure pure", "Eau filtrée"], 1, "Mélange d'herbes aromatiques avant le houblon."),
      q("Quel était le rôle principal du gruit?", ["Activer la fermentation", "Arôme / masquer défauts / conservation faible", "Ajouter de la couleur", "Stabiliser la bière"], 1, "Saveur herbacée et légère conservation."),
      q("À quelle époque le houblon fut-il adopté?", ["IXe siècle", "XIIe–XIVe siècles", "XVe siècle", "XVIIe siècle"], 1, "Adoption depuis les monastères allemands."),
      q("Quelle est la propriété clé du houblon?", ["Ajoute du sucre", "Antibactérien + antioxydant", "Source d'enzyme", "Agent de levain"], 1, "Propriété de conservation majeure."),
      q("Humulus lupulus désigne quoi?", ["Herbe aromatique générale", "Nom scientifique de la plante houblon", "Levure sauvage", "Bactérie lactique"], 1, "Nom scientifique du houblon."),
      q("Quels étaient les ingrédients du Reinheitsgebot?", ["Eau / Malt / Houblon uniquement", "Eau / Malt / Sucre", "Eau / Orge / Levure", "Tous ingrédients"], 0, "Loi de pureté bavaroise stricte."),
      q("Reinheitsgebot but…", ["Qualité", "Blé pain + qualité", "Prévention", "Export"], 1, "Politique économique."),
      q("Pasteur théorie…", ["Spontanée", "Germes (levures)", "Chimique", "Naturelle"], 1, "Fermentation source."),
      q("Pasteur isolement…", ["Levures pures", "Bactéries", "Enzymes", "Protéines"], 0, "Souches contrôlées."),
      q("Pasteurisation impact…", ["Saveur", "Microbes tués/Stabilité", "Couleur", "IBU"], 1, "Stabilité."),
      q("Carlsberg Hansen…", ["Levure ale", "Levure lager pure Saccharomyces carlsbergensis", "Malt hybride", "Houblon"], 1, "1883 Danemark."),
      q("Saccharomyces cerevisiae…", ["Lager", "Ale/Fermentation haute T", "Basse T", "Hybride"], 1, "Levure classique."),
      q("Fermentation température…", ["Pasteur contrôlait", "Variable sauvage avant", "Toujours identique", "Inconnue"], 1, "Variabilité historique."),
      q("Monastères rôle…", ["Production", "Brassage perfectionné", "Distribution", "Médecine"], 1, "Moyen Âge."),
      q("Bière antique durée conservation…", ["Mois", "Jours à semaines", "Années", "Infinie"], 1, "Peu durable sauvage."),
      q("Houblon acides…", ["Alpha (amertume)", "Bêta (conservation)", "Huiles (arôme)", "Tous"], 3, "Multiples."),
      q("IPA origine historique?", ["Belgique", "Inde coloniale britannique longue conservation", "Allemagne", "USA"], 1, "Export houblonné."),
      q("Prohibition USA bière?", ["Augmentation", "1920–1933 interdiction alcool", "Jamais", "Encouragement"], 1, "Loi sèche."),
      q("Révolution industrielle brassage?", ["Manuelle", "Mécanisation production masse", "Déclin", "Interdite"], 1, "Échelle commerciale."),
      q("Porter style origine?", ["Allemagne", "Londres XVIIIe travailleurs", "Belgique", "USA"], 1, "Bière robuste."),
      q("Lager fermentation basse origine?", ["Angleterre", "Bavière caves fraîches", "Belgique", "Écosse"], 1, "Température contrôle."),
      q("Levure spontanée Lambic?", ["Inoculation", "Air ambiant vallée Senne", "Laboratoire", "Commerciale"], 1, "Tradition belge."),
      q("Trappiste certification?", ["Marketing", "Monastère authentique production", "Goût", "Pays"], 1, "Label strict."),
      q("Bière bouteille invention?", ["Antiquité", "Moyen Âge", "XVIIe s. verre + bouchon", "XXe s."], 2, "Conservation améliorée."),
      q("Réfrigération artificielle impact?", ["Aucun", "Lager toute année production", "Réduit qualité", "Optionnel"], 1, "Contrôle température.")
    ]
  },
  {
    id: "houblonIBUcomplet",
    category: "HOUBLON",
    title: "10. Houblon, amertume et IBU (complet)",
    ficheRich: [
      { title: "La Chimie de l'Amertume et l'Isomérisation", items: [
        "**Source**: L'amertume provient des **Acides Alpha (Humulones)**, des résines molles contenues dans les glandes de **lupuline** du houblon. Les Humulones elles-mêmes sont peu solubles et peu amères.",
        "**Isomérisation**: C'est la conversion chimique des Humulones en **Iso-alpha-Acides (Isohumulones)**. Cette réaction nécessite la **chaleur** (ébullition du moût) et augmente leur solubilité et leur amertume de manière exponentielle.",
        "**Conversion**: Le rendement d'isomérisation (ou utilisation) est maximal après 60 à 90 minutes d'ébullition. L'efficacité est influencée par le pH (plus il est basse, mieux c'est) et la densité du moût."
      ]},
      { title: "L'IBU (International Bitterness Unit)", items: [
        "**Définition et Mesure**: **1 IBU = 1 mg d'iso-alpha-acide par litre de bière**. La mesure est réalisée par spectrophotométrie UV à 275 nm après extraction, car les Isohumulones absorbent fortement à cette longueur d'onde.",
        "**Limites de l'IBU**: L'IBU ne mesure que les Iso-alpha-Acides. Il **ne prend pas en compte** d'autres sources d'amertume, comme les polyphénols oxydés ou les acides bêta oxydés. Par conséquent, la corrélation avec l'amertume **perçue** est imparfaite (voir BU:GU).",
        "**Acides Bêta (Lupulones)**: Ils ne sont pas solubles ou amers sans oxydation. Avec l'âge, ils s'oxydent et contribuent à une amertume plus dure et désagréable. Ils ne sont pas inclus dans l'IBU."
      ]}
    ],
    questions: [
      q("Quelle est la source principale de l'amertume dans la bière?", ["Les huiles essentielles du houblon", "Les acides alpha isomérisés (iso-alpha-acides)", "Les polyphénols du malt", "Le FAN des protéines"], 1, "L'isomérisation des humulones crée l'amertume."),
      q("Comment est mesuré l'IBU?", ["En unités EBC", "En NTU de turbidité", "En mg/L d'iso-α-acides", "En degrés Winkler"], 2, "1 IBU = 1 mg d'iso-alpha-acides par litre."),
      q("Comment les humulones sont-elles converties en iso-alpha-acides?", ["Conversion directe à froid", "Chauffage pendant 60-90 minutes d'ébullition", "Fermentation par la levure", "Repos à température ambiante"], 1, "Isomérisation thermique nécessaire."),
      q("Quelle est la solubilité des iso-alpha-acides?", ["Insolubles dans l'eau froide", "Solubles dans le moût chaud après isomérisation", "Solubles uniquement dans l'alcool", "Solubles dans les graisses"], 1, "Rendus accessibles par l'isomérisation."),
      q("Quelle est la différence entre acides bêta et acides alpha?", ["Identiques en fonction", "Les bêta ne s'oxydent pas", "Les bêta s'oxydent → amertume dure et vieillie", "Les bêta sont sucrés"], 2, "Instabilité au stockage."),
      q("À quelle longueur d'onde mesure-t-on l'IBU par spectrophotométrie?", ["400 nm (visible)", "275 nm (pic d'absorption des iso-α)", "550 nm (couleur)", "Infrarouge"], 1, "Méthode standard de dosage IBU."),
      q("Quel est le rendement typique d'isomérisation après ébullition?", ["5-10%", "30-50%", "60-75%", "Quasi-totale 95%+"], 1, "Rendement modéré même avec chauffage long."),
      q("Quel est l'impact du pH sur l'ébullition et l'isomérisation?", ["Le pH est neutre", "L'acidité favorise l'isomérisation", "Un pH basique est meilleur", "Aucun impact"], 1, "Réaction chimique optimale en milieu acide."),
      q("Quel est le seuil de perception de l'IBU pour la plupart des gens?", ["Environ 1 IBU", "Environ 30-40 IBU", "Plus de 100 IBU", "Variable selon les individus"], 1, "La sensibilité à l'amertume varie."),
      q("Quelle est la structure moléculaire des acides alpha?", ["Un sucre simple", "Résine de lupuline avec chaîne isoprénoïde", "Une enzyme", "Produit de la levure"], 1, "Source des humulones."),
      q("D'où provient la lupuline dans le houblon?", ["Des feuilles", "Des glandes résineuses de la fleur", "Des racines", "De la tige"], 1, "Microstructure du cône de houblon."),
      q("Que sont les extraits de houblon au CO₂?", ["Houblon complet", "Concentré pré-isomérisé ou huiles isolées", "Orge moulue", "Eau de brassage"], 1, "Forme ultra-concentrée."),
      q("Quelles sources d'amertume ne sont pas mesurées par l'IBU?", ["Aucune", "Polyphénols oxydés + acides β vieillis", "Levure uniquement", "Sucres du malt"], 1, "Amertume non-IBU contributive."),
      q("Comment la densité initiale (OG) affecte-t-elle l'efficacité de l'IBU?", ["Aucun impact", "Densité élevée = correction à la baisse de l'IBU", "Plus d'IBU si densité haute", "Relation linéaire"], 1, "Phénomène de solubilité réduite."),
      q("Quelle est la structure chimique de l'humulone?", ["Un acide gras", "Pré-résine avec acide valérianique", "Un sucre complexe", "Une protéine"], 1, "Structure phénolique triploïde."),
      q("Quel type de réaction est l'isomérisation?", ["Oxydation simple", "Déshydratation + énolisation", "Hydrolyse basique", "Polymérisation"], 1, "Chimie organique spécifique."),
      q("Quel temps d'ébullition donne le rendement IBU optimal?", ["5 minutes donnent le maximum", "60 minutes donnent le rendement optimal", "90 minutes font diminuer l'IBU", "L'IBU augmente linéairement indéfiniment"], 1, "Rendement maximal entre 60-90 minutes."),
      q("Comment l'amertume ressentie diffère-t-elle de l'IBU mesuré?", ["Identiques toujours", "Variable (sucres résiduels et polyphénols masquent)", "L'IBU est toujours inexact", "Inversement proportionnels"], 1, "Perception complexe et subjective."),
      q("Comment l'extraction des huiles diffère-t-elle de celle des IBU?", ["Même température pour tout", "Températures différentes: IBU = chauffage, huiles = froid", "Mêmes conditions exactes", "Inversées"], 1, "Différence due à la volatilité."),
      q("Qu'est-ce que le myrcène ou bêta-myrcène?", ["Identiques", "Terpène hydrocarbure de formule C10H16", "Un sucre", "Une enzyme"], 1, "Isomère terpénique."),
      q("Que se passe-t-il lors de l'ajout post-ébullition d'extrait isomérisé?", ["IBU nul", "IBU immédiat et stable garanti", "Amertume très variable", "Se dégrade"], 1, "Déjà sous forme iso-α."),
      q("Quel impact a le vieillissement du houblon sur les acides bêta?", ["Stabilisation", "Oxydation → amertume astringente et dure", "Aucun changement", "Amélioration aromatique"], 1, "Dégradation qualitative."),
      q("Pourquoi mesure-t-on l'IBU par UV plutôt que par goût?", ["Plus rapide", "Quantification objective et reproductible", "Moins cher", "Obligatoire légalement"], 1, "Standardisation analytique."),
      q("Les humulones non-isomérisées sont-elles amères?", ["Très amères", "Peu amères et peu solubles", "Extrêmement amères", "Sucrées"], 1, "L'isomérisation est nécessaire."),
      q("Quelle enzyme n'est PAS impliquée dans l'isomérisation?", ["Aucune enzyme (réaction thermique pure)", "Amylase", "Protéase", "Toutes les réponses"], 0, "Réaction chimique non-enzymatique."),
      q("Quel houblon contribue le plus aux IBU?", ["Houblons nobles à faible AA", "Houblons amers à haute teneur en acides alpha (>10%)", "Houblons aromatiques", "Tous identiques"], 1, "Concentration en acides alpha."),
      q("La couleur du moût affecte-t-elle l'IBU mesuré?", ["Non", "Oui, peut interférer avec spectrophotométrie", "Augmente l'IBU", "Réduit l'IBU"], 1, "Interférence analytique possible."),
      q("Les iso-alpha-acides sont-ils stables dans la bière?", ["Totalement stables", "Relativement stables mais s'oxydent lentement", "Très instables", "Se dégradent en minutes"], 1, "Oxydation progressive."),
      q("Pourquoi le rendement d'isomérisation n'est-il jamais de 100%?", ["Limites thermodynamiques et cinétiques", "Manque de temps", "Température trop basse", "pH incorrect"], 0, "Équilibre chimique."),
      q("Quel facteur influence le plus la solubilité des iso-alpha-acides?", ["La couleur du malt", "La température et le pH du moût", "Le type de levure", "La durée de fermentation"], 1, "Solubilité dépend des conditions physico-chimiques.")
    ]
  },
  {
    id: "formesHoublonComplet",
    category: "HOUBLON",
    title: "11. Formes de houblon (complet)",
    ficheRich: [
      { title: "Cônes (Fleurs Entières)", items: [
        "**Avantages**: Représente la forme la plus intacte, offrant un profil aromatique légèrement plus 'frais' et moins d'impuretés. Moins de **trub** fin en moût.",
        "**Désavantages**: **Faible rendement d'utilisation** (les acides sont moins accessibles), très volumineux, et une forte absorption de moût (pertes importantes) lors de la séparation, ce qui les rend coûteux pour les grands volumes."
      ]},
      { title: "Pellets (Granulés T90)", items: [
        "**Processus**: Cônes séchés, moulus, puis compressés. Le T90 signifie que 90 % de la matière première est conservée. Le broyage libère les acides alpha et les huiles des glandes de lupuline.",
        "**Avantages**: **Meilleur rendement** d'amertume (5-15 % de plus que les cônes) grâce à la surface de contact accrue. Excellente conservation sous vide. **Pertes de bière réduites**.",
        "**Pellets T45 (Lupulin Powder)**: Un concentré où une grande partie de la matière végétale fibreuse (feuilles, tiges) a été éliminée. Il est riche en lupuline, augmentant le rendement, mais demandant une filtration plus fine."
      ]},
      { title: "Extraits et Huiles", items: [
        "**Extraits de CO2 (Supercritique)**: Pâtes très concentrées en acides alpha et/ou huiles. Utilisés pour un **dosage d'IBU extrêmement précis et stable**, sans ajout de matière végétale. Idéal pour la standardisation des amertumes dans les grandes brasseries.",
        "**Isomerisés**: Extraits pré-isomérisés. Ajoutés après l'ébullition (ou en fin de fermentation) pour un IBU immédiat et garanti. Particulièrement utiles pour ajuster l'amertume ou pour le *dry hopping* visant uniquement l'amertume sans introduire de matière végétale."
      ]}
    ],
    questions: [
      q("Quelle forme de houblon offre le meilleur rendement d'IBU?", ["Cônes entiers frais", "Pellets T90 compressés", "Extraits liquides", "Lupuline en poudre"], 1, "La compression en pellets augmente la surface de contact."),
      q("À quoi sert principalement l'extrait de houblon?", ["Ajouter du corps à la bière", "Dosage précis d'IBU ou d'arômes", "Colorer la bière", "Réduire le pH du moût"], 1, "Forme concentrée pour contrôle précis."),
      q("Quel est le principal avantage des cônes de houblon?", ["Rendement IBU optimal", "Arôme frais avec peu d'impuretés", "Faible volume de stockage", "Coût très bas"], 1, "Qualité aromatique supérieure."),
      q("Quel est le principal désavantage des cônes de houblon?", ["Volume énorme à stocker", "Pertes de bière par absorption", "Rendement IBU faible (acides moins accessibles)", "Toxicité"], 2, "Accès difficile aux acides alpha."),
      q("Que signifie T90 dans les pellets T90?", ["Humidité de 90%", "90% de la matière première est conservée", "90% d'acides alpha", "90% d'huiles essentielles"], 1, "Densité de résine après compression."),
      q("Comment le broyage des pellets améliore-t-il l'extraction?", ["Perte d'arôme", "Libère les glandes de lupuline → acides alpha + huiles accessibles", "Tue la levure", "Change le pH"], 1, "Écrasement des micro-glandes."),
      q("Quelle est la différence entre T45 et T90?", ["Identiques", "T45 plus concentré en lupuline, moins de fibres", "T90 plus concentré", "T45 a moins de rendement"], 1, "Pellets ultra-concentrés."),
      q("Qu'est-ce que la Lupulin Powder?", ["Malt en poudre", "Concentré de glandes de houblon sans fibres (rendement+++, filtration fine)", "Orge moulue", "Sucre candi"], 1, "Forme ultra-concentrée."),
      q("Que sont les extraits de CO₂ supercritique?", ["Liquide aqueux", "Pâte concentrée en acides/huiles (dosage IBU précis)", "Gaz compressé", "Solide cristallisé"], 1, "Extraction haute pression."),
      q("Que sont les extraits isomérisés?", ["Acides alpha bruts", "Pré-chauffés/isomérisés (ajout post-ébullition = IBU immédiat)", "Huiles essentielles seules", "Acides bêta purs"], 1, "Prêt-à-utiliser pour amertume instantanée."),
      q("Quel est l'avantage principal des extraits CO₂?", ["Économie de coût", "Dosage IBU/arôme extrêmement précis et reproductible", "Meilleur goût naturel", "Prix le plus bas"], 1, "Standardisation pour brassage industriel."),
      q("Quel problème causent les cônes en termes de pertes?", ["Aucune perte", "Absorption importante de moût (coûteux)", "Pertes minimales comme pellets", "Avantage des cônes"], 1, "Macération absorbe le liquide."),
      q("Quelle forme a la volumétrie la plus compacte?", ["Cônes frais", "Pellets (bien moins volumineux, stockage facile)", "Même volume", "Cônes plus compacts"], 1, "Compression augmente la densité."),
      q("Pourquoi utilise-t-on l'extraction au CO₂ en industrie?", ["Goût supérieur", "Précision et standardisation des lots (compensation variabilité)", "Coloration", "Ajout d'enzymes"], 1, "Reproductibilité inter-lots."),
      q("Quel est le gain de rendement des pellets T90 vs cônes?", ["Cônes meilleurs de 50%", "Pellets: +5-15% grâce à surface de contact accrue", "Extraits variables", "Lupulin: -10%"], 1, "Physique de surface augmentée."),
      q("Comment les pellets se conservent-ils?", ["Péremption rapide", "Longue durée sous vide (oxygène minimal)", "Conservation courte comme cônes", "Très instables"], 1, "Stabilité au stockage optimale."),
      q("Comment dose-t-on précisément l'IBU avec les extraits?", ["Dosage approximatif", "Concentration connue = dosage exact en mg", "Très approximatif", "Impossible à doser"], 1, "Chimie quantifiée précisément."),
      q("Les cônes produisent-ils beaucoup de trub?", ["Aucun trub", "Trub fin important (filtration nécessaire)", "Pellets produisent plus", "Favorise la clarté"], 1, "Débris de feuilles et matière végétale."),
      q("Quelle est la composition de la lupuline?", ["Feuilles du houblon", "Glandes résineuses (acides alpha + huiles terpènes)", "Tige ligneuse", "Fleur entière"], 1, "Microscopiques grains jaunes."),
      q("Que signifie vraiment T90?", ["Température de séchage", "Type 90 = 90% matière première conservée (10% fibres perdues)", "Tension de compression", "Temps de broyage"], 1, "Processus de compression."),
      q("Extraits en poudre vs liquide, quelle différence?", ["Même activité exacte", "Poudre sèche (stabilité longue), Liquide (dosage immédiat)", "Poudre instable", "Aucune différence"], 1, "Forme physique et praticité."),
      q("Pourquoi les pellets T45 nécessitent-ils une filtration fine?", ["Contiennent des levures", "Très concentrés en particules fines de lupuline", "Plus de fibres que T90", "Plus de trub que cônes"], 1, "Concentration extrême."),
      q("Quel type de houblon est préféré pour le dry hopping en brasserie artisanale?", ["Extraits liquides", "Pellets (facilité manipulation, rendement)", "Cônes uniquement", "Poudre T45"], 1, "Compromis efficacité/praticité."),
      q("Les extraits isomérisés peuvent-ils être ajoutés à froid?", ["Non, doivent être chauffés", "Oui, car déjà isomérisés (IBU instantané)", "Seulement à chaud", "Jamais utilisés"], 1, "Pré-traitement thermique déjà fait."),
      q("Quel impact a le conditionnement sous vide sur les pellets?", ["Aucun impact", "Préserve les acides alpha et huiles (anti-oxydation)", "Accélère la dégradation", "Réduit l'efficacité"], 1, "Protection contre l'oxydation."),
      q("Les cônes de houblon absorbent combien de moût environ?", ["Négligeable", "Jusqu'à 2-3 fois leur poids sec", "10% de leur poids", "Aucune absorption"], 1, "Perte économique significative."),
      q("Quelle forme permet le meilleur contrôle qualité en brasserie industrielle?", ["Cônes", "Extraits standardisés (analyse précise des lots)", "Pellets artisanaux", "Mélange aléatoire"], 1, "QC et traçabilité optimales."),
      q("Le broyage des pellets libère quoi spécifiquement?", ["Uniquement les fibres", "Les résines des glandes de lupuline (AA, huiles)", "De l'eau", "Des protéines"], 1, "Rupture des structures cellulaires."),
      q("Pourquoi les extraits sont-ils utilisés pour ajuster l'amertume en fin de brassage?", ["Moins chers", "Dosage précis sans affecter le volume ni les arômes", "Meilleur goût", "Plus rapide"], 1, "Ajustement fin post-production."),
      q("Quelle forme de houblon est la plus sujette à l'oxydation?", ["Extraits sous vide", "Cônes entiers non conditionnés", "Pellets sous azote", "Toutes identiques"], 1, "Surface exposée maximale = oxydation rapide.")
    ]
  },
  {
    id: "aromatique",
    category: "HOUBLON",
    title: "12. Houblonnage aromatique (huiles essentielles)",
    ficheRich: [
      { title: "Les Terpènes et leur Volatilité", items: [
        "**Huiles Essentielles**: Composées de terpènes et de sesquiterpènes. Elles sont la source principale des arômes du houblon. Elles sont hautement **volatiles** (s'évaporent facilement par la chaleur).",
        "**Myrcène**: Terpène majeur, très volatile. Notes intenses de **résine, pin, et épicées/terreuses**. Contribue fortement aux arômes du *dry hopping* et du houblonnage tardif.",
        "**Humulène**: Sesquiterpène moins volatile. Notes **boisées, terreuses, et épicées**. Caractéristique des houblons nobles (européens).",
        "**Linalool et Géraniol**: Terpènes responsables des notes **florales, de lavande et d'agrumes**. Ils sont des précurseurs clés de la **biotransformation**."
      ]},
      { title: "Méthodes pour l'Arôme Pur", items: [
        "**Houblonnage Tardif (1-15 min)**: Ajout de houblon vers la fin de l'ébullition. Minimise la perte par volatilisation tout en assurant une stérilisation du houblon et une extraction suffisante.",
        "**Flameout (Coupe-feu)**: Ajout immédiatement après l'arrêt de l'ébullition. Maximise l'extraction d'huiles (moins de perte) avec un IBU très faible.",
        "**Whirlpool (70-90°C)**: Technique idéale. La température est suffisante pour une dissolution optimale des huiles essentielles (solubilité augmente), mais **inférieure au seuil d'isomérisation** significatif des acides alpha. Favorise l'extraction des huiles plus solubles comme le Géraniol."
      ]},
      { title: "Principes de Base", items: [
        "Plus l'ajout est **tôt** (60+ min d'ébullition), plus on favorise l'**amertume** (IBU) par isomérisation. Plus l'ajout est **tardif** (Flameout, Dry Hop), plus on favorise l'**arôme** par rétention des huiles volatiles."
      ]}
    ],
    questions: [
      q("Pourquoi le houblonnage tardif favorise-t-il l'arôme?", ["Pour maximiser l'IBU", "Les huiles sont très volatiles et se perdent en ébullition longue", "Pour réduire le pH", "Pour le Hop Creep"], 1, "Les huiles s'évaporent rapidement à haute température."),
      q("Le myrcène est quel type de composé?", ["Acide alpha", "Polyphénol", "Terpène (huile essentielle)", "Sucre"], 2, "C'est le terpène dominant responsable des arômes résineux et épicés."),
      q("De quoi sont composées les huiles essentielles du houblon?", ["Sucres", "Terpènes + sesquiterpènes (volatiles)", "Acides alpha", "Protéines"], 1, "Composés aromatiques volatils."),
      q("Quel est le profil aromatique du myrcène?", ["Floral", "Résine/Pin/Épicé/Terreux (dominant)", "Fruité", "Sucré"], 1, "Terpène majeur avec notes résineuses."),
      q("Quelle est la caractéristique principale des huiles de houblon?", ["Stables au chauffage", "Très volatiles (s'évaporent avec la chaleur)", "Stables au froid", "Invariantes"], 1, "Problème majeur lors de l'ébullition."),
      q("Quel est le profil de l'humulène?", ["Acide", "Boisé/Terreux/Épicé (moins volatile que myrcène)", "Fruité", "Sucré"], 1, "Caractéristique des houblons nobles."),
      q("Le linalool et le géraniol apportent quels arômes?", ["Acides alpha", "Terpènes floraux/lavande/agrumes (biotransformation)", "Enzymes", "Levure"], 1, "Précurseurs d'arômes floraux."),
      q("Qu'est-ce que le flameout en houblonnage?", ["60 min d'ébullition", "Immédiatement après arrêt ébullition (max huiles, min IBU)", "Fermentation", "Après refroidissement"], 1, "Stérilisation + extraction aromatique maximale."),
      q("Quelle est la température optimale pour le whirlpool?", ["100°C", "70-90°C (huiles solubles, sous seuil isomérisation)", "20°C", "Fluctuante"], 1, "Compromis idéal extraction/préservation."),
      q("Quel est l'avantage principal du whirlpool?", ["IBU maximal", "Extraction huiles optimale, IBU faible garanti", "Arôme zéro", "Augmentation du sucre"], 1, "Température parfaite pour arômes."),
      q("Comment le géraniol est-il converti par la levure?", ["Stable", "Levure convertit → citronellol (rose/agrumes)", "Malt hydroxyde", "Eau"], 1, "Biotransformation enzymatique."),
      q("Quel IBU obtient-on avec un ajout à 60 minutes (pas après)?", ["Nul", "Amertume maximale (70-90% isomérisation)", "Arôme seul", "Enzyme"], 1, "Plein rendement d'isomérisation à 60 minutes."),
      q("À quelle température les terpènes volatils se dégradent-ils?", ["50°C", "65-85°C (chauffage trop élevé = perte)", "25°C", "Variable selon pH"], 1, "Température critique de volatilisation."),
      q("Quel est l'effet d'un ajout à 1-15 minutes?", ["Amertume seule", "Minimise volatilisation + stérilise houblon", "IBU zéro", "Sabotage"], 1, "Équilibre entre stérilisation et arôme."),
      q("Comment classe-t-on chimiquement les huiles essentielles?", ["Acides gras", "Terpènes (C10) + sesquiterpènes (C15)", "Acides alpha", "Sucres"], 1, "Classification par nombre de carbones."),
      q("Comment varie le profil aromatique selon le timing d'ajout?", ["Tôt: arôme", "Tôt: IBU, Tardif: arôme", "Tardif: IBU", "Moyen: arôme"], 1, "Inversement proportionnel au timing."),
      q("Que se passe-t-il lors de l'oxydation du myrcène?", ["Stable", "Oxydation rapide au stockage → off-flavour acide valérianique", "Jamais oxyde", "Augmente"], 1, "Vieillissement problématique."),
      q("Qu'est-ce qu'un terpénol?", ["Acide", "Terpène-alcool (aromatique)", "Acide alpha", "Base pH"], 1, "Classe chimique des alcools terpéniques."),
      q("Quelle perte d'arôme après 60 min de chauffage?", ["Zéro%", "30-50% des huiles volatiles", "100%", "10% minimum"], 1, "Évaporation significative."),
      q("Comment varie la solubilité des huiles avec la température?", ["Augmente à 0°C", "Augmente avec chauffage (jusqu'à 85°C optimum)", "Linéaire au refroidissement", "Chaotique"], 1, "Thermodépendance de la solubilité."),
      q("La levure peut-elle produire du linalool?", ["Zéro", "Levure produit à partir de précurseurs du houblon", "Malt seule source", "Eau"], 1, "Biosynthèse fermentaire."),
      q("Comment se forment les esters fruités du houblon?", ["Directement", "Levure estérifie les terpènes → arômes fruités", "Ébullition les crée", "Refroidissement"], 1, "Transformation post-fermentation."),
      q("Quelle quantité de houblon pour houblonnage aromatique intensif?", ["0.5-1 g/L", "2-5 g/L pour arôme marqué", "10+ g/L", "Traces"], 1, "Dosage typique pour profil aromatique."),
      q("Les huiles essentielles contribuent-elles à l'IBU?", ["Oui fortement", "Non, elles apportent uniquement l'arôme", "Partiellement", "Totalement"], 1, "Séparation arôme/amertume."),
      q("Le houblonnage tardif nécessite-t-il plus de houblon?", ["Non", "Oui, pour compenser extraction réduite", "Identique", "Moins"], 1, "Rendement inférieur = dose supérieure."),
      q("Quel terpène est le plus abondant dans le houblon?", ["Linalool", "Myrcène (30-60% des huiles)", "Humulène", "Géraniol"], 1, "Composant majoritaire."),
      q("Les huiles de houblon sont-elles hydrophobes?", ["Non, hydrophiles", "Oui, peu solubles dans l'eau (besoin chaleur/éthanol)", "Totalement solubles", "Insolubles"], 1, "Nature lipophile des terpènes."),
      q("Le dry hopping apporte-t-il de l'IBU?", ["Oui beaucoup", "Non ou très peu (pas d'isomérisation à froid)", "Identique à chaud", "Plus qu'à chaud"], 1, "Température insuffisante pour isomérisation."),
      q("Quel est l'effet de l'éthanol sur les huiles?", ["Aucun", "Augmente la solubilité des huiles essentielles", "Réduit l'extraction", "Détruit les arômes"], 1, "Solvant pour composés lipophiles."),
      q("Les houblons nobles sont caractérisés par quoi?", ["High AA > 12%", "Low AA + profil humulène/terpènes équilibré", "Très fruités", "Amers uniquement"], 1, "Profil aromatique délicat et complexe.")
    ]
  },
  {
    id: "dryHopping",
    category: "HOUBLON",
    title: "13. Dry hopping / Biotransformation",
    ficheRich: [
      { title: "Dry Hopping (Houblonnage à Cru)", items: [
        "**Définition**: Addition de houblon (cônes ou pellets) à une bière **froide** (post-ébullition, généralement en fermentation ou en maturation).",
        "**But**: Extraire les arômes les plus frais et les plus volatils (Terpènes) sans modifier l'amertume. Le contact se fait généralement entre 3 et 7 jours. Une macération trop longue peut entraîner l'extraction de notes herbacées ou d'astringence.",
        "**Saturage**: On utilise des doses élevées de *dry hopping* (> 10 g/L) pour les styles très aromatiques (NEIPA, Double IPA)."
      ]},
      { title: "La Biotransformation (Interaction Levure-Houblon)", items: [
        "**Définition**: Phénomène biochimique où les levures modifient les composés du houblon, créant de **nouveaux arômes** qui n'existaient pas dans la bière ni dans le houblon d'origine. Se produit pendant la fermentation active (3-5 jours).",
        "**Thiols**: La levure (notamment les souches de NEIPA) possède l'enzyme **bêta-lyase** qui libère les **thiols volatils** (composés soufrés) à partir de précurseurs non aromatiques (Thiols liés) dans le moût et le houblon. Les thiols sont responsables des arômes intenses de **fruits de la passion, pamplemousse, et goyave**.",
        "**Conversion des Terpènes**: La levure peut aussi convertir des terpènes comme le Géraniol en Citronellol (arôme de rose/agrumes), ajoutant une couche de complexité aromatique."
      ]},
      { title: "Optimisation du Timing", items: [
        "**Dry Hop Tôt (1-3 jours de fermentation)**: La présence de levure active favorise la **biotransformation**.",
        "**Dry Hop Tardif (Post-fermentation)**: Maximise l'extraction des huiles pures (Myrcène, Humulène) pour un arôme plus 'vert' et classique."
      ]}
    ],
    questions: [
      q("Quand est réalisé le dry hopping?", ["Pendant l'ébullition", "Pendant ou après la fermentation (à froid)", "Avant l'empâtage", "Après le filtrage"], 1, "À froid pour arôme pur, sans amertume."),
      q("La biotransformation nécessite l'action de quoi?", ["La chaleur", "Les acides alpha", "Les levures actives", "Le lactose"], 2, "Les levures sont essentielles à la conversion des composés aromatiques."),
      q("Quelle est la durée typique du dry hopping?", ["1-2 heures", "3-7 jours (extraction arômes frais)", "2-3 semaines", "Instantané"], 1, "Macération froide contrôlée."),
      q("À quelle température se fait le dry hopping?", ["Ébullition", "Fermentation active/post-fermentation froid", "40°C", "Gelé"], 1, "Température de fermentation ou maturation."),
      q("Qu'est-ce que l'enzyme bêta-lyase?", ["Protéase du malt", "Enzyme de levure qui libère les thiols aromatiques", "Amylase du houblon", "Enzyme bactérienne"], 1, "Clé de la biotransformation."),
      q("Que sont les thiols du houblon?", ["Acides alpha", "Molécules soufrées (passion/pamplemousse/goyave)", "Sucres fermentescibles", "Protéines"], 1, "Précurseurs transformés par la levure."),
      q("Quelle levure est riche en bêta-lyase?", ["Levure lager", "Souches NEIPA (biotransformation arômes)", "Levure classique", "Levure sauvage"], 1, "Profil 'juicy' caractéristique."),
      q("Comment le géraniol est-il converti?", ["Stable", "Levure → citronellol (rose/agrumes)", "Oxydation par le malt", "Par l'eau et le pH"], 1, "Isomérisation aromatique enzymatique."),
      q("Quelle dose de dry hop pour une NEIPA?", ["2 g/L", "10+ g/L pour arôme intense", "0.5 g/L", "Traces"], 1, "Saturation aromatique maximale."),
      q("Quelle est la structure chimique d'un thiol?", ["Hydrocarbure", "Composé R-SH (groupe thiol)", "Acide", "Sucre"], 1, "Fonction chimique soufrée."),
      q("Quelle est la fenêtre optimale de biotransformation?", ["Toujours", "Fermentation active 3-5 jours (levure vivante)", "Post-fermentation", "Aucune"], 1, "Activité microbienne nécessaire."),
      q("Comment la levure modifie-t-elle les terpènes?", ["Jamais", "Levure modifie (ex: géraniol → citronellol)", "Ébullition crée", "Spontanément"], 1, "Transformation enzymatique."),
      q("Quelle différence entre dry hop tôt vs tardif?", ["Même arôme", "Tôt: biotransformation, Tard: huiles pures/vert", "Opposé", "Variable"], 1, "Profil sensoriel distinct."),
      q("Qu'est-ce qu'un précurseur de thiol?", ["Libre immédiatement", "Chaîne peptidique attachée (levure libère)", "Sucre", "Malt"], 1, "Biodisponibilité conditionnelle."),
      q("D'où viennent les arômes de passion/goyave?", ["Myrcène", "Thiols libérés par levure (biotransformation)", "Acides alpha", "Esters"], 1, "Signature NEIPA typique."),
      q("Quelle température pour fermentation active?", ["18-20°C", "20-22°C selon souche Ale (biotransformation optimale)", "Gelée", "Chauffée"], 1, "Température optimale de la levure."),
      q("Quel profil avec dry hop post-fermentation?", ["Biotransformation maximale", "Arômes purs sans transformation (minéral/herbal)", "Même profil que tôt", "Croissance IBU"], 1, "Levure inactive = pas de transformation."),
      q("Pellets vs cônes pour dry hop?", ["Identiques", "Pellets > cônes (intégration facile)", "Cônes meilleurs", "Variables"], 1, "Compactage facilite manipulation."),
      q("Comment fonctionne l'extraction à froid?", ["Amertume maximale", "Huiles/thiols sans isomérisation (chimie douce)", "Zéro extraction", "IBU haute"], 1, "Cinétique froide préserve arômes."),
      q("Que se passe-t-il avec une dose excessive de dry hop?", ["Plus = toujours mieux", "Dose excessive = herbacé/astringent (extraction tannins)", "Jamais d'excès", "Impossible"], 1, "Équilibre nécessaire pour éviter off-flavours."),
      q("Quelle capacité enzymatique possèdent certaines levures?", ["Zéro", "Bêta-lyase + estérase (libère arômes)", "Toutes identiques", "Malt seule source"], 1, "Dépend de la souche spécifique."),
      q("Quel matériel pour dry hop en brasserie?", ["Cônes/pellets/extraits tous", "Cônes/pellets (sacs filtrants pour séparation)", "Cônes seuls", "Extraits seuls"], 1, "Pratique de filtration en brasserie."),
      q("Le dry hopping peut-il créer du trouble?", ["Non jamais", "Oui, particules de houblon en suspension", "Seulement avec cônes", "Impossible"], 1, "Nécessite parfois filtration ou sédimentation."),
      q("Les thiols sont-ils présents naturellement dans le houblon?", ["Oui, libres", "Non, sous forme de précurseurs liés (libérés par levure)", "Oui, en grande quantité", "Jamais présents"], 1, "Forme latente activée par enzymes."),
      q("Quelle souche de levure maximise la biotransformation?", ["Lager à basse température", "Ale NEIPA avec haute activité bêta-lyase", "Sauvage Brettanomyces", "Toutes identiques"], 1, "Sélection souche cruciale."),
      q("Le dry hopping affecte-t-il la densité finale?", ["Non", "Peut légèrement réduire (hop creep)", "Augmente toujours", "Impossible"], 1, "Enzymes du houblon peuvent libérer sucres."),
      q("Les arômes de biotransformation sont-ils stables?", ["Totalement stables", "Relativement stables mais s'oxydent avec le temps", "Très instables", "Éternels"], 1, "Sensibles à l'oxydation et au temps."),
      q("Peut-on dry hopper plusieurs fois?", ["Non, une seule fois", "Oui, ajouts successifs pour profils complexes", "Interdit", "Dangereux"], 1, "Technique de layering aromatique."),
      q("Le CO₂ de fermentation aide-t-il le dry hopping?", ["Non", "Oui, circulation naturelle améliore contact", "Nuit à l'extraction", "Neutre"], 1, "Mouvement facilite extraction."),
      q("Quelle est la limite haute de dry hopping avant saturation?", ["5 g/L", "15-20 g/L (au-delà, rendement décroissant)", "Pas de limite", "50 g/L"], 1, "Saturation des récepteurs aromatiques.")
    ]
  },
  {
    id: "hopCreep",
    category: "HOUBLON",
    title: "14. Hop Creep (Refermentation)",
    ficheRich: [
      { title: "Définition du Hop Creep", items: [
        "**Hop Creep**: Une refermentation **imprévue et lente** qui se produit souvent après un *dry hopping* intensif. Il affecte principalement les bières conditionnées (fûts, canettes, bouteilles) qui ne sont pas pasteurisées.",
        "**Cause**: Le houblon (surtout sous forme de pellet) contient des traces d'**enzymes diastasiques** résiduelles (Amylase et Glucoamylase) provenant du cône frais qui n'ont pas été désactivées par l'ébullition (puisqu'ajouté à froid)."
      ]},
      { title: "Mécanisme de Refermentation", items: [
        "**Saccharification à froid**: Les enzymes du houblon sont réintroduites dans la bière et commencent à hydrolyser les **dextrines** (sucres non fermentescibles) résiduelles, les transformant en sucres simples (maltose, glucose).",
        "**Conséquences**: La levure dormante ou résiduelle (même en très faible quantité) consomme ces nouveaux sucres, provoquant une **baisse de la densité finale** et un dégagement non contrôlé de **CO2** (Dioxyde de Carbone), ce qui mène au risque majeur de **surpression, de gushing ou d'explosion** des contenants."
      ]},
      { title: "Prévention", items: [
        "Pour les brasseurs industriels : **Pasteurisation** du produit après le *dry hop* pour désactiver les enzymes du houblon. Pour les brasseurs artisanaux : S'assurer que la bière est **entièrement exempte de levure viable** avant l'embouteillage, ou utiliser des inhibiteurs de levure/enzymes."
      ]}
    ],
    questions: [
      q("Qu'est-ce que le Hop Creep?", ["Excès de sucre de candi", "Refermentation imprévue causée par enzymes diastasiques du houblon", "Trop de protéines", "Un pH trop bas"], 1, "Les amylases du houblon libèrent des sucres fermentescibles."),
      q("Quel est le risque principal du Hop Creep?", ["Le gushing", "Le trouble à froid", "La surpression des bouteilles (explosion)", "L'amertume faible"], 2, "La refermentation crée du CO2 sous pression."),
      q("Quelle est l'action de l'amylase du houblon?", ["Enzyme pectique", "Décompose les dextrines en sucres fermentescibles (maltose/glucose)", "Protéase", "Lipase"], 1, "Saccharification à froid."),
      q("Quel rôle joue la glucoamylase du houblon?", ["Protéine", "Enzyme qui libère du glucose à partir des dextrines", "Bactérie", "Levure"], 1, "Hydrolyse complète des polymères."),
      q("Les dextrines après ébullition sont-elles fermentescibles?", ["Sucres fermentescibles", "Non-fermentescibles (poids moléculaire élevé)", "Levure les consomme", "Instables"], 1, "Architecture maltose-polymère complexe."),
      q("Quelle est la source de la refermentation dans le Hop Creep?", ["Zéro sucre disponible", "Nouveaux sucres libérés par enzymes houblon → levure dormante consomme", "Levure morte", "Bactérie acétique"], 1, "Reprise de fermentation inattendue."),
      q("Que se passe-t-il avec le CO2 lors du gushing?", ["Dégagement lent", "Surpression rapide des bouteilles (risque explosion)", "Zéro gaz", "Négatif"], 1, "Danger lors du stockage."),
      q("Comment évolue la densité finale avec le Hop Creep?", ["Inchangée", "Baisse de la densité finale (sucres consommés)", "Augmente", "Nulle"], 1, "Disparition des sucres par fermentation."),
      q("Qu'est-ce que la levure dormante?", ["Morte", "Vivante mais inactive (température basse) → réactivée par sucres", "Hyperactive", "Mutante"], 1, "Viabilité latente."),
      q("D'où viennent les enzymes diastasiques du houblon?", ["Production nouvelle", "Résidus de la plante (pellets non bouillis)", "Synthèse par levure", "Destruction"], 1, "Survivance enzymatique."),
      q("Pellets vs cônes : lequel présente plus de risque de Hop Creep?", ["Cônes plus risque", "Pellets plus risque (broyage expose enzymes)", "Identique", "Cônes seule cause"], 1, "Surface de contact augmentée."),
      q("La pasteurisation est-elle une solution au Hop Creep?", ["Zéro effet", "Oui, désactive enzymes du houblon et tue levure", "Aggrave le creep", "Stimule fermentation"], 1, "Traitement thermique préventif."),
      q("Qu'est-ce qu'un inhibiteur enzymatique?", ["Sucre supplémentaire", "Bloque l'amylase/glucoamylase (prévient saccharification)", "Booste levure", "pH-dépendant"], 1, "Chimie de contrôle."),
      q("Quand se manifeste le Hop Creep?", ["Immédiatement après ébullition", "Jours/semaines post-embouteillage (enzymes + levure lente)", "Avant brassage", "Pendant fermentation primaire"], 1, "Cinétique lente et différée."),
      q("Comment détecter la levure viable?", ["Couleur", "Densité cellulaire/viabilité test biochimique", "Odeur", "pH simple"], 1, "Microscopie et culture."),
      q("À quelle température la levure devient-elle dormante?", ["10°C très actif", "0–4°C ralentit métabolisme (lager storage)", "30°C idéal", "Chauffée"], 1, "Physiologie de conservation."),
      q("Combien de temps prend la saccharification des dextrines?", ["Minutes", "Heures/jours (cinétique enzymatique lente)", "Instantanée", "Jamais"], 1, "Réaction biochimique progressive."),
      q("Quelle précaution lors de l'embouteillage?", ["Aucune précaution", "Assurer levure morte (pasteurisation/centrifugation) avant embouteillage", "Levure obligatoire", "Enzymes aidantes"], 1, "Prévention du gushing."),
      q("Qu'est-ce que l'acide valérianique?", ["Arôme agréable", "Off-flavour d'oxydation (fromage, chaussettes)", "Sucre", "Levure"], 1, "Décomposition aromatique."),
      q("Le Hop Creep est-il plus fréquent en dry hopping à froid ou à chaud?", ["Chaud seulement", "Dry hopping à froid (enzymes + levure acclimatée au froid)", "DH épargné", "Inverse"], 1, "Levure basse température."),
      q("Pourquoi les pellets favorisent-ils le Hop Creep?", ["Moins d'enzymes", "Broyage libère et expose enzymes (surface augmentée)", "Protège enzymes", "Aucune différence"], 1, "Structure cellulaire rompue."),
      q("La centrifugation peut-elle prévenir le Hop Creep?", ["Non", "Oui, élimine levure résiduelle (prévient refermentation)", "Aggrave", "Sans effet"], 1, "Séparation physique de la levure."),
      q("Les enzymes du houblon sont-elles thermostables?", ["Totalement", "Non, détruites par ébullition (raison de l'ajout à chaud)", "Partiellement", "Augmentent avec chaleur"], 1, "Dénaturation thermique."),
      q("Le Hop Creep affecte-t-il le taux d'alcool?", ["Non", "Oui, légèrement augmenté (nouveaux sucres fermentés)", "Diminue", "Aucun lien"], 1, "Fermentation supplémentaire = éthanol."),
      q("Les bières pasteurisées risquent-elles le Hop Creep?", ["Oui fortement", "Non, enzymes et levure désactivées", "Partiellement", "Toujours"], 1, "Stabilité microbiologique."),
      q("Peut-on mesurer le Hop Creep?", ["Impossible", "Oui, suivi de la densité finale et pression CO2", "Uniquement visuellement", "Par le goût seulement"], 1, "Monitoring analytique."),
      q("Le dry hopping intensif (>10 g/L) augmente-t-il le risque?", ["Non", "Oui, plus d'enzymes introduites (dose proportionnelle)", "Diminue risque", "Sans corrélation"], 1, "Relation dose-effet."),
      q("Les NEIPA sont-elles particulièrement sensibles au Hop Creep?", ["Non", "Oui, dry hopping massif + embouteillage non pasteurisé", "Moins sensibles", "Immunisées"], 1, "Pratiques à risque combinées."),
      q("L'ajout d'azote lors de l'embouteillage prévient-il le Hop Creep?", ["Totalement", "Non, ne désactive pas enzymes (seulement réduit oxydation)", "Oui partiellement", "Aggrave"], 1, "Atmosphère inerte ≠ inactivation enzymatique."),
      q("Quelle est la température optimale de l'amylase du houblon?", ["0°C", "Température de fermentation (18-22°C) favorise activité", "60°C", "100°C"], 1, "Optimum enzymatique à température ambiante.")
    ]
  },
  {
    id: "stockageHoublon",
    category: "HOUBLON",
    title: "15. Stockage du houblon (HSI)",
    ficheRich: [
      { title: "Facteurs de Dégradation (Oxydation)", items: [
        "Le houblon est chimiquement très instable. Les facteurs de dégradation principaux sont l'**oxygène** (O2), la **chaleur** et la **lumière**.",
        "**Perte d'Amertume**: L'oxydation des acides alpha les transforme en composés moins amers ou amers avec un profil désagréable. Une perte de 30-50 % d'acides alpha peut se produire en un an à température ambiante.",
        "**Création d'Off-Flavours**: L'oxydation du Myrcène et des acides bêta produit de l'**acide isovalérique**, responsable d'un arôme d'**acidité butyrique, de fromage rance ou de chaussettes** (off-flavour majeur)."
      ]},
      { title: "Méthodes de Stockage Optimal", items: [
        "**Température**: Stockage au **congélateur (idéalement -20°C)** pour ralentir au maximum les réactions chimiques d'oxydation.",
        "**Oxygène**: Conditionnement sous **vide** ou purge à l'**Azote** pour éliminer l'oxygène résiduel (dans des sacs multicouches/métallisés).",
        "**Lumière**: Protéger absolument de la lumière (UV et visible), qui catalyse des réactions de dégradation (notamment la création de l'off-flavour 'Skunky' ou 'mouffette')."
      ]},
      { title: "HSI (Hop Storage Index)", items: [
        "**Indice HSI**: Un indicateur spectrophotométrique utilisé pour évaluer la qualité et la fraîcheur. Il mesure le ratio des produits d'oxydation sur les acides alpha/bêta restants.",
        "**Interprétation**: Un **HSI élevé** indique que le houblon est **âgé ou mal conservé**. Les brasseurs utilisent le HSI pour ajuster les taux d'ajout ou déterminer la durée de vie commerciale du houblon."
      ]}
    ],
    questions: [
      q("Comment doit se faire le stockage du houblon?", ["Au chaud et à l'air libre", "Au frais et sous vide", "À la lumière ambiante", "À pH neutre"], 1, "Froid, vide et obscurité sont essentiels."),
      q("Que mesure l'indice HSI?", ["La teneur en huile", "Le taux d'humidité", "La dégradation du houblon par oxydation", "L'isomérisation"], 2, "C'est un indicateur de la perte de qualité."),
      q("Que se passe-t-il lors de l'oxydation des acides alpha?", ["Stabilité", "Perte d'amertume (transformation en composés moins amers/désagréables)", "Augmentation IBU", "Protéine réaction"], 1, "Dégradation chimique."),
      q("Quel est l'arôme de l'acide isovalérique?", ["Fruité", "Fromage rance/chaussettes (putride)", "Sucré", "Vanille"], 1, "Signature off-flavour de la bière oxydée."),
      q("Quelle perte d'acides alpha en un an à température ambiante?", ["5%", "30–50% (oxydation)", "<1%", "100%"], 1, "Instabilité du houblon."),
      q("Que produit l'oxydation du myrcène?", ["Stable", "Acide valérianique (off-flavour putride)", "Augmente arôme", "Production de sucre"], 1, "Dégradation du terpène."),
      q("Quelle est la température idéale de stockage du houblon?", ["–5°C", "–20°C (ralentit réactions chimiques)", "0°C", "20°C"], 1, "Cinétique exponentielle avec température."),
      q("Pourquoi utiliser le vide pour stocker le houblon?", ["Vide expose O2", "Vide élimine O2 → bloque catalyseur d'oxydation", "Air meilleur", "Inchangé"], 1, "Chimie oxydoréductive."),
      q("À quoi sert la purge à l'azote?", ["Alimentation levure", "Remplace O2 par N2 inerte (prévention oxydation)", "Tue arômes", "Acidifie"], 1, "Atmosphère inerte protectrice."),
      q("Quel effet a la lumière UV sur le houblon?", ["Bénéfique", "Catalyse réactions de dégradation (off-flavour skunky)", "Neutre", "Améliore arômes"], 1, "Photochimie destructive."),
      q("Pourquoi utiliser des sacs métallisés?", ["Papier kraft", "Barrière contre lumière + O2 (protection multicouche)", "Plastique clair", "Tissus"], 1, "Emballage protecteur."),
      q("Comment se calcule le HSI?", ["Simple: couleur", "Ratio absorbance produits oxydation/acides restants (spectrophotométrie)", "Poids", "Temps"], 1, "Mesure chimique analytique."),
      q("Un HSI élevé signifie quoi?", ["Fraîcheur", "Houblon âgé/mal conservé (qualité diminuée)", "Jeunesse", "Excellent stock"], 1, "Indicateur inverse de qualité."),
      q("Comment varie la dégradation avec la température?", ["Linéaire", "Exponentielle (doublement temps → perte doublée)", "Nulle", "Négative"], 1, "Loi d'Arrhenius cinétique."),
      q("Pourquoi la date de récolte est-elle critique?", ["Ignorable", "Essentielle pour HSI/qualité (fraîcheur optimale)", "Pas relevante", "Oubliable"], 1, "Traçabilité en brasserie."),
      q("Quelle est la durée de conservation optimale du houblon?", ["Température ambiante", "Congélateur + vide + obscurité (12 mois+ viable)", "Frais simple", "Lumière aide"], 1, "Protocole professionnel."),
      q("Que produit l'oxydation des acides bêta?", ["Jamais", "Amertume dure/végétale (sensation vieille)", "Améliore", "Zéro impact"], 1, "Vieillissement du houblon."),
      q("Pourquoi contrôler l'humidité lors du stockage?", ["Pas d'importance", "Contrôle bas (prévient dégradation enzymatique/moisissure)", "Maximale", "Élevée préférable"], 1, "Mécanismes biologiques."),
      q("Le houblon compressé en sacs conserve-t-il mieux?", ["Détérioration rapide", "Oui, moins de surface O2 (meilleure conservation)", "Plus d'oxydation", "Inchangé"], 1, "Optimisation empaquetage."),
      q("Un HSI > 50% indique quoi?", ["Neuf", "Vieux (plus de 6 mois ou mal stocké)", "Medium", "Parfait usage"], 1, "Seuil de qualité."),
      q("Les acides alpha oxydés ont-ils le même pouvoir d'amertume?", ["Identique", "Non, amertume réduite et profil désagréable", "Augmentée", "Aucune amertume"], 1, "Modification chimique."),
      q("Peut-on régénérer un houblon oxydé?", ["Facilement", "Non, oxydation irréversible", "Avec chauffage", "Sous vide"], 1, "Réaction chimique permanente."),
      q("Les houblons nobles se dégradent-ils plus vite?", ["Non", "Oui, faibles en AA = plus sensibles oxydation", "Moins vite", "Identique"], 1, "Vulnérabilité chimique."),
      q("Le stockage sous azote est-il suffisant sans froid?", ["Totalement", "Non, température contrôle cinétique (azote + froid nécessaire)", "Oui", "Meilleur"], 1, "Combinaison de facteurs."),
      q("Quelle est la durée de vie du houblon à température ambiante?", ["2 ans", "Quelques mois (dégradation rapide)", "5 ans", "Indéfinie"], 1, "Stabilité limitée."),
      q("Les pellets se dégradent-ils plus vite que les cônes?", ["Non", "Oui, surface exposée augmentée (broyage)", "Identique", "Moins vite"], 1, "Structure cellulaire rompue."),
      q("L'off-flavour 'skunky' est causé par quoi?", ["Oxydation seule", "Dégradation photochimique (lumière + houblon)", "Fermentation", "Levure"], 1, "Lightstruck beer."),
      q("Un houblon avec HSI bas est-il préférable?", ["Non", "Oui, indique fraîcheur et qualité préservée", "Identique", "Pire"], 1, "Indicateur de qualité supérieure."),
      q("Les extraits de houblon sont-ils plus stables?", ["Non", "Oui, processus stabilise et réduit oxydation", "Identique", "Moins stables"], 1, "Avantage technologique."),
      q("Quel gaz est utilisé pour la purge des emballages?", ["Oxygène", "Azote (inerte)", "CO2", "Hydrogène"], 1, "Atmosphère protectrice standard.")
    ]
  },
  {
    id: "bugu",
    category: "HOUBLON",
    title: "16. BU:GU et perception",
    ficheRich: [
      { title: "Le Concept du Ratio d'Équilibre", items: [
        "**BU:GU (Bitterness Unit to Gravity Unit)**: Ce ratio est une tentative de quantifier l'**équilibre perçu** entre l'amertume et la douceur de la bière. Il compare l'amertume (IBU) à la densité initiale (DI).",
        "**Calcul**: **BU:GU = IBU / (Densité Initiale en unités de gravité)**. (Ex: DI 1.050 donne 50 Unités de Gravité. Si IBU = 50, BU:GU = 50/50 = 1,0).",
        "**Rôle**: Permet de comparer la 'puissance' d'amertume de bières ayant des densités initiales très différentes. 50 IBU dans une Lager (BU:GU ≈ 1,0) sera perçu comme très amer, alors que 50 IBU dans une Barley Wine (BU:GU ≈ 0,5) sera équilibré."
      ]},
      { title: "Interprétation du BU:GU", items: [
        "**BU:GU < 0,5**: Dominance Maltée/Sucrée. Le corps et la douceur masquent une grande partie de l'amertume (Ex: Stout, Bock, Malt-forward Ales).",
        "**BU:GU 0,5 - 0,8**: Équilibre. L'amertume est présente, mais bien contrebalancée par la douceur résiduelle (Ex: Pale Ale, Lager Classique).",
        "**BU:GU > 0,8**: Dominance Houblonnée/Amère. La bière est sèche, et l'amertume est très affirmée (Ex: IPA, Double IPA). Certaines NEIPA peuvent avoir un BU:GU élevé, mais l'amertume *perçue* est adoucie par le corps et la turbidité."
      ]},
      { title: "Perception Subjective", items: [
        "Le BU:GU est une bonne approximation, mais il ne tient pas compte de la **Densité Finale (DF)** (qui détermine la douceur résiduelle) ni des **polyphénols** (qui ajoutent de l'amertume non IBU) ou des **saveurs fruitées** (qui peuvent masquer l'amertume)."
      ]}
    ],
    questions: [
      q("Un BU:GU de 0.2 indique une bière plutôt…", ["Amère/Sèche", "Équilibrée", "Maltée/Sucrée", "Alcoolisée"], 2, "Le côté malté domine l'amertume."),
      q("Le IBU est divisé par quelle valeur dans le calcul du BU:GU?", ["La densité finale", "L'EBC", "L'OG - 1000 (Unités de Gravité)", "Le Kolbach"], 2, "Les Unités de Gravité sont la partie décimale de la DI."),
      q("Quelle est la formule du BU:GU?", ["Densité/IBU", "IBU / (OG–1000) = IBU / Unités Gravité", "IBU × OG", "Temps ébullition"], 1, "Ratio d'équilibre amertume/douceur."),
      q("Un BU:GU < 0.5 caractérise quel style?", ["IPA", "Stout/Bock/Porter maltée (douceur masque amertume)", "Pilsen", "Lager amère"], 1, "Dominance maltée prononcée."),
      q("Un BU:GU de 0.5–0.8 indique quoi?", ["Très sec", "Équilibre classique (Pale Ale, Lager)", "Fruité", "Excessif"], 1, "Harmonie amertume-douceur."),
      q("Un BU:GU > 0.8 est typique de quel style?", ["Doux", "IPA/Double IPA sèche (amertume forte)", "Bock", "Trappiste"], 1, "Houblonnée affirmée."),
      q("Quelle est la limitation principale du BU:GU?", ["Aucune", "Oublie densité finale (DF) + polyphénols + arômes masquants", "Trop précis", "Parfait"], 1, "Perception plus complexe que le calcul."),
      q("Quel rôle joue la densité finale?", ["Sucre malaise", "Sucres résiduels → douceur contrebalance amertume", "IBU production", "Levure santé"], 1, "Équilibre sensoriel."),
      q("Les polyphénols contribuent-ils à l'amertume?", ["Zéro", "Oui, amertume non-IBU (tannins astringents)", "IBU seulement", "Sucre"], 1, "Sources multiples d'amertume."),
      q("Comment les saveurs fruitées affectent-elles la perception?", ["Acides alpha", "Masquent l'amertume perçue (complexité aromatique)", "Augmentent IBU", "Élevées"], 1, "Interaction psychosensorielle."),
      q("Pourquoi les NEIPA ont-elles un BU:GU paradoxal?", ["Bas <0.3", "BU:GU élevé >0.8 mais amertume perçue basse (turbidité + fruits masquent)", "Zéro", "Moyen"], 1, "Paradoxe sensoriel caractéristique."),
      q("La perception de l'amertume est-elle identique pour tous?", ["Oui, absolue", "Non, variable génétique (sensibilité PROP gustation)", "Universelle", "Constante"], 1, "Biologie individuelle."),
      q("Comment la densité haute du moût affecte-t-elle l'isomérisation?", ["Augmente rendement", "Réduit rendement isomérisation (solubilité diminue)", "Identique", "Inversion"], 1, "Chimie physique."),
      q("Un BU:GU de 1.0 signifie quoi?", ["Malté dominant", "Équilibre parfait 50/50 amertume-douceur", "Sec total", "Fruité"], 1, "Point pivot théorique."),
      q("Quel est le BU:GU typique d'une Pale Ale?", ["0.2", "0.6–0.8 (équilibre référence)", "1.2", "0.1"], 1, "Style classique équilibré."),
      q("Pourquoi une Stout Guinness semble-t-elle maltée malgré des IBU élevés?", ["Très amère", "Densité haute compense (BU:GU bas malgré IBU)", "IPA clone", "Sèche"], 1, "Densité initiale élevée masque amertume."),
      q("Quelle différence entre astringence et amertume?", ["Identiques", "Astringence = polyphénols (sécheresse), Amertume = gustation", "Inverse", "Aucune"], 1, "Mécanismes chimiosensoriels distincts."),
      q("Les produits de fermentation modifient-ils la perception?", ["Neutres", "Oui, esters/alcool/phénols modulent perception globale", "Zéro impact", "Négligeables"], 1, "Interaction sensorielle complexe."),
      q("Le BU:GU est-il une mesure objective?", ["Totalement", "Non, approximation (BU:GU calcul vs perception subjective)", "Identique à IBU", "Inverse"], 1, "Théorie vs réalité sensorielle."),
      q("Quel est le BU:GU typique d'une American IPA?", ["0.5", "0.9–1.2+ (très houblonnée sèche)", "0.2", "0.7"], 1, "Signature style moderne."),
      q("Comment le CO2 affecte-t-il la perception de l'amertume?", ["Aucun effet", "Augmente perception amertume (acidité carbonique)", "Réduit amertume", "Neutre"], 1, "Interaction avec récepteurs gustatifs."),
      q("La température de service influence-t-elle le BU:GU perçu?", ["Non", "Oui, froid atténue amertume perçue (récepteurs moins sensibles)", "Inverse", "Identique"], 1, "Physiologie thermosensible."),
      q("Un BU:GU de 1.5 est-il possible?", ["Non", "Oui, bières très sèches et amères (Imperial IPA)", "Impossible", "Maximum 1.0"], 1, "Valeurs extrêmes réalisables."),
      q("Le corps de la bière affecte-t-il la perception de l'amertume?", ["Non", "Oui, corps plein adoucit amertume perçue", "Inverse", "Aucun lien"], 1, "Texture influence gustation."),
      q("Les acides du malt contribuent-ils au BU:GU?", ["Non calculés", "Oui indirectement (pH influence perception amertume)", "Directement", "Jamais"], 1, "Facteur pH sur chimioréception."),
      q("Pourquoi une Barley Wine supporte-t-elle 80+ IBU?", ["Ne supporte pas", "Densité très haute (BU:GU ~0.5) équilibre sucrosité", "Trop amère", "Impossible"], 1, "Proportion critique douceur/amertume."),
      q("Le BU:GU prédit-il exactement la perception?", ["Parfaitement", "Non, guide approximatif (multiples facteurs sensoriels)", "Toujours exact", "Inutile"], 1, "Outil d'estimation, non absolu."),
      q("Une Session IPA a généralement quel BU:GU?", ["<0.5", "0.8–1.0 (amertume marquée, faible alcool)", ">1.5", "0.3"], 1, "Caractère houblonné malgré faible alcool."),
      q("Les sulfates influencent-ils la perception de l'amertume?", ["Non", "Oui, sulfates accentuent amertume perçue", "Réduisent", "Neutres"], 1, "Chimie de l'eau critique."),
      q("Le BU:GU est-il utilisé pour formuler des recettes?", ["Jamais", "Oui, outil de formulation pour équilibre ciblé", "Obsolète", "Uniquement laboratoire"], 1, "Application pratique brasserie.")
    ]
  },
  {
    id: "choixHoublons",
    category: "HOUBLON",
    title: "17. Choix des houblons et tips",
    ficheRich: [
      { title: "Classification Fonctionnelle et Profils", items: [
        "**Houblons Amérisants (High Alpha)**: Acides alpha élevés (10-17 %). Faible teneur en huiles volatiles spécifiques. Choisi pour maximiser le rendement IBU à 60+ min (Ex: **Magnum, Target, Warrior**).",
        "**Houblons Aromatiques (Low Alpha)**: Acides alpha faibles (3-7 %). Riches en huiles essentielles fines et spécifiques (Humulène, Linalool). Utilisé en houblonnage tardif ou à cru (Ex: **Saaz, Tettnanger, Fuggles**).",
        "**Houblons Dual-Purpose**: Bon équilibre entre acides alpha (7-10 %) et huiles. Polyvalents pour l'amertume et l'arôme (Ex: **Cascade, Centennial, Simcoe**)."
      ]},
      { title: "Familles Aromatiques (Terroir)", items: [
        "**Nobles (Européens)**: Profils élégants, épicés, floraux et terreux. Faible Myrcène. Utilisés pour les Lagers et Pils traditionnelles (Ex: Hallertau Mittelfrüh, Saaz, Tettnanger).",
        "**Américains (C-Hops)**: Riches en Myrcène. Profils intenses d'agrumes, de pamplemousse, de pin et de résine (Ex: Cascade, Centennial, Chinook).",
        "**Nouveau Monde (Océanie/Afrique)**: Profils très modernes, 'juicy', fruités, tropicaux (thiols) ou 'vin blanc' (Ex: Nelson Sauvin, Galaxy, Citra, Mosaic)."
      ]},
      { title: "Tips du Brasseur", items: [
        "**Ratio AA/Huiles**: Pour les bières amères, on choisit des houblons avec un faible ratio Huiles/AA (moins de perte aromatique à l'ébullition). Pour l'arôme, on choisit un ratio élevé.",
        "**SMASH**: Technique **S**ingle **M**alt **A**nd **S**ingle **H**op. Utilisée comme outil d'apprentissage pour isoler et comprendre le profil organoleptique précis d'une variété de malt et de houblon.",
        "**Fraîcheur**: Toujours vérifier la date de récolte et le HSI du houblon pour garantir un arôme optimal."
      ]}
    ],
    questions: [
      q("Un houblon amérisant a un taux d'acide alpha…", ["< 5%", "~ 8%", "~ 1% (faible)", "Environ > 10% (élevé)"], 3, "Les houblons amérisants sont choisis pour leur efficacité en IBU."),
      q("Une recette SMASH utilise…", ["Deux malts, un houblon", "Un malt, un houblon", "Un malt, deux houblons", "Quatre malts"], 1, "SMASH = Single Malt And Single Hop."),
      q("Les houblons nobles européens se caractérisent par…", ["AA élevé", "Faible AA + arôme fin épicé/floral (Hallertau, Saaz, Tettnanger)", "Nouveau Monde", "Américain"], 1, "Tradition et finesse aromatique."),
      q("Quel est le rendement des houblons à haute teneur en alpha-acides?", ["Low Alpha: 90%+", "High Alpha: rendement maximal en ébullition longue (isomérisation)", "Aromatiques meilleurs", "Identique"], 1, "Chimie de l'isomérisation optimisée."),
      q("Cascade est quel type de houblon?", ["Pur Américain", "Dual-Purpose (7–9% AA, agrumes équilibré)", "Noble Européen", "High Alpha"], 1, "Polyvalence caractéristique."),
      q("Quelle différence entre Centennial et Cascade?", ["Identiques", "Centennial plus AA élevé (10%) vs Cascade (7%)", "Opposés en AA", "Même ratio"], 1, "Intensité comparable, puissance différente."),
      q("Simcoe est quel type de houblon?", ["Bas AA", "Dual-purpose (11% AA, pin/épice/fruit)", "Aromatique pur", "Noble"], 1, "Moderne et versatile."),
      q("Quel pourcentage du total des huiles représente le myrcène?", ["< 5%", "30–60% des huiles totales (dominant chez Américains)", "Traces", "100%"], 1, "Composant majoritaire des C-Hops."),
      q("Nelson Sauvin provient de quel terroir?", ["Classique Europe", "Nouveau Monde Nouvelle-Zélande (arômes 'Sauvignon Blanc' fruité)", "Allemand", "Américain"], 1, "Signature terroir unique."),
      q("Galaxy est quel type de houblon?", ["Bas AA", "Aromatique australien intensément fruité (passion/mangue)", "Dual", "High"], 1, "Profil tropical exotique."),
      q("Citra se caractérise par…", ["Alpha élevé", "Aromatique Américain (agrumes intenses linalool/géraniol)", "Dual noble", "Bêta acides"], 1, "Famille C-Hops moderne."),
      q("Mosaic est quel type de houblon?", ["Bas", "Dual-purpose moderne (floral/fruité tropicaux)", "Ancien", "Classique"], 1, "Innovation récente populaire."),
      q("Comment varie le ratio AA/Huiles?", ["Fixe toujours", "High AA = faibles huiles (priorité efficacité IBU)", "Inverse", "Indépendant"], 1, "Relation inverse proportionnelle."),
      q("Qu'est-ce que la technique SMASH?", ["Marque de bière", "Outil pédagogique: isoler profil malt + houblon unique", "Style officiel", "Brasserie commerciale"], 1, "Méthode d'apprentissage par isolation."),
      q("Quels houblons pour une Pilsner noble?", ["Américains", "Hallertau/Saaz/Tettnanger (équilibre fin et finesse)", "IPA hops", "Barley wine"], 1, "Affinité style-terroir."),
      q("Quelle est la stratégie Bittering vs Aroma?", ["Même fonction", "Bittering: AA max rendement, Aroma: faible AA conservation huiles", "Utilisation identique", "Inversé"], 1, "Optimisation selon timing."),
      q("Hallertau Mittelfrüh est…", ["High AA", "Houblon noble allemand (épicé floral équilibré)", "Nouvelle-Zélande", "Américain"], 1, "Référence classique européenne."),
      q("Saaz se caractérise par…", ["Très amer", "Houblon noble tchèque fine florale subtile (référence Pils)", "Intensément fruité", "IPA hop"], 1, "Élégance et délicatesse."),
      q("Tettnanger provient de…", ["Bas AA", "Houblon noble allemand arôme herbal épicé délicat (Bavière)", "Haut AA", "Nouveau Monde"], 1, "Valeur traditionnelle bavaroise."),
      q("Qu'est-ce que la famille C-Hops?", ["Classiques", "Houblons modernes Américains: Centennial, Cascade, Chinook (résineux citrus)", "Nobles", "Néo-Zélandais"], 1, "Génération américaine caractéristique."),
      q("Comment garantir la fraîcheur maximale du houblon?", ["Âge avancé acceptable", "Date récolte récente + HSI bas (conservation optimale)", "HSI élevé", "Peu importe"], 1, "Traçabilité et qualité brasseur."),
      q("Quel houblon pour maximiser l'IBU avec peu de matière?", ["Aromatiques", "High Alpha (Magnum, Warrior, Target)", "Nobles", "Tous égaux"], 1, "Efficacité économique et technique."),
      q("Les houblons du Nouveau Monde sont caractérisés par…", ["Subtilité", "Profils intenses tropicaux/fruités (thiols, notes juicy)", "Amertume pure", "Faible arôme"], 1, "Innovation aromatique moderne."),
      q("Pourquoi utiliser un houblon dual-purpose?", ["Moins cher seulement", "Polyvalence: amertume + arôme avec une seule variété", "Moins efficace", "Obsolète"], 1, "Simplification et économie."),
      q("Chinook se caractérise par…", ["Doux floral", "C-Hop américain (pin/résine/pamplemousse, 12-14% AA)", "Noble", "Faible AA"], 1, "Profil résineux affirmé."),
      q("Les houblons aromatiques ont généralement…", ["> 12% AA", "3-7% AA + huiles essentielles riches", "0% AA", "15% AA"], 1, "Optimisés pour profil aromatique."),
      q("Fuggles est quel type de houblon?", ["Américain", "Aromatique anglais traditionnel (terreux/boisé)", "High Alpha", "Nouveau Monde"], 1, "Héritage britannique classique."),
      q("Quelle famille pour une NEIPA moderne?", ["Nobles européens", "Nouveau Monde + C-Hops (Citra, Mosaic, Galaxy)", "Amérisants purs", "Allemands"], 1, "Profils fruités tropicaux recherchés."),
      q("Magnum est utilisé pour…", ["Arôme uniquement", "Amertume pure (15-17% AA, profil neutre)", "Houblonnage tardif", "Dry hopping"], 1, "Efficacité maximale IBU sans profil aromatique marqué."),
      q("Les houblons néo-zélandais sont réputés pour…", ["Amertume dure", "Profils uniques 'vin blanc'/tropicaux (Nelson, Motueka)", "Subtilité", "Tradition"], 1, "Innovation terroir distinctif.")
    ]
  },
  {
    id: "epices",
    category: "ÉPICES",
    title: "18. Les Épices en brassage",
    ficheRich: [
      { title: "Épices Courantes et Profils", items: [
        "**Coriandre (graines)**: Profil citronné, épicé, légèrement poivré. Utilisée dans les Witbier belges. Dosage typique: 10-20 g/hL, ajout à 5-10 min d'ébullition ou flameout.",
        "**Écorce d'orange (Curaçao)**: Notes d'agrumes, amertume légère. Complémente la coriandre dans les Witbier. Dosage: 5-15 g/hL, ajout tardif (5-10 min).",
        "**Gingembre frais**: Piquant, chaleureux, citronné. Utilisé dans les bières d'hiver et Ginger Beer. Dosage: 20-50 g/hL, ajout flameout ou fermentation.",
        "**Cannelle (bâtons)**: Chaude, sucrée, épicée. Pour bières de Noël, Pumpkin Ale. Dosage: 5-10 g/hL, ajout fin d'ébullition ou maturation.",
        "**Clou de girofle**: Très puissant, médicinal à haute dose. Notes chaudes, épicées. Dosage: 1-3 g/hL, ajout avec parcimonie.",
        "**Cardamome**: Complexe, citronné, mentholé, épicé. Dosage: 3-8 g/hL, ajout flameout.",
        "**Poivre (noir, rose)**: Épicé, piquant. Dosage: 5-15 g/hL, ajout tardif pour préserver arômes volatils.",
        "**Vanille (gousses)**: Notes sucrées, vanillées, crémeuses. Dosage: **2-4 gousses par hectolitre**. Ajout en macération froide (fermentation secondaire) pendant 1-2 semaines pour extraction optimale des arômes complexes sans apporter d'astringence."
      ]},
      { title: "Timing et Extraction", items: [
        "**Ébullition longue (30-60 min)**: Extraction maximale mais perte d'arômes volatils. Réservé aux épices dont on veut l'amertume/profondeur (cannelle, gingembre sec).",
        "**Flameout/Whirlpool (0-10 min)**: Compromis idéal. Extraction des composés aromatiques sans trop de volatilisation (coriandre, orange, cardamome).",
        "**Fermentation/Maturation**: Macération à froid pour épices très volatiles ou délicates. Permet extraction douce sans cuisson (vanille, cannelle en bâton, gingembre frais).",
        "**Teinture alcoolique**: Macération d'épices dans alcool neutre (vodka), puis ajout contrôlé à l'embouteillage. Permet dosage précis et évite contamination."
      ]},
      { title: "Considérations Techniques", items: [
        "**Forme de l'épice**: Entière (lente extraction, profil subtil) vs Moulue (extraction rapide, intense, risque de sur-épicage).",
        "**Huiles essentielles**: Très volatiles. Sensibles à la chaleur et à l'oxydation. Préférer ajouts tardifs.",
        "**Équilibre**: Les épices peuvent dominer facilement. Toujours commencer avec dosages conservateurs et ajuster progressivement.",
        "**Interaction levure**: Certaines épices (clou de girofle, cannelle haute dose) peuvent inhiber la levure ou créer stress fermentaire."
      ]}
    ],
    questions: [
      q("Quelle épice est caractéristique de la Witbier belge?", ["Cannelle", "Coriandre + écorce d'orange", "Vanille", "Gingembre"], 1, "Duo classique des bières blanches belges."),
      q("Quel est le dosage typique de coriandre?", ["1-2 g/hL", "10-20 g/hL (arôme marqué)", "100 g/hL", "Traces"], 1, "Dose pour profil aromatique caractéristique."),
      q("Quand ajouter la coriandre?", ["60 min d'ébullition", "5-10 min fin ébullition ou flameout (préserve arômes)", "Empâtage", "Embouteillage"], 1, "Timing optimal extraction/préservation."),
      q("L'écorce d'orange apporte quel profil?", ["Floral sucré", "Agrumes + légère amertume", "Épicé piquant", "Terreux"], 1, "Caractère citrique typique."),
      q("Le gingembre frais est ajouté quand?", ["Empâtage", "Flameout ou fermentation (préserve piquant)", "60 min ébullition", "Jamais"], 1, "Composés volatils sensibles chaleur."),
      q("Pourquoi le clou de girofle doit être dosé avec parcimonie?", ["Pas puissant", "Très puissant, médicinal à haute dose (1-3 g/hL max)", "Neutre", "Inefficace"], 1, "Intensité aromatique extrême."),
      q("La cannelle en bâton vs moulue?", ["Identiques", "Bâton = extraction lente/subtile, Moulue = rapide/intense", "Inverse", "Bâton inefficace"], 1, "Cinétique d'extraction différente."),
      q("Quel dosage pour la cannelle?", ["50 g/hL", "5-10 g/hL (chaleur épicée)", "100+ g/hL", "1 g/hL"], 1, "Dose équilibrée pour profil hivernal."),
      q("La cardamome apporte quel profil?", ["Uniquement sucré", "Complexe: citronné/mentholé/épicé", "Amer fort", "Neutre"], 1, "Complexité aromatique multicouche."),
      q("L'ajout d'épices en ébullition longue cause quoi?", ["Optimal", "Perte arômes volatils (extraction composés lourds)", "Plus d'arôme", "Neutre"], 1, "Volatilisation thermique."),
      q("Qu'est-ce qu'une teinture d'épices?", ["Infusion eau", "Macération dans alcool neutre puis dosage contrôlé", "Poudre sèche", "Ébullition"], 1, "Technique de dosage précis."),
      q("Avantage d'une teinture alcoolique?", ["Moins efficace", "Dosage précis + évite contamination (ajout post-fermentation)", "Plus lente", "Interdit"], 1, "Contrôle et hygiène."),
      q("Les épices moulues vs entières: extraction?", ["Identique", "Moulues = rapide/intense, Entières = lente/subtile", "Inverse", "Entières plus rapides"], 1, "Surface de contact déterminante."),
      q("Pourquoi débuter avec dosages conservateurs?", ["Économie", "Épices peuvent dominer facilement (ajustement progressif)", "Tradition", "Réglementation"], 1, "Équilibre sensoriel délicat."),
      q("Certaines épices peuvent inhiber quoi?", ["Houblon", "Levure (stress fermentaire à haute dose)", "Enzymes du malt", "Eau"], 1, "Toxicité microbienne potentielle."),
      q("Le poivre est ajouté quand?", ["Empâtage", "Ajout tardif (préserve piquant aromatique)", "60 min", "Jamais en bière"], 1, "Volatilité des composés pipérinés."),
      q("La vanille est généralement ajoutée…", ["Ébullition", "Maturation/fermentation secondaire (macération froide)", "Empâtage", "Flameout"], 1, "Extraction délicate arômes complexes."),
      q("Les bâtons de vanille sont macérés combien de temps?", ["1 heure", "1-2 semaines en fermentation secondaire", "5 minutes", "Instantané"], 1, "Extraction lente composés aromatiques."),
      q("Le dosage de vanille (gousses) est typiquement…", ["1 gousse/100L", "2-4 gousses/hL (profil marqué)", "20 gousses/hL", "Traces"], 1, "Intensité aromatique désirée."),
      q("Les huiles essentielles d'épices sont…", ["Stables chaleur", "Très volatiles et sensibles chaleur/oxydation", "Résistantes", "Inertes"], 1, "Fragilité thermochimique."),
      q("Quel style utilise typiquement gingembre + agrumes?", ["Stout", "Witbier ou Bière d'été", "IPA classique", "Porter"], 1, "Profil rafraîchissant caractéristique."),
      q("Les Pumpkin Ales utilisent quelles épices?", ["Houblon seul", "Cannelle, muscade, gingembre, clou de girofle (pumpkin spice)", "Coriandre seule", "Vanille seule"], 1, "Mélange épices automnal typique."),
      q("La muscade est dosée comment?", ["50 g/hL", "1-3 g/hL (très puissante, notes chaudes)", "100 g/hL", "Traces négligeables"], 1, "Intensité aromatique forte."),
      q("L'anis étoilé apporte quel profil?", ["Agrumes", "Réglisse/anisé (2-5 g/hL)", "Floral", "Amer"], 1, "Caractère réglissé distinctif."),
      q("Les épices peuvent-elles créer du trouble?", ["Non", "Oui, particules en suspension (filtration parfois nécessaire)", "Jamais", "Clarifient"], 1, "Matière particulaire résiduelle."),
      q("Le cacao (fèves) est ajouté quand?", ["Empâtage", "Maturation froide (évite extraction tannins amers)", "60 min ébullition", "Flameout"], 1, "Prévention astringence."),
      q("Les piments (chili) apportent…", ["Douceur", "Piquant/chaleur capsaïcine (1-5 g/hL)", "Amertume houblon", "Acidité"], 1, "Sensation trigéminale brûlante."),
      q("Le timing optimal pour épices délicates?", ["Ébullition 60 min", "Flameout ou fermentation (préservation maximale)", "Empâtage", "Jamais"], 1, "Protection arômes volatils."),
      q("Les épices peuvent-elles oxyder?", ["Non jamais", "Oui, oxydation modifie profil aromatique (stockage sous vide)", "Impossible", "S'améliorent"], 1, "Dégradation oxydative arômes."),
      q("Comment tester un nouveau dosage d'épice?", ["Directement dans brassin", "Teinture test sur échantillon (ajustement avant production)", "Au hasard", "Maximum dose"], 1, "Validation sensorielle préventive.")
    ]
  },
  {
    id: "fruits",
    category: "ÉPICES",
    title: "19. Les Fruits en brassage",
    ficheRich: [
      { title: "Formes de Fruits", items: [
        "**Fruits frais**: Saveur authentique, mais apportent eau, pectine (trouble), levures/bactéries sauvages (risque contamination). Nécessitent pasteurisation ou ajout en fermentation active (alcool + CO2 protègent).",
        "**Purée aseptique**: Pasteurisée, sans pectine ajoutée. Pratique et sûre microbiologiquement. Concentration aromatique constante. Dosage: 10-30% du volume final.",
        "**Concentré de fruit**: Très concentré, stable. Permet dosage précis. Mais parfois profil 'artificiel' si mal choisi. Dosage: 2-5% volume.",
        "**Extraits/arômes**: Dosage très précis (mL/hL). Profil constant mais moins 'naturel'. Ajout à l'embouteillage. Utile pour ajustements fins.",
        "**Fruits lyophilisés**: Déshydratés, légers, longue conservation. Arômes concentrés. Réhydratation en fermentation. Dosage: 0.5-2 kg/hL."
      ]},
      { title: "Timing et Techniques", items: [
        "**Fermentation primaire active**: Idéal pour fruits frais. L'activité fermentaire et l'alcool protègent contre contamination. CO2 purge oxygène. Inconvénient: perte d'arômes volatils par fermentation.",
        "**Fermentation secondaire**: Après fermentation principale. Macération froide (~5-10 jours). Préserve mieux les arômes frais/délicats. Nécessite fruits pasteurisés ou purée aseptique.",
        "**Embouteillage/Packaging**: Extraits uniquement (dosage contrôlé, pas de refermentation)."
      ]},
      { title: "Considérations Techniques", items: [
        "**Refermentation**: Les fruits apportent des sucres fermentescibles (fructose, glucose). Calculer l'atténuation supplémentaire et la production de CO2 pour éviter surpression.",
        "**Pectine**: Polysaccharide des fruits. Cause trouble persistant (voile pectique). Solution: **enzymes pectinases** (ajout avant/pendant macération) pour hydrolyser la pectine.",
        "**Acidité**: Les fruits acidifient la bière (acide citrique, malique). Peut être souhaité (Berliner Weisse aux fruits, Sour) ou nécessiter équilibrage.",
        "**Couleur**: Les fruits rouges/noirs peuvent colorer intensément. Tenir compte dans formulation (dilution couleur possible).",
        "**Oxydation**: Fruits frais exposent à l'oxygène. Ajouter en fermentation active (CO2 protège) ou purger à l'azote."
      ]}
    ],
    questions: [
      q("Quel est le risque principal des fruits frais?", ["Aucun", "Contamination microbiologique (levures/bactéries sauvages)", "Trop chers", "Couleur fade"], 1, "Flore microbienne naturelle des fruits."),
      q("Comment protéger contre la contamination des fruits frais?", ["Impossible", "Ajout en fermentation active (alcool + CO2 protègent)", "Ébullition 60 min", "Ignorer"], 1, "Environnement hostile aux contaminants."),
      q("Qu'est-ce que la purée aseptique?", ["Fruit cru", "Purée pasteurisée, stable microbiologiquement", "Jus concentré", "Lyophilisé"], 1, "Traitement thermique sécurisant."),
      q("Quel dosage typique pour purée de fruits?", ["1%", "10-30% du volume final (intensité aromatique)", "50%", "Traces"], 1, "Proportion pour profil marqué."),
      q("Les fruits apportent quels sucres?", ["Lactose", "Fructose et glucose (fermentescibles)", "Dextrines", "Aucun"], 1, "Sucres simples fermentés par levure."),
      q("Qu'est-ce que la refermentation fruitée?", ["Impossible", "Levure consomme sucres fruits → alcool + CO2 supplémentaires", "Arrêt fermentation", "Contamination"], 1, "Fermentation secondaire des sucres fruits."),
      q("Comment calculer l'impact des fruits sur l'alcool?", ["Ignorer", "Estimer sucres ajoutés (°Brix) et atténuation levure", "Impossible", "Au hasard"], 1, "Prédiction densité finale ajustée."),
      q("Qu'est-ce que la pectine?", ["Sucre", "Polysaccharide des fruits (cause trouble persistant)", "Protéine", "Levure"], 1, "Source de voile pectique."),
      q("Comment éliminer le trouble pectique?", ["Filtration seule", "Enzymes pectinases (hydrolysent pectine)", "Impossible", "Chauffage"], 1, "Hydrolyse enzymatique ciblée."),
      q("Quand ajouter les pectinases?", ["Après embouteillage", "Avant/pendant macération fruits (prévention trouble)", "Jamais", "Empâtage"], 1, "Traitement préventif optimal."),
      q("Les fruits acidifient-ils la bière?", ["Non", "Oui, acides organiques (citrique, malique) abaissent pH", "Alcalinisent", "Neutre"], 1, "Contribution acide naturelle."),
      q("Quel style utilise typiquement fruits + acidité?", ["Stout", "Berliner Weisse, Gose, Lambic aux fruits", "IPA", "Lager"], 1, "Styles acides/sour avec fruits."),
      q("Les fruits rouges/noirs peuvent…", ["Éclaircir", "Colorer intensément la bière", "Pas d'effet", "Clarifier"], 1, "Pigments anthocyanes puissants."),
      q("Quand ajouter fruits en fermentation primaire?", ["Avant levure", "Pendant activité fermentaire (2-3 jours après pitch)", "Fin fermentation", "Jamais"], 1, "Protection maximale CO2 et alcool."),
      q("Quand ajouter fruits en fermentation secondaire?", ["Jamais", "Après fermentation principale (macération froide 5-10 jours)", "Pendant ébullition", "Embouteillage"], 1, "Préservation arômes délicats."),
      q("Quel avantage de la fermentation secondaire pour fruits?", ["Aucun", "Préserve arômes frais/délicats (pas de blow-off)", "Plus rapide", "Moins cher"], 1, "Rétention aromatique maximale."),
      q("Les fruits frais apportent-ils de l'oxygène?", ["Non", "Oui, risque oxydation (ajouter en fermentation active)", "Jamais", "Réduisent O2"], 1, "Exposition atmosphérique lors ajout."),
      q("Comment doser les extraits de fruits?", ["Kg/hL", "mL/hL (dosage précis goutte à goutte)", "%, volume", "Au jugé"], 1, "Concentration élevée = micro-dosage."),
      q("Les extraits peuvent être ajoutés quand?", ["Ébullition", "Embouteillage/packaging (dosage final contrôlé)", "Empâtage", "Fermentation primaire"], 1, "Ajustement post-fermentation."),
      q("Quel est l'avantage des fruits lyophilisés?", ["Moins aromatiques", "Légers, stables, arômes concentrés (longue conservation)", "Frais uniquement", "Interdits"], 1, "Praticité et stabilité."),
      q("Dosage typique fruits lyophilisés?", ["10 kg/hL", "0.5-2 kg/hL (concentration élevée)", "Traces", "50 kg/hL"], 1, "Déshydratation = concentration."),
      q("Peut-on ajouter fruits à l'ébullition?", ["Idéal", "Possible mais perte arômes volatils + extraction pectine/tannins", "Obligatoire", "Interdit"], 1, "Dégradation thermique aromatique."),
      q("Les framboises apportent quel profil?", ["Neutre", "Fruité intense, acidité naturelle (acide éllagique)", "Sucré seul", "Amer"], 1, "Caractère acide-fruité typique."),
      q("Les cerises (griottes) sont utilisées dans…", ["IPA", "Kriek (Lambic belge aux cerises)", "Stout uniquement", "Lager"], 1, "Style traditionnel belge."),
      q("La mangue apporte quel profil?", ["Acide fort", "Tropical fruité intense (esters naturels)", "Amer", "Neutre"], 1, "Arôme exotique caractéristique."),
      q("Le fruit de la passion contient…", ["Peu de saveur", "Acidité marquée + arômes tropicaux intenses", "Neutre", "Uniquement sucre"], 1, "Intensité aromatique et acide."),
      q("Les myrtilles peuvent causer…", ["Clarification", "Coloration violette intense + trouble pectique", "Éclaircissement", "Aucun effet"], 1, "Pigmentation anthocyanique forte."),
      q("Comment pasteuriser des fruits?", ["Ébullition 60 min", "Chauffage 70-80°C pendant 15-30 min (tue microbes)", "Congélation", "Impossible"], 1, "Traitement thermique modéré."),
      q("La congélation des fruits aide-t-elle?", ["Aucun effet", "Oui, rompt cellules (facilite extraction) + réduit charge microbienne", "Détruit arômes", "Interdit"], 1, "Rupture membranaire et hygiène."),
      q("Quel fruit est typique des Lambics belges?", ["Banane", "Framboise, cerise, pêche (fermentation spontanée + fruits)", "Ananas", "Pomme verte"], 1, "Tradition brassicole belge fruité.")
    ]
  },

  // 21. Types de malts
  {
    id: "typesMalts",
    category: "MALT",
    title: "6. Types de malts",
    ficheRich: [
      {
        title: "Définition Centrale",
        items: [
          "Les **types de malts** se classent en deux grandes catégories : les **malts enzymatiques** (pouvoir diastasique) qui fournissent l'extrait et les enzymes, et les **malts inertes** (couleur, saveur, corps) qui ne convertissent pas l'amidon mais enrichissent la bière."
        ]
      },
      {
        title: "Malts de Base (Enzymatiques)",
        items: [
          "**Pilsener / Pale Ale**: Font 80-100% de la grist. **Touraillés à basse T** (60-65°C) pour maximiser la survie des enzymes. **Pouvoir Diastasique élevé**, **Kolbach idéal**.",
          "**Caractéristiques**: Grain accessible, peu de vitrosité, conversion rapide (30-45 min d'empâtage suffisent)."
        ]
      },
      {
        title: "Malts Caramel/Crystal (Caractère)",
        items: [
          "**Processus**: Grain humidifié → étuvage (T interne 65-70°C) → saccharification interne → touraillage (caramélisation).",
          "**Résultat**: **Dextrines vitrifiées** (sucres non fermentescibles) bloquées dans le grain. **Zéro activité enzymatique**.",
          "**Impacts**: Augmentation du **corps**, de la **tenue de mousse**, et des saveurs de caramel/toffee. Couleur EBC varie : CaraPils (5-10°EBC) à CaraMunich (40-80°EBC).",
          "**Usage**: Jamais plus de 40-50% sans malt de base."
        ]
      },
      {
        title: "Malts Torréfiés et Spéciaux",
        items: [
          "**Malts Torréfiés (Black, Chocolat)**: Très haute T (> 200°C) = sucres brûlés. Notes de **café/cacao**, acidité (↓ pH). **Usage strict** : < 5% (Black) ou < 10% (Chocolat).",
          "**Malts Spéciaux (Munich, Vienna)**: T intermédiaire (75-85°C touraillage) = **mélanoïdines intermédiaires**. Conservent une activité enzymatique partielle. Pouvoir diastasique encore exploitable (peuvent faire jusqu'à 60% de la grist).",
          "**Règle d'Or**: Tout malt sans enzymes doit être associé à un **malt de base enzymatique** dans l'empâtage."
        ]
      }
    ],
    questions: [
      q("Que apportent principalement les malts de base?", ["De la couleur", "Des enzymes et de l'extrait fermentescible", "Du corps", "Des polyphénols"], 1, "Les malts de base sont la source principale d'enzymes et de rendement."),
      q("Quel est l'effet des malts Caramel/Crystal?", ["Diminuent la mousse", "Augmentent le corps et la tenue de mousse", "Diminuent les dextrines", "Augmentent l'amertume"], 1, "Les dextrines non fermentescibles apportent du corps."),
      q("Comment sont produits les malts Black et Chocolat?", ["Touraillés à basse température", "Torréfiés à plus de 200°C", "Fumés", "Non chauffés"], 1, "La torréfaction brûle les sucres et crée des arômes de café/cacao."),
      q("Quelle est la température de touraillage des malts Pilsener/Pale Ale?", ["80-90°C", "60-65°C", "75°C", "50°C"], 1, "Basse température pour préserver les enzymes."),
      q("Quel pourcentage de la recette représentent les malts enzymatiques?", ["20-40%", "50-70%", "80-100%", "Illimité"], 2, "Ils forment toujours la base de la recette."),
      q("Quelle est la couleur EBC du CaraPils?", ["5-10", "20-30", "40-50", "80+"], 0, "Caramel léger et doux."),
      q("Quelle est la couleur EBC du CaraMunich?", ["5-10", "20-30", "40-80", "80+"], 2, "Caramel plus foncé."),
      q("Quel est le processus de fabrication des malts Caramel?", ["Torréfaction directe", "Étuvage + saccharification interne + touraillage", "Fumage", "Séchage simple"], 1, "Les dextrines sont vitrifiées à l'intérieur du grain."),
      q("Les dextrines sont-elles fermentescibles?", ["Oui, totalement", "Non, pas du tout", "Partiellement", "Selon la levure"], 1, "Ce sont des sucres de structure non fermentescibles."),
      q("Quelle est la température de touraillage des malts Munich/Vienna?", ["50-60°C", "75-85°C", "90-100°C", "110-120°C"], 1, "Température intermédiaire créant des mélanoïdines."),
      q("Quel est le pourcentage maximum de Munich dans une recette?", ["20%", "40%", "60%", "80%"], 2, "Conserve un pouvoir diastasique utilisable."),
      q("Quelle proportion maximale de Black Malt utiliser?", ["Moins de 5%", "Moins de 10%", "Moins de 20%", "Illimitée"], 0, "Très intense, à utiliser avec parcimonie."),
      q("Quelle proportion maximale de malt Chocolat utiliser?", ["Moins de 5%", "Moins de 10%", "Moins de 20%", "Moins de 30%"], 1, "Moins intense que le Black mais toujours puissant."),
      q("Que apportent les malts colorants?", ["Des enzymes", "Des sucres fermentescibles", "De la couleur et des saveurs", "De l'amertume"], 2, "Pas d'activité enzymatique."),
      q("Que désigne la vitrosité du grain?", ["Sa transparence", "Sa dureté", "Son humidité", "Sa couleur"], 1, "Un grain dur se convertit plus lentement."),
      q("Qu'est-ce que la modification de l'endosperme?", ["La dégradation des protéines uniquement", "La dureté du grain", "La couleur", "Le goût"], 0, "Tous les paramètres sont affectés par la modification."),
      q("Un grain 'accessible' signifie qu'il est...", ["Dur", "Tendre", "Cristallin", "Vitreux"], 1, "Facile à convertir lors de l'empâtage."),
      q("Quels malts permettent une conversion rapide en 30-45 minutes?", ["Les malts spéciaux", "Les malts de base", "Les malts torréfiés", "Les malts caramel"], 1, "Bonne modification enzymatique."),
      q("Pour quels malts le palier protéinique est-il optimal?", ["Les malts modernes", "Les malts de base", "Les malts peu modifiés", "Toujours requis"], 2, "Nécessaire pour les grains moins modifiés."),
      q("Maltose vs Dextrines : lequel donne du corps?", ["Le maltose", "Les dextrines", "Le maltose donne du sec", "Les deux également"], 1, "Les dextrines créent le corps, le maltose la sécheresse."),
      q("Les malts spéciaux (Munich/Vienna) sont-ils enzymatiquement actifs?", ["Complètement morts", "Partiellement actifs", "Très actifs", "Totalement inactifs"], 1, "Conservent des enzymes résiduelles."),
      q("Quelles sont les trois catégories principales de malts?", ["Base/Caramel/Spécial", "Enzymatique/Inerte/Couleur", "Base/Caramel/Torréfié", "Réducteur/Oxydant/Neutre"], 2, "Classification standard."),
      q("Quelle saveur apportent les malts de base?", ["Sucrée", "Biscuitée/maltée", "Caramélisée", "Brûlée"], 1, "Notes maltées fines et délicates."),
      q("Quel est le but du touraillage?", ["La fermentation", "Le séchage, développement d'arômes et arrêt de la germination", "La mouture", "L'empâtage"], 1, "Étape clé du processus de maltage."),
      q("Que signifie 'kilned malt'?", ["Malt torréfié", "Malt touraillé (séché à la chaleur)", "Malt fumé", "Malt cru"], 1, "Méthode de séchage standard."),
      q("Que désigne la modification du grain?", ["La couleur", "La dégradation de l'endosperme (amidon et protéines accessibles)", "Le goût", "L'humidité"], 1, "Indicateur de qualité du maltage."),
      q("Où se produit la saccharification du Crystal malt?", ["À l'extérieur", "À l'intérieur du grain avant touraillage", "Pendant l'empâtage", "Pendant la fermentation"], 1, "Processus unique aux malts Crystal."),
      q("Qu'est-ce que la vitrification des dextrines?", ["Une cristallisation", "Le blocage des sucres dans le grain (non libérés à l'empâtage)", "La fermentation", "L'hydrolyse"], 1, "Caractéristique des malts caramel."),
      q("Quelle est la règle d'or pour les malts inertes?", ["Utilisables seuls", "Toujours associés à un malt de base enzymatique", "Utilisation optionnelle", "Interdits"], 1, "Nécessaire pour la conversion de l'amidon."),
      q("Quel est l'impact des malts torréfiés sur le pH?", ["Neutre", "Baisse du pH (acides organiques)", "Augmentation du pH", "Variable"], 1, "Impact acidifiant sur le moût.")
    ]
  },

  // 22. Pathologie du grain (Fusarium)
  {
    id: "fusarium",
    category: "MALT",
    title: "7. Pathologie du grain (Fusarium)",
    ficheRich: [
      {
        title: "Définition et Contexte",
        items: [
          "**Fusarium** est un **champignon filamenteux** (Ascomycète, ordre Hypocreales) parasite de l'orge et des céréales globalement, favorisé par l'**humidité élevée** (> 85% RH) durant la **croissance** (printemps/été) et la **récolte** (pluies). Il est responsable de la **fusariose de l'épis** (Fusarium Head Blight, FHB).",
          "**Distribution**: Prévalence élevée en régions continentales humides (France Nord, Allemagne, Canada, USA Midwest, Australie). Coûts agricoles annuels estimés milliards €."
        ]
      },
      {
        title: "Mycotoxines Fusarium",
        items: [
          "**Déoxynivalénol (DON / Vomitoxine)**: Principale toxine. Seuil légal max **2000 µg/kg** (2 ppm) malt UE. Seuil nutrition animale **1000 µg/kg** (plus restrictif). Effet émétique (vomissements), immunosuppression chez humains/animaux.",
          "**Zéaralénone (ZEN)**: Toxine secondaire, mimique hormonale (œstrogène). Seuil **200 µg/kg**. Toxicité reproduction.",
          "**Nivalenol (NIV)** et **T2-Toxin**: Semblables DON. Rares dans malt orge (plutôt maïs fourragère).",
          "**Stabilité Thermique (CRITIQUE)**: DON/ZEN **NE se dégradent PAS** lors empâtage (65–75°C) ni ébullition (100°C). Transfert **complet vers moût puis bière**. Aucune étape brassage n'élimine contamination une fois présente."
        ]
      },
      {
        title: "Impacts Brassicoles – Gushing et Autres",
        items: [
          "**Gushing (Débordement Explosif)**: Mousse déborde **violemment incontrolable** à ouverture bouteille (effet champagne). Risque **sécurité** (projection, blessure), **réputation client**, **perte produit**.",
          "**Cause : Hydrophobines**: *Fusarium* produit **protéines hydrophobes très petites** (< 10 kDa). Extrêmement **thermostables** (survivent ébullition et torréfaction malt). Nature : chaînes peptidiques acides aminés hydrophobes (valine, leucine, isoleucine).",
          "**Mécanisme Gushing**: Hydrophobines s'adsorbent sur **bulles CO₂** → sites nucléation **hyperactifs** → libération explosive gaz. Vitesse : secondes post-ouverture.",
          "**Impact Secondaire**: *Fusarium* sécrète **protéases excessives** → dégradation protéines mousse → **IK trop élevé** (> 50%) → mousse faible collapse rapide. Paradoxe : gushing initial puis affaissement rapide = présentation très mauvaise."
        ]
      },
      {
        title: "Diagnostic et Prévention",
        items: [
          "**Inspection Visuelle**: Grain **teinté rose/rougeâtre** (pigmentation *Fusarium*), grain momifié (infection sévère), odeur moisi/foin pourri.",
          "**Tri Optique (Malterie)**: Caméra inspectent chaque grain, comparaison chromatic, élimination contaminés (80–95% efficacité).",
          "**Test DON**: **HPLC** (coûteux €30–100, 24–48h) ou **test rapide/immunoaffinity** (€5–15, 15–30 min, moins précis). Obligatoire réception lot.",
          "**Prévention Agricole**: Variétés résistantes, fongicides, gestion humidité drainage.",
          "**Rôle Brasseur**: Vérifier **COA (Certificat Analyse)**, accepter seulement lots < 2000 µg/kg, documentation traçabilité. **Aucune dé-contamination efficace** une fois malt acquis."
        ]
      }
    ],
    questions: [
      q("Que produit le champignon Fusarium?", ["Des levures", "Des mycotoxines comme le DON", "Du houblon", "Du sucre"], 1, "Champignon parasite produisant des toxines dangereuses."),
      q("Que causent les hydrophobines dans la bière?", ["Une mousse stable", "Le gushing (débordement explosif)", "Des arômes de houblon", "De la couleur"], 1, "Protéines thermostables créant des sites de nucléation sur les bulles de CO₂."),
      q("Quel est le seuil légal maximum de DON en ppm?", ["0.5", "1", "2", "5"], 2, "2 ppm ou 2000 µg/kg maximum en Europe."),
      q("Qu'est-ce que le gushing?", ["Une mousse débordante explosive", "Une fermentation rapide", "Un trouble persistant", "De l'acidité"], 0, "Débordement violent et incontrôlable à l'ouverture."),
      q("À quelle température les hydrophobines sont-elles détruites?", ["Sous 50°C", "Sous 75°C", "Extrêmement thermostables (>100°C)", "À 100°C"], 2, "Survivent à l'ébullition et à la torréfaction."),
      q("Dans quel climat le Fusarium est-il favorisé?", ["Chaud et sec", "Froid et sec", "Chaud et humide", "Froid et humide"], 2, "L'humidité élevée durant la croissance favorise le développement."),
      q("Où le DON est-il transféré lors du brassage?", ["Reste dans la drêche", "Passe dans le moût puis dans la bière", "Absorbé par la levure", "Évacué avec le CO2"], 1, "Traverse tout le processus de brassage."),
      q("Quel est l'effet des hydrophobines sur les sites de nucléation?", ["Les réduisent", "Les augmentent (hyperactifs)", "Les neutralisent", "Les bloquent"], 1, "Créent des sites hyperactifs causant le gushing."),
      q("Qu'est-ce que la Zéaralénone (ZEN)?", ["Un colorant", "Une mycotoxine secondaire du Fusarium", "Un amidon modifié", "Une enzyme"], 1, "Autre toxine produite par Fusarium."),
      q("Qu'est-ce que la T2-Toxin?", ["Une enzyme", "Un polyphénol", "Une mycotoxine produite par Fusarium", "Une levure"], 2, "Toxine additionnelle liée au Fusarium."),
      q("Le diacétyle (goût de beurre) peut être causé par...", ["Fusarium directement", "Les enzymes produites par Fusarium", "Les levures sauvages", "La température"], 1, "Les enzymes de Fusarium peuvent l'induire."),
      q("Comment fonctionne le tri optique en malterie?", ["Inspection visuelle humaine", "Machine détectant la couleur de chaque grain", "Tri par densité", "Tri par humidité"], 1, "Détection automatique des grains contaminés."),
      q("Le COA (Certificat d'Analyse) est-il obligatoire?", ["Optionnel", "Obligatoire à vérifier", "Non exigé", "Purement décoratif"], 1, "Document de traçabilité essentiel."),
      q("Peut-on décontaminer un malt infecté par Fusarium?", ["Oui, par la chaleur", "Oui, par des enzymes", "Non, c'est impossible", "Oui, par surgélation"], 2, "Une fois contaminé, aucun traitement efficace."),
      q("La production d'hydrophobines par Fusarium est...", ["Rare", "Très commune et systématique", "Unique à certaines espèces", "Variable selon la saison"], 1, "Production systématique par le champignon."),
      q("Quels risques présente le gushing?", ["Qualité uniquement", "Sécurité de la bouteille", "Satisfaction client", "Tous ces risques"], 3, "Affecte tous les niveaux de production."),
      q("Le Fusarium est un...", ["Levure", "Bactérie", "Champignon ascomycète filamenteux", "Virus"], 2, "Classification biologique précise."),
      q("Quelle est la stabilité thermique des mycotoxines?", ["Détruites à 75°C", "Partiellement détruites à 100°C", "Complètement stables thermiquement", "Variable"], 2, "Résistent à toutes les températures de brassage."),
      q("Quelle est la couleur typique d'une colonie de Fusarium?", ["Blanche", "Rose à rougeâtre", "Noire", "Verte"], 1, "Pigmentation caractéristique rose."),
      q("Un grain avec des taches blanches indique...", ["Bonne santé", "Possible contamination par Fusarium", "Bonne modification", "Maturité optimale"], 1, "Indicateur visuel de défaut."),
      q("Le test DON par HPLC est-il coûteux?", ["Oui, assez coûteux", "Non, très rapide", "Obligatoire pour tous", "Décisionnel uniquement"], 0, "Toutes ces affirmations sont vraies selon le contexte."),
      q("Quelle est la taille moléculaire des hydrophobines?", ["50 kDa", "Moins de 10 kDa (très petites)", "100 kDa", "200 kDa"], 1, "Protéines de très petite taille."),
      q("Que signifie l'acronyme FHB?", ["Full Head Barley", "Fusarium Head Blight (fusariose de l'épi)", "Fermentation Heat Balance", "First Hop Bittering"], 1, "Terme technique pour la maladie."),
      q("La vomitoxine est le nom commun de...", ["La Zéaralénone", "Le DON (Déoxynivalénol)", "La T2-Toxin", "Le Nivalenol"], 1, "Nom alternatif du DON."),
      q("Quelle humidité relative favorise le Fusarium?", ["Plus de 85% RH", "Plus de 50% RH", "Plus de 70% RH", "Plus de 95% RH"], 0, "Seuil critique d'humidité."),
      q("Un indice de Kolbach élevé dû à Fusarium signifie...", ["Moins de 35%", "36-45%", "Plus de 50% (protéases excessives)", "Indépendant"], 2, "Dégradation excessive des protéines."),
      q("Un grain momifié indique...", ["Une santé excellente", "Une infection sévère par Fusarium", "Un séchage optimal", "La maturité"], 1, "Pathologie très avancée."),
      q("Quelles sont les méthodes de prévention agricole?", ["Aucune méthode", "Variétés résistantes, fongicides et drainage", "Récolte rapide uniquement", "Stockage au sec"], 1, "Stratégie de prévention au champ."),
      q("Quel est le rôle du brasseur face à la contamination?", ["Traiter le malt lui-même", "Refuser les lots avec plus de 2 ppm de DON (vérifier le COA)", "Accepter tous les lots", "Diluer le malt"], 1, "Contrôle qualité à la réception."),
      q("Comment inspecter visuellement un grain suspect?", ["Inspection inutile", "Chercher teinte rose/rougeâtre et odeur de moisi", "Couleur uniquement", "Goûter le grain"], 1, "Premier diagnostic visuel et olfactif.")
    ]
  },

  // 23. Introduction à l'hygiène en brasserie
  {
    id: "hygieneBrasserie",
    category: "CIP",
    title: "20. Introduction à l'hygiène en brasserie",
    ficheRich: [
      {
        title: "Contexte et Importance",
        items: [
          "**L'hygiène est le pilier fondamental** de la production de bière de qualité. Une bière infectée ne correspondra jamais aux attentes du brasseur, peu importe la qualité des ingrédients ou la maîtrise du processus de brassage.",
          "**Principe de Conservation**: Le produit doit pouvoir se conserver dans le temps et rester tel que désiré. Si une bière est infectée, elle ne sera plus ce que vous avez voulu faire et offrir au client.",
          "**Prévention > Traitement**: Les micro-organismes sont partout et se développent rapidement. La prévention est toujours plus efficace que le traitement d'une contamination établie."
        ]
      },
      {
        title: "Bière 'Clean' vs Bière 'Wild' (Sauvage)",
        items: [
          "**Bière Clean**: Fermentée uniquement avec des **levures sélectionnées** (*Saccharomyces*). Goût **maîtrisé et reproductible**. C'est l'objectif standard de la majorité des brasseries commerciales.",
          "**Bière Wild/Sauvage**: Fermentée avec des **micro-organismes sauvages** (intentionnellement ou non). Profil aromatique complexe, souvent 'funky', acidité spontanée. Exemples : Lambics belges, Gueuze, certains Sours artisanaux.",
          "**Distinction Critique**: La différence est **l'intentionnalité** et le **contrôle**. Une bière sauvage est voulue et maîtrisée. Une bière clean infectée est un défaut."
        ]
      },
      {
        title: "Micro-organismes Impliqués",
        items: [
          "**Saccharomyces cerevisiae** (Levure eucaryote) : Levure principale de fermentation. Possède un **noyau** (eucaryote). Fermentation alcoolique contrôlée. Production éthanol + CO₂.",
          "**Brettanomyces** (Levure sauvage) : Donne des arômes **'funky', cuir, ferme, phénoliques**. Parfois recherchés (Lambics, Saisons), souvent indésirables dans bières clean.",
          "**Lactobacilles** (Bactéries lactiques) : Produisent **acide lactique** → acidité douce, tangy. Utilisés intentionnellement (Berliner Weisse, Gose) ou contamination.",
          "**Pédocoques** (Bactéries lactiques) : Contamination généralement **indésirable**. Production acide lactique + diacétyle (beurre rancide). Croissance lente mais persistante.",
          "**Acétobactères** (Bactéries acétiques) : Produisent **acide acétique** (vinaigre) en présence d'oxygène. Défaut majeur → bière imbuvable. Indicateur de mauvaise hygiène ou exposition à l'air."
        ]
      },
      {
        title: "Équipements Concernés (Post-Ébullition)",
        items: [
          "**Zone Critique**: Tout équipement en contact avec le **moût froid** (post-ébullition) ou la **bière** doit être **aseptique**.",
          "**Équipements à risque**: Cuves de refroidissement, échangeurs de chaleur, **fermenteurs**, tuyaux et raccords, vannes, pompes, embouteillage/conditionnement.",
          "**Pré-ébullition**: Les cuves de brassage et d'ébullition sont stérilisées par la chaleur (> 100°C). Hygiène importante mais risque moindre.",
          "**Nettoyage vs Désinfection**: Nettoyage = élimination saleté/résidus. Désinfection = destruction micro-organismes. Les deux sont nécessaires séquentiellement."
        ]
      }
    ],
    questions: [
      q("Quelle est l'importance de l'hygiène en brasserie?", ["Optionnelle", "Pilier fondamental de la qualité", "Secondaire", "Purement esthétique"], 1, "Base essentielle de la production de bière réussie."),
      q("Avec quoi est fermentée une bière 'clean'?", ["Des micro-organismes sauvages", "Des levures sélectionnées Saccharomyces", "Des bactéries lactiques", "Un mélange aléatoire"], 1, "Contrôle strict pour reproductibilité."),
      q("Quelle est la caractéristique d'une bière 'wild' (sauvage)?", ["Goût standardisé", "Fermentation avec micro-organismes sauvages (intentionnelle)", "Production industrielle", "Sans levure"], 1, "Complexité aromatique volontairement recherchée."),
      q("Qu'est-ce que Saccharomyces cerevisiae?", ["Une bactérie", "Une levure eucaryote (avec noyau)", "Un virus", "Un champignon filamenteux"], 1, "Levure principale de fermentation."),
      q("Quels arômes produit Brettanomyces?", ["Fruité et doux", "Funky, cuir, ferme (phénoliques)", "Neutre", "Floral"], 1, "Signature aromatique de cette levure sauvage."),
      q("Que produisent les lactobacilles?", ["De l'éthanol", "De l'acide lactique (acidité douce)", "De l'acide acétique", "Du CO₂ uniquement"], 1, "Bactéries lactiques créant de l'acidité."),
      q("Les pédocoques représentent quel type de contamination?", ["Toujours recherchée", "Généralement indésirable (acide lactique + diacétyle)", "Bénéfique", "Neutre"], 1, "Défaut de qualité fréquent."),
      q("Que produisent les acétobactères?", ["De l'alcool", "De l'acide acétique (vinaigre)", "Des sucres", "De la mousse"], 1, "Défaut majeur en présence d'oxygène."),
      q("Quel est le résultat d'une infection de la bière?", ["Une amélioration", "Un changement irrémédiable du goût", "Aucun effet", "Une stabilisation"], 1, "Perte totale du contrôle du produit."),
      q("Prévention vs Traitement : quelle approche est meilleure?", ["Le traitement est meilleur", "La prévention est plus efficace", "Les deux sont égaux", "Impossible à comparer"], 1, "Approche proactive de l'hygiène."),
      q("Où trouve-t-on les micro-organismes?", ["Ils sont absents", "Partout (ubiquitaires)", "Ils sont rares", "Totalement contrôlables"], 1, "Risque de contamination constant."),
      q("Quelle est l'importance d'un équipement propre?", ["Esthétique uniquement", "Base d'une bière réussie (prévention contamination)", "Marketing", "Optionnelle"], 1, "Qualité fondamentale en brasserie."),
      q("Quelle est la zone critique pour la contamination?", ["Avant l'ébullition", "Après l'ébullition (moût froid et bière)", "L'empâtage", "La mouture"], 1, "Absence de stérilisation thermique."),
      q("Quel est l'effet de l'ébullition sur les micro-organismes?", ["Aucun effet", "Stérilise (plus de 100°C tue les microbes)", "Les favorise", "Variable"], 1, "Barrière thermique efficace."),
      q("Quelle est l'importance de l'hygiène du fermenteur?", ["Peu importante", "Critique (contact prolongé avec la bière)", "Optionnelle", "Visuelle uniquement"], 1, "Risque de contamination très élevé."),
      q("Qu'est-ce que le nettoyage?", ["La destruction des microbes", "L'élimination de la saleté et des résidus physiques", "La désinfection", "La stérilisation"], 1, "Première étape du protocole."),
      q("Qu'est-ce que la désinfection?", ["Le nettoyage physique", "La destruction des micro-organismes (chimique ou thermique)", "Le rinçage", "Le séchage"], 1, "Élimination biologique des microbes."),
      q("Quelle est la séquence d'hygiène correcte?", ["Désinfection puis nettoyage", "Nettoyage puis désinfection", "Simultané", "Aléatoire"], 1, "Protocole standard en brasserie."),
      q("Le Brettanomyces dans les Lambics est...", ["Une contamination", "Intentionnel et recherché", "Une erreur", "Accidentel"], 1, "Style traditionnel belge volontaire."),
      q("Le diacétyle (goût de beurre) est produit par...", ["Une levure saine", "Les pédocoques et levure stressée (contamination)", "Le houblon", "Le malt"], 1, "Off-flavour caractéristique d'une contamination."),
      q("Les acétobactères ont-elles besoin d'oxygène?", ["Non", "Oui (ce sont des bactéries aérobies)", "Variable", "Jamais"], 1, "Métabolisme acétique aérobie."),
      q("Les lactobacilles dans une Berliner Weisse sont...", ["Une contamination", "Utilisés intentionnellement pour l'acidité", "À éviter", "Interdits"], 1, "Contrôle volontaire pour les Sour beers."),
      q("Comment se conserve une bière infectée?", ["Normalement", "Impossible, les défauts évoluent", "Mieux qu'une bière saine", "Sans impact"], 1, "Instabilité microbiologique progressive."),
      q("Quelle est l'importance de l'hygiène des vannes et raccords?", ["Négligeable", "Critique (zones mortes favorisant le biofilm)", "Automatique", "Inutile"], 1, "Points de contamination très fréquents."),
      q("Où doit-on nettoyer les tuyaux?", ["À l'extérieur seulement", "À l'intérieur (surface en contact avec le produit)", "Optionnel", "Visuellement suffisant"], 1, "Surface de contact direct avec la bière."),
      q("Qu'est-ce qu'un biofilm?", ["Un résidu de malt", "Une communauté de microbes adhérant à une surface (protection)", "De la mousse", "De la levure seule"], 1, "Structure résistante au nettoyage."),
      q("À quelle température stocker la bière?", ["Élevée", "Froide (ralentit les microbes)", "Ambiante", "Variable"], 1, "Conservation microbiologique optimale."),
      q("Quel est l'impact du pH bas de la bière sur les microbes?", ["Neutre", "Un pH bas (<4.5) inhibe de nombreux microbes", "Les favorise", "Sans effet"], 1, "Barrière naturelle de protection."),
      q("Le houblon a-t-il des propriétés antimicrobiennes?", ["Aucune", "Oui (grâce aux acides alpha et iso-alpha)", "Négatives", "C'est un mythe"], 1, "Défense naturelle partielle de la bière."),
      q("Quel est l'effet de l'éthanol sur les microbes?", ["Favorise leur croissance", "Les inhibe (antiseptique naturel)", "Neutre", "Variable"], 1, "Barrière alcoolique protectrice.")
    ]
  },
  {
    id: "cip",
    category: "CIP",
    title: "21. Le système CIP/SIP et les paramètres TACCT",
    ficheRich: [
      {
        title: "Définitions",
        items: [
          "CIP - Clean In Place (Nettoyage En Place / NEP) : Système permettant de nettoyer l'intérieur des équipements sans les démonter, par circulation de solutions de nettoyage.",
          "SIP - Sanitizing In Place : Système permettant de désinfecter l'intérieur des équipements sans les démonter."
        ]
      },
      {
        title: "Les 5 paramètres TACCT",
        items: [
          "T - Time to clean (Temps de nettoyage) : Durée de contact entre le produit nettoyant et la surface. Plus le temps est long, plus le nettoyage est efficace. Valeur typique : **15-30 minutes** pour la soude en CIP standard (30-60 minutes pour encrassements lourds ou cuves de grande capacité).",
          "A - Action impact (Action mécanique et chimique) : Force mécanique exercée par le liquide sur les surfaces (pression, débit, turbulence). Décolle les salissures adhérentes. Équipement : boules d'arrosage, pompes propulseuses.",
          "C - Coverage (Surface couverte) : Pourcentage de surface atteinte par le liquide nettoyant. Objectif : 100% de couverture. Problèmes : zones mortes, angles, soudures mal conçues.",
          "C - Chemical concentration (Concentration chimique) : Quantité de produit actif dans la solution. Contrôle par sonde de concentration et conductivimètre. Valeur typique soude : 2% NaOH (~100 mS/cm).",
          "T - Temperature (Température) : Température de la solution de nettoyage. La chaleur améliore l'efficacité chimique. Valeur typique : 60-80°C pour la soude."
        ]
      },
      {
        title: "Cercle de Sinner",
        items: [
          "Principe : Si on diminue un paramètre, il faut compenser en augmentant un ou plusieurs autres.",
          "Les 4 facteurs interdépendants : Temps, Chimie, Mécanique, Température.",
          "Points clés : Les 5 paramètres TACCT sont interdépendants, aucun ne doit être négligé, le contrôle (sondes, conductivimètre) est essentiel, la conception de l'équipement influence la couverture."
        ]
      }
    ],
    questions: [
      q("Que signifie l'acronyme CIP?", ["Clean In Process", "Clean In Place (Nettoyage En Place)", "Chemical In Process", "Cold In Place"], 1, "Système de nettoyage sans démontage."),
      q("Que signifie l'acronyme SIP?", ["Sanitizing In Process", "Sanitizing In Place (Désinfection En Place)", "Sterilizing In Process", "System In Place"], 1, "Système de désinfection sans démontage."),
      q("Quel est l'avantage principal du système CIP?", ["Coût réduit", "Permet de nettoyer sans démonter les équipements", "Plus rapide", "Utilise moins de produits"], 1, "Gain de temps et efficacité opérationnelle."),
      q("Que signifie le premier T dans TACCT?", ["Température", "Time to clean (Temps de nettoyage)", "Turbulence", "Traitement"], 1, "Durée de contact avec la solution nettoyante."),
      q("Que signifie le A dans TACCT?", ["Alcalinité", "Action impact (Action mécanique et chimique)", "Automatisation", "Acidité"], 1, "Force mécanique exercée par le liquide."),
      q("Que signifie le premier C dans TACCT?", ["Chemical concentration", "Coverage (Surface couverte)", "Contrôle", "Conductivité"], 1, "Pourcentage de surface atteinte."),
      q("Que signifie le deuxième C dans TACCT?", ["Coverage", "Chemical concentration (Concentration chimique)", "Contrôle", "Chaleur"], 1, "Quantité de produit actif dans la solution."),
      q("Que signifie le deuxième T dans TACCT?", ["Temps", "Turbulence", "Temperature (Température)", "Traçabilité"], 1, "Température de la solution de nettoyage."),
      q("Quelle est la durée typique de contact pour le détergent en CIP standard?", ["5-10 minutes", "15-30 minutes", "30-60 minutes (cas lourds)", "2-3 heures"], 1, "Temps standard CIP. 30-60 min pour encrassements lourds."),
      q("Quel est l'effet d'un temps de nettoyage trop court?", ["Aucun effet", "Meilleure efficacité", "Nettoyage incomplet", "Économies de produits"], 2, "Temps insuffisant pour éliminer les salissures."),
      q("Quels facteurs influencent l'action mécanique en CIP?", ["Couleur du liquide", "Pression, débit, turbulence du flux", "pH uniquement", "Odeur"], 1, "Forces physiques de décollement."),
      q("Quel équipement est utilisé pour l'action mécanique en CIP?", ["Filtres", "Boules d'arrosage et pompes propulseuses", "Thermomètres", "pH-mètres"], 1, "Dispositifs générant la pression et le flux."),
      q("Quel est l'objectif de couverture en CIP?", ["50% suffit", "75% minimum", "100% de la surface", "90% acceptable"], 2, "Toute la surface doit être nettoyée."),
      q("Quels sont les problèmes typiques de couverture en CIP?", ["Température trop haute", "Zones mortes, angles, soudures mal conçues", "Débit trop fort", "Produit trop concentré"], 1, "Zones difficiles à atteindre par le liquide."),
      q("Comment contrôle-t-on la concentration chimique en CIP?", ["À l'œil", "Par sonde de concentration et conductivimètre", "Par le temps", "Par la température"], 1, "Mesure électrique de la conductivité."),
      q("Quel est le risque d'un sous-dosage de produit chimique?", ["Corrosion", "Nettoyage inefficace", "Coût élevé", "Rinçage difficile"], 1, "Concentration insuffisante pour nettoyer."),
      q("Quels sont les risques d'un surdosage de produit chimique?", ["Nettoyage incomplet", "Corrosion, coût élevé, rinçage difficile", "Aucun risque", "Temps réduit"], 1, "Effets négatifs de l'excès de chimie."),
      q("Quelle est la concentration typique de soude (NaOH) en CIP?", ["0.5%", "1%", "2%", "5%"], 2, "Dosage standard pour le nettoyage alcalin."),
      q("Quelle est la conductivité typique d'une solution de soude à 2%?", ["10 mS/cm", "50 mS/cm", "100 mS/cm", "200 mS/cm"], 2, "Mesure électrique correspondant à 2% NaOH."),
      q("Quelle est la température typique pour la soude en CIP?", ["20-30°C", "40-50°C", "60-80°C", "90-100°C"], 2, "Température optimale pour l'efficacité alcaline."),
      q("Quel est l'effet de la température sur le nettoyage?", ["Aucun effet", "La chaleur améliore l'efficacité chimique", "Réduit l'efficacité", "Variable selon les produits"], 1, "Accélération des réactions chimiques."),
      q("Quelle précaution prendre avec la température en CIP?", ["Toujours maximale", "Respecter les limites des matériaux et joints", "Pas d'importance", "Le plus froid possible"], 1, "Protection des équipements contre la dégradation."),
      q("Qu'est-ce que le cercle de Sinner?", ["Un équipement CIP", "La représentation de l'interdépendance des paramètres de nettoyage", "Une marque de détergent", "Un type de cuve"], 1, "Modèle conceptuel du nettoyage."),
      q("Combien de facteurs comporte le cercle de Sinner classique?", ["2", "3", "4 (Temps, Chimie, Mécanique, Température)", "5"], 2, "4 paramètres interdépendants."),
      q("Quel principe régit le cercle de Sinner?", ["Tous égaux toujours", "Si on diminue un paramètre, il faut compenser en augmentant un ou plusieurs autres", "Indépendants", "Température seule compte"], 1, "Compensation nécessaire entre facteurs."),
      q("Si on réduit le temps de nettoyage, que faut-il faire?", ["Rien", "Augmenter température et/ou concentration et/ou action mécanique", "Réduire la température", "Arrêter le CIP"], 1, "Équilibre par compensation des autres paramètres."),
      q("Pourquoi les 5 paramètres TACCT sont-ils interdépendants?", ["Par hasard", "Parce qu'ils contribuent tous à l'efficacité globale du nettoyage", "Indépendants en réalité", "Seulement 2 sont liés"], 1, "Synergie nécessaire pour un nettoyage optimal."),
      q("Quel paramètre ne doit jamais être négligé en CIP?", ["Uniquement le temps", "Uniquement la température", "Aucun des 5 paramètres TACCT", "Seule la chimie compte"], 2, "Tous les paramètres sont essentiels."),
      q("Pourquoi le contrôle par sondes et conductivimètre est-il essentiel?", ["Pour la documentation", "Pour garantir la concentration et la température correctes en temps réel", "Pour le coût", "Optionnel en réalité"], 1, "Vérification continue des paramètres critiques."),
      q("Comment la conception de l'équipement influence-t-elle le CIP?", ["Aucun impact", "Une bonne conception hygiénique améliore la couverture et réduit les zones mortes", "Complique le nettoyage", "Uniquement esthétique"], 1, "Design facilitant l'accès du liquide partout.")
    ]
  },
  {
    id: "materiaux",
    category: "CIP",
    title: "22. Les matériaux utilisés en brasserie",
    ficheRich: [
      {
        title: "Vue d'ensemble",
        items: [
          "Le choix du matériau pour les cuves et équipements est crucial car il influence : la résistance à la corrosion, la facilité de nettoyage, la durabilité, le goût de la bière, et le coût."
        ]
      },
      {
        title: "L'Acier avec revêtement",
        items: [
          "**Avantage** : Moins cher que l'inox.",
          "**Inconvénient majeur** : Si déchirure du revêtement → nid à bactéries qui s'installent et sont impossibles à déloger.",
          "**Problème** : Les micro-fissures dans le revêtement sont invisibles et créent des sources d'infections récurrentes.",
          "**Durabilité** : Moyenne à faible.",
          "**Recommandation** : ⚠️ À éviter pour usage professionnel intensif."
        ]
      },
      {
        title: "L'Aluminium",
        items: [
          "**Neutralité** : N'affecte pas le goût de la bière.",
          "**Protection** : Forme une couche d'oxyde protectrice en surface.",
          "**Coût** : Relativement économique.",
          "**Résistance aux acides** : Faible - les acides forts l'attaquent.",
          "**Résistance mécanique** : Mou, se déforme facilement.",
          "**Résistance au vide** : Mauvaise → risque de collapse (implosion).",
          "**Trous au niveau de la base** : Création de points d'infection.",
          "**Santé** : ⚠️ Liens suspectés entre aluminium et maladie d'Alzheimer.",
          "**Verdict** : ❌ Non recommandé pour un usage professionnel."
        ]
      },
      {
        title: "L'Inox (Acier inoxydable)",
        items: [
          "**Composition** : Acier allié contenant 17-20% de Chrome, 8-13% de Nickel, 2-3% de Molybdène.",
          "**Principe de protection** : La couche d'oxyde de chrome (film microscopique protecteur) se forme spontanément au contact de l'air et se régénère automatiquement si endommagée.",
          "**Inox 304** : Standard, alimentaire, le plus courant en brasserie.",
          "**Inox 316** : Contient Titane + Niobium, usage pharmaceutique, résistance accrue à la corrosion.",
          "**Entretien en cas de dommage** : Passivation mécanique (ponçage zone chauffée) ou passivation chimique (acide nitrique).",
          "**Signes de problème** : Changement de couleur (bleu, jaune) autour des soudures ou traces de rouille (contamination par du fer).",
          "**Danger du chlore chaud** : Crée des piqûres (pitting) → respecter température, pH, temps de contact, concentration.",
          "**Danger du fer** : Les éclats de fer font rouiller l'inox par contact → ne jamais utiliser d'outils en acier carbone sur l'inox.",
          "**Verdict** : ✅ Matériau de référence pour la brasserie professionnelle."
        ]
      },
      {
        title: "Tableau comparatif",
        items: [
          "**Résistance corrosion** : Acier revêtu ⭐, Aluminium ⭐⭐, Inox 304 ⭐⭐⭐⭐, Inox 316 ⭐⭐⭐⭐⭐",
          "**Facilité nettoyage** : Acier revêtu ⭐⭐, Aluminium ⭐⭐⭐, Inox 304 ⭐⭐⭐⭐⭐, Inox 316 ⭐⭐⭐⭐⭐",
          "**Durabilité** : Acier revêtu ⭐⭐, Aluminium ⭐⭐, Inox 304 ⭐⭐⭐⭐⭐, Inox 316 ⭐⭐⭐⭐⭐",
          "**Coût** : Acier revêtu ⭐⭐⭐⭐⭐, Aluminium ⭐⭐⭐⭐, Inox 304 ⭐⭐⭐, Inox 316 ⭐⭐",
          "**Recommandation** : Acier revêtu ❌, Aluminium ❌, Inox 304 ✅, Inox 316 ✅✅"
        ]
      }
    ],
    questions: [
      q("Quel est l'impact du choix des matériaux en brasserie?", ["Esthétique uniquement", "Influence corrosion, nettoyage, durabilité, goût et coût", "Pas d'importance", "Secondaire"], 1, "Le matériau affecte la qualité et les coûts opérationnels."),
      q("Quel est le principal inconvénient de l'acier avec revêtement?", ["Trop cher", "Si déchirure du revêtement → nid à bactéries impossible à déloger", "Impossible à nettoyer", "Rouille rapidement"], 1, "Les micro-fissures créent des sources d'infection."),
      q("Pourquoi l'acier revêtu présente-t-il un risque élevé d'infection?", ["Matériau poreux", "Les micro-fissures invisibles dans le revêtement abritent les bactéries", "Pas de risque", "Trop lisse"], 1, "Les bactéries s'y installent et sont impossibles à éradiquer."),
      q("Quelle est la recommandation pour l'acier revêtu en brasserie?", ["Excellent choix", "À privilégier", "À éviter pour usage professionnel intensif", "Standard de l'industrie"], 2, "Risque trop élevé pour la qualité."),
      q("Quel est l'avantage principal de l'aluminium?", ["Très résistant", "N'affecte pas le goût de la bière", "Durable indéfiniment", "Facile à souder"], 1, "Neutralité gustative partielle."),
      q("Quel est le problème majeur de l'aluminium en brasserie?", ["Trop cher", "Résistance aux acides faible et se déforme facilement", "Trop lourd", "Non disponible"], 1, "Faible résistance mécanique et chimique."),
      q("Quel risque l'aluminium présente-t-il avec le vide?", ["Aucun", "Collapse (implosion) en cas de mauvaise résistance au vide", "Expansion", "Corrosion"], 1, "Faible résistance structurale sous vide."),
      q("Quel problème l'aluminium crée-t-il au niveau de la base?", ["Rouille", "Création de trous et points d'infection", "Fuites rapides", "Porosité"], 1, "Points de faiblesse mécanique."),
      q("Quel lien de santé est associé à l'aluminium?", ["Allergie", "Liens suspectés avec maladie d'Alzheimer", "Aucun", "Gastrique"], 1, "Préoccupation de santé publique."),
      q("Quel est le verdict pour l'aluminium en brasserie?", ["Recommandé", "Non recommandé pour usage professionnel", "Neutre", "À tester"], 1, "Les désavantages surpassent les avantages."),
      q("Qu'est-ce qui compose principalement l'acier inoxydable?", ["Fer pur", "Chrome (17-20%), Nickel (8-13%), Molybdène (2-3%)", "Cuivre et étain", "Carbone seulement"], 1, "Alliage spécifique pour la protection."),
      q("Quel est le rôle du chrome dans l'inox?", ["Améliore la dureté", "Élément clé anti-corrosion créant une couche passivée", "Ajoute de la couleur", "Baisse le coût"], 1, "Film protecteur microscopique."),
      q("Qu'est-ce que la couche passivée?", ["Une peinture", "Couche d'oxyde de chrome qui se forme spontanément et se régénère", "Un revêtement appliqué", "Une soudure"], 1, "Barrière naturelle et auto-régénérante."),
      q("Comment se forme la couche passivée?", ["Manuellement", "Spontanément au contact de l'air", "Par application chimique", "Lors du chauffage"], 1, "Formation spontanée et continue."),
      q("Que se passe-t-il si la couche passivée est endommagée?", ["Rouille définitive", "Se régénère automatiquement au contact de l'air", "Nécessite remplacement", "Expansion"], 1, "Propriété d'auto-régénération."),
      q("Quel type d'inox est le plus courant en brasserie?", ["Inox 304", "Inox 316", "Inox 410", "Inox 430"], 0, "Standard alimentaire de référence."),
      q("Quel type d'inox offre une résistance accrue à la corrosion?", ["Inox 304", "Inox 316 (+ Titane + Niobium)", "Inox 410", "Inox 201"], 1, "Pour environnements hautement corrosifs."),
      q("Quelle est la passivation mécanique?", ["Utiliser des produits chimiques", "Poncer la zone chauffée avec un abrasif fin", "Appliquer une couche de peinture", "Utiliser du chlore"], 1, "Restauration mécanique de la surface."),
      q("Qu'est-ce que la passivation chimique?", ["Ponçage de la surface", "Traitement avec de l'acide fort (acide nitrique)", "Application de revêtement", "Chauffage intensif"], 1, "Restauration chimique de la couche d'oxyde."),
      q("Quel signe indique un problème de passivation?", ["Couleur normale", "Changement de couleur (bleu, jaune) ou traces de rouille", "Aspect lisse", "Brillance"], 1, "Couleur anormale indique compromission du film."),
      q("Que cause la contamination par du fer sur l'inox?", ["Aucun effet", "Fait rouiller l'inox par contact", "Améliore la brillance", "Renforce la corrosion"], 1, "Rupture locale de la passivation."),
      q("Pourquoi le chlore chaud est-il dangereux pour l'inox?", ["Aucun danger", "Crée des piqûres (pitting) dans le film d'oxyde", "Augmente la brillance", "Améliore la passivation"], 1, "Chlore attaque le film protecteur."),
      q("Quelles précautions prendre avec le chlore sur l'inox?", ["Aucune", "Respecter température, pH, temps de contact, concentration", "Utiliser concentré", "Pas de limite"], 1, "Contrôle strict des paramètres."),
      q("Peut-on utiliser des outils en acier carbone sur l'inox?", ["Oui, sans problème", "Non, les éclats de fer causent la rouille par contact", "Optionnel", "Seulement ponçage"], 1, "Protection de la surface contre la contamination."),
      q("Quel est le matériau de référence pour la brasserie?", ["Acier revêtu", "Aluminium", "Inox (304 ou 316)", "Acier carbone"], 2, "Standard de qualité professionnelle."),
      q("Quel inox privilégier pour une brasserie dans environnement très corrosif?", ["Inox 304", "Inox 316", "Acier revêtu", "Aluminium"], 1, "Meilleure résistance à la corrosion."),
      q("Quel matériau offre le meilleur compromis coût/performance?", ["Acier revêtu", "Inox 304", "Inox 316", "Aluminium"], 1, "Bon rapport qualité-prix."),
      q("Combien de degrés d'étoiles pour l'Inox 304 en résistance corrosion?", ["2 étoiles", "3 étoiles", "4 étoiles", "5 étoiles"], 2, "Très bonne résistance."),
      q("Combien de degrés d'étoiles pour l'Inox 316 en résistance corrosion?", ["2 étoiles", "3 étoiles", "4 étoiles", "5 étoiles"], 3, "Excellente résistance supérieure à 304."),
      q("Pourquoi l'Inox 316 coûte-t-il plus cher que l'Inox 304?", ["Extraction plus difficile", "Ajout de Titane + Niobium améliore la résistance", "Plus lourd", "Moins disponible"], 1, "Alliage plus complexe et performant.")
    ]
  },
  {
    id: "joints",
    category: "CIP",
    title: "23. Les joints et raccords",
    ficheRich: [
      {
        title: "Les joints d'étanchéité - Problématique",
        items: [
          "Les joints sont des points critiques car : ils sont en contact avec la bière, ils peuvent se dégrader avec le temps, les craquelures deviennent des nids à bactéries, ils peuvent donner un mauvais goût à la bière."
        ]
      },
      {
        title: "Types de joints",
        items: [
          "**Bleu (NBR - Nitrile)** : Bonne résistance aux huiles et graisses.",
          "**Noir (EPDM)** : Bonne résistance aux produits chimiques et températures.",
          "**Rouge (Silicone)** : Excellente résistance aux températures extrêmes."
        ]
      },
      {
        title: "Critères de choix des joints",
        items: [
          "**Résistance aux produits de nettoyage** : ⭐⭐⭐⭐⭐ - Critique",
          "**Résistance aux températures** : ⭐⭐⭐⭐⭐ - Critique",
          "**Résistance à l'usure** : ⭐⭐⭐⭐ - Très important",
          "**Compatibilité alimentaire** : ⭐⭐⭐⭐⭐ - Critique"
        ]
      },
      {
        title: "Bonnes pratiques pour les joints",
        items: [
          "✅ Inspecter régulièrement les joints pour détecter l'usure.",
          "✅ Remplacer dès les premiers signes d'usure.",
          "✅ Avoir des joints de rechange pour toutes les vannes.",
          "✅ L'acide péracétique dégrade les joints → rincer soigneusement après utilisation.",
          "✅ De plus en plus remplacés par des tuyaux inox ou plastique pour éviter les points faibles."
        ]
      },
      {
        title: "Les raccords - Standards de raccords",
        items: [
          "**SMS (Suédois)** : Très répandu, filetage fin.",
          "**DIN 11851 (Allemand)** : Standard européen, robuste, le plus utilisé en Europe.",
          "**MACON** : Connexion rapide."
        ]
      },
      {
        title: "Norme DIN 11851",
        items: [
          "**Standard le plus utilisé en Europe** pour la brasserie.",
          "**Conçu spécifiquement pour l'industrie alimentaire.**",
          "**Facilité de démontage** pour le nettoyage CIP.",
          "**Étanchéité fiable** garantie par design robuste.",
          "Critères de sélection : Compatibilité (tous du même standard), État de surface lisse, Facilité de nettoyage et démontage, Étanchéité adaptée au type."
        ]
      }
    ],
    questions: [
      q("Pourquoi les joints sont-ils critiques en brasserie?", ["Purement esthétiques", "Sont en contact avec la bière et peuvent créer des nids à bactéries", "Pas d'importance", "Secondaires"], 1, "Points faibles majeurs du circuit."),
      q("Quel problème les craquelures des joints créent-elles?", ["Aucun", "Deviennent des nids à bactéries impossibles à déloger", "Amélioration de l'étanchéité", "Augmentent la durabilité"], 1, "Source d'infection récurrente."),
      q("Quel impact l'usure des joints a-t-elle sur la bière?", ["Aucun", "Peut donner un mauvais goût à la bière", "Améliore le goût", "Impact minime"], 1, "Transmission de saveurs indésirables."),
      q("Quelle couleur représente le NBR (Nitrile)?", ["Noir", "Bleu", "Rouge", "Vert"], 1, "Code couleur standard pour joints."),
      q("Quel matériau est le NBR (Nitrile)?", ["Silicone", "EPDM", "Nitrile (NBR)", "Caoutchouc naturel"], 2, "Type le plus courant."),
      q("Qu'est-ce que le NBR offre comme résistance?", ["À l'alcool", "Aux huiles et graisses", "Aux températures extrêmes", "Au chlore"], 1, "Avantage principal du NBR."),
      q("Quelle couleur représente l'EPDM?", ["Bleu", "Noir", "Rouge", "Blanc"], 1, "Code couleur pour EPDM."),
      q("Quel matériau est l'EPDM?", ["Nitrile", "EPDM (éthylène-propylène)", "Silicone", "Caoutchouc butyle"], 1, "Résistance chimique et thermique."),
      q("À quoi l'EPDM est-il particulièrement résistant?", ["Aux huiles", "Aux produits chimiques et températures", "À l'usure", "Au chlore"], 1, "Avantages principaux de l'EPDM."),
      q("Quelle couleur représente le Silicone?", ["Bleu", "Noir", "Rouge", "Jaune"], 2, "Code couleur pour le silicone."),
      q("À quoi le silicone est-il particulièrement résistant?", ["Aux acides", "Aux températures extrêmes", "Aux huiles", "Au sel"], 1, "Avantage majeur du silicone."),
      q("Quel est le critère le plus important pour les joints?", ["Couleur", "Résistance aux produits de nettoyage et températures", "Coût", "Disponibilité"], 1, "Sécurité microbiologique."),
      q("Combien d'étoiles pour 'Résistance aux produits de nettoyage'?", ["2 étoiles", "3 étoiles", "5 étoiles", "4 étoiles"], 2, "Critique pour l'hygiène."),
      q("Combien d'étoiles pour 'Résistance aux températures'?", ["2 étoiles", "3 étoiles", "5 étoiles", "4 étoiles"], 2, "Critique pour la durabilité."),
      q("Combien d'étoiles pour 'Résistance à l'usure'?", ["2 étoiles", "3 étoiles", "5 étoiles", "4 étoiles"], 3, "Très important pour la longévité."),
      q("Combien d'étoiles pour 'Compatibilité alimentaire'?", ["2 étoiles", "3 étoiles", "5 étoiles", "4 étoiles"], 2, "Critique pour la sécurité alimentaire."),
      q("Quelle est la recommandation pour l'inspection des joints?", ["Jamais", "Régulièrement pour détecter l'usure", "Une fois par an", "Optionnel"], 1, "Maintenance préventive."),
      q("Quand faut-il remplacer les joints?", ["Jamais", "Dès les premiers signes d'usure", "Quand ils cassent", "Après 5 ans"], 1, "Avant que le problème n'aggrave."),
      q("Pourquoi avoir des joints de rechange?", ["Économies", "Réduction des temps d'arrêt de maintenance", "Esthétique", "Obligation légale"], 1, "Continuité opérationnelle."),
      q("Quel produit dégrade les joints?", ["La soude", "L'acide nitrique", "L'acide péracétique", "L'eau chaude"], 2, "Requiert rinçage soigné après."),
      q("Que faire après utilisation d'acide péracétique?", ["Rien", "Rincer soigneusement les joints", "Désinfecter à nouveau", "Laisser sécher"], 1, "Prévention de la dégradation."),
      q("Quelle est la tendance concernant les joints?", ["Augmentation de l'usage", "Remplacement par tuyaux inox ou plastique", "Plus de qualité", "Utilisation accrue"], 1, "Modernisation du design hygiénique."),
      q("Que signifie l'acronyme SMS?", ["Standard Manufacturing System", "Standard Mondial Suédois", "SMS - Standard de raccord suédois", "System Management Standard"], 2, "Origine suédoise."),
      q("Que signifie DIN 11851?", ["German Standard", "Norme alimentaire allemande pour raccords", "Data Information Network", "Dynamic Industrial Norm"], 1, "Standard européen."),
      q("Quel est le standard le plus utilisé en Europe?", ["SMS", "DIN 11851", "MACON", "ISO 1216"], 1, "Référence européenne."),
      q("Quel standard de raccord offre une connexion rapide?", ["SMS", "DIN 11851", "MACON", "Instantané"], 2, "Spécialité du MACON."),
      q("Pour quel secteur DIN 11851 a-t-il été conçu?", ["Chimie", "Industrie alimentaire", "Pétrole", "Construction"], 1, "Spécificités hygiéniques garanties."),
      q("Quel avantage DIN 11851 offre-t-il pour le nettoyage?", ["Pas de démontage", "Facilité de démontage pour nettoyage CIP", "Augmente la surface", "Réduit l'efficacité"], 1, "Accessibilité pour l'hygiène."),
      q("Qu'est-ce qui assure l'étanchéité en DIN 11851?", ["La pression", "Le design robuste et le joint adapté", "La température", "Le matériau seul"], 1, "Combinaison design-joint."),
      q("Quel est le critère critique lors du choix des raccords?", ["La couleur", "La compatibilité (tous du même standard)", "Le coût minimal", "L'esthétique"], 1, "Évite les incompatibilités.")
    ]
  },
  {
    id: "agentsNettoyage",
    category: "CIP",
    title: "24. Les agents de nettoyage",
    ficheRich: [
      {
        title: "Objectif du nettoyage",
        items: [
          "Retirer de la surface à traiter : résidus de brassage, dépôts (tartre, pierre de bière), protéines coagulées, résines de houblon, huiles et graisses, sels minéraux."
        ]
      },
      {
        title: "Principe fondamental",
        items: [
          "Passer à l'eau sous pression, idéalement chaude, le plus vite possible après la vidange de la cuve.",
          "Notamment pour les vannes qui ne peuvent pas être facilement nettoyées par CIP."
        ]
      },
      {
        title: "Caractéristiques d'un bon agent de nettoyage",
        items: [
          "**Haute solubilité** : Se dissout facilement dans l'eau.",
          "**Bon pouvoir nettoyant** : Efficace contre les salissures.",
          "**Efficace à basse température** : Économie d'énergie.",
          "**Haut pouvoir mouillant** : Additif diminuant la tension superficielle de l'eau.",
          "**Facilement rinçable** : Pas de résidus après rinçage.",
          "**Ne réagit pas avec les sels de l'eau** : Évite les dépôts calcaires.",
          "**Pas corrosif pour les cuves** : Préserve l'équipement.",
          "**Pas cher** : Économiquement viable.",
          "**Facile à utiliser** : Manipulation simple.",
          "**Ne pollue pas l'environnement** : Biodégradable.",
          "**Stable à l'oxygène** : Ne se dégrade pas au stockage."
        ]
      },
      {
        title: "Formes disponibles",
        items: [
          "**Poudre** : Stockage facile, longue conservation. Inconvénient : dosage moins précis.",
          "**Pâte** : Concentration élevée. Inconvénient : dissolution plus lente.",
          "**Liquide** : ✅ Dosage précis, dissolution immédiate. Inconvénient : plus volumineux à stocker.",
          "**Recommandation** : Le liquide est préféré car il se dose mieux et se dissout immédiatement."
        ]
      },
      {
        title: "Les nettoyants BASIQUES (alcalins)",
        items: [
          "**Produit principal** : Soude caustique (NaOH).",
          "**Concentration typique** : 2%.",
          "**Conductivité cible** : ~100 mS/cm.",
          "**Action** : Saponification des graisses, dissolution des protéines.",
          "**Efficacité** : Excellente contre les matières organiques.",
          "**Utilisation** : Peut être employée plusieurs fois, filtrer pour retirer les dépôts, ajouter de la soude concentrée quand la conductivité diminue."
        ]
      },
      {
        title: "Les nettoyants ACIDES",
        items: [
          "**Acide phosphorique** : Détartrage, élimination des dépôts minéraux.",
          "**Acide nitrique** : Passivation de l'inox, détartrage.",
          "**Action** : Dissolution des dépôts minéraux (tartre, pierre de bière), neutralisation des résidus de soude, passivation de l'inox."
        ]
      },
      {
        title: "Cycle de nettoyage recommandé",
        items: [
          "**Soude (2%)** : Élimine les matières organiques (graisses, protéines).",
          "**Acide** : Élimine les dépôts minéraux (tartre, pierre de bière).",
          "**Alternance recommandée** : Pour un nettoyage complet et régénération de la passivation."
        ]
      }
    ],
    questions: [
      q("Quel est l'objectif principal du nettoyage en brasserie?", ["Esthétique", "Retirer résidus, dépôts, protéines, résines, huiles et sels", "Améliorer le goût", "Stockage"], 1, "Hygiène et qualité microbiologique."),
      q("Qu'est-ce que le nettoyage doit retirer?", ["Uniquement la saleté visible", "Résidus, dépôts, protéines coagulées, résines, huiles, sels minéraux", "La couleur du malt", "La mousse"], 1, "Élimination complète des contaminants."),
      q("Quel est le principe fondamental du nettoyage?", ["Utiliser un produit chimique fort", "Eau sous pression, idéalement chaude, le plus vite possible après vidange", "Laisser reposer longtemps", "Température très basse"], 1, "Rapidité et efficacité thermique."),
      q("Pourquoi passer l'eau rapidement après la vidange?", ["Pas de raison", "Pour éviter que les résidus se dessèchent et collent", "Pour économiser de l'eau", "Obligation légale"], 1, "Prévention de l'adhésion des dépôts."),
      q("Pour quels équipements le nettoyage rapide est-il particulièrement important?", ["Grandes cuves", "Vannes qui ne peuvent pas être nettoyées par CIP", "Tout pareil", "Tuyaux seulement"], 1, "Points difficiles d'accès."),
      q("Qu'est-ce que la 'haute solubilité' d'un agent de nettoyage?", ["Couleur claire", "Se dissout facilement dans l'eau", "Odeur forte", "Prix bas"], 1, "Caractéristique essentielle."),
      q("Qu'est-ce que le 'pouvoir mouillant'?", ["La capacité à chauffer", "Additif diminuant la tension superficielle de l'eau", "La couleur du produit", "La conservation"], 1, "Améliore la pénétration."),
      q("Pourquoi un agent doit-il être 'facilement rinçable'?", ["Optionnel", "Pour éviter les résidus qui contaminent la bière", "Pour économiser de l'eau", "Esthétique"], 1, "Prévention de la contamination."),
      q("Quel problème peut créer un agent 'réactif avec les sels'?", ["Aucun", "Formation de dépôts calcaires (tartre)", "Augmente l'efficacité", "Améliore la rincibilité"], 1, "Encrassement résiduel."),
      q("Pourquoi un agent ne doit-il pas être 'corrosif'?", ["Pas de raison", "Pour préserver l'équipement (inox, joints)", "C'est une obligation légale", "Économie de produit"], 1, "Protection des investissements."),
      q("Qu'est-ce qu'un agent 'stable à l'oxygène'?", ["Résiste à la chaleur", "Ne se dégrade pas au stockage", "Coûte moins cher", "Se dissout mieux"], 1, "Longévité en stock."),
      q("Quel est l'avantage de la forme 'poudre'?", ["Dosage précis", "Stockage facile et longue conservation", "Dissolution immédiate", "Volume réduit"], 1, "Logistique avantageuse."),
      q("Quel est l'inconvénient de la forme 'poudre'?", ["Trop volumineuse", "Dosage moins précis", "Se dissout trop vite", "Trop cher"], 1, "Imprécision dosage."),
      q("Quel est l'avantage de la forme 'pâte'?", ["Dissolution immédiate", "Concentration élevée", "Dosage facile", "Pas de volume"], 1, "Densité chimique."),
      q("Quel est l'inconvénient de la forme 'pâte'?", ["Trop chère", "Dissolution plus lente", "Trop diluée", "Instable"], 1, "Temps de dissolution."),
      q("Quel est l'avantage principal de la forme 'liquide'?", ["Moins cher", "Dosage précis et dissolution immédiate", "Longue conservation", "Faible volume"], 1, "Praticité opérationnelle."),
      q("Quel est l'inconvénient de la forme 'liquide'?", ["Cher", "Plus volumineux à stocker", "Se solidifie", "Difficile à doser"], 1, "Logistique encombrante."),
      q("Quelle forme de nettoyant est recommandée?", ["Poudre", "Pâte", "Liquide (dosage précis et dissolution immédiate)", "Toutes égales"], 2, "Meilleure efficacité pratique."),
      q("Quel est le nettoyant basique principal?", ["Acide citrique", "Soude caustique (NaOH)", "Acide phosphorique", "Savon"], 1, "Standard alcalin de référence."),
      q("Quelle est la concentration typique de soude en nettoyage?", ["0.5%", "2%", "5%", "10%"], 1, "Dosage standard."),
      q("Quelle est la conductivité cible pour la soude?", ["50 mS/cm", "100 mS/cm", "150 mS/cm", "200 mS/cm"], 1, "Mesure de concentration."),
      q("Quel est l'effet de la soude sur les graisses?", ["Aucun", "Saponification (conversion en savons)", "Les durcit", "Les dissout partiellement"], 1, "Réaction chimique de nettoyage."),
      q("Quel est l'effet de la soude sur les protéines?", ["Les préserve", "Les dissout et les élimine", "Les durcit", "Les colore"], 1, "Dénaturation protéique."),
      q("Combien de fois peut-on utiliser la soude?", ["Une seule", "Plusieurs fois (filtrer et réutiliser)", "Jamais", "Dépend du malt"], 1, "Réutilisabilité économique."),
      q("Que faire quand la conductivité de la soude diminue?", ["Ajouter de l'eau", "Ajouter de la soude concentrée pour restaurer la concentration", "Remplacer complètement", "Continuer sans ajustement"], 1, "Maintenance du dosage."),
      q("Quel acide est utilisé pour le détartrage?", ["Acide acétique", "Acide phosphorique ou nitrique", "Acide sulfurique", "Acide citrique"], 1, "Standards de détartrage."),
      q("Quel est l'effet des acides sur les dépôts minéraux?", ["Aucun", "Dissolution des tartre et pierre de bière", "Renforcement", "Coloration"], 1, "Chimie acide-base."),
      q("Quel acide permet la passivation de l'inox?", ["Phosphorique", "Nitrique", "Acétique", "Citrique"], 1, "Régénération du film d'oxyde."),
      q("Pourquoi alterner soude et acide?", ["Pas de raison", "Soude élimine matière organique, acide élimine minéraux et régénère inox", "Obligation légale", "Économie de produit"], 1, "Nettoyage complet et entretien."),
      q("Qu'élimine la soude dans le cycle de nettoyage?", ["Tartre", "Matières organiques (graisses, protéines)", "Sels minéraux", "Couleur"], 1, "Cibles du nettoyant alcalin."),
      q("Qu'élimine l'acide dans le cycle de nettoyage?", ["Graisses", "Dépôts minéraux (tartre, pierre de bière)", "Protéines", "Mousse"], 1, "Cibles du nettoyant acide.")
    ]
  },
  {
    id: "agentsDesinfection",
    category: "CIP",
    title: "25. Les agents de désinfection",
    ficheRich: [
      {
        title: "Différence nettoyage vs désinfection",
        items: [
          "**Nettoyage** : Objectif = retirer les salissures. Cible = matière organique et minérale. Ordre = en premier. Surface = sale → propre.",
          "**Désinfection** : Objectif = tuer les micro-organismes. Cible = bactéries, levures, virus, spores. Ordre = après le nettoyage. Surface = propre → stérile.",
          "⚠️ **On ne désinfecte pas une surface sale !** Le nettoyage doit toujours précéder la désinfection."
        ]
      },
      {
        title: "Caractéristiques d'un bon désinfectant",
        items: [
          "Mêmes caractéristiques qu'un agent de nettoyage.",
          "PLUS : doit détruire tous les micro-organismes présents.",
          "Spectre d'action le plus large possible (bactéries, levures, virus, champignons, spores)."
        ]
      },
      {
        title: "Les HALOGÈNES (Chlorés)",
        items: [
          "**Produit principal** : Hypochlorite de soude (eau de Javel).",
          "**Mode d'action** : Pénètre les cellules et détruit les acides aminés essentiels.",
          "**Spectre** : Très large (bactéries, levures, virus, champignons, spores).",
          "**Avantages** : Très efficace, économique, large spectre.",
          "**Inconvénients** : ⚠️ Le chlore chaud crée des piqûres (pitting) dans l'inox, odeur forte, peut laisser des résidus."
        ]
      },
      {
        title: "Les OXYDANTS",
        items: [
          "**Produit principal** : Acide péracétique.",
          "**Concentration typique** : 0.1 - 0.5%.",
          "**Mode d'action** : Réagit avec l'oxygène et détruit les parois cellulaires.",
          "**Dégradation** : En acide acétique, oxygène et eau (inoffensifs).",
          "**Avantages** : Très efficace, se dégrade en produits inoffensifs, pas de rinçage obligatoire (à faible concentration), efficace à froid.",
          "**Inconvénients** : ⚠️ Dégrade les joints à force de contact répété, odeur de vinaigre, plus cher que la Javel."
        ]
      },
      {
        title: "Les AMMONIUMS QUATERNAIRES",
        items: [
          "**Type** : Tensioactifs cationiques.",
          "**Mode d'action** : Bactéricide de surface.",
          "**Spectre** : Plus limité que halogènes et oxydants.",
          "**Avantages** : Pas de corrosion, action résiduelle.",
          "**Inconvénients** : Spectre plus étroit, moins efficace contre les spores."
        ]
      },
      {
        title: "Tableau comparatif des désinfectants",
        items: [
          "**Hypochlorite** : Efficacité ⭐⭐⭐⭐⭐, Spectre très large, Corrosion inox ⚠️ À chaud, Impact joints ✅ Faible, Coût ⭐⭐⭐⭐⭐, Rinçage obligatoire.",
          "**Acide péracétique** : Efficacité ⭐⭐⭐⭐⭐, Spectre très large, Corrosion inox ✅ Faible, Impact joints ⚠️ Dégradation, Coût ⭐⭐⭐, Rinçage optionnel.",
          "**Ammonium quaternaire** : Efficacité ⭐⭐⭐, Spectre moyen, Corrosion inox ✅ Non, Impact joints ✅ Faible, Coût ⭐⭐⭐⭐, Rinçage obligatoire."
        ]
      },
      {
        title: "Points d'attention - Questions à poser",
        items: [
          "**Quel est le but du produit ?** → Nettoyer OU désinfecter",
          "**Quelle est la concentration ?** → Respecter les dosages",
          "**Quelle est la température ?** → Adapter selon le produit",
          "**Quel matériau sera en contact ?** → Vérifier la compatibilité",
          "**Y a-t-il des interactions néfastes ?** → Ne pas mélanger les produits"
        ]
      }
    ],
    questions: [
      q("Quel est l'objectif du nettoyage?", ["Tuer les microbes", "Retirer les salissures", "Colorer la surface", "Améliorer l'odeur"], 1, "Élimination mécanique et chimique."),
      q("Quel est l'objectif de la désinfection?", ["Retirer la saleté", "Tuer les micro-organismes", "Rincer l'équipement", "Chauffer la surface"], 1, "Destruction biologique."),
      q("Quel est le résultat du nettoyage?", ["Surface stérile", "Surface propre", "Surface brillante", "Surface lisse"], 1, "Propreté visuelle et matérielle."),
      q("Quel est le résultat de la désinfection?", ["Surface propre", "Surface stérile (propre + sans microbes)", "Surface sèche", "Surface chaude"], 1, "Absence microbiologique."),
      q("En quel ordre faire nettoyage et désinfection?", ["Désinfection d'abord", "Nettoyage d'abord, puis désinfection", "Simultané", "N'importe quel ordre"], 1, "Séquence logique obligatoire."),
      q("Peut-on désinfecter une surface sale?", ["Oui, c'est équivalent", "Non, le nettoyage doit précéder la désinfection", "Seulement avec chlore", "Optionnel"], 1, "Fondamental de l'hygiène."),
      q("Pourquoi ne pas désinfecter une surface sale?", ["Coût élevé", "Le désinfectant est inactivé par la matière organique", "C'est interdit", "Sans raison particulière"], 1, "Chimie inorganique des interactions."),
      q("Quel est le spectre d'action du nettoyage?", ["Bactéries uniquement", "Matière organique et minérale", "Virus seulement", "Spores"], 1, "Cibles du nettoyant."),
      q("Quel est le spectre d'action de la désinfection?", ["Graisses", "Bactéries, levures, virus, champignons, spores", "Tartre seul", "Minéraux"], 1, "Cibles du désinfectant."),
      q("Qu'est-ce que l'hypochlorite de soude?", ["Acide fort", "Eau de Javel (désinfectant chloré)", "Détergent", "Savon"], 1, "Halogène le plus courant."),
      q("Quel est le mode d'action du chlore?", ["Dilution", "Pénètre les cellules et détruit les acides aminés essentiels", "Chauffage", "Absorption"], 1, "Mécanisme du désinfectant."),
      q("Quel est le spectre du chlore?", ["Limité", "Très large (bactéries, levures, virus, champignons, spores)", "Seulement bactéries", "Uniquement virus"], 1, "Large couverture antimicrobienne."),
      q("Quel est un avantage du chlore?", ["Très cher", "Très efficace, économique, large spectre", "Corrosif toujours", "Mauvais goût"], 1, "Efficacité et coût."),
      q("Quel est un inconvénient majeur du chlore chaud?", ["Inefficace", "Crée des piqûres (pitting) dans l'inox", "Trop cher", "Pas d'odeur"], 1, "Corrosion spécifique."),
      q("Quel autre inconvénient a le chlore?", ["Trop efficace", "Odeur forte et résidus possibles", "Pas de couleur", "Gratuit"], 1, "Effets secondaires désagréables."),
      q("Quel est le produit oxydant principal?", ["Eau de Javel", "Acide péracétique", "Ammonium quaternaire", "Alcool"], 1, "Standard des oxydants."),
      q("Quelle est la concentration typique d'acide péracétique?", ["1-2%", "0.1-0.5%", "5%", "10%"], 1, "Dosage standard."),
      q("Quel est le mode d'action de l'acide péracétique?", ["Acide fort", "Réagit avec l'oxygène et détruit les parois cellulaires", "Chaleur", "Électrolyse"], 1, "Mécanisme oxydatif."),
      q("En quoi se dégrade l'acide péracétique?", ["Chlore", "Acide acétique, oxygène et eau (inoffensifs)", "Alcool", "Peroxyde"], 1, "Produits finaux bénins."),
      q("Quel est un avantage de l'acide péracétique?", ["Très bon marché", "Très efficace, biodégradable, efficace à froid, pas de rinçage obligatoire", "Odeur agréable", "Corrosif"], 1, "Efficacité et sécurité."),
      q("Quel inconvénient l'acide péracétique a-t-il avec les joints?", ["Aucun", "Dégrade les joints à force de contact répété", "Renforce les joints", "Imperceptible"], 1, "Problème d'usure."),
      q("Qu'est-ce qu'un ammonium quaternaire?", ["Sel acide", "Tensioactif cationique", "Oxydant fort", "Halogène"], 1, "Classification chimique."),
      q("Quel est le mode d'action des ammoniums quaternaires?", ["Pénétration cellulaire", "Bactéricide de surface", "Oxydation", "Acidification"], 1, "Action superficielle."),
      q("Quel est le spectre des ammoniums quaternaires?", ["Très large", "Plus limité que autres désinfectants", "Seulement levures", "Uniquement bactéries"], 1, "Couverture restreinte."),
      q("Quel avantage les ammoniums quaternaires offrent-ils?", ["Très bon marché", "Pas de corrosion, action résiduelle", "Forte odeur", "Rapides à agir"], 1, "Non-corrosif et persistant."),
      q("Quel inconvénient majeur ont les ammoniums quaternaires?", ["Cher", "Spectre étroit, moins efficace contre spores", "Trop efficace", "Dangereux"], 1, "Efficacité limitée."),
      q("Combien d'étoiles pour efficacité hypochlorite?", ["2", "3", "5 étoiles", "4"], 2, "Très efficace."),
      q("Combien d'étoiles pour efficacité acide péracétique?", ["2", "3", "5 étoiles", "4"], 2, "Très efficace."),
      q("Combien d'étoiles pour efficacité ammonium quaternaire?", ["2", "3 étoiles", "5", "4"], 1, "Efficacité moyenne."),
      q("Quel désinfectant ne provoque pas de corrosion?", ["Chlore chaud", "Acide péracétique et ammonium quaternaire", "Tous corrosifs", "Aucun"], 1, "Non-corrosifs."),
      q("Quel point d'attention est crucial avant d'utiliser un produit?", ["La couleur", "Quel est le but (nettoyer OU désinfecter)?", "Le prix", "L'odeur"], 1, "Usage correct du produit.")
    ]
  },
  {
    id: "cipInstallation",
    category: "CIP",
    title: "26. Le système CIP - Installation et fonctionnement",
    ficheRich: [
      {
        title: "Composants d'une installation CIP",
        items: [
          "**Cuve NEP/CIP** : Stocke les solutions de nettoyage (centrale).",
          "**Sonde de niveau** : Contrôle le volume de liquide (sécurité).",
          "**Sonde de concentration** : Mesure la concentration en produit (qualité).",
          "**Pompe propulseuse** : Envoie le liquide vers la cuve (pression).",
          "**Boule d'arrosage** : Projette le liquide sur toutes les surfaces (couverture).",
          "**Vanne vidange cuve** : Permet l'évacuation (contrôle).",
          "**Conductivimètre** : Vérifie le rinçage par conductivité de l'eau (contrôle qualité).",
          "**Pompe retour** : Récupère le liquide pour recyclage (économie).",
          "**Ligne égout** : Évacuation des eaux usées (sortie)."
        ]
      },
      {
        title: "Configuration du circuit fermé CIP",
        items: [
          "La cuve NEP/CIP stocke les solutions.",
          "La sonde de niveau contrôle le remplissage.",
          "La sonde de concentration mesure le dosage.",
          "La pompe propulseuse envoie le liquide par la ligne envoi.",
          "La boule d'arrosage projette le liquide sur la cuve à nettoyer.",
          "Le liquide usé retourne par la ligne retour via la pompe retour.",
          "Le conductivimètre contrôle la qualité du rinçage.",
          "Évacuation final par la ligne égout."
        ]
      },
      {
        title: "Méthodes de nettoyage",
        items: [
          "**Circuit fermé (CIP classique)** : Le liquide circule en boucle. Peut être 'mou' (basse pression) ou 'dur' (haute pression). Économique en eau et produits.",
          "**Cuve de trempage** : Pour les petites pièces (vannes, joints, raccords). Attention : changer le bain tous les 15 jours ou en cas de doute. Bien rincer les pièces avant remise en service.",
          "**Acide péracétique en trempage** : Prévoir des joints de rechange car l'acide péracétique les dégrade."
        ]
      },
      {
        title: "Étapes d'un cycle CIP standard",
        items: [
          "**Étape 1 - Rinçage initial** (5 min, eau chaude + froide) : Éliminer les gros résidus, économiser le détergent.",
          "**Étape 2 - Vidange complète** : Évacuer l'eau de rinçage.",
          "**Étape 3 - Détergent nettoyant** (30-60 min, soude 2%) : Dissoudre les matières organiques.",
          "**Étape 4 - Rinçage à l'eau** (5-10 min) : Éliminer le détergent.",
          "**Étape 5 - Désinfection + vidange** (15 min) : Tuer les micro-organismes restants."
        ]
      },
      {
        title: "Paramètres critiques du CIP",
        items: [
          "**Température** : Eau chaude rinçage initial et détergent (améliore efficacité).",
          "**Concentration du détergent** : 2% NaOH (~100 mS/cm conductivité).",
          "**Durée détergent** : 30-60 minutes pour dissolution complète.",
          "**Couverture** : 100% de la surface via boule d'arrosage bien positionnée.",
          "**Pression/débit** : Adapté selon circuit (mou ou dur) et équipement.",
          "**Rinçage final** : Vérifier conductivité < 10 mS/cm pour élimination complète des résidus."
        ]
      }
    ],
    questions: [
      q("Quel est le rôle de la cuve NEP/CIP?", ["Nettoyage des cuves", "Stockage des solutions de nettoyage", "Fermentation", "Refroidissement"], 1, "Centrale du système."),
      q("Quelle sonde contrôle le volume de liquide?", ["Température", "Sonde de niveau", "Conductivité", "Pression"], 1, "Sécurité du remplissage."),
      q("Quelle sonde mesure la concentration en produit?", ["Niveau", "Température", "Sonde de concentration", "pH"], 2, "Qualité du nettoyage."),
      q("Quel est le rôle de la pompe propulseuse?", ["Filtre le liquide", "Envoie le liquide vers la cuve à nettoyer", "Refroidit", "Mesure"], 1, "Circulation principale."),
      q("Quel est le rôle de la boule d'arrosage?", ["Filtre", "Projette le liquide sur toutes les surfaces", "Mesure concentration", "Vidange"], 1, "Couverture et action mécanique."),
      q("Quel est le rôle du conductivimètre en CIP?", ["Chauffer", "Vérifie le rinçage par conductivité de l'eau", "Filtrer", "Mixer"], 1, "Contrôle qualité du rinçage."),
      q("Quel est le rôle de la pompe retour?", ["Chauffer", "Récupère le liquide pour recyclage", "Filtrer", "Mixer"], 1, "Réutilisation économique."),
      q("Qu'est-ce qu'un circuit fermé en CIP?", ["Eau unique", "Liquide circule en boucle (mou ou dur)", "Ouvert à l'air", "Sans recyclage"], 1, "Configuration classique."),
      q("Quel est l'avantage du circuit fermé?", ["Haute température", "Économique en eau et produits", "Très rapide", "Silencieux"], 1, "Efficacité financière."),
      q("Qu'est-ce qu'un nettoyage 'mou' en CIP?", ["Température basse", "Basse pression", "Sans détergent", "Rapide"], 1, "Configuration douce."),
      q("Qu'est-ce qu'un nettoyage 'dur' en CIP?", ["Température élevée", "Haute pression", "Avec acide", "Concentration forte"], 1, "Configuration vigoureuse."),
      q("Pour quoi utilise-t-on une cuve de trempage?", ["Grandes cuves", "Petites pièces (vannes, joints, raccords)", "Tuyaux", "Filtres"], 1, "Pièces difficiles d'accès."),
      q("Combien de temps conserver le bain de trempage?", ["1 mois", "15 jours ou en cas de doute", "3 mois", "Indéfiniment"], 1, "Efficacité du bain."),
      q("Que faire avec les pièces après trempage?", ["Les mettre directement en production", "Bien les rincer avant remise en service", "Les sécher à l'air", "Les stocker"], 1, "Élimination des résidus."),
      q("Quel produit dégrade les joints lors du trempage?", ["Soude", "Acide péracétique", "Chlore", "Alcool"], 1, "Usure matériau."),
      q("Quelle précaution prendre avec l'acide péracétique?", ["Augmenter concentration", "Prévoir des joints de rechange", "Utiliser plus longtemps", "Température maximale"], 1, "Maintenance préventive."),
      q("Combien de temps dure le rinçage initial?", ["15 minutes", "5 minutes", "30 minutes", "1 minute"], 1, "Étape 1 du cycle."),
      q("Quel est l'objectif du rinçage initial?", ["Désinfecter", "Éliminer gros résidus et économiser détergent", "Détartrer", "Chauffer"], 1, "Préparation efficace."),
      q("Quelle est la durée typique du détergent en CIP standard?", ["10 minutes", "15-30 minutes", "2 heures", "5 minutes"], 1, "Standard industriel brassicole."),
      q("Quelle concentration de soude utiliser en CIP?", ["0.5%", "2%", "5%", "10%"], 1, "Standard de nettoyage."),
      q("Quelle conductivité cible pour 2% NaOH?", ["50 mS/cm", "100 mS/cm", "150 mS/cm", "200 mS/cm"], 1, "Mesure de concentration."),
      q("Combien de temps pour le rinçage à l'eau?", ["1-3 minutes", "5-10 minutes", "20 minutes", "30 minutes"], 1, "Élimination du détergent."),
      q("Combien de temps pour la désinfection?", ["5 minutes", "15 minutes", "45 minutes", "1 heure"], 1, "Stérilisation finale."),
      q("Quel est l'ordre correct du cycle CIP?", ["Détergent, rinçage, désinfection", "Rinçage, détergent, rinçage, désinfection", "Désinfection, détergent, rinçage", "Variable"], 1, "Séquence logique."),
      q("Pourquoi commencer par un rinçage?", ["Optionnel", "Élimine gros résidus et économise détergent", "Obligation légale", "Améliore odeur"], 1, "Économie et efficacité."),
      q("Quel paramètre influence le plus l'efficacité?", ["Couleur", "Température, concentration, durée, couverture, pression", "Odeur", "Coût"], 1, "Facteurs multiples critiques."),
      q("Quelle conductivité indique fin du rinçage?", ["100 mS/cm", "< 10 mS/cm", "50 mS/cm", "200 mS/cm"], 1, "Pureté de l'eau de rinçage."),
      q("Quelle température utiliser au rinçage initial?", ["Froide uniquement", "Chaude + froide", "Brûlante", "Ambiante"], 1, "Efficacité thermique."),
      q("Quel est l'objectif du cycle CIP complet?", ["Rapidité", "Nettoyage complet + désinfection", "Économies", "Volume maximum"], 1, "Hygiène complète."),
      q("Peut-on sauter une étape du cycle CIP?", ["Oui", "Non, toutes les étapes sont nécessaires", "Seulement la désinfection", "Seulement le rinçage"], 1, "Intégrité du protocole.")
    ]
  },
  {
    id: "protocoleFermenteur",
    category: "CIP",
    title: "27. Protocole de nettoyage d'un fermenteur",
    ficheRich: [
      {
        title: "Contexte d'importance critique",
        items: [
          "Le fermenteur est l'équipement le plus critique en termes d'hygiène car :",
          "La bière y séjourne longtemps (fermentation active 7-14 jours).",
          "Les levures y sont actives et peuvent être contaminées.",
          "Le contact prolongé augmente les risques d'infection.",
          "Une contamination du fermenteur affecte toute la production ultérieure."
        ]
      },
      {
        title: "Étape 1 : Pré-rinçage à l'eau chaude",
        items: [
          "**Température** : 80°C.",
          "**Source** : Cuve d'empâtage (eau chaude de brassage).",
          "**Durée** : 5 minutes.",
          "**Méthode** : Envoi par pompe dans le fermenteur.",
          "**Objectif** : Ramollir et éliminer les résidus de levure et de houblon."
        ]
      },
      {
        title: "Étape 2 : Nettoyage à la soude",
        items: [
          "**Produit** : Soude caustique (NaOH).",
          "**Concentration** : 2%.",
          "**Durée** : 20 minutes.",
          "**Circulation** : 100% du circuit (fermenteur et tuyauterie).",
          "**Objectif** : Dissoudre les protéines, graisses et résidus organiques."
        ]
      },
      {
        title: "Étape 3 : Vidange",
        items: [
          "**Méthode** : Par le fond du fermenteur (via vanne de vidange).",
          "**Vérification** : S'assurer que tout le liquide est évacué complètement.",
          "**Objectif** : Éliminer la soude et les salissures dissoutes."
        ]
      },
      {
        title: "Étape 4 : Rinçage à l'eau froide",
        items: [
          "**Température** : Froide (eau de ville).",
          "**Durée** : Minimum 5 minutes (adapter selon conductivité).",
          "**Critère d'arrêt** : Ne plus sentir la soude.",
          "**Contrôle** : Conductivimètre pour retour à conductivité eau normale.",
          "**Objectif** : Éliminer totalement les résidus de soude."
        ]
      },
      {
        title: "Étape 5 : Désinfection",
        items: [
          "**Produit** : Acide péracétique.",
          "**Concentration** : 0.1-0.5%.",
          "**Température** : 20°C (eau froide).",
          "**Durée** : 15 minutes.",
          "**Objectif** : Éliminer tous les micro-organismes restants (bactéries, levures sauvages, virus)."
        ]
      },
      {
        title: "Point important : l'échangeur à plaques",
        items: [
          "**L'échangeur à plaques** et **le tuyau de remplissage** vers le fermenteur doivent être mis dans la boucle CIP.",
          "Laisser l'échangeur **rempli de désinfectant** jusqu'à ce que la bière soit refroidie.",
          "**Garantie** : Tout le circuit est stérile au moment du transfert du moût.",
          "**Timing critique** : L'échangeur remplit d'acide péracétique protège le circuit pendant le refroidissement."
        ]
      },
      {
        title: "Schéma simplifié de la brasserie",
        items: [
          "**Empâtage → Filtration → Fermentation/Maturation**",
          "Chaque section nécessite son propre protocole de nettoyage adapté.",
          "Empâtage : Nettoyage du moût résiduel, cuivre/équipement.",
          "Filtration : Nettoyage du filtre à chaud rapidement, plaques de filtration.",
          "Fermentation : Protocole détaillé ci-dessus (5 étapes), échangeur critique."
        ]
      }
    ],
    questions: [
      q("Pourquoi le fermenteur est-il critique en hygiène?", ["Grande capacité", "La bière y séjourne longtemps avec levures actives", "Petit volume", "Facilité de nettoyage"], 1, "Contact prolongé = risque élevé."),
      q("Combien de temps la bière séjourne-t-elle en fermenteur?", ["2-3 jours", "7-14 jours (fermentation active)", "1 mois", "3 mois"], 1, "Période critique."),
      q("Quelle est la température du pré-rinçage?", ["20°C", "60°C", "80°C", "100°C"], 2, "Eau chaude de brassage."),
      q("D'où provient l'eau chaude du pré-rinçage?", ["Cuve de refroidissement", "Cuve d'empâtage", "Cuve de désinfection", "Cuve de stockage"], 1, "Récupération d'énergie."),
      q("Combien de temps dure le pré-rinçage?", ["2 minutes", "5 minutes", "10 minutes", "20 minutes"], 1, "Étape 1 du protocole."),
      q("Quel est l'objectif du pré-rinçage?", ["Désinfecter", "Ramollir et éliminer résidus levure et houblon", "Refroidir", "Changer la couleur"], 1, "Préparation du fermenteur."),
      q("Quel produit utilise-t-on pour le nettoyage fermenteur?", ["Acide péracétique", "Soude caustique (NaOH)", "Chlore", "Alcool"], 1, "Nettoyant basique standard."),
      q("Quelle concentration de soude pour le fermenteur?", ["1%", "2%", "5%", "10%"], 1, "Dosage standard de nettoyage."),
      q("Combien de temps circule la soude?", ["10 minutes", "20 minutes", "30 minutes", "1 heure"], 1, "Étape 2 du protocole."),
      q("Quel pourcentage du circuit doit être couvert par soude?", ["50%", "75%", "100% (fermenteur + tuyauterie)", "Variable"], 2, "Couverture complète."),
      q("Quel est l'effet de la soude sur les protéines?", ["Les renforce", "Les dissout et les élimine", "Les colore", "Les préserve"], 1, "Nettoyage efficace."),
      q("Quel est l'effet de la soude sur les graisses?", ["Les augmente", "Les saponifie et les élimine", "Les durcit", "Aucun"], 1, "Chimie alcaline."),
      q("Comment s'effectue la vidange du fermenteur?", ["Par le haut avec siphon", "Par le fond via vanne de vidange", "Par la tuyauterie", "Par débordement"], 1, "Évacuation complète."),
      q("Quel est l'objectif de la vidange?", ["Remplir le réservoir", "Éliminer soude et salissures dissoutes", "Refroidir", "Agiter le contenu"], 1, "Étape 3 du protocole."),
      q("Quelle est la température du rinçage à l'eau froide?", ["Ambiante", "Eau de ville (froide)", "80°C", "60°C"], 1, "Rinçage économique."),
      q("Quel est le critère d'arrêt du rinçage?", ["5 minutes fixes", "Ne plus sentir la soude, conductivité normale", "10 minutes", "À l'odeur"], 1, "Vérification complète."),
      q("Quel outil mesure la fin du rinçage?", ["Thermomètre", "Conductivimètre", "pH-mètre", "Turbidimètre"], 1, "Conductivité eau < soude."),
      q("Quelle conductivité indique fin du rinçage?", ["100 mS/cm", "Retour à conductivité eau normale", "50 mS/cm", "200 mS/cm"], 1, "Pureté de l'eau."),
      q("Quel désinfectant utilise-t-on pour fermenteur?", ["Eau de Javel", "Acide péracétique", "Ammonium quaternaire", "Alcool"], 1, "Oxydant de référence."),
      q("Quelle concentration d'acide péracétique?", ["0.05%", "0.1-0.5%", "1%", "2%"], 1, "Dosage désinfection."),
      q("Quelle température pour la désinfection?", ["Chaude", "Froide (eau froide, 20°C)", "Tiède", "Variable"], 1, "Économie énergétique."),
      q("Combien de temps dure la désinfection?", ["5 minutes", "15 minutes", "30 minutes", "1 heure"], 1, "Étape 5 du protocole."),
      q("Quel est l'objectif de la désinfection?", ["Refroidissement", "Éliminer tous micro-organismes restants", "Rinçage", "Stockage"], 1, "Stérilisation finale."),
      q("Pourquoi l'échangeur à plaques est-il critique?", ["Trop cher", "Doit être rempli de désinfectant jusqu'au refroidissement du moût", "Facile à nettoyer", "Optionnel"], 1, "Stérilité du transfert."),
      q("Comment traiter le tuyau de remplissage vers fermenteur?", ["Ignorer", "Mettre dans la boucle et remplir de désinfectant", "Nettoyer après", "Inspecter visuellement"], 1, "Inclusion dans CIP."),
      q("Combien de temps laisser désinfectant en échangeur?", ["Pendant chauffage", "Jusqu'au refroidissement du moût", "5 minutes", "Immédiatement après"], 1, "Couverture de la période critique."),
      q("Quel est le résultat d'une bonne désinfection échangeur?", ["Apparence brillante", "Circuit stérile au transfert du moût", "Odeur agréable", "Couleur claire"], 1, "Hygiène garantie."),
      q("Quel équipement brasse-t-on?", ["Filtration uniquement", "Empâtage, Filtration, Fermentation", "Fermentation seulement", "Refroidissement seul"], 1, "Schéma complet brasserie."),
      q("Nécessite-t-on le même protocole pour tous?", ["Oui exactement", "Non, chaque section a son propre protocole adapté", "Variable", "Un seul suffit"], 1, "Protocoles spécifiques."),
      q("Quel est le risque d'une contamination du fermenteur?", ["Peu important", "Affecte toute la production ultérieure de bière", "Minime", "Seulement un batch"], 1, "Cascade d'infection.")
    ]
  },
  {
    id: "bonnesPratiquesCIP",
    category: "CIP",
    title: "28. Points de vigilance et bonnes pratiques CIP",
    ficheRich: [
      {
        title: "Danger 1 : Ne pas mélanger les produits",
        items: [
          "**Soude + Acide** : Réaction violente, risque de projections.",
          "**Javel + Acide** : Dégagement de chlore gazeux (toxique - ⚠️ DANGER MORTEL).",
          "**Différents désinfectants** : Neutralisation, inefficacité du nettoyage.",
          "✅ **RÈGLE D'OR** : Toujours rincer entre deux produits différents."
        ]
      },
      {
        title: "Danger 2 : Réaction Soude + CO₂",
        items: [
          "**Phénomène** : La soude réagit avec le CO₂ résiduel du fermenteur.",
          "**Conséquence** : Création d'un vide (dépression dans la cuve).",
          "**Risque majeur** : Implosion de la cuve (collapse) - ⚠️ DANGER.",
          "**Solutions de prévention** : Vider le CO₂ du fermenteur (laisser ouvert 24h avant CIP), utiliser le casse-vide (si fonctionnel).",
          "**Vigilance** : Attention si le casse-vide est défectueux."
        ]
      },
      {
        title: "Danger 3 : Vanne de surpression",
        items: [
          "**Lors du remplissage** : Utiliser obligatoirement la vanne de surpression.",
          "**Risque** : Surpression pouvant endommager ou déformer la cuve.",
          "**Maintenance** : Vérifier le fonctionnement régulier de la vanne."
        ]
      },
      {
        title: "Checklist avant le CIP",
        items: [
          "✓ Identifier les CCP (Points de Contrôle Critiques).",
          "✓ Vérifier les CCP à chaque nettoyage.",
          "✓ S'assurer que les solutions sont bien séparées (pas de cross-contamination).",
          "✓ Vérifier le dimensionnement des pompes/boules CIP (capacité).",
          "✓ Vérifier l'intégrité des joints et raccords."
        ]
      },
      {
        title: "Checklist pendant le CIP",
        items: [
          "✓ Contrôler le débit des pompes (suffisant et régulier).",
          "✓ Vérifier que les boules CIP ne sont pas bouchées.",
          "✓ Surveiller les températures (atteinte des consignes).",
          "✓ Contrôler les concentrations (conductivimètre).",
          "✓ Vérifier absence de fuites."
        ]
      },
      {
        title: "Équipements à nettoyer spécifiquement",
        items: [
          "**Boules CIP** : Points de projection critique, vérifier absence obstruction.",
          "**Casse-vide** : Éliminer dépression résiduelle, entretien régulier.",
          "**Vannes de surpression** : Vérifier ouverture/fermeture, nettoyage.",
          "**Barboteur** : Points de stagnation possible, trempage recommandé.",
          "**Prises d'échantillons** : Zones mortes potentielles, nettoyage spécifique.",
          "**Toutes les vannes** : Nettoyage et désinfection individuels si nécessaire."
        ]
      },
      {
        title: "Entretien de la station CIP",
        items: [
          "**Rinçage régulier** : Après chaque cycle pour éviter cristallisation.",
          "**Passage à l'acide** : Régulièrement pour éliminer tartre et dépôts.",
          "**Vérification des sondes** : Calibrage, nettoyage, remplacement si défectueux.",
          "**Maintenance pompes** : Contrôle usure, joints, débits.",
          "**Inspection tuyauterie** : Recherche de fuites, dépôts, encrassement."
        ]
      },
      {
        title: "Zones mortes - Problème critique",
        items: [
          "**Définition** : Partie du circuit où le liquide de nettoyage ne circule pas ou stagne.",
          "**Causes principales** : Mauvais dimensionnement pompes, boules CIP mal positionnées, angles morts conception, tuyaux trop longs sans circulation.",
          "**Conséquences graves** : Accumulation de bactéries, contamination récurrente, inefficacité nettoyage.",
          "**Solutions** : Bien dimensionner pompes et boules CIP, conception hygiénique des équipements, vérification régulière de la couverture (100%)."
        ]
      }
    ],
    questions: [
      q("Quel est le résultat du mélange Soude + Acide?", ["Nettoyage optimisé", "Réaction violente et projections", "Aucun effet", "Amélioration efficacité"], 1, "Chimie dangereuse."),
      q("Quel mélange produit du chlore gazeux toxique?", ["Soude + Acide", "Javel + Acide", "Chlore + eau", "Savon + chlore"], 1, "Risque mortel."),
      q("Qu'est-ce qu'une zone morte en CIP?", ["Endroit gelé", "Zone où le liquide ne circule pas ou stagne", "Air chaud", "Désinfectant en excès"], 1, "Problème hygiénique."),
      q("Quel est le risque principal d'une zone morte?", ["Amélioration du nettoyage", "Accumulation de bactéries et contamination", "Augmentation débit", "Température élevée"], 1, "Source d'infection."),
      q("Quel phénomène se produit avec Soude + CO₂?", ["Chauffage rapide", "Création d'un vide (dépression)", "Augmentation de pression", "Coloration du moût"], 1, "Réaction dangereuse."),
      q("Quel est le risque du vide créé par Soude + CO₂?", ["Lenteur du nettoyage", "Implosion de la cuve (collapse)", "Fuite", "Surpression"], 1, "Danger structurel."),
      q("Comment prévenir la création de vide?", ["Ajouter CO₂", "Vider le CO₂ avant (laisser ouvert 24h) et utiliser casse-vide", "Utiliser plus de soude", "Augmenter température"], 1, "Prévention essentielle."),
      q("À quoi sert le casse-vide?", ["Créer pression", "Éliminer dépression/vide dans la cuve", "Chauffer le moût", "Agiter"], 1, "Sécurité contre collapse."),
      q("Quel risque pose la vanne de surpression?", ["Aucun", "Sans utilisation: surpression pouvant endommager cuve", "Sous-pression", "Fuites"], 1, "Contrôle de pression."),
      q("Quand utiliser la vanne de surpression?", ["Toujours", "Lors du remplissage", "Pendant détergent", "Jamais"], 1, "Timing critique."),
      q("Qu'est-ce qu'un CCP en brasserie?", ["Cuve à Cuivre Principal", "Point de Contrôle Critique", "Cercle Complet Process", "Cycle de Circulation"], 1, "Contrôle qualité."),
      q("Que faire avant chaque CIP?", ["Rien de spécial", "Identifier et vérifier les CCP", "Remplir les cuves", "Attendre"], 1, "Étape préalable."),
      q("Comment doivent être séparées les solutions?", ["Ensemble", "Bien séparées pour éviter cross-contamination", "N'importe comment", "Mélangées progressivement"], 1, "Sécurité chimique."),
      q("Quel équipement à vérifier avant CIP?", ["La couleur", "Le dimensionnement des pompes/boules CIP", "La date", "L'étiquette"], 1, "Capacité opérationnelle."),
      q("Quel est le critère pendant le CIP?", ["Silence", "Contrôler débit pompes et concentration", "Attendre", "Observer couleur"], 1, "Monitoring en temps réel."),
      q("Que vérifier sur les boules CIP?", ["Taille", "Absence d'obstruction/bouchage", "Couleur", "Poids"], 1, "Couverture complète."),
      q("Quel équipement contient souvent des zones mortes?", ["Grands tuyaux", "Barboteur, prises d'échantillons, vannes", "Pompes", "Boules"], 1, "Points d'attention critiques."),
      q("Comment nettoyer le barboteur?", ["CIP standard", "Trempage avec circulations spécifiques", "Une seule fois par an", "Non nécessaire"], 1, "Équipement sensible."),
      q("Quelle est l'importance des sondes?", ["Décoratives", "Critiques pour mesurer concentration et température", "Optionnelles", "Peu importantes"], 1, "Monitoring de qualité."),
      q("Que faire des sondes défectueuses?", ["Continuer ainsi", "Remplacement obligatoire", "Ignorer", "Nettoyer seulement"], 1, "Fiabilité des mesures."),
      q("Combien de fois passer l'acide en station CIP?", ["Une seule", "Régulièrement pour éliminer tartre", "Jamais", "Hebdomadaire"], 1, "Maintenance préventive."),
      q("Pourquoi rincer après chaque cycle?", ["Obligation légale", "Pour éviter cristallisation et accumulation dépôts", "Gaspillage d'eau", "Sans importance"], 1, "Conservation de l'équipement."),
      q("Qu'est-ce qu'une bonne couverture CIP?", ["Visible", "100% de la surface", "50% suffit", "Variable"], 1, "Nettoyage complet."),
      q("Quelle cause crée les zones mortes?", ["Trop de pression", "Mauvais dimensionnement pompes, mauvaise position boules", "Eau froide", "Détergent faible"], 1, "Origine du problème."),
      q("Comment éliminer les zones mortes?", ["Accepter", "Bien dimensionner pompes, boules CIP, conception hygiénique", "Utiliser plus de produit", "Augmenter temps"], 1, "Solution par le design."),
      q("Quel résultat apporte vérification régulière couverture?", ["Aucun", "Assurance 100% efficacité nettoyage", "Gaspillage", "Ralentissement"], 1, "Validité du process."),
      q("Que faire si boule CIP est bouchée?", ["Continuer", "Déboucher ou remplacer", "Augmenter pression", "Laisser"], 1, "Maintenance immédiate."),
      q("Quel est l'ordre de rinçage/produit?", ["Produit directement", "Rincer systématiquement entre produits différents", "Optionnel", "Mélanger progressivement"], 1, "Sécurité chimique absolue."),
      q("Combien de temps laisser ouvert fermenteur avant CIP?", ["1 heure", "24 heures (pour vider CO₂)", "1 minute", "Immédiatement"], 1, "Élimination du gaz."),
      q("Quel est l'impact d'une boule CIP défectueuse?", ["Pas d'impact", "Zones mortes et nettoyage incomplet", "Meilleur nettoyage", "Plus rapide"], 1, "Efficacité compromise.")
    ]
  },
  {
    id: "epi",
    category: "CIP",
    title: "29. Protection du personnel (EPI)",
    ficheRich: [
      {
        title: "Contexte – produits dangereux",
        items: [
          "**Soude caustique (pH ~14)** → brûlures chimiques graves.",
          "**Acides** (phosphorique, nitrique, péracétique) → brûlures, irritations.",
          "**Températures élevées (60–80°C)** → brûlures thermiques."
        ]
      },
      {
        title: "EPI obligatoires – Protection de la peau",
        items: [
          "**Gants** : Protection contre les brûlures chimiques (type recommandé : **nitrile** ou **néoprène**).",
          "**Tablier** : Protection contre les **projections**.",
          "**Manches longues** : Limiter le **contact accidentel** sur la peau."
        ]
      },
      {
        title: "EPI – Protection des yeux",
        items: [
          "**Lunettes de protection** : contre les **projections de liquide**.",
          "**Écran facial** : pour les **projections importantes**.",
          "Risques : **brûlure chimique**, **brûlure thermique**, **diphtérie oculaire** (infection grave).",
          "⚠️ **Les projections oculaires sont des urgences médicales !**"
        ]
      },
      {
        title: "EPI – Protection du corps",
        items: [
          "**Vêtement de travail** : **résistant aux acides**.",
          "**Combinaison** : pour les **opérations à risque** (fortes projections, produits concentrés)."
        ]
      },
      {
        title: "EPI – Protection des pieds",
        items: [
          "**Chaussures de sécurité** : **antidérapantes**.",
          "**Bottes** : pour **zones humides**.",
          "Risques : **sol mouillé et glissant**, **projections de produits**, **chutes**."
        ]
      },
      {
        title: "Tableau récapitulatif des EPI",
        items: [
          "**Mains** → Gants chimiques : **Brûlures chimiques**.",
          "**Yeux** → Lunettes/Écran : **Projections**.",
          "**Corps** → Tablier/Combinaison : **Contact chimique**.",
          "**Pieds** → Chaussures antidérapantes : **Glissades**."
        ]
      },
      {
        title: "Consignes de sécurité générales",
        items: [
          "Peau : **rincer abondamment 15–20 min**, retirer vêtements contaminés, **consulter** si brûlure.",
          "Yeux : **rincer immédiatement 15–20 min**, **ne pas frotter**, **urgence médicale**.",
          "Inhalation : **quitter la zone**, respirer **air frais**, **consulter** si symptômes."
        ]
      }
    ],
    questions: [
      q("Pourquoi les EPI sont-ils indispensables en brasserie?", ["Esthétique", "Produits chimiques dangereux (soude, acides) et chaleur", "Optionnel", "Confort"], 1, "Risque chimique et thermique."),
      q("Quel est le pH de la soude caustique?", ["~7", "~10", "~14", "~3"], 2, "Soude très basique et corrosive."),
      q("Quels acides sont cités comme risques?", ["Citrique uniquement", "Phosphorique, nitrique, péracétique", "Acide lactique", "Acide ascorbique"], 1, "Principaux acides utilisés."),
      q("Quelle plage de température crée un risque de brûlure thermique?", ["10–20°C", "60–80°C", "0–5°C", "90–100°C"], 1, "Liquides chauds de nettoyage."),
      q("Quels gants sont recommandés?", ["Coton", "Nitrile ou néoprène", "Laine", "Vinyle"], 1, "Résistants aux produits chimiques."),
      q("Les gants protègent contre…", ["La poussière", "Les brûlures chimiques", "Le froid", "Le bruit"], 1, "Protection cutanée."),
      q("Le tablier sert à…", ["Décorer", "Protéger des projections", "Tenir chaud", "Réduire le bruit"], 1, "Barrière anti-projection."),
      q("Les manches longues réduisent…", ["La transpiration", "Le contact accidentel avec produits", "Le coût", "La visibilité"], 1, "Couverture de la peau."),
      q("Les lunettes de protection protègent de…", ["La poussière sonore", "Projections de liquide", "La chaleur ambiante", "La lumière"], 1, "Barrière oculaire."),
      q("L'écran facial est utile pour…", ["La vision nocturne", "Projections importantes", "Le confort", "Le stockage"], 1, "Grande surface de protection."),
      q("Une projection oculaire est…", ["Banale", "Une urgence médicale", "Optionnelle", "Sans danger"], 1, "Risque majeur immédiat."),
      q("Parmi ces risques oculaires, lequel est cité?", ["Myopie", "Brûlure chimique/thermique, diphtérie oculaire", "UV uniquement", "Fatigue"], 1, "Gravité des projections."),
      q("Un vêtement de travail doit être…", ["Décoratif", "Résistant aux acides", "Transparent", "Jetable"], 1, "Protection corporelle."),
      q("La combinaison est utilisée…", ["Toujours", "Pour les opérations à risque", "Jamais", "Uniquement en bureau"], 1, "Expositions élevées."),
      q("Les chaussures de sécurité doivent être…", ["Souples", "Antidérapantes", "Ouvertes", "Sans embout"], 1, "Prévention des chutes."),
      q("Les bottes sont utiles…", ["Au bureau", "En zones humides", "En montagne", "Jamais"], 1, "Protection en sol mouillé."),
      q("Quel risque est lié au sol mouillé?", ["Bruit", "Glissade et chute", "Allergie", "Chaleur"], 1, "Accident de travail."),
      q("Associer 'Mains' au bon EPI", ["Lunettes", "Gants chimiques", "Chaussures", "Écran facial"], 1, "Protection cutanée."),
      q("Associer 'Yeux' au bon EPI", ["Gants", "Lunettes/Écran", "Chaussures", "Tablier"], 1, "Protection oculaire."),
      q("Associer 'Corps' au bon EPI", ["Chaussures", "Tablier/Combinaison", "Lunettes", "Gants"], 1, "Protection corporelle."),
      q("Associer 'Pieds' au bon EPI", ["Gants", "Chaussures antidérapantes", "Lunettes", "Écran facial"], 1, "Antichute."),
      q("Premier geste en cas de contact peau?", ["Essuyer", "Rincer 15–20 min à l'eau", "Attendre", "Appliquer chaleur"], 1, "Dilution immédiate."),
      q("Que faire des vêtements contaminés?", ["Les garder", "Les retirer", "Les laver plus tard", "Les sécher"], 1, "Supprimer source chimique."),
      q("Quand consulter un médecin (peau)?", ["Jamais", "Si brûlure", "Après une semaine", "Seulement si douleur"], 1, "Évaluation médicale."),
      q("Premier geste en cas de projection oculaire?", ["Fermer les yeux", "Rincer immédiatement 15–20 min", "Regarder la lumière", "Mettre des lunettes"], 1, "Urgence vitale."),
      q("Que ne faut-il pas faire pour les yeux?", ["Rincer", "Ne pas frotter", "Appeler le médecin", "Retirer lentilles"], 1, "Éviter aggravation."),
      q("Que faire en cas d'inhalation de vapeurs?", ["Rester sur place", "Quitter la zone et respirer air frais", "Boire de l'eau", "Augmenter la ventilation"], 1, "Éloignement immédiat."),
      q("Quand consulter après inhalation?", ["Jamais", "Si symptômes", "Toujours", "Après 1 mois"], 1, "Suivi médical."),
      q("Quel EPI n'est pas pour les yeux?", ["Lunettes", "Écran facial", "Bottes", "Visière"], 2, "Protection pieds ≠ yeux."),
      q("Quel EPI réduit le risque de glissade?", ["Gants", "Chaussures antidérapantes", "Lunettes", "Tablier"], 1, "Adhérence au sol.")
    ]
  },
  {
    id: "introductionLevure",
    category: "LEVURE",
    title: "30. Introduction à la levure",
    ficheRich: [
      {
        title: "Classification biologique - Place dans le monde vivant",
        items: [
          "**MONDE VIVANT** → Cellulaire (Eucaryotes et Procaryotes) / Acellulaire (Virus)",
          "**EUCARYOTES** (avec noyau) → Plantes, Animaux, Protistes, FUNGI (Champignons)",
          "**FUNGI** → Comprend les levures et champignons",
          "**LEVURES** → Champignons unicellulaires eucaryotes"
        ]
      },
      {
        title: "Caractéristiques de la levure",
        items: [
          "**Règne**: Fungi (champignons)",
          "**Type cellulaire**: Eucaryote (possède un noyau)",
          "**Taille**: ~10 µm de diamètre",
          "**Structure**: Unicellulaire",
          "**Particularité**: Présence de mitochondries (contrairement aux bactéries)"
        ]
      },
      {
        title: "Reproduction",
        items: [
          "**Mode principal**: Bourgeonnement asexué (budding en anglais)",
          "**Processus**: La cellule mère forme un bourgeon qui se détache pour former une nouvelle cellule"
        ]
      },
      {
        title: "Utilisations de la levure",
        items: [
          "**Brasserie**: Production de bière",
          "**Vinification**: Production de vin",
          "**Distillerie**: Production d'alcools",
          "**Boulangerie**: Levée du pain",
          "**Pharmaceutique**: Production d'antibiotiques et vaccins"
        ]
      },
      {
        title: "Espèces principales en brasserie",
        items: [
          "**Saccharomyces cerevisiae**: Fermentation haute (ales)",
          "**Saccharomyces carlsbergensis (pastorianus)**: Fermentation basse (lagers)"
        ]
      },
      {
        title: "Historique",
        items: [
          "**1857**: Louis Pasteur publie 'Mémoire sur la fermentation alcoolique'",
          "**1883-1885**: Emil Hansen isole la levure basse chez Carlsberg"
        ]
      },
      {
        title: "Aspects négatifs",
        items: [
          "Certaines levures sont **pathogènes**",
          "**Candida albicans** → mycose, muguet"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ La levure est un champignon unicellulaire eucaryote",
          "✅ Elle se reproduit par bourgeonnement",
          "✅ Mise en évidence scientifique par Pasteur en 1857",
          "✅ Utilisée dans de nombreuses industries alimentaires"
        ]
      }
    ],
    questions: [
      q("À quel règne appartient la levure?", ["Plantes", "Animaux", "Fungi (Champignons)", "Bactéries"], 2, "La levure appartient au règne Fungi."),
      q("Quel type de cellule est la levure?", ["Procaryote", "Eucaryote", "Virus", "Bactérie"], 1, "La levure est eucaryote avec un noyau."),
      q("Quelle est la taille approximative d'une levure?", ["1 µm", "10 µm", "100 µm", "1 mm"], 1, "Environ 10 µm de diamètre."),
      q("Quel organite la levure possède-t-elle contrairement aux bactéries?", ["Chloroplaste", "Mitochondrie", "Vacuole", "Ribosome"], 1, "Les mitochondries sont présentes dans les eucaryotes."),
      q("Quel est le mode principal de reproduction de la levure?", ["Division binaire", "Bourgeonnement", "Sporulation", "Conjugaison"], 1, "Reproduction par bourgeonnement (budding)."),
      q("Comment appelle-t-on le bourgeonnement en anglais?", ["Splitting", "Budding", "Growing", "Dividing"], 1, "Budding = bourgeonnement."),
      q("Qui a publié le 'Mémoire sur la fermentation alcoolique' en 1857?", ["Emil Hansen", "Louis Pasteur", "Carlsberg", "Darwin"], 1, "Pasteur a mis en évidence le rôle de la levure."),
      q("Qui a isolé la levure basse chez Carlsberg?", ["Louis Pasteur", "Emil Hansen", "Charles Darwin", "Robert Koch"], 1, "Emil Hansen entre 1883-1885."),
      q("Quelle espèce de levure est utilisée pour les fermentations hautes (ales)?", ["Saccharomyces pastorianus", "Saccharomyces cerevisiae", "Candida albicans", "Aspergillus"], 1, "S. cerevisiae pour les ales."),
      q("Quelle espèce est utilisée pour les fermentations basses (lagers)?", ["Saccharomyces cerevisiae", "Saccharomyces carlsbergensis", "Candida albicans", "Aspergillus"], 1, "S. carlsbergensis (pastorianus) pour les lagers."),
      q("Dans quel domaine la levure n'est-elle PAS utilisée?", ["Brasserie", "Boulangerie", "Métallurgie", "Pharmaceutique"], 2, "La métallurgie n'utilise pas de levure."),
      q("Quel est un exemple de levure pathogène?", ["Saccharomyces cerevisiae", "Candida albicans", "S. pastorianus", "Toutes"], 1, "Candida albicans cause mycoses et muguet."),
      q("La levure est-elle unicellulaire ou pluricellulaire?", ["Unicellulaire", "Pluricellulaire", "Les deux", "Ni l'un ni l'autre"], 0, "La levure est unicellulaire."),
      q("Dans quelle branche du vivant se trouvent les levures?", ["Acellulaire", "Procaryotes", "Eucaryotes", "Virus"], 2, "Les levures sont des eucaryotes."),
      q("Quelle industrie utilise la levure pour faire lever le pain?", ["Brasserie", "Boulangerie", "Distillerie", "Vinification"], 1, "La boulangerie utilise la levure pour le pain."),
      q("Quel produit les levures ne produisent-elles PAS directement?", ["Alcool", "CO2", "Antibiotiques (certaines souches)", "Acier"], 3, "L'acier n'est pas produit par levure."),
      q("En quelle année Pasteur a-t-il publié son mémoire?", ["1850", "1857", "1883", "1900"], 1, "1857 est l'année de publication."),
      q("Quelle période correspond à l'isolement de la levure basse?", ["1857-1860", "1883-1885", "1900-1910", "1950-1960"], 1, "1883-1885 par Emil Hansen."),
      q("Comment se forme une nouvelle cellule de levure?", ["Par division du noyau seul", "Par bourgeonnement de la cellule mère", "Par fusion de deux cellules", "Par fragmentation"], 1, "Bourgeonnement = formation d'un bourgeon qui se détache."),
      q("Quelle est la principale différence entre levure et bactérie?", ["Taille uniquement", "Présence d'un noyau et mitochondries", "Couleur", "Forme"], 1, "Levure = eucaryote avec noyau, bactérie = procaryote sans noyau."),
      q("Les levures font-elles partie du monde acellulaire?", ["Oui", "Non, elles sont cellulaires", "Seulement certaines", "Parfois"], 1, "Les levures sont des organismes cellulaires."),
      q("Quel est le nom scientifique complet de la levure de bière haute?", ["Saccharomyces pastorianus", "Saccharomyces cerevisiae", "Candida cerevisiae", "Fungi cerevisiae"], 1, "S. cerevisiae = levure de fermentation haute."),
      q("Que signifie 'Saccharomyces'?", ["Champignon du sucre", "Levure alcoolique", "Cellule simple", "Bourgeonnement"], 0, "Saccharo = sucre, myces = champignon."),
      q("Les levures possèdent-elles une paroi cellulaire?", ["Non", "Oui, comme les champignons", "Seulement les pathogènes", "Uniquement S. cerevisiae"], 1, "Comme tous les champignons, les levures ont une paroi."),
      q("Quelle maladie n'est PAS causée par Candida albicans?", ["Mycose", "Muguet", "Tuberculose", "Candidose"], 2, "La tuberculose est bactérienne, pas fongique."),
      q("Dans quelle industrie la levure produit-elle des vaccins?", ["Brasserie", "Boulangerie", "Pharmaceutique", "Distillerie"], 2, "L'industrie pharmaceutique utilise la levure."),
      q("Quel gaz la levure produit-elle lors de la fermentation?", ["Oxygène", "CO2 (dioxyde de carbone)", "Azote", "Hydrogène"], 1, "La fermentation produit CO2 et alcool."),
      q("Où Emil Hansen a-t-il isolé la levure basse?", ["À Paris", "Chez Carlsberg", "À Munich", "À Londres"], 1, "Hansen travaillait pour la brasserie Carlsberg."),
      q("Les virus font-ils partie de la même branche que les levures?", ["Oui", "Non, les virus sont acellulaires", "Parfois", "Seulement certains"], 1, "Virus = acellulaire, levure = cellulaire eucaryote."),
      q("Quel alcool principal la levure produit-elle?", ["Méthanol", "Éthanol", "Propanol", "Butanol"], 1, "L'éthanol est le produit principal de fermentation.")
    ]
  },
  {
    id: "theorieFermentation",
    category: "LEVURE",
    title: "31. Théorie de la fermentation",
    ficheRich: [
      {
        title: "Métabolisme de la levure - Principe fondamental",
        items: [
          "La levure peut vivre de **deux façons** selon la présence ou l'absence d'oxygène",
          "**Respiration** : en présence d'O₂ → production maximale d'énergie",
          "**Fermentation** : en absence d'O₂ → production d'alcool + CO₂"
        ]
      },
      {
        title: "Respiration aérobie (avec O₂)",
        items: [
          "**Équation** : C₆H₁₂O₆ + 6O₂ → 6CO₂ + 6H₂O + ÉNERGIE",
          "**Rendement** : Élevé (production d'énergie maximale)",
          "**Produits** : CO₂ + eau (pas d'alcool)",
          "**Usage** : Multiplication des levures (propagation)"
        ]
      },
      {
        title: "Fermentation alcoolique (sans O₂)",
        items: [
          "**Équation** : C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂ + ÉNERGIE",
          "**Rendement** : ~14x moins rentable énergétiquement",
          "**Produits** : Éthanol + CO₂",
          "**Usage** : Production de bière !"
        ]
      },
      {
        title: "Facteur déterminant : concentration en sucres",
        items: [
          "La **concentration en sucres** est très importante pour orienter le métabolisme",
          "**Faible concentration + O₂** → Respiration privilégiée",
          "**Concentration élevée (même avec O₂)** → Fermentation (effet Crabtree)",
          "**Effet Crabtree** : La levure fermente même en présence d'oxygène si les sucres sont abondants"
        ]
      },
      {
        title: "Les densités - Définitions clés",
        items: [
          "**OG (Original Gravity)** : Densité primitive = quantité de sucre en début de fermentation",
          "**FG (Final Gravity)** : Densité finale = quantité de sucre en fin de fermentation",
          "**Atténuation apparente (Att)** : Capacité de la levure à dégrader les sucres"
        ]
      },
      {
        title: "Formule de l'atténuation",
        items: [
          "**Formule** : Atténuation (%) = (OG - FG) / OG × 100",
          "**Exemple** : OG = 16°P, FG = 1°P → Att = (16-1)/16 = 93.75%"
        ]
      },
      {
        title: "Échelle d'atténuation",
        items: [
          "**65-70%** : Atténuation faible",
          "**71-75%** : Atténuation moyenne",
          "**76-80%** : Atténuation élevée",
          "**100%** : Possible avec Brettanomyces (super-atténuation)"
        ]
      },
      {
        title: "Pourquoi 'apparente' ?",
        items: [
          "On mesure directement les densités sans tenir compte de l'**éthanol présent**",
          "Densité de l'éthanol = 0.8 (plus léger que l'eau)",
          "L'atténuation réelle serait légèrement différente si on corrigeait pour l'alcool"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ Respiration = énergie maximale, pas d'alcool",
          "✅ Fermentation = alcool + CO₂, moins d'énergie",
          "✅ La concentration en sucres influence le métabolisme",
          "✅ L'atténuation mesure l'efficacité de la fermentation"
        ]
      }
    ],
    questions: [
      q("Que produit la levure en présence d'oxygène?", ["Éthanol + CO₂", "CO₂ + H₂O + énergie", "Seulement CO₂", "Rien"], 1, "La respiration produit CO₂ + eau + énergie maximale."),
      q("Que produit la levure en absence d'oxygène?", ["CO₂ + H₂O", "Éthanol + CO₂ + énergie", "Seulement éthanol", "Rien"], 1, "La fermentation produit éthanol + CO₂."),
      q("Quel processus donne le plus d'énergie?", ["Fermentation", "Respiration", "Les deux pareil", "Aucun"], 1, "La respiration produit ~14x plus d'énergie."),
      q("Combien de molécules de CO₂ sont produites par fermentation d'1 glucose?", ["1", "2", "4", "6"], 1, "C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂"),
      q("Combien de molécules d'éthanol sont produites par glucose?", ["1", "2", "4", "6"], 1, "1 glucose → 2 éthanol"),
      q("Quelle est la formule de la respiration?", ["C₆H₁₂O₆ → 2C₂H₅OH + 2CO₂", "C₆H₁₂O₆ + 6O₂ → 6CO₂ + 6H₂O", "C₆H₁₂O₆ → 6CO₂", "Aucune"], 1, "Glucose + oxygène → CO₂ + eau + énergie."),
      q("Quel est l'usage principal de la respiration?", ["Production de bière", "Multiplication des levures", "Aromatisation", "Aucun"], 1, "La respiration permet la propagation (multiplication)."),
      q("Quel est l'usage principal de la fermentation?", ["Multiplication", "Production d'alcool et bière", "Stockage", "Aucun"], 1, "La fermentation produit l'alcool pour la bière."),
      q("Que signifie OG?", ["Oxygen Gas", "Original Gravity", "Organic Growth", "Old Grain"], 1, "OG = densité primitive (début fermentation)."),
      q("Que signifie FG?", ["Final Grain", "Final Gravity", "Fast Growth", "Fermentation Gas"], 1, "FG = densité finale (fin fermentation)."),
      q("Comment calcule-t-on l'atténuation?", ["FG / OG", "(OG - FG) / OG × 100", "OG - FG", "FG × OG"], 1, "Atténuation = (OG - FG) / OG × 100."),
      q("Avec OG=16°P et FG=4°P, quelle est l'atténuation?", ["25%", "50%", "75%", "100%"], 2, "(16-4)/16 = 12/16 = 75%."),
      q("Une atténuation de 68% est…", ["Faible", "Moyenne", "Élevée", "Très élevée"], 0, "65-70% = faible atténuation."),
      q("Une atténuation de 73% est…", ["Faible", "Moyenne", "Élevée", "Très élevée"], 1, "71-75% = moyenne atténuation."),
      q("Une atténuation de 78% est…", ["Faible", "Moyenne", "Élevée", "Très élevée"], 2, "76-80% = élevée atténuation."),
      q("Quelle levure peut atteindre 100% d'atténuation?", ["Saccharomyces cerevisiae", "Brettanomyces", "Candida", "Aucune"], 1, "Brettanomyces = super-atténuation."),
      q("Qu'est-ce que l'effet Crabtree?", ["Fermentation même avec O₂ si sucres élevés", "Respiration sans O₂", "Multiplication lente", "Aucun effet"], 0, "Concentration élevée en sucres → fermentation même avec O₂."),
      q("Quelle densité a l'éthanol?", ["1.0", "0.8", "1.2", "0.5"], 1, "Éthanol = densité 0.8 (plus léger que l'eau)."),
      q("Pourquoi parle-t-on d'atténuation 'apparente'?", ["C'est une estimation", "On ne tient pas compte de l'éthanol", "Elle varie", "C'est une erreur"], 1, "On mesure sans corriger pour la densité de l'éthanol."),
      q("En présence d'O₂ et faible sucre, la levure…", ["Fermente", "Respire", "Meurt", "Ne fait rien"], 1, "Faible sucre + O₂ → respiration privilégiée."),
      q("En présence d'O₂ et forte concentration de sucre, la levure…", ["Respire uniquement", "Fermente (effet Crabtree)", "Meurt", "Ne fait rien"], 1, "Sucres élevés → fermentation même avec O₂."),
      q("Combien de fois la respiration est-elle plus rentable que la fermentation?", ["2x", "7x", "14x", "100x"], 2, "~14x plus d'énergie par respiration."),
      q("Quel gaz est produit lors de la respiration?", ["O₂", "CO₂", "N₂", "H₂"], 1, "Respiration produit CO₂ + H₂O."),
      q("La fermentation produit-elle de l'eau?", ["Oui", "Non", "Parfois", "En grande quantité"], 1, "Fermentation → éthanol + CO₂ (pas d'eau)."),
      q("La respiration produit-elle de l'alcool?", ["Oui", "Non", "Parfois", "Toujours"], 1, "Respiration → CO₂ + H₂O (pas d'alcool)."),
      q("Quel est le substrat de départ pour les deux métabolismes?", ["Éthanol", "Glucose", "CO₂", "Eau"], 1, "Glucose (C₆H₁₂O₆) est le substrat."),
      q("Si OG=12°P et FG=3°P, l'atténuation est…", ["25%", "50%", "75%", "90%"], 2, "(12-3)/12 = 9/12 = 75%."),
      q("Une levure avec 82% d'atténuation est…", ["Faible", "Moyenne", "Élevée", "Exceptionnelle"], 3, "Au-delà de 80% = exceptionnelle (type Brett)."),
      q("Quelle formule chimique représente l'éthanol?", ["C₂H₆O", "C₂H₅OH", "CH₃OH", "C₆H₁₂O₆"], 1, "Éthanol = C₂H₅OH."),
      q("Pendant la propagation, on privilégie…", ["La fermentation", "La respiration", "Les deux", "Aucun"], 1, "Propagation = multiplication → besoin de respiration (énergie max).")
    ]
  },
  {
    id: "typesFermentation",
    category: "LEVURE",
    title: "32. Types de fermentation",
    ficheRich: [
      {
        title: "Vue d'ensemble des 4 types",
        items: [
          "**Fermentation HAUTE** : 15-25°C, S. cerevisiae, surface → Ales",
          "**Fermentation BASSE** : 12-14°C, S. pastorianus, fond → Lagers",
          "**Fermentation SPONTANÉE** : Variable, levures sauvages → Lambics, Gueuze",
          "**Fermentation MIXTE** : Variable, plusieurs micro-organismes → Bières complexes"
        ]
      },
      {
        title: "1. Fermentation SPONTANÉE",
        items: [
          "**Méthode la plus ancienne** de fermentation",
          "**Principe** : Le moût est exposé à l'air libre, ensemencement par l'environnement",
          "**Levures sauvages** : Brettanomyces bruxellensis, Brettanomyces lambicus",
          "**Saison** : Uniquement saison froide (mi-septembre à mi-mai)",
          "**Région** : Vallée de la Senne (Belgique), Pajottenland",
          "**Styles** : Lambics, Gueuzes, Krieks, Faros"
        ]
      },
      {
        title: "2. Fermentation HAUTE",
        items: [
          "**Levure** : Saccharomyces cerevisiae",
          "**Température** : 15-25°C",
          "**Comportement** : Levures remontent à la surface et forment une 'croûte'",
          "**Origine du nom** : Position haute + température haute",
          "**Arômes** : Complexes et fruités",
          "**Styles (Ales)** : Pale Ales, IPAs, Stouts, Porters, Bières belges",
          "**Consommation** : 6-12°C"
        ]
      },
      {
        title: "3. Fermentation BASSE",
        items: [
          "**Levure** : Saccharomyces pastorianus (= carlsbergensis)",
          "**Température** : 12-14°C",
          "**Comportement** : Levures sédimentent au fond",
          "**Origine du nom** : Position basse + température basse",
          "**Histoire** : Popularisation de la pils au milieu 19ᵉ siècle à Pilsen (Tchécoslovaquie)",
          "**1883-1885** : Hansen isole S. pastorianus chez Carlsberg",
          "**Hybride** : S. pastorianus = S. cerevisiae × S. eubayanus",
          "**Styles (Lager)** : Pilsners, Märzen, Bock, Helles",
          "**'Lager'** vient de l'allemand 'lagern' = stocker",
          "**Caractéristiques** : Moins fruitées, moins alcoolisées, CO₂ supérieur",
          "**Consommation** : Fraîches 4-7°C"
        ]
      },
      {
        title: "4. Fermentation MIXTE",
        items: [
          "**Définition** : Utilisation de deux types de micro-organismes",
          "**Combinaison** : Levures de fermentation haute ET bactéries",
          "**Principe** : Mélange des processus haute + spontanée",
          "**Exemples** : Bières vieillies en fûts de chêne",
          "**Effet** : Saveur plus fruitée grâce aux micro-organismes du bois",
          "**Garde** : Plusieurs mois"
        ]
      },
      {
        title: "La floculation",
        items: [
          "**Définition** : Phénomène par lequel la levure crée des agrégats multicellulaires qui sédimentent",
          "**Rapidité** : Variable selon les souches",
          "**Risque** : Floculation trop précoce → sucres résiduels élevés",
          "**Impact** : Les souches très floculentes peuvent s'arrêter avant la fin"
        ]
      },
      {
        title: "Tableau comparatif",
        items: [
          "**HAUTE** : 15-25°C, surface, fruités, ales, durée courte",
          "**BASSE** : 12-14°C, fond, propres/nets, lagers, durée longue",
          "**SPONTANÉE** : Variable, levures sauvages, funky/acides, lambics, très longue",
          "**MIXTE** : Variable, multiples organismes, arômes variés, longue"
        ]
      }
    ],
    questions: [
      q("Combien de types principaux de fermentation existe-t-il?", ["2", "3", "4", "5"], 2, "4 types : haute, basse, spontanée, mixte."),
      q("Quelle levure est utilisée en fermentation haute?", ["S. pastorianus", "S. cerevisiae", "Brettanomyces", "S. eubayanus"], 1, "S. cerevisiae pour les ales."),
      q("Quelle levure est utilisée en fermentation basse?", ["S. cerevisiae", "S. pastorianus", "Brettanomyces", "Levures sauvages"], 1, "S. pastorianus pour les lagers."),
      q("À quelle température fermente la fermentation haute?", ["4-7°C", "12-14°C", "15-25°C", "30-35°C"], 2, "15-25°C pour fermentation haute."),
      q("À quelle température fermente la fermentation basse?", ["4-7°C", "12-14°C", "15-25°C", "30-35°C"], 1, "12-14°C pour fermentation basse."),
      q("Où se positionnent les levures en fermentation haute?", ["Au fond", "À la surface", "Au milieu", "Partout"], 1, "Les levures remontent à la surface."),
      q("Où se positionnent les levures en fermentation basse?", ["À la surface", "Au fond", "Au milieu", "Partout"], 1, "Les levures sédimentent au fond."),
      q("Comment appelle-t-on les bières de fermentation haute?", ["Lagers", "Ales", "Lambics", "Pils"], 1, "Ales = fermentation haute."),
      q("Comment appelle-t-on les bières de fermentation basse?", ["Ales", "Lagers", "Lambics", "Stouts"], 1, "Lagers = fermentation basse."),
      q("Que signifie 'Lager' en allemand?", ["Fermenter", "Stocker", "Refroidir", "Brasser"], 1, "Lagern = stocker."),
      q("Quelle est la méthode de fermentation la plus ancienne?", ["Haute", "Basse", "Spontanée", "Mixte"], 2, "La fermentation spontanée est la plus ancienne."),
      q("Quelles levures sont utilisées en fermentation spontanée?", ["S. cerevisiae", "S. pastorianus", "Levures sauvages", "Aucune"], 2, "Levures sauvages de l'air."),
      q("Pendant quelle saison fait-on la fermentation spontanée?", ["Toute l'année", "Été uniquement", "Saison froide (sept-mai)", "Printemps"], 2, "Mi-septembre à mi-mai uniquement."),
      q("Où se pratique traditionnellement la fermentation spontanée?", ["Munich", "Pilsen", "Vallée de la Senne (Belgique)", "Dublin"], 2, "Belgique, Pajottenland, vallée de la Senne."),
      q("Quel style est produit par fermentation spontanée?", ["IPA", "Stout", "Lambic", "Pilsner"], 2, "Lambics, gueuzes, krieks."),
      q("Quelle ville tchèque a popularisé la Pils?", ["Prague", "Pilsen", "Brno", "Ostrava"], 1, "Pilsen au milieu du 19ᵉ siècle."),
      q("Quand Hansen a-t-il isolé S. pastorianus?", ["1857", "1883-1885", "1900", "1920"], 1, "Entre 1883 et 1885 chez Carlsberg."),
      q("S. pastorianus est un hybride de…", ["S. cerevisiae × S. eubayanus", "S. cerevisiae × Brettanomyces", "Deux bactéries", "Aucune réponse"], 0, "Hybride de cerevisiae et eubayanus."),
      q("Quel type de fermentation forme une 'croûte' en surface?", ["Basse", "Haute", "Spontanée", "Mixte"], 1, "Fermentation haute forme une croûte."),
      q("Les ales sont généralement…", ["Moins fruitées que lagers", "Plus fruitées que lagers", "Identiques aux lagers", "Sans arôme"], 1, "Ales = arômes fruités et complexes."),
      q("Les lagers ont généralement…", ["Moins de CO₂", "Plus de CO₂", "Pas de CO₂", "Autant de CO₂"], 1, "Teneur en CO₂ supérieure."),
      q("À quelle température consomme-t-on les ales?", ["0-4°C", "4-7°C", "6-12°C", "15-20°C"], 2, "6-12°C pour les ales."),
      q("À quelle température consomme-t-on les lagers?", ["0-2°C", "4-7°C", "10-15°C", "15-20°C"], 1, "4-7°C (fraîches) pour les lagers."),
      q("Qu'est-ce que la fermentation mixte?", ["Deux levures hautes", "Levures + bactéries", "Deux bactéries", "Aucun micro-organisme"], 1, "Levures haute + bactéries."),
      q("Dans quoi vieillit-on les bières mixtes?", ["Bouteilles plastique", "Fûts de chêne", "Cuves inox", "Jarres en terre"], 1, "Fûts de chêne pour micro-organismes du bois."),
      q("Qu'est-ce que la floculation?", ["Division cellulaire", "Formation d'agrégats qui sédimentent", "Production de CO₂", "Mort cellulaire"], 1, "Agrégats multicellulaires qui sédimentent."),
      q("Quel risque avec une floculation trop précoce?", ["Trop d'alcool", "Sucres résiduels élevés", "Pas de CO₂", "Bière trop amère"], 1, "Arrêt fermentation → sucres résiduels."),
      q("Quel style n'est PAS une ale?", ["IPA", "Stout", "Porter", "Pilsner"], 3, "Pilsner = lager (fermentation basse)."),
      q("Quel style n'est PAS un lager?", ["Pilsner", "Bock", "Märzen", "Pale Ale"], 3, "Pale Ale = ale (fermentation haute)."),
      q("Quelle levure sauvage est typique des lambics?", ["S. cerevisiae", "Brettanomyces bruxellensis", "S. pastorianus", "Aucune"], 1, "Brettanomyces bruxellensis et lambicus.")
    ]
  },
  {
    id: "terminologieLevure",
    category: "LEVURE",
    title: "33. Terminologie de la levure",
    ficheRich: [
      {
        title: "Les composés aromatiques",
        items: [
          "**Deux grandes familles** : Les ESTERS et les ALCOOLS SUPÉRIEURS",
          "Tous deux sont produits par la levure lors de la fermentation",
          "Leur concentration dépend fortement de la température de fermentation"
        ]
      },
      {
        title: "1. Les ESTERS (totaux)",
        items: [
          "**Nature** : Composés aromatiques",
          "**Composition** : Acide + Alcool",
          "**Origine** : Issus de la fermentation",
          "**Production** : Essentiellement par les levures de haute fermentation",
          "**Arômes** : Fruités (banane, ananas, pomme, solvant)"
        ]
      },
      {
        title: "Principaux esters",
        items: [
          "**Éthyl acétate** : Arôme fruit/solvant (le plus commun)",
          "**Isoamyl acétate** : Arôme banane (très reconnaissable)",
          "**Éthyl hexanoate** : Arôme ananas (fruité tropical)",
          "**Éthyl caprylate** : Arôme pomme (fruité)"
        ]
      },
      {
        title: "2. Les ALCOOLS SUPÉRIEURS (Fusel alcohols)",
        items: [
          "**Nature** : Alcools autres que l'éthanol",
          "**Concentration souhaitée** : Faible",
          "**À faible dose** : Positifs (roses, banane, complexité)",
          "**À forte dose** : Négatifs (solvant, chimique, médicinal)",
          "**Exemples** : Alcool isoamylique (banane/solvant), Isobutanol (solvant), n-Propanol (alcool)"
        ]
      },
      {
        title: "Styles recherchant les alcools supérieurs",
        items: [
          "**Triple belge** : Alcools supérieurs recherchés",
          "**Barley wine** : Complexité aromatique",
          "**Bières fortes** : Profil aromatique riche"
        ]
      },
      {
        title: "3. Température de fermentation",
        items: [
          "**T° idéale** : Fournie par le fabricant de levure",
          "**Importance** : Cruciale pour le profil aromatique",
          "**T° basse** : Moins d'esters, profil plus propre",
          "**T° haute** : Plus d'esters, profil plus fruité",
          "**Impact** : La température influence fortement les arômes"
        ]
      },
      {
        title: "4. Levures vivantes",
        items: [
          "**Concentration** : ~7 × 10⁹ cellules/gramme de levure sèche",
          "**Utilité** : Calcul des populations et ensemencements",
          "**Importance** : Connaître la quantité pour un bon ensemencement"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ Les esters donnent les arômes fruités",
          "✅ Les alcools supérieurs peuvent être positifs ou négatifs selon la concentration",
          "✅ La température de fermentation influence fortement le profil aromatique",
          "✅ Connaître la concentration en levures vivantes est essentiel pour l'ensemencement"
        ]
      }
    ],
    questions: [
      q("Que sont les esters?", ["Des sucres", "Des composés aromatiques (Acide + Alcool)", "Des protéines", "Des enzymes"], 1, "Esters = Acide + Alcool = arômes."),
      q("D'où proviennent les esters?", ["Du malt", "Du houblon", "De la fermentation par les levures", "De l'eau"], 2, "Les levures produisent les esters."),
      q("Quel type de levure produit le plus d'esters?", ["Levures basses", "Levures hautes", "Levures sauvages", "Aucune"], 1, "Levures de haute fermentation = plus d'esters."),
      q("Quel est l'ester le plus commun?", ["Isoamyl acétate", "Éthyl acétate", "Éthyl hexanoate", "Éthyl caprylate"], 1, "Éthyl acétate = le plus commun."),
      q("Quel arôme donne l'isoamyl acétate?", ["Pomme", "Banane", "Ananas", "Solvant"], 1, "Isoamyl acétate = arôme banane."),
      q("Quel arôme donne l'éthyl hexanoate?", ["Banane", "Pomme", "Ananas", "Solvant"], 2, "Éthyl hexanoate = arôme ananas (tropical)."),
      q("Quel arôme donne l'éthyl caprylate?", ["Banane", "Pomme", "Ananas", "Solvant"], 1, "Éthyl caprylate = arôme pomme."),
      q("Que sont les alcools supérieurs?", ["L'éthanol uniquement", "Alcools autres que l'éthanol", "Des esters", "Des acides"], 1, "Alcools supérieurs = autres que éthanol."),
      q("Comment appelle-t-on les alcools supérieurs en anglais?", ["Higher alcohols", "Fusel alcohols", "Super alcohols", "Strong alcohols"], 1, "Fusel alcohols = alcools supérieurs."),
      q("À faible dose, les alcools supérieurs sont…", ["Positifs (roses, banane)", "Négatifs", "Neutres", "Toxiques"], 0, "Faible dose = positif (complexité)."),
      q("À forte dose, les alcools supérieurs sont…", ["Positifs", "Négatifs (solvant, chimique)", "Neutres", "Bénéfiques"], 1, "Forte dose = négatif (médicinal, solvant)."),
      q("Quel alcool supérieur donne un arôme banane/solvant?", ["Isobutanol", "n-Propanol", "Alcool isoamylique", "Méthanol"], 2, "Alcool isoamylique = banane/solvant."),
      q("Quelle concentration d'alcools supérieurs est souhaitée?", ["Très élevée", "Élevée", "Moyenne", "Faible"], 3, "Concentration faible souhaitée."),
      q("Dans quel style recherche-t-on les alcools supérieurs?", ["Pilsner", "Triple belge", "Lager légère", "Bière sans alcool"], 1, "Triple belge, barley wine, bières fortes."),
      q("Quel effet a une température de fermentation basse?", ["Plus d'esters", "Moins d'esters, profil propre", "Aucun effet", "Arrêt fermentation"], 1, "T° basse = moins d'esters, plus propre."),
      q("Quel effet a une température de fermentation haute?", ["Moins d'esters", "Plus d'esters, profil fruité", "Aucun effet", "Arrêt fermentation"], 1, "T° haute = plus d'esters, plus fruité."),
      q("Qui fournit la température idéale de fermentation?", ["Le brasseur", "Le fabricant de levure", "Le malteur", "Personne"], 1, "Le fabricant indique la T° idéale."),
      q("La température de fermentation influence…", ["Uniquement la durée", "Le profil aromatique", "Uniquement l'alcool", "Rien"], 1, "T° = impact crucial sur arômes."),
      q("Combien de cellules vivantes dans 1g de levure sèche?", ["7 × 10⁶", "7 × 10⁹", "7 × 10¹²", "7 × 10³"], 1, "~7 milliards de cellules/gramme."),
      q("Pourquoi connaître la concentration en levures vivantes?", ["Pour la couleur", "Pour l'ensemencement", "Pour l'amertume", "Pour le pH"], 1, "Calcul des populations et ensemencements."),
      q("Les esters donnent des arômes…", ["Amers", "Fruités", "Terreux", "Métalliques"], 1, "Esters = arômes fruités."),
      q("Quelle famille aromatique est produite par haute fermentation?", ["Esters", "Tannins", "Acides aminés", "Minéraux"], 0, "Levures hautes produisent beaucoup d'esters."),
      q("Un arôme de banane vient de…", ["Éthyl acétate", "Isoamyl acétate", "Éthyl hexanoate", "Éthyl caprylate"], 1, "Isoamyl acétate = banane caractéristique."),
      q("Un arôme d'ananas vient de…", ["Éthyl acétate", "Isoamyl acétate", "Éthyl hexanoate", "n-Propanol"], 2, "Éthyl hexanoate = ananas tropical."),
      q("Les alcools supérieurs à forte dose donnent un arôme…", ["Fruité agréable", "Médicinal/solvant", "Floral", "Neutre"], 1, "Forte dose = chimique, médicinal."),
      q("Dans quelle bière recherche-t-on la complexité des alcools supérieurs?", ["Lager légère", "Pilsner", "Barley wine", "Bière de table"], 2, "Barley wine = bière forte complexe."),
      q("Que faut-il contrôler pour influencer le profil aromatique?", ["La couleur du malt", "La température de fermentation", "Le pH de l'eau", "Le temps d'ébullition"], 1, "T° fermentation = profil aromatique."),
      q("Les esters sont composés de…", ["Acide + Alcool", "Sucre + Enzyme", "Protéine + Lipide", "Eau + Minéraux"], 0, "Ester = Acide + Alcool."),
      q("Un profil 'propre' et 'net' est obtenu avec…", ["T° haute", "T° basse", "T° variable", "Sans levure"], 1, "T° basse = profil propre (moins d'esters)."),
      q("Quel arôme l'éthyl acétate peut-il donner?", ["Banane", "Fruit/Solvant", "Ananas", "Rose"], 1, "Éthyl acétate = fruit ou solvant.")
    ]
  },
  {
    id: "tauxEnsemencement",
    category: "LEVURE",
    title: "34. Taux d'ensemencement",
    ficheRich: [
      {
        title: "Définition",
        items: [
          "**Taux d'ensemencement** (Yeast pitching rate) : Quantité initiale de levure introduite au début de la fermentation",
          "**Important** : On compte toujours les levures VIVANTES !"
        ]
      },
      {
        title: "Règle fondamentale",
        items: [
          "**TOUJOURS ensemencer le plus tôt possible** dès que le brassin est refroidi !",
          "**Pourquoi ?**",
          "→ Assure une fermentation complète sans blocage",
          "→ Résultat reproductible et de qualité",
          "→ Évite la colonisation par d'autres micro-organismes"
        ]
      },
      {
        title: "Règles d'ensemencement",
        items: [
          "**Règle classique** : 1 million de cellules / ml / °Plato",
          "**Fermentation basse (lager)** : 1.5 millions/ml/°P",
          "**Fermentation haute (ale)** : 0.75 millions/ml/°P",
          "**Observation** : On a 'toujours' tendance à trop peu ensemencer !"
        ]
      },
      {
        title: "Conséquences d'un ensemencement EXCESSIF (rare)",
        items: [
          "**Déséquilibre des esters** : Moins d'arômes fruités",
          "**Fermentation trop rapide** : Moins de développement aromatique",
          "Ce cas est rare en pratique"
        ]
      },
      {
        title: "Conséquences d'un ensemencement INSUFFISANT (fréquent)",
        items: [
          "**Esters excessifs** : Trop d'arômes fruités/solvant",
          "**Diacétyle** : Goût de beurre rance",
          "**H₂S** : Odeur d'œuf pourri",
          "**Côté solvant** : Arômes désagréables",
          "**Démarrage lent** : Fermentation qui traîne",
          "**Atténuation incomplète** : Sucres résiduels élevés",
          "**Risque de contamination** : Si démarrage trop lent"
        ]
      },
      {
        title: "Ensemencement pour refermentation en bouteille",
        items: [
          "**Minimum** : 100 000 cellules/ml",
          "**Recommandé** : 3 à 4 millions/ml",
          "**Objectif** : Éviter que la levure se comporte mal (Levure F2)",
          "**Attention** : Grande variabilité possible, mesurer la densité jusqu'à stabilisation"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ Ensemencer dès que possible après refroidissement",
          "✅ Compter uniquement les levures VIVANTES",
          "✅ Lagers nécessitent plus de levures que les ales",
          "✅ Sous-ensemencement = problème le plus fréquent"
        ]
      }
    ],
    questions: [
      q("Que signifie 'pitching rate' en français?", ["Densité primitive", "Taux d'ensemencement", "Température de fermentation", "Atténuation"], 1, "Pitching rate = taux d'ensemencement."),
      q("Qu'est-ce que le taux d'ensemencement?", ["La température", "La quantité de levure introduite", "Le pH du moût", "La durée de fermentation"], 1, "Quantité initiale de levure au début."),
      q("Quelles levures compte-t-on?", ["Toutes les levures", "Les levures VIVANTES", "Les levures mortes", "Les bactéries"], 1, "On compte uniquement les levures vivantes."),
      q("Quand faut-il ensemencer?", ["Avant le brassage", "Le plus tôt possible après refroidissement", "Après 24h", "N'importe quand"], 1, "Dès que le brassin est refroidi !"),
      q("Pourquoi ensemencer rapidement?", ["Pour la couleur", "Pour éviter les contaminations", "Pour l'amertume", "Pour le pH"], 1, "Évite colonisation par autres micro-organismes."),
      q("Quelle est la règle classique d'ensemencement?", ["0.5 million/ml/°P", "1 million/ml/°P", "2 millions/ml/°P", "5 millions/ml/°P"], 1, "1 million de cellules/ml/°Plato."),
      q("Quel taux pour une fermentation basse (lager)?", ["0.75 million/ml/°P", "1 million/ml/°P", "1.5 millions/ml/°P", "2 millions/ml/°P"], 2, "Lagers = 1.5 millions/ml/°P."),
      q("Quel taux pour une fermentation haute (ale)?", ["0.75 million/ml/°P", "1 million/ml/°P", "1.5 millions/ml/°P", "2 millions/ml/°P"], 0, "Ales = 0.75 millions/ml/°P."),
      q("Quelle est la tendance commune en ensemencement?", ["Trop ensemencer", "Trop peu ensemencer", "Ensemencer juste", "Ne pas ensemencer"], 1, "Tendance à sous-ensemencer."),
      q("Un ensemencement excessif est…", ["Très fréquent", "Rare", "Impossible", "Normal"], 1, "L'ensemencement excessif est rare."),
      q("Un ensemencement excessif donne…", ["Plus d'esters", "Moins d'esters", "Plus de diacétyle", "Plus de H₂S"], 1, "Trop de levure = moins d'arômes fruités."),
      q("Un ensemencement insuffisant donne…", ["Moins d'esters", "Esters excessifs", "Pas d'alcool", "Bière claire"], 1, "Sous-ensemencement = trop d'esters."),
      q("Quel défaut vient d'un sous-ensemencement?", ["Trop d'amertume", "Diacétyle (beurre rance)", "Trop de CO₂", "Bière trop claire"], 1, "Diacétyle = goût beurre rance."),
      q("Que signifie H₂S?", ["Sucre résiduel", "Sulfure d'hydrogène (œuf pourri)", "Alcool supérieur", "Ester"], 1, "H₂S = odeur d'œuf pourri."),
      q("Un sous-ensemencement provoque…", ["Démarrage rapide", "Démarrage lent", "Pas de fermentation", "Trop de CO₂"], 1, "Démarrage lent de la fermentation."),
      q("Quel risque avec un démarrage lent?", ["Bière trop amère", "Contamination", "Trop d'alcool", "Bière trop claire"], 1, "Risque de contamination microbienne."),
      q("Un sous-ensemencement cause une atténuation…", ["Complète", "Incomplète", "Excessive", "Nulle"], 1, "Atténuation incomplète = sucres résiduels."),
      q("Quel type de fermentation nécessite plus de levure?", ["Fermentation haute", "Fermentation basse", "Les deux pareil", "Aucune"], 1, "Lagers = 1.5M vs Ales = 0.75M."),
      q("Pour une refermentation en bouteille, le minimum est…", ["10 000 cellules/ml", "100 000 cellules/ml", "1 million/ml", "10 millions/ml"], 1, "Minimum 100 000 cellules/ml."),
      q("Pour une refermentation en bouteille, le taux recommandé est…", ["100 000 cellules/ml", "1 million/ml", "3 à 4 millions/ml", "10 millions/ml"], 2, "Recommandé 3-4 millions/ml."),
      q("Qu'est-ce que la levure F2?", ["Levure fraîche", "Levure de deuxième génération (refermentation)", "Levure morte", "Levure sauvage"], 1, "F2 = refermentation en bouteille."),
      q("Un goût de beurre rance indique…", ["Trop de houblon", "Diacétyle", "Trop d'alcool", "Infection lactique"], 1, "Diacétyle = beurre rance."),
      q("Une odeur d'œuf pourri indique…", ["Diacétyle", "H₂S", "Esters", "Tannins"], 1, "H₂S = sulfure d'hydrogène."),
      q("Un arôme de solvant peut venir de…", ["Sur-ensemencement", "Sous-ensemencement", "Trop de malt", "Trop d'eau"], 1, "Sous-ensemencement = esters/solvant excessifs."),
      q("Pourquoi ensemencer assure la qualité?", ["Couleur uniforme", "Résultat reproductible", "Moins de houblon", "Plus d'amertume"], 1, "Résultat reproductible et fermentation complète."),
      q("Une fermentation trop rapide peut donner…", ["Plus d'arômes", "Moins de développement aromatique", "Plus d'alcool", "Moins de CO₂"], 1, "Trop rapide = moins d'arômes complexes."),
      q("Le problème le plus fréquent est…", ["Sur-ensemencement", "Sous-ensemencement", "Bonne quantité", "Aucun problème"], 1, "Tendance à trop peu ensemencer."),
      q("Pour 20L à 15°P en lager, combien de cellules faut-il?", ["150 millions", "300 millions", "450 millions", "600 millions"], 2, "1.5M × 20000ml × 15°P = 450M."),
      q("Pour 10L à 12°P en ale, combien de cellules faut-il?", ["45 millions", "90 millions", "120 millions", "180 millions"], 1, "0.75M × 10000ml × 12°P = 90M."),
      q("Quelle unité utilise-t-on pour les densités?", ["°C", "°Plato (°P)", "%", "g/L"], 1, "°Plato pour les densités.")
    ]
  },
  {
    id: "attenuationLimite",
    category: "LEVURE",
    title: "35. Atténuation limite (AL)",
    ficheRich: [
      {
        title: "Définition",
        items: [
          "**Atténuation limite (AL)** : Atténuation maximale qui pourrait être atteinte si toutes les conditions optimales étaient remplies",
          "**Représentativité** : Dépend du couple 'moût-levure'",
          "**Usage** : Savoir quand 'donner le coup de froid' et terminer la fermentation"
        ]
      },
      {
        title: "Comment déterminer l'atténuation limite ?",
        items: [
          "**1.** Prélever stérilement du moût en pleine fermentation",
          "**2.** Ajouter un excédent de levure",
          "**3.** Placer l'échantillon à la température optimale de fermentation",
          "**4.** Sans agitation",
          "**5.** Mesurer la densité jusqu'à stabilisation (2-3 jours)"
        ]
      },
      {
        title: "Interprétation des résultats",
        items: [
          "**Différence AL - FG ≈ 0.2°P** : Normal, acceptable",
          "**Différence AL - FG ≥ 1°P** : Problème de fermentation",
          "**AL** = atténuation maximale théorique",
          "**FG** = densité finale réelle"
        ]
      },
      {
        title: "Causes d'une différence importante (≥1°P)",
        items: [
          "**Ensemencement insuffisant** : Pas assez de levures au départ",
          "**Aération insuffisante** : Manque d'oxygène pour la levure",
          "**Problème de gestion** : Température, nutriments, stress de la levure"
        ]
      },
      {
        title: "Utilité pratique pour le brasseur",
        items: [
          "**Timing** : Savoir quand la fermentation est terminée",
          "**Décision** : Quand refroidir ou transférer la bière",
          "**Diagnostic** : Identifier les problèmes de fermentation",
          "**Référence** : Compare AL vs FG pour évaluer la performance"
        ]
      },
      {
        title: "Paramètres à surveiller",
        items: [
          "**Activité de la fermentation** : Observation visuelle du dégagement de CO₂",
          "**pH** : Évolution pendant la fermentation",
          "**Quantité de sucre restant** : Mesure de la densité",
          "**Stabilisation** : Densité constante sur 2-3 jours"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ AL = atténuation maximale théorique du couple moût-levure",
          "✅ Différence normale AL-FG ≈ 0.2°P",
          "✅ Différence ≥1°P indique un problème",
          "✅ Permet de savoir quand terminer la fermentation"
        ]
      }
    ],
    questions: [
      q("Que signifie AL?", ["Alcool Limite", "Atténuation Limite", "Acidité Limite", "Amertume Limite"], 1, "AL = Atténuation Limite."),
      q("Qu'est-ce que l'atténuation limite?", ["L'alcool maximum", "L'atténuation maximale théorique", "La densité finale", "Le pH final"], 1, "AL = atténuation max dans conditions optimales."),
      q("De quoi dépend l'atténuation limite?", ["Du houblon", "Du couple moût-levure", "De l'eau", "Du temps"], 1, "AL dépend du couple moût-levure."),
      q("À quoi sert l'atténuation limite?", ["Calculer l'IBU", "Savoir quand terminer la fermentation", "Mesurer l'amertume", "Calculer la couleur"], 1, "Savoir quand donner le coup de froid."),
      q("Comment prélève-t-on pour mesurer l'AL?", ["N'importe comment", "Stérilement en pleine fermentation", "À la fin de la fermentation", "Avant la fermentation"], 1, "Prélèvement stérile pendant fermentation."),
      q("Que fait-on après le prélèvement pour l'AL?", ["On le chauffe", "On ajoute un excédent de levure", "On le dilue", "On le filtre"], 1, "Ajouter un excédent de levure."),
      q("À quelle température place-t-on l'échantillon AL?", ["Température ambiante", "Température optimale de fermentation", "4°C", "30°C"], 1, "T° optimale de fermentation."),
      q("Faut-il agiter l'échantillon pour l'AL?", ["Oui constamment", "Non, sans agitation", "Parfois", "Seulement au début"], 1, "Sans agitation."),
      q("Combien de temps mesure-t-on l'AL?", ["1 heure", "Jusqu'à stabilisation (2-3 jours)", "1 semaine", "1 mois"], 1, "Mesurer jusqu'à stabilisation 2-3 jours."),
      q("Quelle différence AL-FG est normale?", ["0°P", "≈0.2°P", "≥1°P", "≥5°P"], 1, "Différence normale ≈ 0.2°P."),
      q("Quelle différence AL-FG indique un problème?", ["0.1°P", "0.2°P", "≥1°P", "0.5°P"], 2, "Différence ≥1°P = problème."),
      q("Que signifie FG?", ["Fast Growth", "Final Gravity", "First Gravity", "Fermentation Goal"], 1, "FG = Final Gravity (densité finale)."),
      q("Si AL-FG = 1.5°P, que se passe-t-il?", ["Tout est normal", "Problème de fermentation", "Fermentation parfaite", "Trop d'alcool"], 1, "≥1°P = problème de fermentation."),
      q("Quelle cause peut expliquer AL-FG élevé?", ["Trop de houblon", "Ensemencement insuffisant", "Trop d'eau", "Trop de couleur"], 1, "Sous-ensemencement = différence AL-FG."),
      q("Une aération insuffisante provoque…", ["Trop d'alcool", "Différence AL-FG importante", "Bière trop amère", "Bière trop claire"], 1, "Manque O₂ = fermentation incomplète."),
      q("L'AL permet de décider…", ["La couleur", "Quand refroidir", "L'amertume", "Le pH"], 1, "Décision de refroidir/transférer."),
      q("L'AL permet d'identifier…", ["La couleur du malt", "Les problèmes de fermentation", "Le type de houblon", "La source d'eau"], 1, "Diagnostic des problèmes."),
      q("Que surveille-t-on pendant la fermentation?", ["Uniquement la couleur", "Activité, pH, sucre restant", "Uniquement l'amertume", "Uniquement le houblon"], 1, "Activité, pH, densité (sucres)."),
      q("Comment sait-on que la densité est stabilisée?", ["Après 1 heure", "Constante sur 2-3 jours", "Elle change toujours", "Après 1 mois"], 1, "Stabilisation = constante 2-3 jours."),
      q("L'AL est une valeur…", ["Réelle mesurée en cuve", "Théorique maximale", "Aléatoire", "Sans importance"], 1, "AL = valeur théorique max."),
      q("Pour un bon diagnostic, on compare…", ["AL vs OG", "AL vs FG", "FG vs OG", "pH vs T°"], 1, "Comparer AL et FG."),
      q("Si AL = FG (différence 0), c'est…", ["Parfait", "Suspect, vérifier", "Normal", "Impossible"], 1, "Différence 0 est rare, vérifier."),
      q("Que signifie 'donner le coup de froid'?", ["Chauffer la bière", "Refroidir pour arrêter la fermentation", "Ajouter de l'eau froide", "Filtrer"], 1, "Refroidir pour terminer fermentation."),
      q("L'AL dépend-elle uniquement de la levure?", ["Oui", "Non, du couple moût-levure", "Oui, uniquement du moût", "Elle est constante"], 1, "Couple moût-levure = AL spécifique."),
      q("Pourquoi ajoute-t-on un excédent de levure pour l'AL?", ["Pour diluer", "Pour assurer fermentation complète", "Pour le goût", "Pour la couleur"], 1, "Excès levure = conditions optimales."),
      q("L'AL mesure…", ["La densité initiale", "Le potentiel d'atténuation max", "L'amertume", "La couleur"], 1, "Potentiel max d'atténuation."),
      q("Une mauvaise gestion de fermentation provoque…", ["Couleur parfaite", "Différence AL-FG élevée", "Plus de houblon", "Moins d'eau"], 1, "Gestion = impact sur AL-FG."),
      q("Quel paramètre n'est PAS surveillé pour l'AL?", ["Activité fermentation", "pH", "Sucre restant", "Couleur du houblon"], 3, "Couleur houblon non pertinente pour AL."),
      q("L'AL permet d'optimiser…", ["La couleur", "Le timing de fin de fermentation", "L'amertume", "Le type de malt"], 1, "Timing optimal de fin."),
      q("Si AL-FG = 0.3°P, c'est…", ["Problème grave", "Acceptable (proche de 0.2)", "Très mauvais", "Impossible"], 1, "0.3°P proche de 0.2 = acceptable.")
    ]
  },
  {
    id: "calculRefermentation",
    category: "LEVURE",
    title: "36. Calcul de refermentation en bouteille",
    ficheRich: [
      {
        title: "Prérequis - Ce qu'il faut connaître",
        items: [
          "**Volume de bière** : À refermenter",
          "**Densité apparente** : Mesurée",
          "**Atténuation limite** : De la souche utilisée",
          "**Saturation actuelle en CO₂** : Mesurée ou estimée",
          "**Saturation ciblée en CO₂** : Souhaitée selon le style"
        ]
      },
      {
        title: "Niveaux de carbonatation selon le type de bière",
        items: [
          "**Sous-saturée** : 0 à 2.8 g CO₂/L",
          "**Stout & Porters** : 3 à 4.5 g/L (légère)",
          "**Pils et bières classiques** : 4.5 à 5.2 g/L (moyenne)",
          "**Spéciales fort saturées** (blanches, lambics) : 5.2 à 8 g/L",
          "**Sur-saturée** (bière très typée) : >8 g/L",
          "**Duvel** : 9 g/L (extrême)"
        ]
      },
      {
        title: "Formule de calcul générale",
        items: [
          "**Formule** : Sucre (g) = ((CO₂ visé - CO₂ présent - CO₂ 'limite') × Volume (L) × 2) / concentration du sucre",
          "**Facteur 2** : Car 1g de sucre produit ~0.5g de CO₂",
          "**CO₂ limite** : CO₂ qui sera produit par les sucres résiduels fermentescibles"
        ]
      },
      {
        title: "Exemple pratique - Calcul détaillé",
        items: [
          "**Volume** : 100 L",
          "**CO₂ visé** : 8 g/L (fort pétillante)",
          "**Température garde** : 4°C",
          "**Saturation actuelle** : ~3.8 g/L (table de solubilité)",
          "**Atténuation mesurée** : 2.5°P",
          "**Atténuation limite** : 2.0°P",
          "**Reste fermentescible** : 0.5°P = 5g/L",
          "**Facteur correctif** : 30-60% (empirique) → 30% × 5g = 1.5g",
          "**CO₂ des résidus** : 1.5g sucre × 0.5 = 0.75g CO₂/L",
          "**Calcul final** : ((8 - 3.8 - 0.75) × 100 × 2) / 1 = 690g",
          "**Résultat** : ~6.9 g/L de sucre à ajouter"
        ]
      },
      {
        title: "Types de sucre pour refermentation",
        items: [
          "**Sucre blanc (cristaux)** : Concentration 100% (référence)",
          "**Miel** : Concentration ~80% (apporte des arômes)",
          "**Sirop** : Concentration ~70% (plus facile à dissoudre)",
          "**Adapter la quantité** selon la concentration du sucre utilisé"
        ]
      },
      {
        title: "Facteurs à prendre en compte",
        items: [
          "**Température de garde** : Influence la saturation en CO₂",
          "**Contre-pression** : Si présente, augmente la saturation",
          "**Sucres résiduels** : Peuvent fermenter partiellement (30-60%)",
          "**Table de solubilité** : Pour estimer le CO₂ actuel selon T°"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ 1g de sucre produit ~0.5g de CO₂",
          "✅ Le niveau de carbonatation varie selon le style de bière",
          "✅ Tenir compte du CO₂ déjà présent et des sucres résiduels",
          "✅ Adapter la quantité selon le type de sucre utilisé"
        ]
      }
    ],
    questions: [
      q("Que faut-il connaître pour calculer la refermentation?", ["Uniquement le volume", "Volume, densité, AL, CO₂ actuel/visé", "Uniquement le CO₂ visé", "Uniquement la température"], 1, "5 prérequis nécessaires."),
      q("Quelle saturation pour un Stout?", ["0-2.8 g/L", "3-4.5 g/L", "4.5-5.2 g/L", ">8 g/L"], 1, "Stout = 3-4.5 g/L (légère)."),
      q("Quelle saturation pour une Pils?", ["3-4.5 g/L", "4.5-5.2 g/L", "5.2-8 g/L", ">8 g/L"], 1, "Pils = 4.5-5.2 g/L (moyenne)."),
      q("Quelle saturation pour une blanche/lambic?", ["3-4.5 g/L", "4.5-5.2 g/L", "5.2-8 g/L", ">8 g/L"], 2, "Blanches/lambics = 5.2-8 g/L."),
      q("Quelle saturation a la Duvel?", ["5 g/L", "7 g/L", "9 g/L", "12 g/L"], 2, "Duvel = 9 g/L (extrême)."),
      q("Combien de CO₂ produit 1g de sucre?", ["0.25g", "0.5g", "1g", "2g"], 1, "1g sucre → ~0.5g CO₂."),
      q("Pourquoi y a-t-il un facteur 2 dans la formule?", ["Pour doubler le volume", "Car 1g sucre → 0.5g CO₂", "Pour la sécurité", "C'est une erreur"], 1, "Rendement = 0.5, donc ×2 pour compenser."),
      q("Que représente le CO₂ 'limite' dans la formule?", ["Le maximum possible", "Le CO₂ des sucres résiduels", "Le CO₂ minimal", "Le CO₂ initial"], 1, "CO₂ limite = produit par résidus fermentescibles."),
      q("Quelle est la concentration du sucre blanc?", ["70%", "80%", "100%", "50%"], 2, "Sucre blanc = 100% (référence)."),
      q("Quelle est la concentration du miel?", ["~70%", "~80%", "~100%", "~50%"], 1, "Miel = ~80% de concentration."),
      q("Quelle est la concentration du sirop?", ["~50%", "~70%", "~80%", "~100%"], 1, "Sirop = ~70% de concentration."),
      q("Quel avantage a le miel?", ["Plus concentré", "Apporte des arômes", "Moins cher", "Plus rapide"], 1, "Miel = arômes supplémentaires."),
      q("Quel avantage a le sirop?", ["Plus concentré", "Plus d'arômes", "Plus facile à dissoudre", "Plus cher"], 2, "Sirop = dissolution facile."),
      q("Dans l'exemple, quel est le volume?", ["50 L", "100 L", "200 L", "500 L"], 1, "Volume = 100 L."),
      q("Dans l'exemple, quel est le CO₂ visé?", ["4.5 g/L", "6 g/L", "8 g/L", "10 g/L"], 2, "CO₂ visé = 8 g/L (fort pétillante)."),
      q("Dans l'exemple, quelle est la saturation actuelle?", ["2.8 g/L", "3.8 g/L", "4.8 g/L", "5.8 g/L"], 1, "Saturation actuelle = 3.8 g/L."),
      q("Dans l'exemple, combien reste-t-il de fermentescible?", ["0.5°P", "1°P", "2°P", "5°P"], 0, "Reste = AL - Att mesurée = 0.5°P."),
      q("Que vaut 0.5°P en g/L de sucre?", ["2.5g", "5g", "10g", "15g"], 1, "0.5°P = 5g sucre/L."),
      q("Quel facteur correctif applique-t-on aux résidus?", ["10-20%", "30-60%", "70-90%", "100%"], 1, "Facteur empirique 30-60%."),
      q("Si 30% de 5g fermente, combien de sucre?", ["0.5g", "1.5g", "2.5g", "4.5g"], 1, "30% × 5g = 1.5g."),
      q("Combien de CO₂ produisent 1.5g de sucre?", ["0.5g", "0.75g", "1g", "1.5g"], 1, "1.5g × 0.5 = 0.75g CO₂."),
      q("Dans l'exemple, quel est le résultat final?", ["490g", "590g", "690g", "790g"], 2, "690g de sucre total."),
      q("Combien de g/L de sucre dans l'exemple?", ["4.9 g/L", "5.9 g/L", "6.9 g/L", "7.9 g/L"], 2, "690g / 100L = 6.9 g/L."),
      q("Qu'influence la température de garde?", ["La couleur", "La saturation en CO₂", "L'amertume", "Le pH"], 1, "T° = solubilité du CO₂."),
      q("Que consulte-t-on pour estimer le CO₂ actuel?", ["Table IBU", "Table de solubilité CO₂", "Table des malts", "Table des houblons"], 1, "Table de solubilité selon T°."),
      q("Une bière sous-saturée a…", ["0-2.8 g/L", "3-4.5 g/L", "4.5-5.2 g/L", ">8 g/L"], 0, "Sous-saturée = 0-2.8 g/L."),
      q("Une bière sur-saturée a…", ["3-4.5 g/L", "4.5-5.2 g/L", "5.2-8 g/L", ">8 g/L"], 3, "Sur-saturée = >8 g/L."),
      q("Pourquoi soustraire le CO₂ présent?", ["Pour l'amertume", "Pour ne compter que le CO₂ à ajouter", "Pour la couleur", "C'est une erreur"], 1, "On calcule uniquement le CO₂ à produire."),
      q("Si on utilise du miel à 80%, comment ajuster?", ["Diviser par 0.8", "Multiplier par 0.8", "Ne rien faire", "Diviser par 2"], 0, "Quantité / concentration = / 0.8."),
      q("Quel type de bière est le plus carbonaté?", ["Stout", "Pils", "Duvel", "Bière sous-saturée"], 2, "Duvel = 9 g/L (le plus élevé cité).")
    ]
  },
  {
    id: "levureSecheVsLiquide",
    category: "LEVURE",
    title: "40. Levure sèche vs liquide",
    ficheRich: [
      {
        title: "Levures SÈCHES - Marques principales",
        items: [
          "**Fermentis** : Leader du marché",
          "**Munton's** : Marque britannique",
          "**Danstar** : Producteur canadien",
          "**Brewferm** : Marque belge",
          "**Cooper's** : Marque australienne"
        ]
      },
      {
        title: "Levures SÈCHES - Avantages",
        items: [
          "**Prix** : Bon marché, économique",
          "**Facilité** : Pas besoin de starter",
          "**Population** : Élevée par sachet",
          "**Viabilité** : Maintenue pendant le transport",
          "**Conservation** : BBD (Best Before Date) de 1 à 2 ans",
          "**Simplicité** : Prêt à l'emploi"
        ]
      },
      {
        title: "Levures SÈCHES - Inconvénients",
        items: [
          "**Choix limité** : Moins de variétés disponibles",
          "**Sélection** : Le processus de séchage 'sélectionne' certaines levures",
          "**Profil** : Peut ne pas correspondre exactement au profil voulu",
          "**Moins spécifique** : Profils aromatiques plus génériques"
        ]
      },
      {
        title: "Levures SÈCHES - Processus de fabrication",
        items: [
          "**1.** Laboratoire : Culture initiale",
          "**2.** Fermentation : Multiplication",
          "**3.** Centrifugation : Concentration",
          "**4.** Séchage : Élimination de l'eau",
          "**5.** Conditionnement : Mise en sachets"
        ]
      },
      {
        title: "Levures LIQUIDES - Marques principales",
        items: [
          "**White Labs** : Leader américain",
          "**Wyeast** : Marque américaine de référence"
        ]
      },
      {
        title: "Levures LIQUIDES - Avantages",
        items: [
          "**Grand choix** : Beaucoup de variétés disponibles",
          "**Profil gustatif** : Idéal, proche de la souche d'origine",
          "**Spécificité** : Souches très spécifiques disponibles",
          "**Authenticité** : Profils aromatiques précis"
        ]
      },
      {
        title: "Levures LIQUIDES - Inconvénients",
        items: [
          "**Prix** : Plus élevé que les sèches",
          "**Starter** : Souvent requis pour atteindre le taux d'ensemencement",
          "**Viabilité** : Perte pendant le transport",
          "**Conservation** : BBD très limitée (quelques mois)",
          "**Conditionnement** : Tubes ou sachets multiples nécessaires"
        ]
      },
      {
        title: "Tableau comparatif résumé",
        items: [
          "**Prix** : Sèche ⭐⭐⭐⭐⭐ | Liquide ⭐⭐",
          "**Choix variétés** : Sèche ⭐⭐ | Liquide ⭐⭐⭐⭐⭐",
          "**Facilité** : Sèche ⭐⭐⭐⭐⭐ | Liquide ⭐⭐⭐",
          "**Profil aromatique** : Sèche ⭐⭐⭐ | Liquide ⭐⭐⭐⭐⭐",
          "**Conservation** : Sèche ⭐⭐⭐⭐⭐ | Liquide ⭐⭐",
          "**Viabilité transport** : Sèche ⭐⭐⭐⭐⭐ | Liquide ⭐⭐⭐"
        ]
      }
    ],
    questions: [
      q("Quelle marque N'est PAS une levure sèche?", ["Fermentis", "White Labs", "Danstar", "Munton's"], 1, "White Labs = levure liquide."),
      q("Quelle marque N'est PAS une levure liquide?", ["White Labs", "Wyeast", "Fermentis", "Aucune des deux"], 2, "Fermentis = levure sèche."),
      q("Quel est le principal avantage des levures sèches?", ["Profil aromatique", "Prix et facilité", "Grande variété", "Starter facile"], 1, "Sèches = bon marché et faciles."),
      q("Quel est le principal avantage des levures liquides?", ["Prix", "Conservation", "Grand choix et profil précis", "Facilité"], 2, "Liquides = variétés et profils."),
      q("Les levures sèches nécessitent-elles un starter?", ["Toujours", "Généralement non", "Toujours oui", "Parfois"], 1, "Pas besoin de starter (population élevée)."),
      q("Les levures liquides nécessitent-elles un starter?", ["Jamais", "Rarement", "Souvent requis", "Toujours"], 2, "Souvent requis pour levures liquides."),
      q("Quelle est la durée BBD des levures sèches?", ["1-2 semaines", "1-2 mois", "1-2 ans", "10 ans"], 2, "BBD sèches = 1-2 ans."),
      q("Quelle est la durée BBD des levures liquides?", ["Très limitée (quelques mois)", "1-2 ans", "5 ans", "Illimitée"], 0, "BBD liquides = très limitée."),
      q("Quel type de levure a le plus grand choix?", ["Sèche", "Liquide", "Les deux pareil", "Aucune"], 1, "Liquides = beaucoup de variétés."),
      q("Quel type de levure est le moins cher?", ["Sèche", "Liquide", "Les deux pareil", "Variable"], 0, "Sèches = bon marché."),
      q("Quel type de levure maintient mieux la viabilité au transport?", ["Sèche", "Liquide", "Les deux pareil", "Aucune"], 0, "Sèches = viabilité maintenue."),
      q("Quel type de levure a le meilleur profil aromatique?", ["Sèche", "Liquide", "Les deux pareil", "Aucune"], 1, "Liquides = profil idéal."),
      q("Que signifie BBD?", ["Best Brewery Date", "Best Before Date", "Better Beer Date", "Begin Brewing Date"], 1, "BBD = Best Before Date."),
      q("Quelle est la première étape de fabrication des levures sèches?", ["Séchage", "Laboratoire", "Conditionnement", "Centrifugation"], 1, "Laboratoire → Fermentation → etc."),
      q("Quelle est l'étape après la fermentation pour les sèches?", ["Conditionnement", "Séchage", "Centrifugation", "Laboratoire"], 2, "Fermentation → Centrifugation."),
      q("Quelle est la dernière étape de fabrication?", ["Séchage", "Fermentation", "Conditionnement", "Laboratoire"], 2, "Conditionnement en sachets."),
      q("Pourquoi le séchage 'sélectionne' les levures?", ["Toutes survivent", "Seules les plus résistantes survivent", "Aucune ne survit", "C'est aléatoire"], 1, "Séchage = sélection naturelle."),
      q("Quel inconvénient ont les levures sèches?", ["Prix élevé", "Choix limité", "Pas de conservation", "Trop de starter"], 1, "Sèches = moins de variétés."),
      q("Quel inconvénient ont les levures liquides?", ["Choix limité", "Prix élevé et starter requis", "Conservation excellente", "Trop faciles"], 1, "Liquides = cher + starter."),
      q("Quelle marque est leader des levures sèches?", ["White Labs", "Wyeast", "Fermentis", "Aucune"], 2, "Fermentis = leader marché sèches."),
      q("Quelle marque est leader des levures liquides?", ["Fermentis", "Danstar", "White Labs", "Cooper's"], 2, "White Labs et Wyeast = leaders liquides."),
      q("La population par sachet de levure sèche est…", ["Faible", "Moyenne", "Élevée", "Variable"], 2, "Sèches = population élevée."),
      q("Les levures liquides sont proches de…", ["Rien", "La souche d'origine", "Les levures sèches", "Les bactéries"], 1, "Liquides = proche souche origine."),
      q("Pour un profil aromatique précis, on préfère…", ["Sèches", "Liquides", "Les deux", "Aucune"], 1, "Liquides = profil précis."),
      q("Pour la facilité d'utilisation, on préfère…", ["Sèches", "Liquides", "Les deux", "Aucune"], 0, "Sèches = plus faciles."),
      q("Cooper's est une marque de levure…", ["Sèche", "Liquide", "Les deux", "Ni l'une ni l'autre"], 0, "Cooper's = levure sèche."),
      q("Wyeast est une marque de levure…", ["Sèche", "Liquide", "Les deux", "Ni l'une ni l'autre"], 1, "Wyeast = levure liquide."),
      q("Le processus de séchage élimine…", ["Les levures", "L'eau", "Les arômes", "Le sucre"], 1, "Séchage = élimination eau."),
      q("Quel type se conserve le mieux?", ["Sèche", "Liquide", "Les deux pareil", "Aucune"], 0, "Sèches = meilleure conservation."),
      q("Pour une souche très spécifique, on choisit…", ["Sèche", "Liquide", "N'importe", "Aucune"], 1, "Liquides = souches spécifiques.")
    ]
  },
  {
    id: "diacetyle",
    category: "LEVURE",
    title: "38. Composés de fermentation - Le Diacétyle",
    ficheRich: [
      {
        title: "Identification",
        items: [
          "**Famille** : VDK (Vicinal DiKetones)",
          "**Molécule** : 2,3-Pentanedione",
          "**Flaveur** : Beurre rance, caramel au beurre",
          "**Seuil de perception** : Très bas (détectable à faible concentration)"
        ]
      },
      {
        title: "Acceptabilité du diacétyle",
        items: [
          "**Très légère touche** : Peut être positive dans certaines ales anglaises",
          "**Concentration élevée** : Défaut majeur, inacceptable",
          "**Contexte** : Dépend du style de bière"
        ]
      },
      {
        title: "Facteurs favorisant le diacétyle",
        items: [
          "**Ensemencement insuffisant** : Stress de la levure → production VDK",
          "**Fermentation trop froide** : Levure moins active, réduction lente",
          "**Contamination bactérienne** : Certaines bactéries en produisent"
        ]
      },
      {
        title: "Réduction naturelle du diacétyle",
        items: [
          "**Mécanisme** : Le diacétyle est réduit par la levure tant qu'elle est présente et active",
          "**Condition** : La levure doit rester en contact avec la bière",
          "**Processus naturel** : Fait partie du cycle de fermentation normal"
        ]
      },
      {
        title: "Conditions favorables à la réduction",
        items: [
          "**Températures élevées** : Réduction plus rapide du diacétyle",
          "**Fermentations hautes** : Moins de risque de diacétyle résiduel",
          "**Levure active** : Population suffisante et en bonne santé"
        ]
      },
      {
        title: "Diacetyl rest (repos diacétyle)",
        items: [
          "**Principe** : Laisser monter légèrement la température en fin de fermentation",
          "**Objectif** : Permettre à la levure de réduire les VDK",
          "**Application** : Surtout pour les lagers (fermentation basse)",
          "**Timing** : En fin de fermentation principale"
        ]
      },
      {
        title: "Solutions en cas de problème",
        items: [
          "**Stripping au CO₂** : Faire passer du CO₂ dans la bière pour éliminer le diacétyle",
          "**Stripping à l'azote** : Alternative au CO₂",
          "**⚠️ JAMAIS à l'air normal** : Risque d'oxydation",
          "**Ajout de levure fraîche** : Relancer la réduction enzymatique"
        ]
      },
      {
        title: "Évolution temporelle",
        items: [
          "**0-40h** : Production de diacétyle (augmentation)",
          "**40-80h** : Pic de concentration",
          "**80-240h** : Réduction par la levure (diminution)",
          "**Graphique** : Le diacétyle augmente puis diminue, tandis que l'éthanol augmente progressivement"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ Diacétyle = VDK = goût beurre rance",
          "✅ Seuil de perception très bas",
          "✅ Favorisé par sous-ensemencement et fermentation froide",
          "✅ Réduit naturellement par la levure active",
          "✅ Diacetyl rest utile pour les lagers"
        ]
      }
    ],
    questions: [
      q("Que signifie VDK?", ["Very Dark Ketones", "Vicinal DiKetones", "Volatile Dry Ketones", "Variable Diacetyl Ketones"], 1, "VDK = Vicinal DiKetones."),
      q("Quel est le nom de la molécule du diacétyle?", ["2,3-Butanedione", "2,3-Pentanedione", "2,4-Pentanedione", "Acétaldéhyde"], 1, "2,3-Pentanedione."),
      q("Quel goût donne le diacétyle?", ["Fruit", "Beurre rance", "Houblon", "Caramel sucré"], 1, "Beurre rance, caramel au beurre."),
      q("Le seuil de perception du diacétyle est…", ["Très élevé", "Moyen", "Très bas", "Variable"], 2, "Seuil très bas = détectable facilement."),
      q("Une légère touche de diacétyle est…", ["Toujours un défaut", "Peut être positive (ales anglaises)", "Toujours positive", "Impossible"], 1, "Acceptable dans certaines ales anglaises."),
      q("Une concentration élevée de diacétyle est…", ["Positive", "Défaut majeur", "Normale", "Recherchée"], 1, "Concentration élevée = défaut majeur."),
      q("Qu'est-ce qui favorise le diacétyle?", ["Sur-ensemencement", "Ensemencement insuffisant", "Trop de houblon", "Trop d'eau"], 1, "Sous-ensemencement = stress levure → VDK."),
      q("Une fermentation trop froide provoque…", ["Moins de diacétyle", "Plus de diacétyle", "Pas d'effet", "Meilleure qualité"], 1, "Fermentation froide = levure moins active → VDK."),
      q("Quelle contamination peut produire du diacétyle?", ["Virale", "Bactérienne", "Fongique", "Aucune"], 1, "Certaines bactéries produisent VDK."),
      q("Qui réduit naturellement le diacétyle?", ["Les bactéries", "La levure", "Le houblon", "Le malt"], 1, "La levure réduit le diacétyle."),
      q("Pour réduire le diacétyle, la levure doit être…", ["Morte", "Présente et active", "Absente", "Congelée"], 1, "Levure présente et active = réduction."),
      q("Quelle température favorise la réduction du diacétyle?", ["Très froide", "Élevée", "Variable", "Gelée"], 1, "Températures élevées = réduction rapide."),
      q("Quel type de fermentation a moins de diacétyle résiduel?", ["Basse", "Haute", "Spontanée", "Mixte"], 1, "Fermentation haute = moins de VDK résiduel."),
      q("Qu'est-ce que le 'diacetyl rest'?", ["Repos de la levure", "Montée de T° en fin de fermentation", "Ajout de diacétyle", "Filtration"], 1, "Repos diacétyle = montée T° pour réduction."),
      q("Le diacetyl rest est surtout utilisé pour…", ["Les ales", "Les lagers", "Les lambics", "Toutes les bières"], 1, "Surtout pour lagers (fermentation basse)."),
      q("Quand applique-t-on le diacetyl rest?", ["Au début", "En fin de fermentation", "Avant fermentation", "Jamais"], 1, "Fin de fermentation principale."),
      q("Que permet le diacetyl rest?", ["Augmenter le diacétyle", "Réduire les VDK", "Arrêter la fermentation", "Ajouter des arômes"], 1, "Permet à la levure de réduire VDK."),
      q("Le stripping au CO₂ permet de…", ["Augmenter le CO₂", "Éliminer le diacétyle", "Ajouter du goût", "Refroidir"], 1, "Stripping = élimination du diacétyle."),
      q("Peut-on faire un stripping à l'air normal?", ["Oui toujours", "NON, risque d'oxydation", "Oui parfois", "C'est recommandé"], 1, "JAMAIS à l'air normal → oxydation."),
      q("Quelle alternative au stripping CO₂?", ["Air", "Azote", "Oxygène", "Vapeur"], 1, "Azote = alternative au CO₂."),
      q("En cas de problème de diacétyle, on peut ajouter…", ["Du houblon", "De la levure fraîche", "Du malt", "De l'eau"], 1, "Levure fraîche = relance la réduction."),
      q("Quand le diacétyle atteint-il son pic?", ["0-20h", "40-80h", "120-160h", "200-240h"], 1, "Pic vers 40-80h de fermentation."),
      q("Après le pic, le diacétyle…", ["Augmente", "Reste stable", "Diminue", "Disparaît instantanément"], 2, "Diminue grâce à la levure."),
      q("Pendant que le diacétyle diminue, l'éthanol…", ["Diminue", "Reste stable", "Augmente", "Disparaît"], 2, "Éthanol augmente progressivement."),
      q("Le diacétyle est produit au…", ["Début de fermentation", "Milieu de fermentation", "Fin de fermentation", "Jamais"], 0, "Production en début, puis réduction."),
      q("Le diacétyle fait partie de quelle famille?", ["Esters", "VDK", "Alcools supérieurs", "Acides"], 1, "Famille VDK (Vicinal DiKetones)."),
      q("Pour éviter le diacétyle, il faut un ensemencement…", ["Insuffisant", "Suffisant", "Excessif", "Aucun"], 1, "Ensemencement suffisant = pas de stress."),
      q("Une levure stressée produit…", ["Moins de VDK", "Plus de VDK", "Pas de VDK", "Aucun effet"], 1, "Stress levure → plus de diacétyle."),
      q("Le diacétyle est réduit par un processus…", ["Chimique seulement", "Enzymatique par la levure", "Physique", "Impossible"], 1, "Réduction enzymatique par levure."),
      q("Dans quel style une touche de diacétyle est acceptable?", ["Pilsner", "Certaines ales anglaises", "Lagers", "Lambics"], 1, "Ales anglaises = touche légère acceptable.")
    ]
  },
  {
    id: "esters",
    category: "LEVURE",
    title: "39. Composés de fermentation - Les Esters",
    ficheRich: [
      {
        title: "Définition des esters",
        items: [
          "**Nature** : Composés aromatiques",
          "**Composition** : Acide + Alcool",
          "**Origine** : Produits lors de la fermentation",
          "**Flaveurs** : Arômes fruités (banane, pomme, poire, fruit)",
          "**Impact** : Caractéristiques aromatiques des bières, surtout ales"
        ]
      },
      {
        title: "Principaux esters en brasserie",
        items: [
          "**Isoamyl acétate** : Arôme banane (très courant, typique des weizen)",
          "**Éthyl acétate** : Arôme fruit/léger solvant (le plus abondant)",
          "**Éthyl caprylate** : Arôme pomme (fruité délicat)"
        ]
      },
      {
        title: "Facteurs favorisant la production d'esters (↑)",
        items: [
          "**Diminution de l'aération** : Moins d'O₂ → Plus d'esters",
          "**Augmentation de la température** : Fermentation plus chaude → Plus d'esters",
          "**Augmentation des précurseurs** : Plus d'alcools supérieurs → Plus d'esters",
          "**Densité plus élevée** : OG élevée → Plus d'esters",
          "**Trub plus important** : Plus de matière en suspension → Plus d'esters"
        ]
      },
      {
        title: "Contrôle des esters - Pour AUGMENTER",
        items: [
          "**Fermenter plus chaud** : Température élevée stimule production",
          "**Réduire l'aération du moût** : Moins d'oxygène disponible",
          "**Utiliser des levures productrices d'esters** : Souches de haute fermentation",
          "**Augmenter la densité initiale** : OG plus élevée"
        ]
      },
      {
        title: "Contrôle des esters - Pour DIMINUER",
        items: [
          "**Fermenter plus froid** : Température basse limite production",
          "**Bien aérer le moût** : Oxygène favorise respiration vs fermentation",
          "**Utiliser des levures 'propres'** : Souches de basse fermentation (lagers)",
          "**Ensemencement adéquat** : Population suffisante réduit le stress"
        ]
      },
      {
        title: "Relation esters et styles de bière",
        items: [
          "**Fermentation haute (ales)** : Profil riche en esters recherché",
          "**Fermentation basse (lagers)** : Profil propre, peu d'esters",
          "**Weizen/Hefeweizen** : Isoamyl acétate (banane) caractéristique",
          "**Bières belges** : Esters complexes et fruités"
        ]
      },
      {
        title: "Lien avec d'autres composés",
        items: [
          "**Alcools supérieurs** : Précurseurs des esters (Alcool + Acide → Ester)",
          "**Température** : Facteur commun pour esters ET alcools supérieurs",
          "**Stress levure** : Favorise à la fois esters et alcools supérieurs"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ Esters = Acide + Alcool = Arômes fruités",
          "✅ T° élevée et faible aération → Plus d'esters",
          "✅ T° basse et bonne aération → Moins d'esters",
          "✅ Ales riches en esters, Lagers pauvres en esters"
        ]
      }
    ],
    questions: [
      q("Que sont les esters?", ["Des sucres", "Des composés aromatiques (Acide + Alcool)", "Des protéines", "Des enzymes"], 1, "Esters = Acide + Alcool."),
      q("Quelle est la composition d'un ester?", ["Sucre + Enzyme", "Acide + Alcool", "Protéine + Lipide", "Eau + Minéral"], 1, "Ester = Acide + Alcool."),
      q("D'où proviennent les esters?", ["Du malt", "De la fermentation", "Du houblon", "De l'eau"], 1, "Esters produits lors de la fermentation."),
      q("Quels arômes donnent les esters?", ["Amers", "Fruités", "Terreux", "Métalliques"], 1, "Esters = arômes fruités."),
      q("Quel arôme donne l'isoamyl acétate?", ["Pomme", "Banane", "Poire", "Ananas"], 1, "Isoamyl acétate = banane."),
      q("Quel arôme donne l'éthyl caprylate?", ["Banane", "Pomme", "Solvant", "Rose"], 1, "Éthyl caprylate = pomme."),
      q("Quel est l'ester le plus abondant?", ["Isoamyl acétate", "Éthyl acétate", "Éthyl caprylate", "Aucun"], 1, "Éthyl acétate = le plus abondant."),
      q("Une diminution de l'aération provoque…", ["Moins d'esters", "Plus d'esters", "Pas d'effet", "Arrêt fermentation"], 1, "Moins O₂ → Plus d'esters."),
      q("Une augmentation de la température provoque…", ["Moins d'esters", "Plus d'esters", "Pas d'effet", "Arrêt fermentation"], 1, "T° haute → Plus d'esters."),
      q("Une densité plus élevée provoque…", ["Moins d'esters", "Plus d'esters", "Pas d'effet", "Moins d'alcool"], 1, "OG élevée → Plus d'esters."),
      q("Un trub plus important provoque…", ["Moins d'esters", "Plus d'esters", "Pas d'effet", "Clarification"], 1, "Plus de trub → Plus d'esters."),
      q("Que sont les précurseurs des esters?", ["Sucres", "Alcools supérieurs", "Enzymes", "Minéraux"], 1, "Alcools supérieurs = précurseurs."),
      q("Pour augmenter les esters, on fermente…", ["Plus froid", "Plus chaud", "À température constante", "Sans levure"], 1, "Fermenter plus chaud → Plus d'esters."),
      q("Pour augmenter les esters, on…", ["Augmente l'aération", "Réduit l'aération", "Ne change rien", "Ajoute de l'O₂"], 1, "Réduire aération → Plus d'esters."),
      q("Pour diminuer les esters, on fermente…", ["Plus chaud", "Plus froid", "À température variable", "Sans contrôle"], 1, "Fermenter plus froid → Moins d'esters."),
      q("Pour diminuer les esters, on…", ["Réduit l'aération", "Bien aère le moût", "Ne fait rien", "Enlève l'O₂"], 1, "Bien aérer → Moins d'esters."),
      q("Quel type de levure produit le plus d'esters?", ["Levures basses", "Levures hautes", "Levures sauvages", "Toutes pareil"], 1, "Levures hautes = plus d'esters."),
      q("Quel type de levure produit le moins d'esters?", ["Levures hautes", "Levures 'propres' (basses)", "Levures sauvages", "Toutes pareil"], 1, "Levures lagers = propres, peu d'esters."),
      q("Les ales ont un profil…", ["Pauvre en esters", "Riche en esters", "Sans esters", "Variable"], 1, "Ales = riches en esters."),
      q("Les lagers ont un profil…", ["Riche en esters", "Propre, peu d'esters", "Très fruité", "Variable"], 1, "Lagers = propres, peu d'esters."),
      q("Quel style est caractérisé par l'isoamyl acétate?", ["Pilsner", "Weizen/Hefeweizen", "Stout", "IPA"], 1, "Weizen = banane caractéristique."),
      q("Les bières belges ont des esters…", ["Absents", "Simples", "Complexes et fruités", "Neutres"], 2, "Belges = esters complexes."),
      q("Un ensemencement adéquat permet de…", ["Augmenter les esters", "Diminuer les esters", "Pas d'effet", "Arrêter fermentation"], 1, "Ensemencement suffisant → Moins de stress → Moins d'esters."),
      q("Le stress de la levure favorise…", ["Moins d'esters", "Plus d'esters", "Pas d'effet", "Meilleure qualité"], 1, "Stress → Plus d'esters et alcools supérieurs."),
      q("Quelle relation entre alcools supérieurs et esters?", ["Aucune", "Alcools = précurseurs des esters", "Esters = précurseurs des alcools", "Opposés"], 1, "Alcool + Acide → Ester."),
      q("Pour un profil fruité, on préfère fermenter…", ["Froid", "Chaud", "À température ambiante", "Sans contrôle"], 1, "Chaud = plus d'esters = plus fruité."),
      q("Pour un profil propre, on préfère fermenter…", ["Chaud", "Froid", "À température variable", "Sans contrôle"], 1, "Froid = moins d'esters = plus propre."),
      q("L'éthyl acétate peut donner un arôme de…", ["Banane uniquement", "Fruit ou léger solvant", "Terre", "Métal"], 1, "Éthyl acétate = fruit/solvant."),
      q("Une bonne aération favorise…", ["Fermentation avec plus d'esters", "Respiration avec moins d'esters", "Arrêt fermentation", "Plus d'alcool"], 1, "O₂ → Respiration → Moins d'esters."),
      q("Quel paramètre commun pour esters ET alcools supérieurs?", ["Le pH", "La température", "La couleur", "L'amertume"], 1, "T° influence esters ET alcools supérieurs.")
    ]
  },
  {
    id: "acetaldehyde",
    category: "LEVURE",
    title: "40. Composés de fermentation - L'Acétaldéhyde",
    ficheRich: [
      {
        title: "Identification de l'acétaldéhyde",
        items: [
          "**Flaveur** : 'Bière verte', herbale, pomme verte",
          "**Nature** : Produit intermédiaire central de la fermentation",
          "**Statut** : Précurseur de l'éthanol",
          "**Caractéristique** : Normalement temporaire, doit être converti"
        ]
      },
      {
        title: "Voie métabolique",
        items: [
          "**Séquence** : Glucose → ... → Acétaldéhyde → Éthanol",
          "**Position** : Étape intermédiaire avant l'éthanol final",
          "**Problème** : Peut s'accumuler si conversion incomplète",
          "**Normal** : Présent temporairement pendant la fermentation"
        ]
      },
      {
        title: "Facteurs favorisant l'accumulation",
        items: [
          "**Augmentation de la température** : Fermentation plus rapide → accumulation temporaire",
          "**Augmentation de l'oxygène** : Dévie le métabolisme normal",
          "**Taux d'ensemencement élevé** : Fermentation très active et rapide",
          "**Pression élevée** : Stress de la levure → conversion perturbée"
        ]
      },
      {
        title: "Conséquences de l'accumulation",
        items: [
          "**Goût de 'bière verte'** : Immaturité de la bière",
          "**Arôme herbacé** : Désagréable et non désiré",
          "**Pomme verte** : Caractéristique typique",
          "**Signe d'immaturité** : La bière n'est pas prête"
        ]
      },
      {
        title: "Réduction de l'acétaldéhyde",
        items: [
          "**Temps** : L'acétaldéhyde est naturellement converti en éthanol avec le temps",
          "**Levure active** : Continue la conversion vers l'éthanol",
          "**Maturation suffisante** : Permet la réduction complète",
          "**Patience** : Laisser la fermentation se terminer complètement"
        ]
      },
      {
        title: "Évolution temporelle",
        items: [
          "**Début de fermentation** : Production d'acétaldéhyde",
          "**Phase intermédiaire** : Pic d'acétaldéhyde",
          "**Fin de fermentation** : Réduction progressive vers éthanol",
          "**Maturation** : Niveau très bas d'acétaldéhyde",
          "**Éthanol** : Augmente progressivement tout au long"
        ]
      },
      {
        title: "Prévention",
        items: [
          "**Maturation adéquate** : Ne pas embouteiller trop tôt",
          "**Levure en bonne santé** : Assure conversion complète",
          "**Éviter stress levure** : Température, pression, oxygénation contrôlées",
          "**Temps suffisant** : Laisser la fermentation aller à son terme"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ Acétaldéhyde = précurseur de l'éthanol",
          "✅ Goût 'bière verte', pomme verte, herbacé",
          "✅ Accumulation favorisée par T° haute, O₂, sur-ensemencement",
          "✅ Réduction naturelle avec temps et levure active",
          "✅ Signe d'immaturité de la bière"
        ]
      }
    ],
    questions: [
      q("Quel goût donne l'acétaldéhyde?", ["Banane", "Bière verte/pomme verte", "Beurre rance", "Solvant"], 1, "Acétaldéhyde = bière verte, herbacé."),
      q("Quelle est la nature de l'acétaldéhyde?", ["Produit final", "Produit intermédiaire", "Sucre", "Enzyme"], 1, "Intermédiaire central de la fermentation."),
      q("L'acétaldéhyde est le précurseur de…", ["Glucose", "Éthanol", "CO₂", "Diacétyle"], 1, "Acétaldéhyde → Éthanol."),
      q("Quelle est la séquence métabolique correcte?", ["Éthanol → Acétaldéhyde → Glucose", "Glucose → Acétaldéhyde → Éthanol", "Glucose → Éthanol → Acétaldéhyde", "Acétaldéhyde → Glucose → Éthanol"], 1, "Glucose → Acétaldéhyde → Éthanol."),
      q("L'acétaldéhyde peut s'accumuler si…", ["La conversion est complète", "La conversion est incomplète", "Il n'y a pas de levure", "Il fait froid"], 1, "Accumulation = conversion incomplète."),
      q("Une augmentation de température provoque…", ["Moins d'acétaldéhyde", "Plus d'acétaldéhyde", "Pas d'effet", "Arrêt fermentation"], 1, "T° haute → fermentation rapide → accumulation."),
      q("Une augmentation d'oxygène provoque…", ["Moins d'acétaldéhyde", "Plus d'acétaldéhyde", "Pas d'effet", "Meilleure qualité"], 1, "Plus O₂ → dévie métabolisme → accumulation."),
      q("Un taux d'ensemencement élevé provoque…", ["Moins d'acétaldéhyde", "Plus d'acétaldéhyde", "Pas d'effet", "Fermentation lente"], 1, "Sur-ensemencement → fermentation active → accumulation."),
      q("Une pression élevée provoque…", ["Moins d'acétaldéhyde", "Plus d'acétaldéhyde", "Pas d'effet", "Meilleure qualité"], 1, "Pression → stress levure → accumulation."),
      q("Un goût de 'bière verte' indique…", ["Bière mature", "Bière immature", "Bière parfaite", "Contamination"], 1, "Bière verte = immaturité."),
      q("L'arôme de pomme verte vient de…", ["Diacétyle", "Acétaldéhyde", "Esters", "Alcools supérieurs"], 1, "Acétaldéhyde = pomme verte."),
      q("Comment réduire l'acétaldéhyde?", ["Ajouter du sucre", "Laisser du temps, levure active", "Filtrer rapidement", "Ajouter du houblon"], 1, "Temps + levure active = conversion."),
      q("L'acétaldéhyde est converti naturellement en…", ["Glucose", "Éthanol", "CO₂", "Diacétyle"], 1, "Conversion naturelle vers éthanol."),
      q("Pour la conversion, la levure doit être…", ["Morte", "Active", "Absente", "Congelée"], 1, "Levure active = conversion continue."),
      q("Une maturation suffisante permet…", ["Accumulation", "Réduction complète", "Arrêt fermentation", "Plus d'acétaldéhyde"], 1, "Maturation = réduction complète."),
      q("Quand l'acétaldéhyde atteint-il son pic?", ["Début fermentation", "Phase intermédiaire", "Fin fermentation", "Après embouteillage"], 1, "Pic en phase intermédiaire."),
      q("En fin de fermentation, l'acétaldéhyde…", ["Augmente", "Reste stable", "Diminue progressivement", "Disparaît instantanément"], 2, "Réduction progressive en fin."),
      q("L'éthanol pendant la fermentation…", ["Diminue", "Reste stable", "Augmente progressivement", "Fluctue"], 2, "Éthanol augmente tout au long."),
      q("Un défaut d'acétaldéhyde indique…", ["Sur-maturation", "Sous-maturation", "Perfection", "Contamination"], 1, "Acétaldéhyde = bière immature."),
      q("Pour éviter l'acétaldéhyde, il faut…", ["Embouteiller tôt", "Maturation adéquate", "Fermentation rapide", "Plus de pression"], 1, "Maturation adéquate = prévention."),
      q("Une levure en bonne santé assure…", ["Plus d'acétaldéhyde", "Conversion complète", "Arrêt fermentation", "Contamination"], 1, "Levure saine = conversion complète."),
      q("Il faut éviter de stresser la levure pour…", ["Plus d'acétaldéhyde", "Moins d'acétaldéhyde", "Plus d'alcool", "Plus de CO₂"], 1, "Stress levure = accumulation acétaldéhyde."),
      q("L'acétaldéhyde est-il un produit final?", ["Oui", "Non, c'est un intermédiaire", "Parfois", "Uniquement en lagers"], 1, "Intermédiaire, pas final."),
      q("L'arôme herbacé vient de…", ["Houblon uniquement", "Acétaldéhyde", "Malt", "Eau"], 1, "Acétaldéhyde = herbacé/bière verte."),
      q("Pour convertir l'acétaldéhyde en éthanol, il faut…", ["Filtrer", "Du temps", "Plus de houblon", "Plus de sucre"], 1, "Temps nécessaire pour conversion."),
      q("Embouteiller trop tôt peut causer…", ["Trop d'alcool", "Acétaldéhyde résiduel", "Trop de couleur", "Moins de CO₂"], 1, "Trop tôt = acétaldéhyde pas converti."),
      q("L'acétaldéhyde est normalement…", ["Permanent", "Temporaire pendant fermentation", "Absent", "Toujours présent"], 1, "Temporaire, doit être converti."),
      q("Quel facteur NE favorise PAS l'acétaldéhyde?", ["T° haute", "Pression haute", "Maturation longue", "Sur-ensemencement"], 2, "Maturation longue = réduction."),
      q("Pendant la maturation, l'acétaldéhyde…", ["Augmente", "Se maintient", "Est converti en éthanol", "Reste constant"], 2, "Maturation = conversion en éthanol."),
      q("Un niveau très bas d'acétaldéhyde indique…", ["Bière immature", "Bière mature", "Contamination", "Défaut majeur"], 1, "Niveau bas = bière mature.")
    ]
  },
  {
    id: "alcoolsSuperieurs",
    category: "LEVURE",
    title: "41. Composés de fermentation - Alcools supérieurs",
    ficheRich: [
      {
        title: "Définition des alcools supérieurs",
        items: [
          "**Nom anglais** : Fusel alcohols",
          "**Nature** : Alcools autres que l'éthanol",
          "**Effet à faible dose** : Positif (roses, banane, complexité)",
          "**Effet à forte dose** : Négatif (solvant, chimique, médicinal)",
          "**Concentration** : Doit être contrôlée, concentration faible souhaitée"
        ]
      },
      {
        title: "Principaux alcools supérieurs",
        items: [
          "**Isoamyl alcohol (alcool isoamylique)** : Arôme banane/solvant",
          "**Isobutanol** : Arôme alcool/solvant",
          "**n-Propanol** : Arôme alcool",
          "**Variété** : Plusieurs types avec profils différents"
        ]
      },
      {
        title: "Facteurs favorisant la production (↑)",
        items: [
          "**Trop ou trop peu d'aération** : Extrêmes défavorables (trop OU pas assez → ↑)",
          "**Augmentation de la température** : T° haute → Plus d'alcools supérieurs",
          "**Augmentation de la densité** : OG élevée → Plus d'alcools supérieurs",
          "**Composition en acides aminés** : Influence le profil spécifique",
          "**Stress de la levure** : Favorise la production"
        ]
      },
      {
        title: "Effet selon la dose",
        items: [
          "**À faible concentration** : Roses, banane, complexité aromatique agréable",
          "**À forte concentration** : Solvant, chimique, médicinal (défaut)",
          "**Équilibre crucial** : Trop = défaut, juste assez = complexité",
          "**Dose-dépendant** : L'effet change radicalement selon la quantité"
        ]
      },
      {
        title: "Flaveurs associées selon concentration",
        items: [
          "**Faible dose** : Rose, banane, complexité agréable",
          "**Dose élevée** : Solvant, chimique, médicinal, désagréable",
          "**Seuil critique** : Passage rapide du positif au négatif"
        ]
      },
      {
        title: "Relation avec les esters",
        items: [
          "**Alcools supérieurs = précurseurs des esters**",
          "**Réaction** : Alcool supérieur + Acide → Ester",
          "**Lien métabolique** : Production liée (mêmes conditions favorisent les deux)",
          "**Température** : Facteur commun pour alcools supérieurs ET esters"
        ]
      },
      {
        title: "Styles recherchant les alcools supérieurs",
        items: [
          "**Triple belge** : Alcools supérieurs recherchés pour complexité",
          "**Barley wine** : Profil riche et complexe",
          "**Bières fortes** : Alcools supérieurs contribuent au caractère",
          "**Styles à éviter** : Lagers, pilsners (profil propre recherché)"
        ]
      },
      {
        title: "Contrôle des alcools supérieurs",
        items: [
          "**Pour diminuer** : Température modérée, aération optimale, ensemencement adéquat",
          "**Pour augmenter** : Température élevée, densité haute, stress levure",
          "**Aération** : Trouver l'équilibre (ni trop, ni trop peu)",
          "**Levure** : Santé et population influencent la production"
        ]
      },
      {
        title: "Points à retenir",
        items: [
          "✅ Fusel alcohols = alcools autres que l'éthanol",
          "✅ Faible dose = positif (rose, banane), forte dose = négatif (solvant)",
          "✅ Favorisés par T° haute, densité haute, aération déséquilibrée",
          "✅ Précurseurs des esters (Alcool + Acide → Ester)",
          "✅ Recherchés dans triples belges et barley wines"
        ]
      }
    ],
    questions: [
      q("Comment appelle-t-on les alcools supérieurs en anglais?", ["Higher alcohols", "Fusel alcohols", "Super alcohols", "Strong alcohols"], 1, "Fusel alcohols = alcools supérieurs."),
      q("Que sont les alcools supérieurs?", ["L'éthanol uniquement", "Alcools autres que l'éthanol", "Des esters", "Des acides"], 1, "Alcools autres que éthanol."),
      q("À faible dose, les alcools supérieurs sont…", ["Négatifs", "Positifs (roses, banane)", "Neutres", "Toxiques"], 1, "Faible dose = positif, complexité."),
      q("À forte dose, les alcools supérieurs sont…", ["Positifs", "Négatifs (solvant, médicinal)", "Neutres", "Bénéfiques"], 1, "Forte dose = négatif, chimique."),
      q("Quel arôme donne l'isoamyl alcohol?", ["Pomme", "Banane/solvant", "Rose", "Caramel"], 1, "Isoamyl alcohol = banane/solvant."),
      q("Quel arôme donne l'isobutanol?", ["Banane", "Alcool/solvant", "Fruit", "Fleur"], 1, "Isobutanol = alcool/solvant."),
      q("Quel arôme donne le n-propanol?", ["Banane", "Alcool", "Rose", "Fruit"], 1, "n-Propanol = arôme alcool."),
      q("Trop d'aération provoque…", ["Moins d'alcools supérieurs", "Plus d'alcools supérieurs", "Pas d'effet", "Meilleure qualité"], 1, "Trop d'aération → ↑ alcools supérieurs."),
      q("Trop peu d'aération provoque…", ["Moins d'alcools supérieurs", "Plus d'alcools supérieurs", "Pas d'effet", "Meilleure qualité"], 1, "Trop peu d'aération → ↑ alcools supérieurs."),
      q("Une température élevée provoque…", ["Moins d'alcools supérieurs", "Plus d'alcools supérieurs", "Pas d'effet", "Arrêt fermentation"], 1, "T° haute → ↑ alcools supérieurs."),
      q("Une densité élevée provoque…", ["Moins d'alcools supérieurs", "Plus d'alcools supérieurs", "Pas d'effet", "Moins d'alcool"], 1, "OG haute → ↑ alcools supérieurs."),
      q("Qu'influence la composition en acides aminés?", ["Rien", "Le profil des alcools supérieurs", "La couleur", "L'amertume"], 1, "Acides aminés influencent le profil."),
      q("Le stress de la levure favorise…", ["Moins d'alcools supérieurs", "Plus d'alcools supérieurs", "Pas d'effet", "Meilleure qualité"], 1, "Stress → ↑ alcools supérieurs."),
      q("À faible concentration, on perçoit…", ["Solvant", "Rose, banane, complexité", "Médicinal", "Chimique"], 1, "Faible = rose, banane, complexité."),
      q("À forte concentration, on perçoit…", ["Rose agréable", "Solvant, chimique, médicinal", "Fruit", "Fleur"], 1, "Forte = solvant, médicinal."),
      q("Quelle relation entre alcools supérieurs et esters?", ["Aucune", "Alcools = précurseurs des esters", "Esters = précurseurs des alcools", "Opposés"], 1, "Alcool + Acide → Ester."),
      q("Quelle réaction forme les esters?", ["Sucre + Enzyme", "Alcool supérieur + Acide", "Protéine + Lipide", "Eau + Minéral"], 1, "Alcool + Acide = Ester."),
      q("Quel paramètre favorise à la fois alcools supérieurs ET esters?", ["Le pH", "La température élevée", "La couleur", "L'amertume"], 1, "T° haute favorise les deux."),
      q("Dans quel style recherche-t-on les alcools supérieurs?", ["Pilsner", "Triple belge", "Lager légère", "Bière sans alcool"], 1, "Triple belge, barley wine, bières fortes."),
      q("Dans quel style évite-t-on les alcools supérieurs?", ["Triple belge", "Barley wine", "Lagers/Pilsners", "Bières fortes"], 2, "Lagers = profil propre, peu d'alcools supérieurs."),
      q("Quelle concentration est souhaitée?", ["Très élevée", "Élevée", "Moyenne", "Faible"], 3, "Concentration faible souhaitée."),
      q("L'effet des alcools supérieurs est…", ["Constant", "Dose-dépendant", "Toujours positif", "Toujours négatif"], 1, "Effet change selon la dose."),
      q("Le passage du positif au négatif est…", ["Progressif", "Rapide (seuil critique)", "Impossible", "Très lent"], 1, "Seuil critique, passage rapide."),
      q("Pour diminuer les alcools supérieurs, il faut…", ["T° élevée", "T° modérée et aération optimale", "Stress levure", "Densité haute"], 1, "T° modérée + aération optimale."),
      q("Pour augmenter les alcools supérieurs, il faut…", ["T° basse", "T° élevée et densité haute", "Aération parfaite", "Ensemencement adéquat"], 1, "T° haute + densité haute."),
      q("L'aération doit être…", ["Excessive", "Absente", "Équilibrée (ni trop, ni trop peu)", "Variable"], 2, "Équilibre nécessaire pour l'aération."),
      q("La santé de la levure influence…", ["Rien", "La production d'alcools supérieurs", "Uniquement la couleur", "Uniquement l'amertume"], 1, "Santé levure = influence production."),
      q("Un arôme de solvant vient de…", ["Houblon", "Alcools supérieurs à forte dose", "Malt", "Eau"], 1, "Solvant = alcools supérieurs élevés."),
      q("Un arôme de rose peut venir de…", ["Houblon uniquement", "Alcools supérieurs à faible dose", "Malt", "Contamination"], 1, "Rose = alcools supérieurs faible dose."),
      q("Les alcools supérieurs contribuent à…", ["L'amertume", "La complexité aromatique", "La couleur", "Le pH"], 1, "Complexité aromatique (à faible dose).")
    ]
  },
  {
    id: "fermentationBloquee",
    category: "LEVURE",
    title: "42. Fermentation bloquée et rappels d'hygiène",
    ficheRich: [
      {
        title: "Fermentation 'bloquée' - Définition",
        items: [
          "**Définition** : Une fermentation qui démarre mal est une fermentation à problème",
          "**Symptôme** : Le moût n'atteint pas l'atténuation limite",
          "**Gravité** : Probablement impossible de relancer une fermentation arrêtée",
          "**Importance** : Diagnostic rapide essentiel"
        ]
      },
      {
        title: "Origine possible d'une fermentation bloquée",
        items: [
          "**Salle de brassage (SDB)** : Problème en amont avec le moût",
          "**Fermentation elle-même** : Problème de levure ou conditions de fermentation",
          "**Deux sources** : Nécessite diagnostic pour identifier"
        ]
      },
      {
        title: "Diagnostic d'une fermentation bloquée",
        items: [
          "**1.** Prélever un échantillon représentatif du moût",
          "**2.** Ajouter une nouvelle dose de la même levure",
          "**3.** Essayer de fermenter l'échantillon",
          "**4.** Observer après 24h",
          "**Test simple** : Permet d'identifier la source du problème"
        ]
      },
      {
        title: "Interprétation du diagnostic",
        items: [
          "**Densité a chuté après 24h** : Problème de levure (ensemencement, génération, viabilité)",
          "**Densité stable après 24h** : Problème vient de la salle de brassage (moût)",
          "**Action** : Adapter la solution selon la source identifiée"
        ]
      },
      {
        title: "Rappels d'hygiène - Environnement de travail",
        items: [
          "**Espace stérile** : Travailler dans un espace le plus stérile possible",
          "**Pièce sous désinfectant** : Pour l'ensemencement",
          "**Bacs de trempage** : Sortir les bacs le plus tard possible",
          "**Levure** : Ouvrir le plus tard possible pour limiter contamination"
        ]
      },
      {
        title: "Rappels d'hygiène - Équipements",
        items: [
          "**Cuves stériles** : Vannes préalablement passées au désinfectant",
          "**Cuve de destination** : Maintenue fermée jusqu'à l'arrivée du moût",
          "**Ustensiles** : TOUJOURS lavés AVANT d'être mis dans les bains de désinfectant",
          "**Ordre** : Lavage puis désinfection (pas l'inverse)"
        ]
      },
      {
        title: "Rappels d'hygiène - Moût",
        items: [
          "**Densité primitive** : Éviter de récolter sur une bière de trop haute densité primitive",
          "**Refroidissement** : Ensemencer dès que le moût est refroidi",
          "**Timing** : Ensemencement immédiat = sécurité microbiologique"
        ]
      },
      {
        title: "Checklist hygiène fermentation",
        items: [
          "✓ Espace de travail désinfecté",
          "✓ Levure sortie au dernier moment",
          "✓ Bacs de trempage prêts",
          "✓ Cuve de fermentation stérile et fermée",
          "✓ Vannes désinfectées",
          "✓ Ustensiles lavés puis désinfectés",
          "✓ Moût refroidi avant ensemencement",
          "✓ Ensemencement immédiat après refroidissement"
        ]
      },
      {
        title: "Message clé - Maîtrise de la levure",
        items: [
          "**Art du brasseur** : La maîtrise de la levure",
          "**Trois piliers** : Comprendre le métabolisme, contrôler l'environnement, respecter l'hygiène",
          "**Résultat** : Fermentation réussie et bière de qualité",
          "**Importance** : L'hygiène est fondamentale pour éviter les problèmes"
        ]
      }
    ],
    questions: [
      q("Qu'est-ce qu'une fermentation bloquée?", ["Fermentation normale", "Fermentation qui démarre mal", "Fermentation rapide", "Fermentation froide"], 1, "Fermentation bloquée = démarre mal."),
      q("Peut-on relancer une fermentation arrêtée?", ["Toujours", "Facilement", "Probablement impossible", "Parfois"], 2, "Probablement impossible de relancer."),
      q("Quelles sont les deux origines possibles?", ["Houblon et malt", "Salle de brassage et fermentation", "Eau et levure", "Température et pH"], 1, "SDB (moût) ou fermentation (levure)."),
      q("Première étape du diagnostic?", ["Jeter le moût", "Prélever un échantillon représentatif", "Ajouter du sucre", "Chauffer"], 1, "Prélever un échantillon."),
      q("Que fait-on après le prélèvement?", ["On filtre", "On ajoute une nouvelle dose de levure", "On chauffe", "On jette"], 1, "Ajouter nouvelle dose de levure."),
      q("Combien de temps observe-t-on?", ["1 heure", "24 heures", "1 semaine", "1 mois"], 1, "Observer après 24h."),
      q("Si la densité a chuté après 24h, le problème vient…", ["Du moût", "De la levure", "Du houblon", "De l'eau"], 1, "Densité chute = problème levure."),
      q("Si la densité est stable après 24h, le problème vient…", ["De la levure", "De la salle de brassage (moût)", "Du houblon", "De la température"], 1, "Densité stable = problème SDB (moût)."),
      q("Où doit-on travailler pour ensemencer?", ["N'importe où", "Espace le plus stérile possible", "À l'extérieur", "Dans la cave"], 1, "Espace stérile pour ensemencement."),
      q("Quand sortir les bacs de trempage?", ["Le plus tôt possible", "Le plus tard possible", "N'importe quand", "Jamais"], 1, "Sortir le plus tard possible."),
      q("Quand ouvrir la levure?", ["Au début", "Le plus tard possible", "N'importe quand", "24h avant"], 1, "Ouvrir le plus tard possible."),
      q("Comment doivent être les vannes?", ["Sales", "Préalablement désinfectées", "Humides", "Ouvertes"], 1, "Vannes passées au désinfectant."),
      q("Comment maintenir la cuve de destination?", ["Ouverte", "Fermée jusqu'à l'arrivée du moût", "À moitié ouverte", "Sans couvercle"], 1, "Maintenue fermée jusqu'au moût."),
      q("Dans quel ordre nettoyer les ustensiles?", ["Désinfectant puis lavage", "Lavage puis désinfectant", "Désinfectant uniquement", "Lavage uniquement"], 1, "TOUJOURS lavés AVANT désinfection."),
      q("Que faut-il éviter pour la densité primitive?", ["Densité trop basse", "Densité trop haute", "Densité moyenne", "Mesure de densité"], 1, "Éviter densité primitive trop haute."),
      q("Quand ensemencer le moût?", ["Le lendemain", "Dès qu'il est refroidi", "Après 24h", "Quand on veut"], 1, "Ensemencer dès refroidissement."),
      q("L'ensemencement doit être…", ["Différé", "Immédiat après refroidissement", "Le lendemain", "Après 1 semaine"], 1, "Ensemencement immédiat."),
      q("Que désinfecte-t-on en premier?", ["Rien", "Espace de travail", "Le houblon", "L'eau"], 1, "Espace de travail désinfecté."),
      q("Quand préparer les bacs de trempage?", ["Jamais", "À l'avance, prêts", "Après fermentation", "Le lendemain"], 1, "Bacs de trempage prêts."),
      q("La cuve de fermentation doit être…", ["Sale", "Stérile et fermée", "Ouverte", "Humide"], 1, "Cuve stérile et fermée."),
      q("Le moût doit être… avant ensemencement", ["Chaud", "Refroidi", "Bouillant", "Tiède"], 1, "Moût refroidi avant ensemencement."),
      q("Combien de piliers pour maîtriser la levure?", ["1", "2", "3", "5"], 2, "3 piliers : métabolisme, environnement, hygiène."),
      q("Quels sont les 3 piliers?", ["Houblon, malt, eau", "Métabolisme, environnement, hygiène", "T°, pH, densité", "Couleur, amertume, alcool"], 1, "Métabolisme + environnement + hygiène."),
      q("L'hygiène est…", ["Optionnelle", "Fondamentale", "Secondaire", "Inutile"], 1, "Hygiène = fondamentale."),
      q("La maîtrise de la levure est…", ["Un détail", "L'art du brasseur", "Facultative", "Secondaire"], 1, "Art du brasseur = maîtrise levure."),
      q("Un problème d'ensemencement indique…", ["Problème moût", "Problème levure", "Problème houblon", "Problème eau"], 1, "Ensemencement = problème levure."),
      q("Un problème de génération de levure indique…", ["Problème moût", "Problème levure", "Problème température", "Problème pH"], 1, "Génération levure = problème levure."),
      q("Pourquoi laver AVANT de désinfecter?", ["C'est plus rapide", "Le désinfectant ne fonctionne pas sur surface sale", "C'est obligatoire", "Pour l'odeur"], 1, "Désinfectant inefficace sur surface sale."),
      q("Pourquoi ensemencer immédiatement?", ["Pour la couleur", "Sécurité microbiologique", "Pour l'amertume", "C'est plus rapide"], 1, "Immédiat = évite contamination."),
      q("Le résultat d'une bonne maîtrise est…", ["Bière médiocre", "Fermentation réussie et bière de qualité", "Contamination", "Arrêt fermentation"], 1, "Maîtrise = fermentation réussie + qualité.")
    ]
  }
];

// Test de compatibilité localStorage (Safari en navigation privée)
function isLocalStorageAvailable() {
  // Safari private mode throws on setItem even if API exists
  if (!('localStorage' in window)) return false;
  try {
    const test = '__storage_test__';
    window.localStorage.setItem(test, test);
    window.localStorage.removeItem(test);
    return true;
  } catch (e) {
    return false;
  }
}

const storageAvailable = isLocalStorageAvailable();
const memoryStore = {}; // Fallback pour Safari privé
if (!storageAvailable) {
  console.warn('⚠️ localStorage non disponible (Safari en navigation privée ?). Les données ne seront pas sauvegardées.');
}

// Fonctions wrapper pour localStorage avec gestion d'erreurs Safari
function safeSetItem(key, value) {
  if (!storageAvailable) {
    memoryStore[key] = value;
    return true;
  }
  try {
    localStorage.setItem(key, value);
    return true;
  } catch (e) {
    console.error('Erreur localStorage:', e);
    return false;
  }
}

function safeGetItem(key, defaultValue = null) {
  if (!storageAvailable) {
    return Object.prototype.hasOwnProperty.call(memoryStore, key) ? memoryStore[key] : defaultValue;
  }
  try {
    return localStorage.getItem(key) || defaultValue;
  } catch (e) {
    console.error('Erreur localStorage:', e);
    return defaultValue;
  }
}

function safeRemoveItem(key) {
  if (!storageAvailable) {
    delete memoryStore[key];
    return true;
  }
  try {
    localStorage.removeItem(key);
    return true;
  } catch (e) {
    console.error('Erreur localStorage:', e);
    return false;
  }
}

const nav = document.getElementById("nav");
const quizContainer = document.getElementById("quizContainer");
const startQuizBtn = document.getElementById("startQuiz");
const questionCountSel = document.getElementById("questionCount");
const toggleFicheBtn = document.getElementById("toggleFiche");
const ficheEl = document.getElementById("fiche");
const ficheTitle = document.getElementById("ficheTitle");
const ficheContent = document.getElementById("ficheContent");
const progressEl = document.getElementById("progress");

let currentTheme = null;
let currentQuestions = [];
let answers = [];
let showFiche = true;

// Système de suivi des thèmes (compatible Safari)
let themeProgress = JSON.parse(safeGetItem('quizProgress', '{}'));

function saveProgress() {
  safeSetItem('quizProgress', JSON.stringify(themeProgress));
}

function updateThemeStatus(themeId, status) {
  themeProgress[themeId] = status;
  saveProgress();
  updateThemeButtons();
}

function getThemeStatus(themeId) {
  return themeProgress[themeId] || 'not-started';
}

function updateThemeButtons() {
  document.querySelectorAll('.theme-btn').forEach(btn => {
    const themeId = btn.getAttribute('data-theme-id');
    if (themeId) {
      btn.classList.remove('started', 'completed');
      const status = getThemeStatus(themeId);
      if (status === 'started') btn.classList.add('started');
      if (status === 'completed') btn.classList.add('completed');
    }
  });
}

function resetThemeQuiz(themeId) {
  // Réinitialiser le statut du thème
  delete themeProgress[themeId];
  saveProgress();
  
  // Supprimer les stats du thème
  const themeStats = JSON.parse(safeGetItem('themeStats', '{}') || '{}');
  delete themeStats[themeId];
  safeSetItem('themeStats', JSON.stringify(themeStats));
  
  // Supprimer les questions ratées du thème
  const failed = JSON.parse(safeGetItem('failedQuestions', '{}') || '{}');
  delete failed[themeId];
  safeSetItem('failedQuestions', JSON.stringify(failed));
  
  updateThemeButtons();
  updateStats();
  
  // Si c'est le thème actuel, réinitialiser aussi les questions
  if (currentTheme && currentTheme.id === themeId) {
    currentQuestions = [];
    answers = [];
    progressEl.textContent = "—";
    renderQuiz();
  }
}

// Group themes by category
const categoryOrder = ["MALT", "HOUBLON", "ÉPICES", "CIP", "LEVURE", "GÉNÉRAL"];
const themesByCategory = {};
categoryOrder.forEach(cat => { themesByCategory[cat] = []; });
THEMES.forEach(t => {
  if (!themesByCategory[t.category]) themesByCategory[t.category] = [];
  themesByCategory[t.category].push(t);
});

// Render navigation grouped by category
categoryOrder.forEach(category => {
  const themes = themesByCategory[category] || [];
  
  const catDiv = document.createElement("div");
  catDiv.className = "category-group";
  
  const catTitle = document.createElement("h3");
  catTitle.className = "category-title";
  catTitle.textContent = category;
  catDiv.appendChild(catTitle);
  
  if (themes.length === 0) {
    const emptyMsg = document.createElement("p");
    emptyMsg.style.color = "var(--muted)";
    emptyMsg.style.fontStyle = "italic";
    emptyMsg.style.padding = "0.5rem";
    emptyMsg.textContent = "Aucun thème pour l'instant";
    catDiv.appendChild(emptyMsg);
    nav.appendChild(catDiv);
    return;
  }
  
  themes.forEach((t, idx) => {
    const btn = document.createElement("button");
    btn.className = "theme-btn";
    btn.textContent = t.title;
    btn.setAttribute('data-theme-id', t.id);
    btn.onclick = () => selectTheme(t, btn);
    catDiv.appendChild(btn);
    
    if (THEMES.indexOf(t) === 0 && !currentTheme) {
      currentTheme = t;
      btn.classList.add("active");
      renderFiche(t);
    }
  });
  nav.appendChild(catDiv);
});

// Appliquer les indicateurs de progression
updateThemeButtons();

function selectTheme(theme, btn) {
  currentTheme = theme;
  currentQuestions = [];
  answers = [];
  document.querySelectorAll(".theme-btn").forEach(b => b.classList.remove("active"));
  btn.classList.add("active");
  renderFiche(theme);
  quizContainer.innerHTML = "";
  progressEl.textContent = "—";
  
  // Réinitialiser la recherche dans le thème
  themeSearchBar.value = '';
  themeSearchResultsDiv.style.display = 'none';
  themeSearchResultsContent.innerHTML = '';
}

function shuffle(arr) {
  const copy = arr.slice();
  for (let i = copy.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [copy[i], copy[j]] = [copy[j], copy[i]];
  }
  return copy;
}

function pickExactCount(base, n) {
  return shuffle(base).slice(0, Math.min(n, base.length));
}

function renderFiche(theme) {
  ficheTitle.textContent = theme.title;
  ficheContent.innerHTML = "";
  if (theme.ficheRich) {
    theme.ficheRich.forEach(sec => {
      const div = document.createElement("div");
      div.className = "section";
      const h3 = document.createElement("h3");
      h3.textContent = sec.title;
      div.appendChild(h3);
      const ul = document.createElement("ul");
      sec.items.forEach(item => {
        const li = document.createElement("li");
        li.innerHTML = item.replace(/\*\*(.+?)\*\*/g, "<strong>$1</strong>");
        ul.appendChild(li);
      });
      div.appendChild(ul);
      ficheContent.appendChild(div);
    });
  }
}

function renderQuiz() {
  quizContainer.innerHTML = "";
  if (currentQuestions.length === 0) {
    quizContainer.innerHTML = "<p style='text-align:center;padding:2rem;'>Sélectionnez un thème et cliquez Démarrer.</p>";
    return;
  }

  let answered = answers.filter(a => a !== null).length;
  let correct = answers.filter((a, i) => a === currentQuestions[i].correctIndex).length;
  progressEl.textContent = `Tentées: ${answered}/${currentQuestions.length} • Correctes: ${correct}`;
  
  // Sauvegarder les statistiques du thème actuel
  if (currentTheme) {
    const themeStats = JSON.parse(safeGetItem('themeStats', '{}') || '{}');
    if (!themeStats[currentTheme.id]) {
      themeStats[currentTheme.id] = {};
    }
    themeStats[currentTheme.id].answered = answered;
    themeStats[currentTheme.id].correct = correct;
    safeSetItem('themeStats', JSON.stringify(themeStats));
  }
  
  // Marquer comme terminé si toutes les questions sont correctes
  if (answered === currentQuestions.length && correct === currentQuestions.length) {
    updateThemeStatus(currentTheme.id, 'completed');
    updateThemeButtons();
    updateStats();
  } else if (answered > 0) {
    // Marquer comme démarré si au moins une question répondue
    if (getThemeStatus(currentTheme.id) === 'not-started') {
      updateThemeStatus(currentTheme.id, 'started');
      updateThemeButtons();
    }
    updateStats();
  }

  currentQuestions.forEach((q, idx) => {
    const div = document.createElement("div");
    div.className = "question";
    const h3 = document.createElement("h3");
    h3.textContent = `${idx + 1}. ${q.question}`;
    div.appendChild(h3);

    const optDiv = document.createElement("div");
    optDiv.className = "options";
    q.options.forEach((opt, optIdx) => {
      const btn = document.createElement("button");
      btn.className = "option";
      btn.textContent = opt;
      if (answers[idx] !== null) {
        if (optIdx === q.correctIndex) btn.classList.add("correct");
        else if (optIdx === answers[idx]) btn.classList.add("incorrect");
      }
      btn.onclick = () => {
        if (answers[idx] === null) {
          answers[idx] = optIdx;
          
          // Suivre les questions ratées
          if (optIdx !== q.correctIndex) {
            addFailedQuestion(currentTheme.id, idx);
          } else {
            removeFailedQuestion(currentTheme.id, idx);
          }
          
          renderQuiz();
        }
      };
      optDiv.appendChild(btn);
    });
    div.appendChild(optDiv);

    if (answers[idx] !== null) {
      const exp = document.createElement("div");
      exp.className = "explanation";
      exp.innerHTML = `✓ <strong>Explication:</strong> ${q.explanation}`;
      div.appendChild(exp);
    }

    quizContainer.appendChild(div);
  });
}

// ===================== NOUVELLES FONCTIONNALITÉS =====================

// Barre de recherche
const searchBar = document.getElementById('searchBar');
const searchResultsDiv = document.getElementById('searchResults');
const searchResultsContent = document.getElementById('searchResultsContent');
searchBar.addEventListener('input', filterThemes);

function highlightText(text, searchTerm) {
  const regex = new RegExp(`(${searchTerm})`, 'gi');
  return text.replace(regex, '<mark style="background: #ffd700; color: #000; padding: 0 3px; border-radius: 2px; font-weight: bold;">$1</mark>');
}

function filterThemes() {
  const searchTerm = searchBar.value.toLowerCase().trim();
  const themeButtons = document.querySelectorAll('.theme-btn');
  
  if (searchTerm === '') {
    // Si pas de recherche, tout afficher
    themeButtons.forEach(btn => {
      btn.parentElement.style.display = '';
    });
    document.querySelectorAll('.category-group').forEach(cat => {
      cat.style.display = '';
    });
    searchResultsDiv.style.display = 'none';
    searchResultsContent.innerHTML = '';
    return;
  }
  
  const results = [];
  
  themeButtons.forEach(btn => {
    const themeId = btn.getAttribute('data-theme-id');
    const theme = THEMES.find(t => t.id === themeId);
    
    if (!theme) {
      btn.parentElement.style.display = 'none';
      return;
    }
    
    // Rechercher dans le titre
    let found = theme.title.toLowerCase().includes(searchTerm);
    
    if (found) {
      results.push({
        theme: theme.title,
        type: 'Titre',
        content: theme.title
      });
    }
    
    // Rechercher dans les explications uniquement (pas les questions ni les réponses)
    if (theme.questions) {
      theme.questions.forEach((q, idx) => {
        // Chercher seulement dans les explications
        if (q.explanation.toLowerCase().includes(searchTerm)) {
          results.push({
            theme: theme.title,
            type: 'Explication',
            content: q.explanation
          });
          found = true;
        }
      });
    }
    
    // Rechercher dans la fiche
    if (theme.ficheRich) {
      theme.ficheRich.forEach(sec => {
        if (sec.title.toLowerCase().includes(searchTerm)) {
          results.push({
            theme: theme.title,
            type: 'Fiche - Section',
            content: sec.title
          });
          found = true;
        }
        
        sec.items.forEach(item => {
          if (item.toLowerCase().includes(searchTerm)) {
            results.push({
              theme: theme.title,
              type: 'Fiche - Contenu',
              content: item.replace(/\*\*(.+?)\*\*/g, '$1')
            });
            found = true;
          }
        });
      });
    }
    
    if (found) {
      btn.parentElement.style.display = '';
    } else {
      btn.parentElement.style.display = 'none';
    }
  });
  
  // Afficher les résultats
  if (results.length > 0) {
    searchResultsDiv.style.display = 'block';
    searchResultsContent.innerHTML = results.map(r => `
      <div style="background: rgba(88, 166, 255, 0.1); padding: 1rem; margin-bottom: 0.8rem; border-radius: 6px; border-left: 3px solid var(--accent);">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.5rem;">
          <strong style="color: var(--accent);">${r.theme}</strong>
          <span style="background: rgba(167, 139, 250, 0.3); color: #a78bfa; padding: 0.2rem 0.6rem; border-radius: 4px; font-size: 0.85em;">${r.type}</span>
        </div>
        <div style="color: var(--text); line-height: 1.6;">${highlightText(r.content, searchTerm)}</div>
      </div>
    `).join('');
  } else {
    searchResultsDiv.style.display = 'block';
    searchResultsContent.innerHTML = '<p style="color: var(--muted); text-align: center; padding: 1rem;">Aucun résultat trouvé</p>';
  }
  
  // Masquer les catégories vides
  const categories = document.querySelectorAll('.category-group');
  categories.forEach(cat => {
    const visibleButtons = Array.from(cat.querySelectorAll('.theme-btn')).filter(btn => btn.parentElement.style.display !== 'none');
    if (visibleButtons.length === 0) {
      cat.style.display = 'none';
    } else {
      cat.style.display = '';
    }
  });
}

// ===================== RECHERCHE DANS LE THÈME ACTUEL =====================
const themeSearchBar = document.getElementById('themeSearchBar');
const themeSearchResultsDiv = document.getElementById('themeSearchResults');
const themeSearchResultsContent = document.getElementById('themeSearchResultsContent');

themeSearchBar.addEventListener('input', filterCurrentTheme);

function filterCurrentTheme() {
  const searchTerm = themeSearchBar.value.toLowerCase().trim();
  
  if (searchTerm === '') {
    themeSearchResultsDiv.style.display = 'none';
    themeSearchResultsContent.innerHTML = '';
    return;
  }
  
  if (!currentTheme) {
    themeSearchResultsDiv.style.display = 'block';
    themeSearchResultsContent.innerHTML = '<p style="color: var(--muted); text-align: center; padding: 1rem;">⚠️ Veuillez sélectionner un thème d\'abord</p>';
    return;
  }
  
  const results = [];
  
  // Rechercher dans la fiche du thème
  if (currentTheme.ficheRich) {
    currentTheme.ficheRich.forEach(section => {
      // Recherche dans le titre de section
      if (section.title.toLowerCase().includes(searchTerm)) {
        results.push({
          type: 'Titre de section',
          content: section.title
        });
      }
      
      // Recherche dans les items de la section
      section.items.forEach(item => {
        if (item.toLowerCase().includes(searchTerm)) {
          results.push({
            type: `Section: ${section.title}`,
            content: item.replace(/\*\*(.+?)\*\*/g, '$1')
          });
        }
      });
    });
  }
  
  // Rechercher dans les explications des questions (pas les questions elles-mêmes)
  currentTheme.questions.forEach((q, idx) => {
    if (q.explanation.toLowerCase().includes(searchTerm)) {
      results.push({
        type: `Explication Q${idx + 1}`,
        content: q.explanation
      });
    }
  });
  
  // Afficher les résultats
  if (results.length > 0) {
    themeSearchResultsDiv.style.display = 'block';
    themeSearchResultsContent.innerHTML = `
      <div style="margin-bottom: 1rem; color: var(--accent); font-weight: 600;">
        ${results.length} résultat(s) trouvé(s) dans "${currentTheme.title}"
      </div>
    ` + results.map(r => `
      <div style="background: rgba(88, 166, 255, 0.1); padding: 1rem; margin-bottom: 0.8rem; border-radius: 6px; border-left: 3px solid var(--accent);">
        <div style="margin-bottom: 0.5rem;">
          <span style="background: rgba(167, 139, 250, 0.3); color: #a78bfa; padding: 0.2rem 0.6rem; border-radius: 4px; font-size: 0.85em;">${r.type}</span>
        </div>
        <div style="color: var(--text); line-height: 1.6;">${highlightText(r.content, searchTerm)}</div>
      </div>
    `).join('');
  } else {
    themeSearchResultsDiv.style.display = 'block';
    themeSearchResultsContent.innerHTML = '<p style="color: var(--muted); text-align: center; padding: 1rem;">Aucun résultat trouvé dans ce thème</p>';
  }
}

// Bouton de réinitialisation complète (à côté de la recherche)
const resetAllDataBtn = document.getElementById('resetAllData');
resetAllDataBtn.addEventListener('click', () => {
  if (confirm('⚠️ ATTENTION ! Voulez-vous vraiment tout effacer ?\n\n- Tous les thèmes\n- Toutes les réponses\n- Toutes les statistiques\n- Toutes les questions ratées\n\nCette action est IRRÉVERSIBLE !')) {
    safeRemoveItem('quizProgress');
    safeRemoveItem('failedQuestions');
    safeRemoveItem('themeStats');
    themeProgress = {};
    THEMES.forEach(t => {
      updateThemeStatus(t.id, 'not-started');
    });
    updateThemeButtons();
    updateStats();
    currentQuestions = [];
    answers = [];
    renderQuiz();
    searchBar.value = '';
    filterThemes();
    alert('✅ Toutes les données ont été effacées !');
  }
});

// Mise à jour des statistiques globales
function updateStats() {
  const started = THEMES.filter(t => getThemeStatus(t.id) === 'started').length;
  const completed = THEMES.filter(t => getThemeStatus(t.id) === 'completed').length;
  
  // Compter le NOMBRE TOTAL de questions ratées (pas le nombre de thèmes)
  const failedQuestions = JSON.parse(safeGetItem('failedQuestions', '{}') || '{}');
  const failedCount = Object.values(failedQuestions).reduce((sum, arr) => sum + arr.length, 0);
  
  // Calculer le taux de réussite basé sur les réponses réelles
  const themeStats = JSON.parse(safeGetItem('themeStats', '{}') || '{}');
  let totalAnswered = 0;
  let totalCorrect = 0;
  
  Object.values(themeStats).forEach(stat => {
    if (stat.answered !== undefined && stat.correct !== undefined) {
      totalAnswered += stat.answered;
      totalCorrect += stat.correct;
    }
  });
  
  const successRate = totalAnswered > 0 ? Math.round((totalCorrect / totalAnswered) * 100) : 0;
  
  const statCards = document.querySelectorAll('.stat-card div:first-child');
  statCards[0].textContent = started;
  statCards[1].textContent = completed;
  statCards[2].textContent = successRate + '%';
  statCards[3].textContent = failedCount;
  
  updateCharts();
}

// Graphiques circulaires
function createCircularChart(canvasId, value, total, color) {
  const canvas = document.getElementById(canvasId);
  const ctx = canvas.getContext('2d');
  const centerX = canvas.width / 2;
  const centerY = canvas.height / 2;
  const radius = 60;
  const lineWidth = 15;
  
  // Effacer le canvas
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  
  // Cercle de fond
  ctx.beginPath();
  ctx.arc(centerX, centerY, radius, 0, 2 * Math.PI);
  ctx.strokeStyle = '#21262d';
  ctx.lineWidth = lineWidth;
  ctx.stroke();
  
  // Arc de progression
  const percentage = total > 0 ? (value / total) : 0;
  const endAngle = -0.5 * Math.PI + (2 * Math.PI * percentage);
  
  ctx.beginPath();
  ctx.arc(centerX, centerY, radius, -0.5 * Math.PI, endAngle);
  ctx.strokeStyle = color;
  ctx.lineWidth = lineWidth;
  ctx.stroke();
  
  // Texte au centre
  ctx.fillStyle = '#fff';
  ctx.font = 'bold 28px Arial';
  ctx.textAlign = 'center';
  ctx.textBaseline = 'middle';
  ctx.fillText(value, centerX, centerY);
}

function updateCharts() {
  const completed = THEMES.filter(t => getThemeStatus(t.id) === 'completed').length;
  const started = THEMES.filter(t => getThemeStatus(t.id) === 'started').length;
  const notStarted = THEMES.filter(t => getThemeStatus(t.id) === 'not-started').length;
  const total = THEMES.length;
  
  createCircularChart('completedChart', completed, total, '#3fb950');
  createCircularChart('startedChart', started, total, '#1f6feb');
  createCircularChart('notStartedChart', notStarted, total, '#6e7681');
}

// Mode révision
let revisionModeActive = false;
const revisionBtn = document.getElementById('revisionMode');

revisionBtn.addEventListener('click', () => {
  if (!currentTheme) {
    alert('⚠️ Veuillez d\'abord sélectionner un thème.');
    return;
  }
  
  revisionModeActive = !revisionModeActive;
  
  if (revisionModeActive) {
    // Récupérer les questions ratées pour le thème actuel
    const failed = JSON.parse(safeGetItem('failedQuestions', '{}') || '{}');
    const failedIndices = failed[currentTheme.id] || [];
    
    if (failedIndices.length === 0) {
      alert('🎉 Aucune question ratée dans ce thème !\n\nVous pouvez faire un quiz normal pour créer des questions à réviser.');
      revisionModeActive = false;
      return;
    }
    
    // Charger uniquement les questions ratées
    const failedQuestions = failedIndices.map(idx => currentTheme.questions[idx]).filter(q => q !== undefined);
    
    if (failedQuestions.length === 0) {
      alert('⚠️ Erreur : Questions ratées introuvables.');
      revisionModeActive = false;
      return;
    }
    
    // Mélanger les options pour chaque question ratée
    currentQuestions = failedQuestions.map(q => {
      const optionsWithIndex = q.options.map((opt, idx) => ({ opt, idx }));
      const shuffledOptions = shuffle(optionsWithIndex);
      const newCorrectIndex = shuffledOptions.findIndex(item => item.idx === q.correctIndex);
      
      return {
        question: q.question,
        options: shuffledOptions.map(item => item.opt),
        correctIndex: newCorrectIndex,
        explanation: q.explanation
      };
    });
    
    const revisionLength = currentQuestions.length;
    answers = new Array(revisionLength);
    for (let i = 0; i < revisionLength; i++) {
      answers[i] = null;
    }
    renderQuiz();
    
    revisionBtn.style.background = '#f85149';
    revisionBtn.textContent = '❌ Quitter révision';
    alert(`📚 Mode révision activé !\n\n${failedQuestions.length} question(s) ratée(s) chargée(s) pour ce thème.`);
    
  } else {
    // Quitter le mode révision
    revisionBtn.style.background = '#a78bfa';
    revisionBtn.textContent = '🔄 Mode révision';
    currentQuestions = [];
    answers = [];
    renderQuiz();
  }
});

// Gestion des questions ratées
function addFailedQuestion(themeId, questionIndex) {
  const failed = JSON.parse(safeGetItem('failedQuestions', '{}') || '{}');
  if (!failed[themeId]) {
    failed[themeId] = [];
  }
  if (!failed[themeId].includes(questionIndex)) {
    failed[themeId].push(questionIndex);
  }
  safeSetItem('failedQuestions', JSON.stringify(failed));
  updateStats();
}

function removeFailedQuestion(themeId, questionIndex) {
  const failed = JSON.parse(safeGetItem('failedQuestions', '{}') || '{}');
  if (failed[themeId]) {
    failed[themeId] = failed[themeId].filter(i => i !== questionIndex);
    if (failed[themeId].length === 0) {
      delete failed[themeId];
    }
  }
  safeSetItem('failedQuestions', JSON.stringify(failed));
  updateStats();
}

// Réinitialiser tout
const resetAllBtn = document.getElementById('resetAllBtn');
resetAllBtn.addEventListener('click', () => {
  if (confirm('⚠️ Voulez-vous vraiment réinitialiser TOUS les thèmes ? Cette action est irréversible.')) {
    safeRemoveItem('quizProgress');
    safeRemoveItem('failedQuestions');
    safeRemoveItem('themeStats');
    themeProgress = {};
    THEMES.forEach(t => {
      updateThemeStatus(t.id, 'not-started');
    });
    updateThemeButtons();
    updateStats();
    currentQuestions = [];
    answers = [];
    renderQuiz();
    alert('✅ Tous les thèmes ont été réinitialisés.');
  }
});

// Afficher/masquer la fiche
let ficheVisible = true;

toggleFicheBtn.addEventListener('click', () => {
  ficheVisible = !ficheVisible;
  if (ficheVisible) {
    ficheEl.style.display = '';
    toggleFicheBtn.textContent = '👁️ Masquer la fiche';
  } else {
    ficheEl.style.display = 'none';
    toggleFicheBtn.textContent = '👁️ Afficher la fiche';
  }
});

// Mode plein écran (compatible Safari)
const fullscreenBtn = document.getElementById('fullscreenBtn');
fullscreenBtn.addEventListener('click', () => {
  const docEl = document.documentElement;
  
  // Vérifier si on est en plein écran (compatible Safari)
  const isFullscreen = document.fullscreenElement || 
                      document.webkitFullscreenElement || 
                      document.mozFullScreenElement || 
                      document.msFullscreenElement;
  
  if (!isFullscreen) {
    // Entrer en plein écran avec support Safari
    if (docEl.requestFullscreen) {
      docEl.requestFullscreen();
    } else if (docEl.webkitRequestFullscreen) { // Safari
      docEl.webkitRequestFullscreen();
    } else if (docEl.mozRequestFullScreen) { // Firefox
      docEl.mozRequestFullScreen();
    } else if (docEl.msRequestFullscreen) { // IE11
      docEl.msRequestFullscreen();
    }
    fullscreenBtn.textContent = '🖥️ Quitter plein écran';
  } else {
    // Sortir du plein écran avec support Safari
    if (document.exitFullscreen) {
      document.exitFullscreen();
    } else if (document.webkitExitFullscreen) { // Safari
      document.webkitExitFullscreen();
    } else if (document.mozCancelFullScreen) { // Firefox
      document.mozCancelFullScreen();
    } else if (document.msExitFullscreen) { // IE11
      document.msExitFullscreen();
    }
    fullscreenBtn.textContent = '🖥️ Plein écran';
  }
});

// Écouter les changements de plein écran (compatible Safari)
document.addEventListener('fullscreenchange', updateFullscreenButton);
document.addEventListener('webkitfullscreenchange', updateFullscreenButton); // Safari
document.addEventListener('mozfullscreenchange', updateFullscreenButton); // Firefox
document.addEventListener('MSFullscreenChange', updateFullscreenButton); // IE11

function updateFullscreenButton() {
  const isFullscreen = document.fullscreenElement || 
                      document.webkitFullscreenElement || 
                      document.mozFullScreenElement || 
                      document.msFullscreenElement;
  
  if (!isFullscreen) {
    fullscreenBtn.textContent = '🖥️ Plein écran';
  }
}

// Initialiser les statistiques et graphiques au chargement
updateStats();

startQuizBtn.onclick = () => {
  if (!currentTheme) return;
  const count = Math.min(parseInt(questionCountSel.value) || 25, currentTheme.questions.length);
  
  // Sélectionner les questions et mélanger les options
  const selectedQuestions = pickExactCount(currentTheme.questions, count);
  currentQuestions = selectedQuestions.map(q => {
    // Créer une copie de la question avec les options mélangées
    const optionsWithIndex = q.options.map((opt, idx) => ({ opt, idx }));
    const shuffledOptions = shuffle(optionsWithIndex);
    
    // Trouver la nouvelle position de la bonne réponse
    const newCorrectIndex = shuffledOptions.findIndex(item => item.idx === q.correctIndex);
    
    return {
      question: q.question,
      options: shuffledOptions.map(item => item.opt),
      correctIndex: newCorrectIndex,
      explanation: q.explanation
    };
  });
  
  answers = new Array(count);
  for (let i = 0; i < count; i++) {
    answers[i] = null;
  }
  
  // Marquer le thème comme commencé
  updateThemeStatus(currentTheme.id, 'started');
  updateThemeButtons();
  
  renderQuiz();
};

toggleFicheBtn.onclick = () => {
  showFiche = !showFiche;
  ficheEl.style.display = showFiche ? "block" : "none";
  toggleFicheBtn.textContent = showFiche ? "Masquer la fiche" : "Afficher la fiche";
};

// ===================== EXPORT EN PAGE WEB =====================

function escapeHtml(text) {
  const div = document.createElement('div');
  div.textContent = text;
  return div.innerHTML;
}

function generateThemeHtmlDocument(theme) {
  let html = `<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>${escapeHtml(theme.title)}</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { 
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.8; 
      padding: 40px;
      max-width: 900px;
      margin: 0 auto;
      background: #f5f5f5;
      color: #333;
    }
    .container {
      background: white;
      padding: 50px;
      border-radius: 8px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    }
    h1 { 
      color: #2c5aa0; 
      font-size: 2.5em; 
      border-bottom: 4px solid #2c5aa0; 
      padding-bottom: 15px; 
      margin-bottom: 10px; 
    }
    .category-info {
      color: #666;
      font-style: italic;
      margin-bottom: 40px;
      font-size: 1.1em;
    }
    h2 { 
      color: #3b7dd6; 
      font-size: 2em; 
      margin-top: 50px; 
      margin-bottom: 25px; 
      border-bottom: 3px solid #3b7dd6; 
      padding-bottom: 10px; 
    }
    h3 { 
      color: #4a8ee0; 
      font-size: 1.5em; 
      margin-top: 30px; 
      margin-bottom: 15px; 
    }
    ul { 
      margin: 15px 0 25px 0; 
      padding-left: 40px; 
    }
    li { 
      margin: 12px 0; 
      line-height: 1.8;
    }
    strong { 
      color: #000; 
      font-weight: 600; 
    }
    .fiche-section {
      margin-bottom: 30px;
    }
    .question-block { 
      margin: 30px 0; 
      padding: 25px; 
      background: linear-gradient(to right, #f0fdf4, #fff);
      border-left: 5px solid #3fb950;
      border-radius: 8px;
      box-shadow: 0 1px 3px rgba(0,0,0,0.05);
    }
    .question-title { 
      font-weight: 600; 
      font-size: 1.2em; 
      color: #1a1a1a; 
      margin-bottom: 15px; 
    }
    .correct-answer { 
      color: #16a34a; 
      font-weight: 600; 
      margin: 12px 0; 
      padding: 10px 20px;
      background: #dcfce7;
      border-radius: 6px;
      display: inline-block;
    }
    .explanation { 
      color: #555; 
      font-style: italic; 
      margin: 15px 0; 
      padding: 15px 20px; 
      background: #fafafa; 
      border-left: 3px solid #e5e5e5;
      border-radius: 4px; 
    }
    .page-break { 
      height: 2px;
      background: linear-gradient(to right, transparent, #3b7dd6, transparent);
      margin: 60px 0;
    }
    @media print {
      body { background: white; padding: 0; }
      .container { box-shadow: none; padding: 20px; }
      .question-block { page-break-inside: avoid; }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>${escapeHtml(theme.title)}</h1>
    <p class="category-info">📂 Catégorie : ${escapeHtml(theme.category)}</p>
`;

  // Ajouter la fiche complète
  if (theme.ficheRich && theme.ficheRich.length > 0) {
    html += '<h2>📚 Fiche de cours</h2>\n';
    theme.ficheRich.forEach(section => {
      html += `<div class="fiche-section">\n`;
      html += `<h3>${escapeHtml(section.title)}</h3>\n<ul>\n`;
      section.items.forEach(item => {
        let formattedItem = escapeHtml(item);
        formattedItem = formattedItem.replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>');
        html += `  <li>${formattedItem}</li>\n`;
      });
      html += '</ul>\n</div>\n';
    });
    html += '<div class="page-break"></div>\n';
  }

  // Ajouter les questions avec bonnes réponses et explications
  html += '<h2>📝 Questions et réponses</h2>\n';
  theme.questions.forEach((q, idx) => {
    const correctAnswer = q.options[q.correctIndex];
    html += `
<div class="question-block">
  <div class="question-title">${idx + 1}. ${escapeHtml(q.question)}</div>
  <div class="correct-answer">✓ Réponse correcte : ${escapeHtml(correctAnswer)}</div>
  <div class="explanation">💡 Explication : ${escapeHtml(q.explanation)}</div>
</div>
`;
  });

  html += `
  </div>
</body>
</html>`;
  return html;
}

function downloadHtmlFile(content, filename) {
  const blob = new Blob([content], {
    type: 'text/html;charset=utf-8'
  });
  const url = URL.createObjectURL(blob);
  const link = document.createElement('a');
  link.href = url;
  link.download = filename;
  link.style.display = 'none';
  document.body.appendChild(link);
  link.click();
  setTimeout(() => {
    document.body.removeChild(link);
    URL.revokeObjectURL(url);
  }, 100);
}

function openInNewTab(content) {
  const blob = new Blob([content], { type: 'text/html;charset=utf-8' });
  const url = URL.createObjectURL(blob);
  window.open(url, '_blank');
  setTimeout(() => URL.revokeObjectURL(url), 1000);
}

// Bouton exporter thème actuel
const exportThemeBtn = document.getElementById('exportThemeBtn');
if (exportThemeBtn) {
  exportThemeBtn.addEventListener('click', () => {
    if (!currentTheme) {
      alert('⚠️ Veuillez sélectionner un thème à exporter.');
      return;
    }
    try {
      const html = generateThemeHtmlDocument(currentTheme);
      const filename = `${currentTheme.id}_${currentTheme.title.replace(/[^a-z0-9]/gi, '_')}.html`;
      downloadHtmlFile(html, filename);
      // Ouvrir aussi dans un nouvel onglet pour prévisualisation
      openInNewTab(html);
      alert(`✅ Page HTML téléchargée et ouverte dans un nouvel onglet !\n\nVous pouvez maintenant :\n- Copier-coller le contenu dans Google Docs\n- Imprimer en PDF (Ctrl+P)\n- Sauvegarder la page`);
    } catch(e) {
      alert('❌ Erreur lors de l\'export : ' + e.message);
      console.error(e);
    }
  });
} else {
  console.error('Bouton exportThemeBtn non trouvé !');
}

// Bouton exporter tous les thèmes
const exportAllThemesBtn = document.getElementById('exportAllThemes');
if (exportAllThemesBtn) {
  exportAllThemesBtn.addEventListener('click', () => {
    if (!confirm('📦 Exporter tous les 45 thèmes en 45 pages HTML séparées ?\n\nCela va télécharger 45 fichiers HTML.')) {
      return;
    }
    
    let exportedCount = 0;
    THEMES.forEach((theme, index) => {
      setTimeout(() => {
        try {
          const html = generateThemeHtmlDocument(theme);
          const filename = `Theme_${String(index + 1).padStart(2, '0')}_${theme.id}.html`;
          downloadHtmlFile(html, filename);
          exportedCount++;
          
          if (exportedCount === THEMES.length) {
            setTimeout(() => {
              alert(`✅ Export terminé !\n\n${THEMES.length} pages HTML ont été téléchargées.\n\nVous pouvez les ouvrir dans votre navigateur\net les importer dans Google Docs.`);
            }, 500);
          }
        } catch(e) {
          console.error(`Erreur export thème ${theme.id}:`, e);
        }
      }, index * 300);
    });
  });
} else {
  console.error('Bouton exportAllThemes non trouvé !');
}

</script>
</body>
</html>

