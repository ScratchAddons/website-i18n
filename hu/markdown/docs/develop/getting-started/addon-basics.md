---
title: Egy kiegészítő alapjai
---

## Mi is egy kiegészítő most komolyan?
Valójában egy kiegészítő (angol: addon) nem több, mint egy felhasználói szkript (angol: userscript), egy felhasználói stílus (userstyle), vagy a kettő kombinációja. Ha bármelyikük összeillő, akkor egy név alatt ugyanazon kiegészítő részévé tesszük. Például a "Scratch 3 Fejlesztői Eszközök" kiegészítő tartalmaz egy userszkriptet, ami a keresőmező hozzáadásáért felelős, és tartalmaz userstyle-t is, ami CSS-sel bővíti azt a mezőt.

## Mi az a userscript?
A userscript, vagy felhasználói szkript egy JavaScript darab, ami együtt fog lefutni  egy Scratch oldallal. Lefektethető, hogy hol fusson le az a userscript, mint például a projektek oldalán. A userszkriptek hasonlóak a böngészőbővítmények content scriptjeihez, és ha bármikor használt már userszkriptkezelőt, akkor biztosan észreveheti, hogy alapvetően ez a kettő ugyanaz.
A userscriptek nagyon hasznosak a Scratch weboldalak viselkedésének megváltoztatásához, mint például a navigációs sáv gombjaihoz új adása, vagy elvétele.

## Mi az a userstyle?
Egy userstyle hasonlít a userscriptekhez, hiszen itt is meg lehet határozni URL sablonokat hozzájuk. Habár a userstylok CSS-t adnak hozzá a weboldalakhoz Javascript helyett. Gyakran használják együtt a userszkriptekkel, hogy az általuk készített elemeket stíusokkal bővítsék, de eredeti Scratch elemek stílusait is módosítani tudják. Amikor ez a helyzet, akkor "témáknak" hívjuk őket.

## Conceptually, what should be an addon?
You might wonder if it's a better idea to create a new addon, or modify an existing one.  
If 2 addons share some of these, they should probably be merged. 
- Both need, or don't need, permissions that require user interaction (like notifications).
- They share lots of code.
- The user would expect that addon to offer both features.
- If being separated, they would interfere with each other.  

Remember addons are customizable by the user - adding new functionality does not affect old users of the addon, unless we intentionally make it do so.