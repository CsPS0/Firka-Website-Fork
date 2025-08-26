<script lang="ts">
    import '$lib/global.css';
    import { onMount } from 'svelte';

    let currentTab: 'home' | 'ipa' | 'revoke' = 'home';

    // Content for each tab
    const homeContent = `
        <h1>Firka Docs</h1>
        <p>Welcome to the documentation!</p>
    `;

    const ipaContent = `
        <h1><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#a-firka-ipa-fájlainak-telepítéséhez-kövesd-ezt-az-útmutatót"><img src="/Ipa_files/dadb8ed3-7073-4591-a004-0d4c646fa963" alt="" width="24px"> A Firka IPA fájlainak telepítéséhez kövesd ezt az útmutatót.</a></h1>
        <p>Három lehetőséged van a Firka telepítésére:</p>
        <ul>
            <li><a href="https://docs.qwit.org/Firka/ipa_telepites.html#1-feather-metódus">Feather</a> - Fizetős, nem kell gép hozzá, 1 évre érvényes (ha lejár a certificate, újra meg kell vásárolni!)</li>
            <li><a href="https://docs.qwit.org/Firka/ipa_telepites.html#2-esign-metódus">ESign</a> - Ingyenes, nem kell gép hozzá, örökre van (ajánlott)</li>
            <li><a href="https://docs.qwit.org/Firka/ipa_telepites.html#3-sidestore-metódus-a-sidestore-az-altstore-nak-egy-jobb-verziója">SideStore</a> - Ingyenes, kell hozzá Mac, viszont Windowsal is működik, 7 naponta resign (telefonon megteheted lejárat előtt.)</li>
        </ul>
        
        <h2 id="1-feather-metódus"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#1-feather-metódus">1. Feather metódus</a></h2>
        
        <h3 id="1-a-p12-és-mobileprovision-beszerzése"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#1-a-p12-és-mobileprovision-beszerzése">1. A .p12 és .mobileprovision beszerzése</a></h3>
        <ul>
            <li>Vegyél certet a <a href="https://kravasign.com/">kravasign.com</a> oldalon</li>
            <li>Várnod kell kis időt (általában 72 óra)</li>
            <li>Csatlakozz a <a href="https://discord.gg/kravasign">Discord szerverükhöz</a> és nyiss egy ticketet a rendelési számoddal</li>
        </ul>
        
        <h3 id="2-a-várakozás-után-kapsz-egy-letöltési-linket-egy-zip-fájlhoz-ami-három-dolgot-tartalmaz"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#2-a-várakozás-után-kapsz-egy-letöltési-linket-egy-zip-fájlhoz-ami-három-dolgot-tartalmaz">2. A várakozás után kapsz egy letöltési linket egy zip fájlhoz, ami három dolgot tartalmaz:</a></h3>
        <ul>
            <li>.p12</li>
            <li>.mobileprovision</li>
            <li>Egy mappa a tanúsítvány jelszavával</li>
        </ul>
        
        <h3 id="3-töltsd-le-a-legújabb-feather-ipa-t-innen-feather-github-releases"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#3-töltsd-le-a-legújabb-feather-ipa-t-innen-feather-github-releases">3. Töltsd le a legújabb Feather ipa-t innen: </a><a href="https://github.com/khcrysalis/Feather/releases">Feather GitHub Releases</a></h3>
        <ul>
            <li>Menj a sign.kravasign.com oldalra</li>
            <li>Töltsd fel a szükséges fájlokat:
                <ul>
                    <li>.p12</li>
                    <li>.mobileprovision</li>
                    <li>feather.ipa</li>
                    <li>Add meg a tanúsítvány jelszavát</li>
                </ul>
            </li>
            <li>Nyomd meg az <code class="hljs">Upload and Sign</code> gombot, és várj, ez egy kis ideig eltarthat</li>
        </ul>
        
        <h3 id="5-certificate-importálása"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#5-certificate-importálása">5. Certificate importálása:</a></h3>
        <ul>
            <li>Menj a <code class="hljs">Settings</code> fülre és kattints a <code class="hljs">Add Certificate</code> gombra</li>
            <li>Kattints a <code class="hljs">+</code>-ra és importáld a .mobileprovision-t a .p12-t és írd be a .p12 jelszavát aztán kattints a <code class="hljs">Save</code> gombra</li>
        </ul>
        
        <h3 id="6-firka-telepítése"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#6-firka-telepítése">6. Firka telepítése:</a></h3>
        <ul>
            <li>Amint telepített a Feather, nyisd meg és menj a <code class="hljs">Sources</code> fülre alul</li>
            <li>Kattints a <code class="hljs">Add Repo</code> gombra és másold be hogy <code class="hljs">https://raw.githubusercontent.com/spitkov/firkarepo/refs/heads/main/feather.json</code> és kattints az <code class="hljs">Add</code> gombra</li>
            <li>Menj a <code class="hljs">Firka Repository</code> menüpontra és kattints a letöltésre</li>
            <li>Ha letöltött menj a <code class="hljs">Library</code> fülre és kattints a Firka appra azután <code class="hljs">Sign Firka</code> aztán <code class="hljs">Start Signing</code></li>
            <li>A Signed Apps alatt látni fogod a firkát kattints rá és <code class="hljs">Install Firka</code></li>
        </ul>
        
        <h2 id="2-esign-metódus"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#2-esign-metódus">2. ESign metódus</a></h2>
        
        <h2 id="szükséged-van-ios-16-vagy-újabb-iosre"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#szükséged-van-ios-16-vagy-újabb-iosre">Szükséged van iOS 16 vagy újabb iOSre.</a></h2>
        
        <h3 id="1-dns-profil-telepítése"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#1-dns-profil-telepítése">1. DNS profil telepítése</a></h3>
        <ul>
            <li>Nyisd meg az <a href="https://whysoooofurious.netlify.app/">WSF Sideloading</a> weboldalt a Safariban</li>
            <li>Nyomj rá a <code class="hljs">Downloads</code> gombra, majd a <code class="hljs">Config Profiles</code> gombra</li>
            <li>Válaszd a <code class="hljs">madNS</code> profilt</li>
            <li>A profil letöltése után nyisd meg a <strong>Beállításokat</strong></li>
            <li>A neved alatt megjelenik a <strong>Profil Letöltve</strong> (vagy angolul: <strong>Profile Downloaded</strong>)</li>
            <li>Nyomj rá, majd nyomd meg a <strong>Telepítés/Install</strong> gombot</li>
            <li>Kövesd az utasításokat (a felugró ablakokon nyomd a <strong>Következő/Next</strong> gombot)</li>
            <li>A telepítés után görgess le az <strong>Általános/General</strong> menüpontra</li>
            <li>Nyomj a <strong>VPN, DNS, és eszközfelügyelet</strong> (vagy iOS 18-ban: <strong>VPN és eszközfelügyelet</strong>) opcióra</li>
            <li>Válaszd a <strong>DNS</strong> opciót és válassz egyet a lehetőségek közül:
                <ul>
                    <li><strong>Sima</strong>: Ajánlott, alap funkcionalitás</li>
                    <li><strong>AdBlock</strong>: Letiltja a reklámokat (néhány script is letiltásra kerülhet, ami problémákat okozhat)</li>
                    <li><strong>OTA blocker</strong>: Letiltja az Over-The-Air (Apple szerverekről küldött) frissítéseket</li>
                </ul>
            </li>
        </ul>
        
        <h3 id="2-tanúsítványok-letöltése"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#2-tanúsítványok-letöltése">2. Tanúsítványok letöltése</a></h3>
        <ul>
            <li>Menj vissza a korábban megnyitott weboldalra</li>
            <li>Nyomj a <code class="hljs">Certificates</code> gombra, majd újra a <code class="hljs">Certificates</code> opcióra</li>
            <li>Engedélyezd a fájl letöltését és töltsd le.</li>
        </ul>
        
        <h3 id="3-portal-telepítése"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#3-portal-telepítése">3. Portal telepítése</a></h3>
        <ul>
            <li>Menj vissza a letöltési oldalra</li>
            <li>Nyomj a <code class="hljs">Portal</code> gombra</li>
            <li>Próbáld meg az egyik <code class="hljs">Portal - XXXXX</code> opciót</li>
            <li>Ha "<em>Integritás nem ellenőrizhető</em>" hibát kapsz, próbáld a többi lehetőséget</li>
            <li>Vannak ESign only certificatek, de ez minket nem zavar mivel ESign-t akarunk telepíteni, csak később lesz másab</li>
            <li>Ha egyik sem működik, feketelistán lehetsz - írj a Firka Discord szerverbe segítségért, vagy olvasd el a "<a href="https://docs.qwit.org/Firka/revoke_fix.html">Revoke Fix Guide</a>"-ot.</li>
            <li>Menj a beállitásokba utána általános az alatt VPN és eszközfelügyelet ott keresd meg a Profilt amit letöltöttél menjn rá és azon belül kattints a megbizásra utána megbizás (vagy megbizás és újraindítás)</li>
        </ul>
        
        <h3 id="4-esign-telepítése"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#4-esign-telepítése">4. ESign telepítése</a></h3>
        <ul>
            <li>Nyisd meg a <strong>Portal</strong>t</li>
            <li>Menj végig a beállítási folyamaton</li>
            <li>Navigálj a <code class="hljs">Downloads</code> fülre</li>
            <li>Nyomd meg az <strong>ESign</strong> opciót, és válassza ki ugyanazt amilyen nevű Portal-t töltöttél le, majd telepítsd ugyanúgy, mint a <strong>Portal</strong>-t</li>
            <li>Nyisd meg az <strong>ESignt</strong> és fogadd el a licencszerződést</li>
        </ul>
        
        <h3 id="5-tanúsítványok-telepítése"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#5-tanúsítványok-telepítése">5. Tanúsítványok telepítése</a></h3>
        <ul>
            <li>Kattints alul a <code class="hljs">File</code> gombra</li>
            <li>Aztán a 3 pöttyére jobb felül</li>
            <li>Keresd meg a letöltött <code class="hljs">certificates.zip</code> file-t és importáld</li>
            <li>Kattints a zip-re és utána Unzip</li>
            <li>Keresd meg amilyen portál-t telepítettél</li>
            <li>Ha ESign only-s certificates Portált töltöttél le akkor a <code class="hljs"># ESign Only Certs</code> mappába találod</li>
            <li>Az ilyeneket úgy telepíted, hogy rányomsz a <code class="hljs">certificatname.esigncert</code> fájlra utána <code class="hljs">Import Certificate Managment</code></li>
            <li>Ha nem ESign only portált telepítettél akkor a mappába egy .p12 és .mobileprovision fájlt fogsz látni</li>
            <li>Először kattints a .mobileprovision fájlra és Import (Itt egy kínai szöveg fog megjelenni xd)</li>
            <li>Azután kattints a .p12 fájlra és ha kér jelszót írd be, hogy <code class="hljs">WSF</code></li>
        </ul>
        
        <h3 id="6-firka-telepítése-1"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#6-firka-telepítése-1">6. Firka telepítése</a></h3>
        <ul>
            <li>Menj az <code class="hljs">AppStore</code> fülre alul aztán bal felül kattints az <code class="hljs">App Source</code> gombra azután jobb felül kattints az +-ra és másold be hogy <code class="hljs">https://raw.githubusercontent.com/spitkov/firkarepo/refs/heads/main/esign.json</code></li>
            <li>Menj vissza és az AppStore fülben látni fogod a Firkát</li>
            <li>Kattints hogy <code class="hljs">Download</code></li>
            <li>A <code class="hljs">Download</code> fülben láthatod a letöltést, ha letöltött kattints rá és nyomd meg a <code class="hljs">Import App Library</code> gombot</li>
            <li>Azután menj a <code class="hljs">Apps</code> fülre és válaszd ki a Firkát kattints a <code class="hljs">Signature</code>-re aztán megint <code class="hljs">Signature</code> (fontos ne lépj ki az esign-bol amíg nem jelentek meg az <code class="hljs">Install</code> és az <code class="hljs">Exit</code> gombok)</li>
            <li>Ha végzett kattints az <code class="hljs">Install</code> gombra és fel fog jönni egy kis menü hogy esign.yyyue.xyz telepíteni akarja a Firkát akkor kattints arra hogy Telepítés</li>
            <li>És kész is 🎉</li>
        </ul>
        
        <h3 id="esign-faq"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#esign-faq">ESign FAQ:</a></h3>
        <ul>
            <li>Q1: Törölhetem az ESignt meg a profilt amiután meg lett a Firka?</li>
            <li>A1: Igen, ha elakarod b*szni az egészet. Nem, ha meg szeretnéd tartani.</li>
            <li>Több kérdés? Írj a Firka Discord szerverére.</li>
        </ul>
        
        <h2 id="3-sidestore-metódus-a-sidestore-az-altstore-nak-egy-jobb-verziója"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#3-sidestore-metódus-a-sidestore-az-altstore-nak-egy-jobb-verziója">3. SideStore metódus (A SideStore az AltStore-nak egy jobb verziója)</a></h2>
        
        <h3 id="1-előfeltételek"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#1-előfeltételek">1. Előfeltételek</a></h3>
        <ul>
            <li>Mac számítógép macOS 10.15 vagy újabb verzióval</li>
            <li>Apple fiók</li>
            <li>Internet kapcsolat</li>
            <li>iPhone iOS 14 vagy újabb verzióval</li>
        </ul>
        
        <h3 id="2-szükséges-fájlok-letöltése-maceden"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#2-szükséges-fájlok-letöltése-maceden">2. Szükséges fájlok letöltése (Maceden)</a></h3>
        <ul>
            <li>AltServer: https://cdn.altstore.io/file/altstore/altserver.zip</li>
            <li>SideStore IPA: https://github.com/sidestore/sidestore/releases/latest/download/sidestore.ipa</li>
            <li>JitterBugPair: https://github.com/osy/Jitterbug/releases/download/v1.3.1/jitterbugpair-macos.zip</li>
        </ul>
        
        <h3 id="3-altserver-telepítése-és-beállítása-maceden"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#3-altserver-telepítése-és-beállítása-maceden">3. AltServer telepítése és beállítása (Maceden)</a></h3>
        <ul>
            <li>Csomagold ki az AltServer-t a ZIP fájlból</li>
            <li>Helyezd át az Alkalmazások mappába</li>
            <li>Indítsd el az AltServer-t</li>
        </ul>
        
        <h3 id="4-sidestore-telepítése-maceden-és-az-iphoneodon"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#4-sidestore-telepítése-maceden-és-az-iphoneodon">4. SideStore telepítése (Maceden és az iPhoneodon)</a></h3>
        <ul>
            <li>Csatlakoztasd az iPhone-od a Mac-hez</li>
            <li>Engedélyezd a "Megbízható számítógép" opciót az iPhone-on (ha kéri)</li>
            <li>A Mac menüsorában tartsd nyomva az Option⌥/Alt⌥ gombot</li>
            <li>Kattints az AltStore ikonra (rombusz alakú)</li>
            <li>Válaszd a "Sideload .ipa" opciót</li>
            <li>Válaszd ki az eszközöd nevét</li>
            <li>Válaszd ki a letöltött SideStore IPA fájlt</li>
            <li>Add meg az Apple fiókod adatait</li>
            <li>Várd meg a telepítést</li>
            <li>Az iPhone-on menj a Beállítások > Általános > VPN & Eszközfelügyelet menübe</li>
            <li>Keresd meg az Apple email címed és nyomd meg a "Megbízható" gombot</li>
        </ul>
        
        <h3 id="5-fejlesztői-mód-engedélyezése-ios-16-vagy-újabb-esetén-iphoneodon"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#5-fejlesztői-mód-engedélyezése-ios-16-vagy-újabb-esetén-iphoneodon">5. Fejlesztői mód engedélyezése (iOS 16 vagy újabb esetén) (iPhoneodon)</a></h3>
        <ul>
            <li>Menj a Beállítások > Adatvédelem és Biztonság menübe</li>
            <li>Görgess az aljára</li>
            <li>Kapcsold be a Fejlesztői módot</li>
            <li>Várd meg az iPhone újraindulását</li>
            <li>Húzd fel a képernyőt az indítás közben amikor kéri</li>
        </ul>
        
        <h3 id="6-párosítás-beállítása-maceden"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#6-párosítás-beállítása-maceden">6. Párosítás beállítása (Maceden)</a></h3>
        <ul>
            <li>Csomagold ki a JitterBugPair ZIP fájlt</li>
            <li>Állíts be jelkódot az iPhone-on (ha még nincs)</li>
            <li>Csatlakoztasd az iPhone-od</li>
            <li>Oldd fel az eszközt és hagyd a kezdőképernyőn</li>
            <li>Futtasd a JitterBugPair parancs fájlt</li>
            <li>A generált párosító fájl neve: "(UDID).mobiledevicepairing"</li>
            <li>Tömörítsd be a párosító fájlt</li>
            <li>Küldd át az iPhone-ra (AirDrop vagy email)</li>
            <li>Az iPhone-on nyisd meg a Fájlok alkalmazást</li>
            <li>Csomagold ki a ZIP fájlt.</li>
        </ul>
        
        <h3 id="7-wireguard-vpn-beállítása-iphoneodon"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#7-wireguard-vpn-beállítása-iphoneodon">7. WireGuard VPN beállítása (iPhoneodon)</a></h3>
        <ul>
            <li>Töltsd le a WireGuard VPN alkalmazást az App Store-ból: https://apps.apple.com/us/app/wireguard/id1441195209 <a href="https://apps.apple.com/us/app/wireguard/id1441195209">WireGuard App Store link</a></li>
            <li>Telepítsd az alábbi Configuration Fájlt: https://github.com/sidestore/sidestore/releases/download/0.1.1/sidestore.conf Amint ez megvan, nyisd meg a Fájlok alkalmazást, és keresd meg hogy "SideStore.conf". Nyomj rá hosszan és "oszd meg". A Megosztó ablakba ha kell, görgess a "Több/More" gombra, és nyisd meg a WireGuard-al.</li>
            <li>Nyomj az Engedélyezésre mikor azt mondja hogy: "A "WireGuard" VPN konfigurációt szeretne hozzáadni". Megynyitja a Beállításokat. Mikor kéri, írd be a jelkódodat. Ez vissza fog dobni a WireGuardba. Kapcsold be a SideStore-t. (Ez a "VPN" quote-unquote nem egy VPN, csak letiltja az Applenek az oscp-jét. Az OSCP az ami ellenőrzi hogy mit sideloadingolsz. Magyarul, ez bisztonsásgos)</li>
        </ul>
        
        <h3 id="8-sidestore-app-beállítása-iphoneodon"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#8-sidestore-app-beállítása-iphoneodon">8. SideStore app beállítása (iPhoneodon)</a></h3>
        <ul>
            <li>Indítsd el a SideStore alkalmazást</li>
            <li>Nyomj az OK gombra</li>
            <li>Válaszd ki a párosító fájlt</li>
            <li>Jelentkezz be az Apple Fiókodmal</li>
        </ul>
        
        <h3 id="megjegyzések"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#megjegyzések">Megjegyzések:</a></h3>
        <ul>
            <li>Ha frissíted az eszközöd, újra kell csinálnod a párosítást</li>
            <li>Új párosító fájl hozzáadásához:
                <ul>
                    <li>Menj a SideStore beállításaiba</li>
                    <li>Nyomd meg a "Reset Pairing File" gombot</li>
                    <li>Add hozzá az új verziót</li>
                    <li>Sajnáljuk a komplikált fojamatot. Sajnálatos módon a Testflight vagy az App Storera való kitétel jelenleg nem nagyon egy opció, mivel az Applenek 100 eurós fejelsztői membership vásárlása kötelező.</li>
                </ul>
            </li>
        </ul>
        
        <h2 id="kreditek"><a class="header" href="https://docs.qwit.org/Firka/ipa_telepites.html#kreditek">Kreditek</a></h2>
        <ul>
            <li><strong>A Firka csapat</strong>: Az app zöld verziójának fejlesztői
                <ul>
                    <li>Discord: <a href="https://discord.gg/6awUPSMFKe">https://discord.gg/6awUPSMFKe</a></li>
                    <li>GitHub: <a href="https://github.com/QwIT-Development/app-legacy">https://github.com/QwIT-Development/app-legacy</a></li>
                </ul>
            </li>
            <li><strong>WSF</strong>: A Permanent Signing lehetővé tétele
                <ul>
                    <li>X (korábban Twitter): <a href="https://x.com/wsf_team">https://x.com/wsf_team</a></li>
                </ul>
            </li>
            <li><strong>Spitkov</strong>: A Feather útmutató írója, és a repok készítője/maintainelője.
                <ul>
                    <li>Weboldal: <a href="https://spitkov.hu/">https://spitkov.hu</a></li>
                </ul>
            </li>
            <li><strong>TheAppleUser</strong>: Az Esign és SideStore útmutató írója.
                <ul>
                    <li>X (korábban Twitter): <a href="https://x.com/TheAppleUser11">https://x.com/TheAppleUser11</a></li>
                </ul>
            </li>
        </ul>
    `;

    const revokeContent = `
        <h1><a class="header" href="https://docs.qwit.org/Firka/revoke_fix.html#revoke-fixing-guide-a-firkához">Revoke-Fixing-Guide a Firkához!!!</a></h1>
        
        <h2 id="tartalomjegyzék"><a class="header" href="https://docs.qwit.org/Firka/revoke_fix.html#tartalomjegyzék">Tartalomjegyzék</a></h2>
        <ul>
            <li><a href="https://docs.qwit.org/Firka/revoke_fix.html#1-módszer">1. módszer: Alacsony sikerességi arány, nem szükséges számítógép</a></li>
            <li><a href="https://docs.qwit.org/Firka/revoke_fix.html#2-módszer">2. módszer: Közepes-magas sikerességi arány, számítógép szükséges</a></li>
            <li><a href="https://docs.qwit.org/Firka/revoke_fix.html#3-módszer">3. módszer: Magas sikerességi arány, számítógép szükséges</a></li>
            <li><a href="https://docs.qwit.org/Firka/revoke_fix.html#4-módszer">4. módszer: Működni fog, számítógép szükséges, de törli az adataidat</a></li>
        </ul>
        
        <h1 id="revoke-javítása"><a class="header" href="https://docs.qwit.org/Firka/revoke_fix.html#revoke-javítása">Revoke javítása</a></h1>
        
        <h2 id="1-módszer-alacsony-sikerességi-arány-nem-szükséges-számítógép"><a class="header" href="https://docs.qwit.org/Firka/revoke_fix.html#1-módszer-alacsony-sikerességi-arány-nem-szükséges-számítógép"></a><a name="1-módszer"></a>1. módszer: Alacsony sikerességi arány, nem szükséges számítógép.</h2>
        <ol>
            <li>Távolítsd el a konfigurációs profilt, és törölj minden sideloadolt alkalmazást.</li>
            <li>Készíts biztonsági mentést az iCloud segítségével.</li>
            <li>Állítsd vissza a készüléket: Beállítások > Általános > iPhone átvitele vagy visszaállítása > Összes tartalom és beállítás törlése.</li>
            <li>Állítsd vissza az iCloud biztonsági mentésedet.</li>
            <li>Kövesd újra az útmutatót.</li>
        </ol>
        
        <h2 id="2-módszer-közepes-magas-sikerességi-arány-számítógép-szükséges"><a class="header" href="https://docs.qwit.org/Firka/revoke_fix.html#2-módszer-közepes-magas-sikerességi-arány-számítógép-szükséges"></a><a name="2-módszer"></a>2. módszer: Közepes-magas sikerességi arány, számítógép szükséges.</h2>
        <ol>
            <li>Távolítsd el a konfigurációs profilt, és törölj minden sideloadolt alkalmazást.</li>
            <li>Készíts biztonsági mentést, majd állítsd a készüléket helyreállítási módba, és Finderben vagy iTunesban kattints a frissítésre.</li>
            <li>Kövesd újra az útmutatót.</li>
        </ol>
        
        <h2 id="3-módszer-magas-sikerességi-arány-számítógép-szükséges"><a class="header" href="https://docs.qwit.org/Firka/revoke_fix.html#3-módszer-magas-sikerességi-arány-számítógép-szükséges"></a><a name="3-módszer"></a>3. módszer: Magas sikerességi arány, számítógép szükséges.</h2>
        <ol>
            <li>Távolítsd el a konfigurációs profilt, és törölj minden sideloadolt alkalmazást.</li>
            <li>Készíts biztonsági mentést iTunes vagy Finder segítségével.</li>
            <li>Állítsd vissza a készüléket DFU módban.</li>
            <li>Csatlakoztasd a telefont a számítógéphez, majd Finderben vagy iTunesban válaszd a biztonsági mentés visszaállítását.</li>
            <li>Kövesd újra az útmutatót.</li>
        </ol>
        
        <h2 id="4-módszer-működni-fog-számítógép-szükséges-de-törli-az-adataidat"><a class="header" href="https://docs.qwit.org/Firka/revoke_fix.html#4-módszer-működni-fog-számítógép-szükséges-de-törli-az-adataidat"></a><a name="4-módszer"></a>4. módszer: Működni fog, számítógép szükséges, de törli az adataidat.</h2>
        <ol>
            <li>Állítsd vissza a készüléket DFU módban az iTunes vagy Finder segítségével.</li>
            <li>Kövesd újra az útmutatót.</li>
        </ol>
    `;

    // Function to set the active tab
    function selectTab(tab: 'home' | 'ipa' | 'revoke') {
        currentTab = tab;
    }
