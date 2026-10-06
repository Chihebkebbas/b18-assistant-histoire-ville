# Carnet de bord J1 · Appareillage

Un carnet par binôme, rempli au fil de l'eau avec vos propres mots. Une phrase honnête (« j'ai essayé X, j'ai vu Y, je ne comprends pas pourquoi ») vaut mieux qu'une phrase parfaite recopiée. Aucune donnée personnelle, aucune clé ni jeton, ni l'adresse complète que `dsh web` affiche (elle contient un jeton). C'est aussi votre journal de décisions (astuce 13) : ce que vous avez demandé, ce qui a cassé, ce que vous avez refusé, et pourquoi.

Binôme : Chiheb KEBBAS & Alexandre GUMERY

Thème provisoire et public visé : Histoire d'une ville

Trois questions auxquelles l'assistant pourrait répondre :

1.  Quelle est l’histoire de ce lieu ?
2.  Que s’est-il passé ici à cette date ?
3.  Quels sont les lieux historiques incontournables de la ville ?

Rôles de départ et moments d'échange : Chiheb manipule, Alexandre vérifie

## Cahier personnel (remis par le formateur en J1-01)

Recopiez les valeurs telles que le formateur vous les a remises. Ne les changez pas, ne les échangez pas avec un autre binôme.

- Limite de caractères d'un message (le nombre N) : 220
- Premier mot reconnu, en plus de « salut », « aide » et « test » : lanterne
- Second mot reconnu : voisin

## Commandes essayées

Notez le dossier de lancement, la commande et sa sortie exacte, surtout quand un outil a bloqué.

