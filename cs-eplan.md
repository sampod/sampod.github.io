# sampod.github.io
Sami Heino's eplan cheat sheet
http://gh.heino.cc

| Key Combination  | Command
| ---------------- | ---
| A                | Change handle in 3D mounting layout navigator
| V                | Move
| CTRL + B         | Move property text
| CTRL + SHIFT + R | Modify rotation angle of 3D macro

This is my own reduced version of official help document. This version includes only commands which I use on regular basis. Full list can be found at: 
[Eplan.help - Overview of Shortcut Keys](https://www.eplan.help/help/platform/2.7/en-US/help/EPLAN_Help.htm#htm/gededitgui_k_tastaturbefehle.htm#kanchor426).

## Ulkoisen STEP-tiedoston tuonti
- Avaa Macro-projekti (Type of project == Macro Project)
- Valikosta: Layout Space -> Import (3D graphic) ja valitse STEP-tiedosto, josta tuonti tehdään
- Ote näkyviin Layout space navigator jos ei ole jo
- Jos komponentti koostuu useasta logcal itemistä, niin valitse ensin kaikki, ja sitten valikosta: edit -> graphic -> unite
- Layout space navigatorista paina tuotuun malliin oikeaa hiiren nappia, ja valitse properties
- Lisää ja täytä Properties'it Macro: Name ja Macro: Variant (Macro name on Macron tiedoston sijainti)
- Sitten pyöritä kappaletta sen verran, että näet pinnan, joka asennetaan esim oveen tai asennuslevylle tms (valikosta view -> rotate viewing angle)
- lisää placement area (edit -> device logic -> placement area -> define) ja valitse 
- sitten vielä lisää handle (edit -> device logic -> define handle)
- macro on nyt valmis! \o/
- jos kaikki asetukset ovat oikein ja kivasti, niin macrot saa päivitettyä oikeisiin paikkoisin valitsemalla valikosta: Procject data -> MAcros -> Generate automatically...