</script>

<svelte:head>
    <title>QwIT Docs</title>
    <meta content="QwIT Docs" property="og:title" />
    <meta content="A Firka dokumentációja." property="og:description" />
    <meta content="https://firka.qwit.org/docs" property="og:url" />
    <meta content="#32a852" data-react-helmet="true" name="theme-color" />
    <link rel="stylesheet" href="/Docs_files/variables.css">
    <link rel="stylesheet" href="/Docs_files/general.css">
    <link rel="stylesheet" href="/Docs_files/chrome.css">
    <link rel="stylesheet" href="/Docs_files/print.css" media="print">
    <link rel="stylesheet" href="/Docs_files/font-awesome.css">
    <link rel="stylesheet" href="/Docs_files/fonts.css">
    <link rel="stylesheet" href="/Docs_files/highlight.css">
    <link rel="stylesheet" href="/Docs_files/tomorrow-night.css">
    <link rel="stylesheet" href="/Docs_files/ayu-highlight.css">
</svelte:head>

<div class="docs-container">
    <aside class="docs-sidebar">
        <div class="tab-buttons">
            <button 
                on:click={() => selectTab('home')} 
                class:active={currentTab === 'home'}
            >
                Home
            </button>
            <button 
                on:click={() => selectTab('ipa')} 
                class:active={currentTab === 'ipa'}
            >
                Ipa Telepítés
            </button>
            <button 
                on:click={() => selectTab('revoke')} 
                class:active={currentTab === 'revoke'}
            >
                Revoke Fix
            </button>
        </div>
    </aside>
    
    <main class="docs-content">
        {#if currentTab === 'home'}
            {@html homeContent}
        {:else if currentTab === 'ipa'}
            {@html ipaContent}
        {:else if currentTab === 'revoke'}
            {@html revokeContent}
        {/if}
    </main>
</div>

<style>
    .docs-container {
        display: flex;
        width: 100%;
        max-width: 1200px;
        margin: 0 auto;
        padding: 20px;
        background-color: var(--background);
        color: var(--text_primary);
    }

    .docs-sidebar {
        width: 250px;
        flex-shrink: 0;
        padding-right: 20px;
        border-right: 1px solid var(--text_teritary);
    }

    .tab-buttons {
        display: flex;
        flex-direction: column;
    }

    .tab-buttons button {
        background-color: transparent;
        border: none;
        padding: 10px 15px;
        text-align: left;
        cursor: pointer;
        font-family: 'Montserrat', sans-serif;
        font-weight: 600;
        font-size: 16px;
        color: var(--text_secondary);
        transition: color 0.2s ease-in-out;
    }

    .tab-buttons button:hover {
        color: var(--text_primary);
    }

    .tab-buttons button.active {
        color: var(--accent_accent);
    }

    .docs-content {
        flex-grow: 1;
        padding-left: 20px;
    }

    /* Basic styling for content to match main site's fonts */
    :global(.docs-content h1),
    :global(.docs-content h2),
    :global(.docs-content h3),
    :global(.docs-content h4),
    :global(.docs-content h5),
    :global(.docs-content h6) {
        font-family: 'Montserrat', sans-serif;
        font-weight: 700;
        color: var(--text_primary);
        margin-top: 1.5em;
        margin-bottom: 0.5em;
    }

    :global(.docs-content p) {
        font-family: 'Figtree', sans-serif;
        font-weight: 500;
        color: var(--text_secondary);
        line-height: 1.6;
        margin-bottom: 1em;
    }

    :global(.docs-content a) {
        color: var(--accent_accent);
        text-decoration: none;
    }

    :global(.docs-content a:hover) {
        text-decoration: underline;
    }

    :global(.docs-content ul),
    :global(.docs-content ol) {
        padding-left: 1.5em;
        margin-bottom: 1em;
    }

    :global(.docs-content li) {
        font-family: 'Figtree', sans-serif;
        font-weight: 500;
        color: var(--text_secondary);
        line-height: 1.6;
        margin-bottom: 0.5em;
    }

    :global(.docs-content code) {
        background-color: rgba(128, 128, 128, 0.1);
        padding: 2px 4px;
        border-radius: 3px;
        font-family: 'Courier New', monospace;
        font-size: 0.9em;
    }

    :global(.docs-content strong) {
        font-weight: 700;
        color: var(--text_primary);
    }
</style>