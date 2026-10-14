# Epistemic Logic Modeling in IDP3

Een kennisrepresentatie- en redeneerproject waarin **epistemische logica** (kennis van meerdere agenten) computationeel gemodelleerd en geëvalueerd wordt met behulp van het **IDP3** Knowledge Base System (KBS).

Het systeem modelleert Kripke-structuren, formule-syntaxbomen en inductieve semantiek voor modale logica, inclusief uitbreidingen voor **Common Knowledge** ($C_G$) en **Distributed Knowledge** ($D_G$).

---

## Over het Project

In epistemische logica wordt de kennis van agenten formeel gerepresenteerd via **Kripke-structuren** $(S, \pi, \mathcal{K}_1, \dots, \mathcal{K}_n)$, waarbij de relaties $\mathcal{K}_i$ equivalentierelaties vormen (reflexief, symmetrisch en transitief).

Dit project implementeert:
1. **Kripke-structuren als Equivalentierelaties:** Specificatie van reflexiviteit, symmetrie en transitiviteit over toegankelijkheidsrelaties `pos(agent, state, state)`.
2. **Model Expansion voor Wereldmodellen:** Automatisch genereren van geldige Kripke-modellen via SAT-gebaseerde model expansion (`modelexpand`).
3. **Syntaxboom Modellering:** Een inductieve specificatie die garandeert dat modale formules geldige, gerichte, acyclische syntaxbomen vormen met exact één root en zonder cycli of meervoudige ouders.
4. **Inductieve Semantiek (`satisfies`):** Formele evaluatie van modale formules in verschillende werelden:
   - Proposities en booleaanse operatoren ($\neg, \wedge$).
   - Individuele agentkennis ($K_a \varphi$): waar als $\varphi$ waar is in alle werelden die agent $a$ mogelijk acht.
   - **Distributed Knowledge ($D_G \varphi$):** Kennis die impliciet aanwezig is in de groep (doorsnede van mogelijke werelden van groepsleden).
   - **Common Knowledge ($C_G \varphi$):** Publieke kennis die iedereen weet, weet dat iedereen weet, enz. (gemodelleerd via transitieve afsluiting `CommonAccess`).
5. **Gevalstudies & Validatie:** Automatisch genereren en verifiëren van formules en structuren voor validiteit, satisfiability en unsatisfiability.

---

## Structuur van het Project

- `solution.idp`: De volledige specificatie bevattende:
  - `vocabulary shared`, `FormulaVoc`, `KripkeStructureVoc`, `ModalLogicVoc`: Ontologieën en types.
  - `theory ValidKripkeStructureTheory`: Axioma's voor Kripke-structuren.
  - `theory SyntaxOfModalFormulas`: Regels voor geldige formulebomen.
  - `theory SemanticsOfModalFormulas`: Inductieve semantiek voor $K$, $C_G$ en $D_G$.
  - `procedure main()`: Lua-gebaseerde sturing voor het uitvoeren van model expansion en testen.

---

## Uitvoeren

Dit project vereist het **IDP3 Knowledge Base System**.

Voer de specificatie uit via de terminal:

```bash
idp solution.idp
