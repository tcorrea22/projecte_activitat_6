# Guia de seguretat: gestors de contrasenyes i verificació en dos passos (2FA)

**Toni Correa** · Seguretat Informàtica · SMX 2n A

---

## 1. Per què les contrasenyes febles són un perill

Sovint la contrasenya és l'única cosa que hi ha entre un atacant i les dades de l'empresa. Els atacs més habituals són:

| Atac | En poques paraules |
|---|---|
| **Diccionari** | Es proven contrasenyes típiques (`Password123`, noms, anys...). Les previsibles cauen de seguida. |
| **Força bruta** | Es proven totes les combinacions possibles. Com més curta és la contrasenya, abans es troba. |
| **Credential stuffing** | Es fan servir contrasenyes filtrades d'una web en altres serveis. Només funciona si la persona **repeteix** la contrasenya. |
| **Phishing** | Una web o un correu fals fa que la víctima escrigui ella mateixa la contrasenya. |

---

## 2. El problema de reutilitzar contrasenyes

- Si fas servir la mateixa contrasenya a tot arreu, la seguretat de tots els teus comptes depèn del servei **menys protegit**.
- Si es filtra una web poc important, l'atacant pot provar aquesta contrasenya al correu, a la VPN, al repositori de codi...
- **N'hi ha prou amb un sol compte feble** perquè un atacant entri a l'empresa.

---

## 3. Què pot perdre una empresa

- **Projectes exposats:** codi, documents i dades de clients.
- **Accés a sistemes interns** i a eines dels clients.
- **Robatori d'informació** abans que ningú se n'adoni.
- **Pèrdua de reputació:** els clients deixen de confiar-hi.
- **Costos:** investigar l'incident, canviar credencials, avisar clients i possibles problemes legals.

---

## 4. Solució 1: el gestor de contrasenyes

Un gestor de contrasenyes és com una **caixa forta digital xifrada** on es guarden totes les contrasenyes. Només cal recordar com s'obre la caixa.

**Què aporta:**

- **Crea contrasenyes llargues, aleatòries i úniques**, sense haver de pensar-les.
- **Les guarda**: ja no cal recordar-ne desenes.
- **Les sincronitza** entre l'ordinador, el mòbil i el navegador.
- **Les omple automàticament**, i normalment només a la web correcta, cosa que ajuda a detectar webs falses.
- **S'acaba la reutilització**, perquè crear una contrasenya nova no costa res.

---

## 5. Comparativa de gestors

| | **Proton Pass** | **Bitwarden** | **KeePassXC** |
|---|---|---|---|
| Tipus | Al núvol | Al núvol | Local (fitxer `.kdbx`) |
| Xifrat | D'extrem a extrem (AES-256-GCM) | Coneixement zero (AES-256) | Base de dades sempre xifrada (Argon2) |
| Sincronització | Sí | Sí | No integrada |
| Gratuït | Sí, amb pla gratuït | Sí, amb pla gratuït | Sí, programari lliure |
| Per a empreses | Proton Pass for Business | Plans Teams/Enterprise | Sense administració central |
| Punt feble | Depèn del compte Proton | Depèn d'un servei extern | Si perds el fitxer o la contrasenya, ho perds tot |

**Idea clau:** que les dades estiguin al núvol **no vol dir que siguin insegures**, perquè el servidor només guarda dades ja xifrades. Un gestor local tampoc és invulnerable: només canvia qui s'encarrega de protegir les dades.

---

## 6. L'eina recomanada: Proton Pass

**Per què:**

- És fàcil d'usar, i això fa que el personal la faci servir de veritat.
- Té app de Windows i extensions per a Chrome, Firefox, Edge, Safari i Brave.
- Té generador de contrasenyes i autocompletat.
- Permet fer una còpia de seguretat xifrada (ZIP amb PGP).
- Té codi obert, xifrat d'extrem a extrem i auditories públiques.
- Té pla gratuït i versió per a empreses.