- Dossier : atelier
- Commande et résultat :
  chihebkebbas@MacBook-Air-de-KEBBAS atelier % npm test

                        > cap-web-atelier@0.1.0 test
                        > node --test tests/*.test.js

                        ✔ GET / sert la page d’accueil en HTML (31.6885ms)
                        ✔ GET /styles.css sert la feuille de style en CSS (3.4375ms)
                        ✔ GET /js/app.js sert le script en JavaScript (2.500083ms)
                        ✔ HEAD / répond sans corps avec les mêmes en-têtes (7.568958ms)
                        ✔ GET /version.json renvoie la version fournie (4.235333ms)
                        ✔ GET inconnu répond 404 (3.888084ms)
                        ✔ POST sur une ressource statique est refusé avec 405 (2.368333ms)
                        ✔ les chemins privés ne divulguent aucun fichier (7.8305ms)
                        ✔ traversal et chemins encodés ne divulguent aucun fichier (7.075166ms)
                        ℹ tests 9
                        ℹ suites 0
                        ℹ pass 9
                        ℹ fail 0
                        ℹ cancelled 0
                        ℹ skipped 0
                        ℹ todo 0
                        ℹ duration_ms 197.138125

  chihebkebbas@MacBook-Air-de-KEBBAS atelier % npm start

                        > cap-web-atelier@0.1.0 start
                        > node server/start.js

                        Cap Web prêt sur http://127.0.0.1:3000/

Pour chaque checkpoint : cochez la case quand toute la preuve de la fiche est réunie, collez la preuve (texte, commande ou phrase), puis notez ce que vous avez prédit, essayé, observé, et une difficulté qui reste.

## Le chat web (N0 Subir)

### J1-01 · 🧭 Équipage — [fiche](checkpoints/J1-01-equipage.md)

- [x] Validé
- Preuve (page de départ affichée sur votre poste, cahier personnel recopié ci-dessus) :
- Le `p#status` est-il vide dans le HTML ? Qui écrit sa phrase ?

> Dans le fichier HTML c'est vide, mais c'est public/js/app.js qui écrit la phrase avec textContent

- Décision prise ensemble :
  _ Chiheb commence à manipuler par ce que toutes les prérequis de l'application sont déjà installées sur son pc
  _ Les trois questions couverent date, lieu et découverte
- Difficulté qui reste : Rien pour l'instant

### J1-02 · 💬 Premier prompt — [fiche](checkpoints/J1-02-premier-prompt.md)

- [x] Validé
- Preuve : `essais-n0/chatbot-v1.html` s'ouvre ; le prompt et la première réponse sont collés ci-dessous, en entier, sans donnée personnelle.
- Mon prompt, tel quel : "Fais-moi un chatbot sur "Histoire d'une ville", dans une seule page HTML que j'ouvre dans mon navigateur."
- La première réponse du chat (texte et code), telle quelle :

        De quelle ville le chatbot doit-il parler ?

        Paris

        Modifié un Canvas

        Réfléchi pendant 1s
        Create a single-page HTML chatbot about Paris history, knowledge-based Q&A (rule-based, keyword matching), nice UI. Should it be a canvas? User says "une seule page HTML que j'ouvre dans mon navigateur" — a canvas of type text/html fits. Load canvas skill first.

        Lu canvas

        Lu Canvas – Html

        Réfléchi pendant 1s
        Create the HTML chatbot about Paris history. Rule-based keyword matching with a knowledge base of Paris history topics. Self-contained. Write the canvas file.

        Créé Chatbot – Histoire de Paris

        Chatbot – Histoire de Paris

              <!doctype html>
              <html lang="fr">
              <head>
              <meta charset="UTF-8" />
              <meta name="viewport" content="width=device-width, initial-scale=1.0" />
              <title>Chatbot – Histoire de Paris</title>
              <style>
                :root { font-family: 'Segoe UI', system-ui, sans-serif; }
                * { box-sizing: border-box; }
                body { margin: 0; background: #12122b; color: #f3f3f7; min-height: 100vh; display: flex; flex-direction: column; }
                header {
                  padding: 18px 24px; background: linear-gradient(135deg, #3b2f63, #6b4fa0);
                  box-shadow: 0 3px 12px rgba(0,0,0,.45); position: sticky; top: 0; z-index: 2;
                }
                header h1 { margin: 0; font-size: 1.3rem; }
                header p { margin: 4px 0 0; font-size: .85rem; opacity: .8; }
                #chat { flex: 1; width: 100%; max-width: 760px; margin: 0 auto; padding: 20px 16px 130px; overflow-y: auto; }
                .msg { max-width: 82%; margin: 10px 0; padding: 12px 15px; border-radius: 16px; line-height: 1.5; font-size: .95rem; white-space: pre-wrap; box-shadow: 0 1px 4px rgba(0,0,0,.3); }
                .bot { background: #232347; border-bottom-left-radius: 4px; }
                .user { background: #6b4fa0; margin-left: auto; border-bottom-right-radius: 4px; }
                .msg b { color: #ffd97a; }
                .msg .hint { display: inline-block; margin: 5px 6px 0 0; padding: 4px 10px; background: rgba(255,255,255,.1); border: 1px solid rgba(255,255,255,.2); border-radius: 999px; font-size: .8rem; cursor: pointer; }
                .msg .hint:hover { background: rgba(255,255,255,.22); }
                #suggestions { max-width: 760px; margin: 0 auto; padding: 0 16px; display: flex; flex-wrap: wrap; gap: 8px; }
                #suggestions button, #bar button.send { padding: 8px 14px; border-radius: 999px; border: 1px solid rgba(255,255,255,.25); background: #232347; color: #f3f3f7; font-size: .82rem; cursor: pointer; }
                #suggestions button:hover { background: #34345f; }
                #bar {
                  position: fixed; bottom: 0; left: 0; right: 0; padding: 12px 16px;
                  background: #1a1a38; border-top: 1px solid rgba(255,255,255,.12);
                  display: flex; gap: 10px; max-width: 792px; margin: 0 auto;
                }
                #bar { width: 100%; }
                #inp { flex: 1; padding: 12px 16px; border-radius: 999px; border: none; background: #2b2b52; color: #fff; font-size: .95rem; outline: none; }
                #inp:focus { box-shadow: 0 0 0 2px #6b4fa0; }
                .send { background: #6b4fa0; border: none; font-weight: 600; }
                .send:hover { background: #7f61b8; }
                .typing span { display: inline-block; width: 7px; height: 7px; margin-right: 3px; background: #9d9dd0; border-radius: 50%; animation: blink 1s infinite; }
                .typing span:nth-child(2) { animation-delay: .2s; } .typing span:nth-child(3) { animation-delay: .4s; }
                @keyframes blink { 0%,100%{opacity:.25} 50%{opacity:1} }
              </style>
              </head>
              <body>
              <header>
                <h1>🏛️ Chatbot — Histoire de Paris</h1>
                <p>Pose-moi tes questions sur l'histoire de la ville, des origines à nos jours !</p>
              </header>

              <div id="chat"></div>
              <div id="suggestions"></div>

              <form id="bar" autocomplete="off">
                <input id="inp" type="text" placeholder="Ex. : Raconte-moi la prise de la Bastille…" />
                <button class="send" type="submit">Envoyer</button>
              </form>

              <script>
              const KB = [
                { k: ["origine", "lutece", "lutèce", "fondation", "fondé", "création", "gaulois", "romain", "antiquité", "cite", "cité"],
                  a: "**Paris à ses origines** 🏺\n\nLes Parisii, un peuple gaulois, se sont installés au IIIᵉ siècle av. J.-C. sur l'île de la Cité, un gué naturel sur la Seine favorable au commerce. Vers 52 av. J.-C., les Romains conquièrent le site et fondent la ville de Lutetia (Lutèce), qui s'étend bientôt sur la rive gauche : forum, thermes (les arènes de Lutèce et les thermes de Cluny en sont des vestiges), aqueducs…\n\nC'est au IVᵉ siècle que la ville prend le nom de « Paris », en référence aux Parisii.\n\nEssaie : « le Moyen Âge » ou « la révolution française »." },

                { k: ["moyen age", "moyen âge", "cathedrale", "cathédrale", "notre-dame", "clovis", "capet", "philippe auguste", "sorbonne", "universite", "université"],
                  a: "**Paris au Moyen Âge** ⚜️\n\nSous Clovis, roi des Francs, Paris devient l'une des capitales du royaume (fin du Vᵉ siècle). L'île de la Cité reste le cœur du pouvoir avec le palais royal.\n\n- **Philippe Auguste** (1180-1223) fortifie la ville et fait paver les rues ; Paris devient la plus grande ville d'Europe avec environ 200 000 habitants.\n- L'université et la **Sorbonne** fondée au XIIIᵉ siècle font de Paris le centre intellectuel de la chrétienté.\n- La **cathédrale Notre-Dame**, commencée en 1163 et achevée vers 1345, est un chef-d'œuvre de l'art gothique.\n\nEssaie : « la Renaissance » ou « Henri IV »." },

                { k: ["renaissance", "henri iv", "henri quatre", "place royale", "louvre", "francois 1er", "françois 1er"],
                  a: "**Paris à la Renaissance** 🎨\n\nAu XVIᵉ siècle, la ville s'embellit à l'italienne : François Iᵉʳ fait agrandir le Louvre et en fait sa résidence principale, ramenant de l' italianiser la cour. Les guerres de Religion secouent pourtant la ville (massacre de la Saint-Barthélemy en 1572).\n\n**Henri IV** (1589-1610) ramène la paix et lance de grands travaux : la place Royale (aujourd'hui place des Vosges), la première place publique de France, et la pose de « la poule au pot » comme symbole de prospérité. Il achève aussi le pont Neuf (achevé en 1607), le plus ancien pont de Paris encore debout.\n\nEssaie : « Louis XIV » ou « la révolution »." },

                { k: ["louis xiv", "versailles", "fronde", "moliere", "17e", "18e", "lumieres", "lumières", " enlightenment", "diderot", "voltaire"],
                  a: "**Paris classique et des Lumières** ✨\n\nSous **Louis XIV**, Paris reste la première ville d'Europe, mais le roi préfère Versailles, où la cour déménage en 1682. Les faubourgs parisiens s'étendent, les places royales (Vendôme, Victoire) embellissent la ville.\n\nAu XVIIIᵉ siècle, Paris est le foyer des **Lumières** : Voltaire, Diderot, Rousseau y débattent, l'Encyclopédie y est publiée. Cafés, salons et brochures font de la ville le centre intellectuel de l'Europe… et un foyer d'agitation qui prépare 1789.\n\nEssaie : « la révolution française » ou « le haussmann »." },

                { k: ["bastille", "revolution", "révolution", "1789", "roi", "louis xvi", "guillotine", "terreur", "concorde"],
                  a: "**Paris et la Révolution française** 🚩\n\nLe 14 juillet **1789**, les Parisiens prennent la **Bastille**, prison royale symbole de l'absolutisme : c'est le début de la Révolution. Le peuple de Paris joue un rôle moteur : marche sur Versailles en octobre 1789, la famille royale ramenée aux Tuileries, insurrections de 1792 et 1793.\n\nLouis XVI est guillotiné en 1793 place de la Révolution (aujourd'hui **place de la Concorde**). Pendant la Terreur, Robespierre et le Comité de salut public gouvernent, avant sa chute en juillet 1794 (thermidor).\n\nEssaie : « Napoléon » ou « haussmann »." },

                { k: ["napoleon", "napoléon", "empire", "arc de triomphe", "1804", "vandome"],
                  a: "**Paris napoléonien** 🎖️\n\nNapoléon Bonaparte, couronné empereur en **1804** à Notre-Dame, veut faire de Paris la plus belle ville d'Europe : il lance l'**Arc de triomphe** (commandé en 1806), la rue de Rivoli, le canal de l'Ourcq et les fontaines du Palais-Borghèse. La colonne Vendôme célèbre ses victoires.\n\nLa ville dépasse 500 000 habitants et s'équipe de numérotation des maisons et de trottoirs modernes. Après Waterloo, Paris connaît les occupations de 1814-1815… et la ville continue de grandir, couronnée par l'Arc de Triomphe achevé en 1836.\n\nEssaie : « haussmann » ou « la tour eiffel »." },

                { k: ["haussmann", "osman", "second empire", "napoleon iii", "napoléon iii", "grands boulevards", "boulevard", "1850", "modernisation"],
                  a: "**La transformation de Haussmann** 🏙️\n\nSous Napoléon III (Second Empire), le préfet **Georges-Eugène Haussmann** refait Paris de 1853 à 1870 : percement de grandes avenues rectilignes (boulevard Saint-Michel, rue de Rivoli…), immeubles en pierre de taille aux balcons en fer forgé, réseaux d'eau potable, égouts, parcs (Bois de Boulogne et de Vincennes, parc Montsouris) et gares.\n\nLe résultat : une ville aérée, salubre et prestigieuse — le « Paris postcard » que l'on connaît aujourd'hui. La ville annexe aussi ses communes limitrophes en 1860, donnant naissance aux 20 arrondissements.\n\nEssaie : « la commune » ou « la tour eiffel »." },

                { k: ["eiffel", "tour eiffel", "1889", "exposition universelle", "exposition"],
                  a: "**La tour Eiffel** 🗼\n\nÉrigée par Gustave Eiffel pour l'**Exposition universelle de 1889** (centenaire de la Révolution), la tour de 300 mètres — alors la plus haute structure du monde — était censée être temporaire. Elle a été sauvée grâce à son utilité scientifique et radiotélégraphique.\n\nLa Belle Époque fait de Paris la capitale mondiale des arts : Montmartre et Montparnasse accueillent peintres, écrivains et premiers cinémas des frères Lumière.\n\nEssaie : « les deux guerres » ou « mai 68 »." },

                { k: ["commune", "1871", "secession", "siege", "1870"],
                  a: "**La Commune de Paris (1871)** ✊\n\nAprès la défaite de la guerre franco-prussienne de 1870 et le siège de Paris (bombardements, famine), les Parisiens, furieux contre le gouvernement, se soulèvent le 18 mars **1871** et proclament la **Commune** : une insurrection populaire de 72 jours.\n\nLa Commune instaure des mesures sociales avancées (séparation Église-État, écoles laïques, remise des loyers) mais se termine dans le sang lors de la « semaine sanglante » de mai 1871, où des milliers de communards sont tués.\n\nEssaie : « la tour eiffel » ou « les deux guerres »." },

                { k: ["guerre", "1940", "occupation", "resistance", "résistance", "liberation", "libération", "1944", "hitler", "nazi", "1914", "1918", "premiere guerre", "première guerre"],
                  a: "**Paris aux deux guerres mondiales** 🕊️\n\n- **1914-1918** : les taxis de la Marne (septembre 1914) acheminent des soldats au front et sauvent Paris ; la ville est à nouveau capitale du monde artistique dans l'entre-deux-guerres.\n- **1940-1944** : Paris est occupée par l'Allemagne nazie en juin 1940 ; la Wehrmacht y défile, les Juifs parisiens sont raflés (Vél d'Hiv, juillet 1942) et la Résistance s'organise.\n- **25 août 1944** : Paris est **libérée** par les FFI et la 2ᵉ DB du général Leclerc ; le général de Gaulle descend les Champs-Élysées le 26 août.\n\nEssaie : « mai 68 » ou « paris aujourd'hui »." },

                { k: ["mai 68", "1968", "etudiant", "étudiant", "sorbonne", "manifestation"],
                  a: "**Mai 68 à Paris** ✌️\n\nEn mai **1968**, des manifestations étudiantes, parties de la Sorbonne et du Quartier latin, dégénèrent en affrontements avec la police ; le 10 mai, la « nuit des barricades » voit des centaines de barricades dans les rues.\n\nUne grève générale de 10 millions de travailleurs suit, paralysant le pays. Le mouvement aboutit à des avancées sociales (hausse du SMIG, Grenelle) et à une profonde transformation culturelle et politique.\n\nEssaie : « paris aujourd'hui » ou « chiffres clés »." },

                { k: ["aujourd'hui", "moderne", "contemporain", "population", "arrondissement", "grand paris", "2024", "jo"],
                  a: "**Paris aujourd'hui** 🌆\n\nParis intra-muros compte environ **2,1 millions d'habitants**, et la métropole du Grand Paris plus de 7 millions — l'une des plus grandes aires urbaines d'Europe. La ville est divisée en **20 arrondissements** en spirale, comme un escargot.\n\nGrandes étapes récentes : Beaubourg (1977), pyramide du Louvre (1989), Bibliothèque François-Mitterrand (1995), musée du quai Branly (2006), Grand Paris Express (nouveau métropole en travaux), et les **Jeux olympiques de 2024**, dont la cérémonie d'ouverture s'est déroulée sur la Seine.\n\nEssaie : « chiffres clés » ou « quiz »." },

                { k: ["chiffre", "clé", "cles", "clés", "statistique", "nombre", "date", "frise", "chronologie", "resume", "résumé"],
                  a: "**Frise express de l'histoire de Paris** 📜\n\n- ~52 av. J.-C. : fondation de Lutèce par les Romains\n- 508 : Clovis fait de Paris sa capitale\n- 1163-1345 : construction de Notre-Dame\n- 14 juillet 1789 : prise de la Bastille\n- 1853-1870 : transformations de Haussmann\n- 1889 : tour Eiffel et Exposition universelle\n- 25 août 1944 : libération de Paris\n- Mai 1968 : révolte étudiante\n- 2024 : Jeux olympiques\n\nDemande-moi d'approfondir une de ces époques !" },

                { k: ["quiz", "jeu", "test", "question"],
                  a: "**Quiz !** 🎯 Réponds par A, B ou C.\n\nEn quelle année la tour Eiffel a-t-elle été construite ?\n**A)** 1789  **B)** 1889  **C)** 1989\n\nEt une deuxième : qui a transformé Paris au XIXᵉ siècle ?\n**A)** Haussmann  **B)** Louis XIV  **C)** Napoléon\n\n(Écris ta réponse, je corrige !)" },
                { k: ["1889", "b)"], qreply: true,
                  a: "✅ Bravo ! La tour Eiffel a bien été inaugurée pour l'Exposition universelle de **1889**.\n\nEt pour la deuxième question, c'est bien **Haussmann** qui a transformé Paris sous Napoléon III. Tu maîtrises !" },

                { k: ["bonjour", "salut", "hello", "coucou", "bonsoir", "hey"],
                  a: "Bonjour ! 👋 Je suis ton guide dans l'histoire de **Paris**, des origines gauloises jusqu'à aujourd'hui.\n\nQue veux-tu découvrir ? Par exemple : « le Moyen Âge », « la révolution », « haussmann », « la tour eiffel »… ou « quiz » pour te tester !" },

                { k: ["merci", "thanks", "cool", "super", "génial", "genial"],
                  a: "Avec plaisir ! 😊 N'hésite pas si tu veux découvrir une autre époque ou lancer un quiz !" },

                { k: ["au revoir", "bye", "a+", "ciao"],
                  a: "Au revoir ! 👋 Reviens quand tu veux pour voyager dans le temps à Paris !" }
              ];

              const FALLBACK = "Hmm, je ne suis pas sûr de comprendre 😅. Essaie par exemple : « les origines de Paris », « le Moyen Âge », « la révolution française », « haussmann », « la tour eiffel », « mai 68 », ou tape « quiz » pour un petit test !";

              const chat = document.getElementById("chat");
              const suggestions = document.getElementById("suggestions");
              const inp = document.getElementById("inp");
              const bar = document.getElementById("bar");

              function addMsg(text, who) {
                const d = document.createElement("div");
                d.className = "msg " + who;
                d.innerHTML = text
                  .replace(/\*\*(.+?)\*\*/g, "<b>$1</b>")
                  .replace(/\n/g, "<br>");
                chat.appendChild(d);
                chat.scrollTop = chat.scrollHeight;
                return d;
              }

              function addTyping() {
                const d = document.createElement("div");
                d.className = "msg bot typing";
                d.innerHTML = "<span></span><span></span><span></span>";
                chat.appendChild(d);
                chat.scrollTop = chat.scrollHeight;
                return d;
              }

              function normalize(s) {
                return s.toLowerCase()
                  .replace(/[éèêë]/g, "e").replace(/[àâä]/g, "a").replace(/[îï]/g, "i")
                  .replace(/[ôö]/g, "o").replace(/[ûü]/g, "u").replace(/ç/g, "c");
              }

              function answer(q) {
                const n = normalize(q);
                // Quiz reply first if waiting
                if (/^a\b|^b\b|^c\b/.test(n.trim()) || /\b1889\b/.test(n)) {
                  for (const e of KB) if (e.qreply) return e.a;
                }
                let best = null, bestScore = 0;
                for (const e of KB) {
                  let score = 0;
                  for (const k of e.k) if (n.includes(normalize(k))) score += normalize(k).length;
                  if (score > bestScore) { bestScore = score; best = e; }
                }
                return best ? best.a : FALLBACK;
              }

              function send(text) {
                text = text.trim();
                if (!text) return;
                addMsg(text.replace(/</g, "&lt;"), "user");
                inp.value = "";
                const t = addTyping();
                setTimeout(() => {
                  t.remove();
                  const a = answer(text);
                  const d = addMsg(a, "bot");
                  // add follow-up chips
                  const chips = document.createElement("div");
                  const ideas = ["Frise chronologique", "Quiz", "Haussmann", "La tour Eiffel"];
                  ideas.forEach(i => {
                    const s = document.createElement("span");
                    s.className = "hint";
                    s.textContent = i;
                    s.onclick = () => send(i);
                    chips.appendChild(s);
                  });
                  d.appendChild(document.createElement("br"));
                  d.appendChild(chips);
                  chat.scrollTop = chat.scrollHeight;
                }, 450);
              }

              bar.addEventListener("submit", e => { e.preventDefault(); send(inp.value); });

              // suggestions initiales
              ["Les origines (Lutèce)", "Le Moyen Âge", "La Révolution", "Haussmann", "Frise chronologique", "Quiz"].forEach(s => {
                const b = document.createElement("button");
                b.textContent = s;
                b.onclick = () => send(s);
                suggestions.appendChild(b);
              });

              // message d'accueil
              addMsg("Bonjour ! 👋 Bienvenue sur le chatbot de l'**histoire de Paris**.\n\nJe peux te raconter la ville des **Parisii** et de **Lutèce** jusqu'aux **Jeux olympiques de 2024**. Choisis un sujet ci-dessous, ou pose ta question !", "bot");
              </script>
              </body>
              </html>

        C'est prêt ! 🏛️ Le chatbot Histoire de Paris s'affiche dans le panneau à côté : une seule page HTML autonome (CSS et JS inclus, aucune dépendance exterque), que tu peux télécharger depuis le canvas et ouvrir directement dans ton navigateur.
        Ce qu'il sait faire :
        Répondre sur toutes les grandes époques : Lutèce et les origines gauloises, le Moyen Âge, la Renaissance, la Révolution, Napoléon, Haussmann, la tour Eiffel, la Commune, les guerres, Mai 68 et Paris aujourd'hui
        Une frise chronologique résumée
        Un mini quiz interactif avec correction
        Des boutons de suggestions cliquables et des puces de relance après chaque réponse
        Le moteur est par mots-clés : tu peux facilement enrichir la base de connaissances en ajoutant des entrées dans le tableau KB du script (mots-clés + réponse). Dis-moi si tu veux ajouter des sujets, changer le style ou passer sur une autre ville !

