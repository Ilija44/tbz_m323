# Deklarative Problemlösungen in Scala

## Aufgabe 1 – Reiseplanung als Funktion

Hier verwalten wir eine Liste von Reisezielen und ermöglichen das Ändern von Zielen.

```scala
// Funktion zur Verwaltung der Reiseziele
def reisePlanen(destinationen: List[String]): List[String] = destinationen

// Funktion zur Änderung eines Reiseziels
def reiseAendern(destinationen: List[String], alteDestination: String, neueDestination: String): List[String] = {
  destinationen.map(dest => if (dest == alteDestination) neueDestination else dest)
}

// Testfälle
val route = List("Berlin", "Paris", "Rom")
val neueRoute = reiseAendern(route, "Paris", "Madrid")
println(neueRoute) // Erwartet: List("Berlin", "Madrid", "Rom")
```

## Aufgabe 1 – Autorennen-Zeitberechnung
### Diese Funktion berechnet die Gesamtzeit (ohne die erste Runde) und die Durchschnittszeit pro Auto.
```scala
// Funktion zur Berechnung der Gesamtzeit ohne die erste Runde
def rennzeitBerechnen(zeiten: List[Double]): Double = zeiten.tail.sum

// Funktion zur Berechnung der Durchschnittszeit
def durchschnittszeitBerechnen(zeiten: List[Double]): Double = {
  val relevanteZeiten = zeiten.tail
  if (relevanteZeiten.nonEmpty) relevanteZeiten.sum / relevanteZeiten.length else 0.0
}

// Testfälle
val rennzeiten = List(50.0, 48.5, 47.8, 49.2) // Erste Runde zählt nicht
println(rennzeitBerechnen(rennzeiten)) // Erwartet: 145.5
println(durchschnittszeitBerechnen(rennzeiten)) // Erwartet: 48.5
```

## Aufgabe 2 - Wörter mit Punkten bewerten
 Diese Funktion bewertet Wörter nach der Anzahl ihrer Buchstaben, wobei der Buchstabe a nicht gezählt wird. Danach werden die Wörter nach Punktzahl sortiert.
```scala
// Funktion zur Bewertung eines Wortes
def wortBewertung(wort: String): Int = wort.count(_ != 'a')

// Funktion zum Sortieren der Wörter nach Punkten
def wörterSortieren(wörter: List[String]): List[(String, Int)] = {
  wörter.map(w => (w, wortBewertung(w))).sortBy(-_._2)
}

// Testfälle
val wörter = List("scala", "programmieren", "funktional", "lernen")
println(wörterSortieren(wörter))
// Erwartete Ausgabe: List(("programmieren", 11), ("funktional", 9), ("lernen", 6), ("scala", 3))
```
## Fazit
### Diese Lösungen wurden in funktionaler und deklarativer Programmierung umgesetzt, indem sie sich auf das WAS anstelle des WIE konzentrieren. Sie vermeiden explizite Schleifen und Mutationen und setzen auf höhere Funktionen und Listenoperationen.