**Abans d'implantar-lo a tota l'empresa** cal revisar l'administració central d'usuaris, la recuperació de comptes, la compartició entre equips, la normativa de protecció de dades i el cost del pla. **Bitwarden** és una alternativa igual de vàlida.

---

## 7. Com es configura Proton Pass

1. **Instal·lar** l'app des de la web oficial de Proton.
2. **Iniciar sessió** amb una contrasenya llarga i única, i **activar la MFA**.
3. **Afegir l'extensió** del navegador (comprovant que l'editor és Proton AG).
4. **Generar una contrasenya**: mode aleatori, 20 caràcters o més, amb majúscules, números i símbols.
5. **Guardar les credencials** de cada servei.
6. **Fer servir l'autocompletat**, mirant sempre que el domini sigui el correcte.
7. **Fer una còpia de seguretat xifrada** (ZIP amb PGP) i guardar-la en un lloc segur, **separada de la frase de pas**.

---

## 8. Solució 2: la verificació en dos passos (2FA)

**Què és:** per entrar no n'hi ha prou amb la contrasenya. També cal un **codi temporal** que genera una aplicació al mòbil.

**Per què és tan important:** encara que un atacant aconsegueixi la contrasenya (per phishing, per una filtració...), **sense el mòbil no pot entrar**.

**Com funciona Google Authenticator:**

- Genera codis de **6 xifres que canvien cada 30 segons**.
- El codi es calcula al mòbil, així que funciona fins i tot sense connexió.

---

## 9. Com s'activa el 2FA amb Google Authenticator

1. **Instal·lar** Google Authenticator al mòbil.
2. Entrar al compte de Google, a la pestanya **Seguretat**.
3. Anar a **Verificació en dos passos** i triar **Authenticator**. Apareix un **codi QR**.
4. **Escanejar el QR** amb l'aplicació del mòbil. Així el compte queda vinculat.
5. **Escriure el codi** del mòbil a l'ordinador per validar-ho.

✅ A partir d'ara, per entrar cal la **contrasenya + el codi**.

> **Consell:** guardeu els **codis de recuperació** que ofereix Google en un lloc segur. Si perdeu el mòbil, són la manera de tornar a entrar al compte.

---

## 10. Gestor + 2FA = molt més segur

| Només contrasenya | Gestor de contrasenyes | Gestor + 2FA |
|---|---|---|
| Fàcil d'endevinar o de reutilitzar | Contrasenyes fortes i úniques | Contrasenyes fortes **i** un segon pas |
| Si es filtra, l'atacant entra | Una filtració no afecta els altres comptes | Encara que es filtri, sense el mòbil no s'entra |

---

## 11. Què NO soluciona cap d'aquestes eines

- Un ordinador amb **programari maliciós**.
- La **manca de formació** contra el phishing.
- Els sistemes **sense actualitzar**.

Per això cal combinar-les amb altres mesures.

---

## 12. Altres mesures recomanades

1. Activar la **MFA a tots els comptes** (correu, VPN, repositoris, gestor).
2. Fer servir **contrasenyes úniques** a cada servei.
3. **Canviar les credencials** si hi ha sospita que s'han filtrat.
4. **Revocar sessions i tokens** actius quan calgui.
5. **Formar el personal** contra el phishing.
6. **Mantenir-ho tot actualitzat.**
7. Aplicar el **mínim privilegi**: cadascú només té els accessos que necessita.
8. Tenir un **pla de resposta a incidents** escrit.
9. Tenir **còpies de seguretat** xifrades i comprovar que es poden restaurar.

---

## 13. Conclusió

- **Una sola contrasenya feble pot posar en perill tota una empresa.**
- El **gestor de contrasenyes** fa que totes les contrasenyes siguin fortes i úniques sense esforç.
- El **2FA** afegeix una segona barrera: encara que robin la contrasenya, no poden entrar.
- Junts redueixen molt el risc, però han d'anar acompanyats de formació, actualitzacions i un pla d'incidents.
