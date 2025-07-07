#  Project Energieverbruik en Cashflow Analyse

## 1. Project Setup — Clone de Repository

Om met dit project te starten:

1. Open je terminal of command prompt.
2. Voer dit commando uit om de repository te klonen:
   ```bash
   git clone (https://github.com/RubaMansour/PraeterBV_opdracht.git)
   ```
3. Ga naar de map van de gekloonde repository:
   ```bash
   cd PraeterBV_opdracht
   ```
4. Wissel naar de branch met het definitieve werk:
   ```bash
   git checkout final-branch
   ```
5. Zorg dat Python en de benodigde libraries (`pandas`, `matplotlib`, `numpy_financial`) geïnstalleerd zijn.

---

## 2. Opdracht 1 — Analyse Energieverbruik

### Data Input

- Excel-bestand: `PraeterBV_Case.xlsx`
- Bladen gebruikt:  
  - `Opdracht_1_voorbeeld` (klantgegevens)  
  - `Opdracht_1_CBS` (gemiddelde energiewaarden)

### Stappen en Berekeningen

1. **Basisgegevens uitlezen:**  
   Naam, adres, postcode, plaats, gas- en elektriciteitsverbruik, gebouwkenmerken (verdiepingen, bouwjaar, oppervlakte, hoogte).

2. **Berekenen van volume:**  
   `volume = oppervlakte × hoogte` (in m³).

3. **Verbruik per m² en per m³:**  
   - Gas per m² = gasverbruik ÷ oppervlakte  
   - Gas per m³ = gasverbruik ÷ volume  
   - Elektriciteit per m² = elektriciteitsverbruik ÷ oppervlakte  
   - Elektriciteit per m³ = elektriciteitsverbruik ÷ volume

4. **Omrekenen naar totale energie in kWh:**  
   - Gas wordt vermenigvuldigd met factor 10 om om te rekenen naar kWh.  
   - Totaal per m² = (gas per m² × 10) + elektriciteit per m²  
   - Totaal per m³ = (gas per m³ × 10) + elektriciteit per m³  
   - Totaal verbruik = (gasverbruik × 10) + elektriciteitsverbruik

5. **Vergelijking met CBS gemiddelden:**  
   Gemiddelde waarden voor gas en elektriciteit per m² en m³ worden uitgelezen uit CBS-data en vergeleken met huidig verbruik.

6. **Visualisatie (Plot):**  
   Een staafdiagram wordt gemaakt met `matplotlib` waarin het huidige energieverbruik wordt vergeleken met het gemiddelde verbruik:  
   - De x-as toont twee categorieën: `per_m2` en `per_m3`.  
   - Voor elke categorie worden twee balken weergegeven: één voor huidig verbruik (blauw) en één voor gemiddeld verbruik (bruin).  
   - De grafiek heeft een titel en een legenda.

---

## 3. Opdracht 2 — Cashflow Berekening

### Data Input

- Excel-bladen:  
  - `Opdracht_2_input_output`  
  - `Opdracht_2_berekening en output`

### Stappen en Berekeningen

1. **Lees investerings- en subsidiegegevens in:**  
   Investering, subsidies (eenmalig en jaarlijks), restwaarde, besparing, belastingpercentage, kosten (eenmalig, exploitatie, herinvestering), looptijd, inflatie, herinvesteringsjaar, afschrijving, aflossing.

2. **Bereken eigen vermogen:**  
   `Eigen vermogen = 20% van totale investering + eenmalige kosten`

3. **Rente over vreemd vermogen:**  
   Jaarlijkse rente wordt berekend als 4% van een jaarlijks afnemend vreemd vermogen.

4. **Bereken jaarlijkse cashflows:**  
   Voor elk jaar in de looptijd:  
   - Inkomsten = (besparing + subsidie jaarlijks) × (1 + inflatie)^(jaar - 1)  
   - Kosten = exploitatiekosten × (1 + inflatie)^(jaar - 1), plus eventuele herinvestering in het aangegeven jaar  
   - EBITDA = inkomsten - kosten  
   - EBIT = EBITDA - afschrijving  
   - Rente = rente op vreemd vermogen  
   - EBT (winst vóór belasting) = EBIT - rente  
   - Belasting = EBT × belastingpercentage (of 0 als EBT ≤ 0)  
   - Winst na belasting (PAT) = EBT - belasting  
   - Cashflow IRR = PAT + afschrijving + rente  
   - Cashflow REV = (PAT + afschrijving) - aflossing

5. **Financiële indicatoren:**  
   - IRR: interne rentevoet van cashflow IRR  
   - REV: interne rentevoet van cashflow REV  
   - Netto winst: som van winst na belasting min eigen vermogen

6. **Bereken Terugverdientijd (TVT):**  
   Bepalen wanneer cumulatieve cashflow REV groter is dan eigen vermogen, inclusief fractioneel jaar.

7. **Output:**  
   - Printen van cashflows, IRR, REV, winst en TVT.  
   - Resultaten worden opgeslagen in een Excel-bestand (`output_cashflows.xlsx`).

