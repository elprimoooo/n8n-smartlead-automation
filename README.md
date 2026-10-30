# n8n-smartlead-automation
Komplexní automatizační workflow vytvořené v n8n. Cílem je automatizovat zpracování realitních poptávek (leadů) – od přijetí e-mailu přes AI extrakci dat a geografické zpracování až po přiřazení vhodného makléře a odeslání notifikací.

SmartLead Automation (n8n + AI)


<img width="944" height="174" alt="Snímek obrazovky 2026-10-30 v 22 36 23" src="https://github.com/user-attachments/assets/07ae6f66-3583-4605-ba85-b0e4cb6304ab" />

**Architektura a flow
Email Trigger (IMAP): Workflow reaguje na nově příchozí e-mail obsahující transkript komunikace s klientem.
AI Extrakce (OpenAI): Model GPT-4o-mini parsuje nestrukturovaný text a vrací klíčová data (adresa, dispozice, telefon) ve striktním JSON formátu.
Geocoding: Získaná adresa je přes Mapy.cz API převedena na GPS souřadnice pro další výpočty.
Scoring a routing (JavaScript): Vlastní JS kód načte databázi makléřů, spočítá vzdálenosti (Haversinova formule) a vybere optimálního makléře na základě dojezdové zóny a kompetenčního skóre.
Zápis a notifikace: Workflow zapíše zpracovaný lead do CRM (Google Sheets) a odesílá okamžité upozornění vybranému makléři přes Gmail a Telegram.

**Tech Stack
n8n
OpenAI API (GPT-4o-mini)
Mapy.cz API, Google Sheets API, Telegram Bot API, Gmail API
JavaScript (Custom routing logika)

**Spuštění
Pro lokální nasazení stačí v prostředí n8n importovat přiložený soubor .json. Pro plnou funkcionalitu je nutné dodat vlastní API klíče a credentials k jednotlivým službám.