> Explique-moi ce code, ligne par ligne, pour un débutant.

        Réfléchi pendant 1s


        Réfléchi pendant 1s
        Explain the chatbot code for a beginner, in French. Line-by-line is long; explain section by section with key lines. Keep reasonably structured.



        Voici une explication complète du code, pensée pour un débutant. Je la découpe par blocs, en reprenant les lignes les plus importantes. 🧑‍🏫
        1. L'en-tête HTML
        html
        Copier

        <!doctype html>          <!-- Dit au navigateur : "c'est une page HTML moderne" -->
        <html lang="fr">          <!-- La page commence ici, en français -->
        <head>                   <!-- Partie invisible : réglages et style -->
        <meta charset="UTF-8">   <!-- Permet d'afficher les accents (é, à…) correctement -->
        <meta name="viewport"...> <!-- Fait que la page s'adapte aux écrans de téléphone -->
        <title>...</title>        <!-- Le texte dans l'onglet du navigateur -->




        Tout ce qui est dans <head> n'apparaît pas à l'écran : ce sont les instructions techniques.
        2. Le CSS (<style>) — l'apparence
        Le CSS décrit comment ça s'affiche : couleurs, tailles, arrondis.
        css
        Copier

        body { background: #12122b; ... }   /* Fond sombre de toute la page */
        .msg { ... border-radius: 16px; }   /* Les bulles de message, avec coins arrondis */
        .bot { background: #232347; }       /* Bulles du robot : violet foncé */
        .user { background: #6b4fa0; margin-left: auto; }  /* Bulles de l'utilisateur : violet clair, poussées à droite */
        #bar { position: fixed; bottom: 0; ... }  /* La barre de saisie reste collée en bas de l'écran */




        Astuces à retenir :
        #chat, #bar visent les éléments avec id="chat", id="bar"
        .bot, .user visent les éléments avec class="bot", etc.
        @keyframes blink définit une petite animation (les points de frappe qui clignotent)
        3. Le squelette visible (<body>)
        html
        Copier

        <header>...</header>      <!-- Titre en haut, avec un dégradé violet -->
        <div id="chat"></div>     <!-- Zone vide : les messages s'afficheront ici -->
        <div id="suggestions"></div> <!-- Zone des boutons de suggestion -->
        <form id="bar">           <!-- Le formulaire du bas -->
          <input id="inp">        <!-- La case où on écrit -->
          <button>Envoyer</button>
        </form>




        Au chargement, les zones chat et suggestions sont vides : c'est le JavaScript qui les remplit.
        4. La base de connaissances (KB)
        C'est le cœur du chatbot :
        js
        Copier

        const KB = [
          { k: ["bastille", "revolution", "1789"],      // mots-clés
            a: "**Paris et la Révolution...**" },       // réponse associée
          ...
        ];




        k : la liste des mots-clés qui déclenchent cette réponse
        a : le texte affiché si un mot-clé est trouvé (**mot** sera mis en gras)
        C'est un simple tableau d'objets : pour ajouter un sujet, tu ajoutes une ligne ici, rien d'autre.
        5. Les variables de travail
        js
        Copier

        const chat = document.getElementById("chat");   // "attrape" la zone de messages
        const inp  = document.getElementById("inp");   // attrape la case de saisie
        const bar  = document.getElementById("bar");   // attrape le formulaire




        document.getElementById(...) sert à récupérer un élément HTML pour pouvoir le manipuler en JS.
        6. addMsg — afficher une bulle
        js
        Copier

        function addMsg(text, who) {
          const d = document.createElement("div");     // crée une nouvelle div (invisible pour l'instant)
          d.className = "msg " + who;                 // lui donne la classe "msg bot" ou "msg user"
          d.innerHTML = text.replace(...);            // convertit **gras** en <b>gras</b> et \n en <br>
          chat.appendChild(d);                         // l'ajoute dans la zone de chat → elle apparaît !
          chat.scrollTop = chat.scrollHeight;         // fait défiler vers le bas (le dernier message)
        }




        Deux petites transformations sympas : on écrit les réponses avec **gras** et des retours à la ligne simples, et la fonction les convertit en HTML.
        7. addTyping — l'animation "il écrit…"
        js
        Copier

        function addTyping() {
          // crée une bulle avec 3 petits points qui clignotent (via l'animation CSS "blink")
        }




        Effet purement cosmétique : ça donne l'impression que le robot réfléchit.
        8. normalize — ignorer les accents
        js
        Copier

        function normalize(s) {
          return s.toLowerCase()          // tout en minuscules
                .replace(/[éèêë]/g, "e") // é → e
                ...                     // etc. pour chaque accent
        }




        Grâce à ça, "Révolution" et "REVOLUTION" et "revolution" sont traités pareil.
        9. answer — le cerveau 🧠
        js
        Copier

        function answer(q) {
          const n = normalize(q);        // on "nettoie" la question

          // étape 1 : si l'utilisateur répond "A/B/C" au quiz, on renvoie la correction
          if (/^a\b|^b\b|^c\b/.test(n.trim())) { ... }

          // étape 2 : on cherche la meilleure entrée de KB
          let best = null, bestScore = 0;
          for (const e of KB) {                  // pour chaque sujet...
            for (const k of e.k)                 // ...pour chaque mot-clé...
              if (n.includes(normalize(k)))      // ...est-il dans la question ?
                score += normalize(k).length;    // oui → points (les mots longs comptent plus)
          }
          return best ? best.a : FALLBACK;       // meilleure réponse, ou message "je n'ai pas compris"
        }




        En résumé : la question contient-elle un des mots-clés ? Si oui → la réponse correspondante. Sinon → le message de secours FALLBACK.
        10. send — le tour complet d'un échange
        js
        Copier

        function send(text) {
          addMsg(text, "user");          // 1. affiche le message de l'utilisateur
          inp.value = "";                // 2. vide la case de saisie
          const t = addTyping();         // 3. affiche les points "..."
          setTimeout(() => {             // 4. attend 450 ms (effet de réflexion)
            t.remove();                  // 5. enlève les points
            const d = addMsg(answer(text), "bot");  // 6. calcule et affiche la réponse
            // 7. ajoute des puces cliquables ("Quiz", "Haussmann"…) sous la réponse
          }, 450);
        }




        11. Les connexions et le démarrage
        js
        Copier

        bar.addEventListener("submit", e => {   // quand on valide le formulaire...
          e.preventDefault();                   // ...empêche le rechargement de la page
          send(inp.value);                      // ...envoie le texte
        });

        // crée les boutons de suggestion du départ, un par un
        ["Les origines (Lutèce)", ...].forEach(s => { ... });

        // affiche le message de bienvenue
        addMsg("Bonjour ! 👋 ...", "bot");




        addEventListener("submit", ...) = « quand l'utilisateur appuie sur Entrée ou sur Envoyer, exécute cette fonction ».
        🎯 En une phrase
        Le chatbot est une base de mots-clés → réponses : la question est nettoyée, comparée aux mots-clés, et la meilleure correspondance est affichée dans une bulle de chat stylée — tout le reste (bulles, animation, boutons) est de la présentation autour de cette idée simple.
        Dis-moi si tu veux que je détaille un point précis (les regex, setTimeout, le scoring des mots-clés…) !

- Trois lignes d'observation (ce que j'ai vu en utilisant la page) :
  > L'application a une interface très générique et il y a pas mal d'erreurs dans le css
  > Sur les questions qui contiennent un mot-clé, par exemple « Haussmann », le chatbot donne une réponse détaillée.
  > Le chatbot n’est pas intelligent : il répond uniquement selon sa base de connaissances. Pour deux questions différentes qui contiennent un mot-clé commun, il donne la même réponse.
- Difficulté qui reste :
  > La logique de la fonction answer qui est le cerveau du chat

### J1-03 · 💥 Ça marche… jusqu'à quand — [fiche](checkpoints/J1-03-jusqua-quand.md)

- [x] Validé
- Liste de contrôle de la version 1 (cinq à huit comportements essayés) :

        > Taper un message et cliquer « Envoyer » l'affiche dans la conversation
        > Appuyer sur Entrée envoie aussi le message
        > Un message vide n'est pas envoyé
        > Le bot répond juste quand un mot-clé du thème est présent (ex: « Haussmann »)
        > Une animation de points (« typing ») s'affiche avant la réponse
        > Les boutons de suggestion en bas on les voit pas, leur css et mal géré
        > Des puces de relance apparaissent après chaque réponse du bot
        > Taper « quiz » lance le mini-quiz mais il donnes directemnt la bonne réponse quand on réponds avec A,b ou meme quand on se trompe

- Journal des régressions, une entrée par modification : ce que j'ai demandé · ce qui marche maintenant · ce qui marchait et ne marche plus · ce que je n'avais pas vu, et comment je l'ai trouvé.
  - Modification 1 : Ajoute un bouton Effacer qui vide toute la conversation.

            - Demandé : Ajoute un bouton Effacer qui vide toute la conversation.
            - Marche maintenant : le bouton "🗑️ Effacer" vide le chat et réaffiche le message d'accueil.
            - Testé : fonctionne.
            - Cassé : rien, le reste de la liste de contrôle fonctionne encore.
            - Pas vu avant : les boutons de suggestion du bas restent mal affichés (déjà repéré).

  - Modification 2 : Garde les messages affichés même si je recharge la page.

            - Demandé : Garde les messages affichés même si je recharge la page.
            - Marche maintenant : chatbot-v3.html contient la sauvegarde (localStorage) : testé, après F5 la conversation reste affichée.
            - Cassé : rien d'autre ne semble cassé dans v3.
            - Pas vu avant : rien pour l'instant

  - Modification 3 : Vérifie ma réponse quand je séléctionne quizz

            - Demandé : Vérifie ma réponse quand je sélectionne quizz
            - Marche maintenant : : le quiz corrige vraiment les réponses A/B/C, avec 4 questions et un score.
            - Cassé : rien, mais tant que le quiz est actif, le bot ignore toute question normale et redemande "A, B ou C" — même sur une vraie question hors quiz.
            - Pas vu avant : il n'y a aucun moyen d'abandonner le quiz en cours de route

- Chasse à l'angle mort (ce qui a été trouvé, et par qui) :
  > Chiheb : Sur chatbot-v4.html : J’ai trouvé un bug : si on lance le quiz puis qu’on clique sur « Effacer » avant la fin, le chat est bien vidé, mais le bot reste en mode quiz. Si on pose ensuite une question normale, il demande de répondre par A, B ou C. Le bouton « Effacer » ne réinitialise donc pas le quiz.
- Deux phrases de conclusion :
  > C’est la modification 3 (le quiz) avec la modification 1 (Effacer) qui a créé le plus de problèmes. Le bouton « Effacer » vidait le chat, mais ne réinitialisait pas le quiz
- Difficulté qui reste :

### J1-04 · 🎲 Même prompt, autre réponse — [fiche](checkpoints/J1-04-meme-prompt.md)

- [ ] Validé
- Le prompt de référence (identique aux trois essais) :
- Le tableau des écarts (trois colonnes A, B, C ; au moins quatre critères ; des faits, pas des impressions) :
- Une phrase de conclusion (ce que ces écarts autorisent, ce qu'ils interdisent de supposer) :
- Difficulté qui reste :

## L'agent (N1 Demander)

### J1-05 · 🛠 dsh en main — [fiche](checkpoints/J1-05-dsh-en-main.md)

- [ ] Validé
- Preuve (`dsh --version`, mode Read Only, modèle `capweb-ia`, `git status -- atelier` propre ; **jamais la clé**) :
- La consigne exacte envoyée à l'agent et sa réponse :
- Pour chaque fichier cité : existe ou non, description juste ou fausse, pourquoi ; et un fichier qu'il n'a pas cité :
- Difficulté qui reste :

### J1-06 · 🧱 Anatomie d'un prompt — [fiche](checkpoints/J1-06-anatomie-dun-prompt.md)

- [ ] Validé
- Preuve (deux prompts, deux résultats, grille remplie, commit du squelette) :
- Prompt vague et ce que montre la page (trois lignes, fichiers touchés) :
- Prompt structuré, en six parties, tel qu'envoyé :
- Les hypothèses de l'agent, et ma réponse :
- La grille (✔ ou ✘ et un mot, pour « vague » puis « structuré ») :
- Une phrase : entre les deux résultats, ce qui a le plus changé, c'est… parce que la partie… de mon prompt disait…
- Difficulté qui reste :

### J1-07 · 👣 Petits pas — [fiche](checkpoints/J1-07-petits-pas.md)

- [ ] Validé
- Preuve (découpage écrit avant la première demande, trois diffs relus, un refus écrit, un commit par étape acceptée, trois boutons de questions qui fonctionnent) :
- La tâche, mes trois questions et mon découpage en trois étapes (écrit avant la première demande d'écriture) :
- Ce que l'agent a proposé comme découpage, ce que j'ai gardé, pourquoi :
- Mon refus écrit : ce que l'agent avait fait, pourquoi je le refuse, ce que j'ai demandé à la place :
- Difficulté qui reste :

**Journal des décisions.** Une ligne par demande faite à l'agent, de J1-07 à J1-09 (les trois étapes de J1-07, puis la correction de J1-08, puis les six demandes de J1-09) : la demande copiée, le diff relu (fichiers, nombre de lignes, une chose que je n'avais pas demandée ?), le verdict et pourquoi.

| N°  | Demande | Diff relu | Verdict et pourquoi |
| --- | ------- | --------- | ------------------- |
| 1   |         |           |                     |
| 2   |         |           |                     |
| 3   |         |           |                     |
| 4   |         |           |                     |
| 5   |         |           |                     |
| 6   |         |           |                     |
| 7   |         |           |                     |
| 8   |         |           |                     |
| 9   |         |           |                     |
| 10  |         |           |                     |

### J1-08 · 🔎 Revue de la page — [fiche](checkpoints/J1-08-revue-de-la-page.md)

- [ ] Validé
- Preuve (trois défauts, un corrigé avec son avant et son après, diff relu, revue adverse vérifiée) :
- Mes défauts, un par ligne :

  | Lentille (structure, clavier, écrans) | Où (élément ou fichier) | Comment je l'ai vu |
  | ------------------------------------- | ----------------------- | ------------------ |
  |                                       |                         |                    |
  |                                       |                         |                    |
  |                                       |                         |                    |

- La revue adverse : trois affirmations de l'agent, la référence qu'il a donnée (fichier, ligne), mon verdict (vrai, faux, rejeté sans référence) et comment j'ai vérifié :
- Le défaut corrigé : l'avant (capture ou valeur), ma demande ciblée (copiée), le diff relu (fichiers, lignes, changement non demandé ?), l'après (même geste, même mesure) :
- Difficulté qui reste :

### J1-09 · 🧠 Un cerveau à règles, par prompts — [fiche](checkpoints/J1-09-cerveau-a-regles.md)

- [ ] Validé
- Preuve (comportements vérifiés : « Vous : … », message vide, `<b>gras</b>`, mes deux mots, ma limite ; `/js/brain.js` et `/js/view.js` affichés ; F5 ; « Effacer ») :
- Mes six demandes et leurs verdicts : dans le journal des décisions ci-dessus.
- Le rôle de chaque fichier, en une phrase chacun :
  - `app.js` :
  - `brain.js` :
  - `view.js` :
- Ce que j'ai vu quand j'ai mis `{pas du json` dans la mémoire :
- Difficulté qui reste :

### J1-10 · 🧪 Épreuve de l'explication — [fiche](checkpoints/J1-10-epreuve-explication.md)

- [ ] Validé
- Preuve (`npm test` vert avec cinq tests dont ma limite, commit de sauvegarde, remise faite) :
- Le test rouge : son nom, son message exact, et ce qu'il m'a appris :
- Épreuve de l'explication, éditeur fermé :
  - Ce que je n'ai pas su expliquer :
  - Ce que mon binôme n'a pas su expliquer :
- Difficulté qui reste :

## Quatre questions pour finir

1. Pourquoi `textContent` et pas `innerHTML` ?
2. Pourquoi trois fichiers plutôt qu'un seul ?
3. L'agent a écrit le code : comment savez-vous qu'il est juste, et qu'est-ce qui l'a vu échouer ?
4. Quelle astuce avez-vous le plus utilisée aujourd'hui, et laquelle avez-vous oubliée ?

## Aides utilisées

- Indices, aide-mémoire, voisins :
- Ce que j'ai demandé à une IA, et comment j'ai vérifié sa réponse :

## Notes personnelles (chacun)

Pour préparer l'explication de votre part du code. Chacun écrit avec ses mots.

- Nom :
- Ce que j'ai compris :
- Ce que je n'ai pas encore compris :

- Nom :
- Ce que j'ai compris :
- Ce que je n'ai pas encore compris :

Git sert à sauvegarder chaque étape acceptée : lisez les différences et nommez les fichiers à enregistrer, jamais `git add -A`. Attendez la consigne du formateur avant tout envoi vers un dépôt commun.

[README du jour](README.md) · [Aide-mémoire HTML/CSS](ressources/aide-memoire.md) · [Aide-mémoire JavaScript](ressources/aide-memoire-js.md) · [Notice dsh](ressources/dsh.md)
