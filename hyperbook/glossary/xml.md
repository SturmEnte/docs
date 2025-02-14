---
name: Einführung in XML
index: 4
---

## Einführung in XML

Die Kommunikation zwischen [Spielleiter](glossary/server) und [Computerspieler](glossary/player) 
wird mittels XML-Nachrichten realisiert.
XML ist eine Auszeichnungssprache, d.h eine Sprache,
die nicht nur die Daten selbst, sondern auch Informationen über die Interpretation oder Bearbeitung liefert.
Der Vorteil dieser Sprache liegt darin,
dass sie sowohl vom Computer als auch vom Menschen gut gelesen werden kann.
Dieser Abschnitt gibt einen Einstieg in die Struktur von XML.

### Tags

Die Grundelemente von XML sind _Tags_. Ein Tag liefert Informationen über die Art der Daten, die verarbeitet werden sollen. In XML wird ein Tag gebildet, indem man den Tagnamen zwischen spitze Klammern setzt. Dabei kennt XML drei verschiedene Tag-Arten:

-   Öffnendes Tag: `<Tag>`
    
-   Schließendes Tag: `</Tag>`
    
-   Leeres Tag: `<Tag />`
    

Der Schrägstrich bedeuted, dass das Tag geschlossen wird. Durch den Schrägstrich am Ende wird das soeben geöffnete Tag direkt wieder geschlossen.

Zwischen den öffnenden und schliessenden Tag steht die Information, die mitgeteilt werden soll.

**Hinweis:** XML unterscheidet strikt zwischen Groß- und Kleinschreibung.

#### Bildungsregeln

Die Tags dürfen nicht beliebig in Dokumenten verwendet werden. Es gelten hier die folgenden Regeln:

-   Zu jedem öffnenden Tag muss ein schließendes Tag existieren.
    
-   Man kann Tags ineinander schachteln. Die einzelnen Tags dürfen sich jedoch nicht überkreuzen.
    
-   Es darf nur ein Root-Tag geben, d.h. es gibt auf oberster Ebene genau ein Tag, in dem alle anderen enthalten sind.
    

#### Beispiel für korrekte XML-Syntax

```xml
<addiere>
    <komplexe_zahl>
        <realteil>3.5</realteil>
        <imaginaerteil>4.2</imaginaerteil>
    </komplexe_zahl>
    <komplexe_zahl>
        <realteil>1</realteil>
        <imaginaerteil>6.9</imaginaerteil>
    </komplexe_zahl>
</addiere>
```

#### Beispiele für fehlerhafte XML-Syntax

-   Fehlerhaft, da es mehrere Elemente auf oberster Ebene gibt:
    

```xml
<ueberschrift>
    Beispieldokument
</ueberschrift>
<text>
    Dies ist ein <unterstrichen>Beispieltext</unterstrichen>
    <absatz />
    Noch mehr Text
</text>
```

-   Fehlerhaft, da Tags sich kreuzen:
    

```xml
<dokument>
    <ueberschrift>
        Beispieldokument
    </ueberschrift>
    <text>
        <kursiv>Dies <unterstrichen>ist </kursiv>ein Beispieltext</unterstrichen>
        <absatz />
        Noch mehr Text
    </text>
</dokument>
```

### Attribute

Man kann im Tag auch Attribute einfügen, in denen Informationen übertragen werden:

```xml
<Tag attribut="wert" />
```

Auf diese Weise lässt sich das Beispiel mit den komplexen Zahlen etwas übersichtlicher gestalten:

```xml
<addiere>
    <komplexe_zahl realteil="3.5" imaginaerteil="4.2" />
    <komplexe_zahl realteil="1" imaginaerteil="6.9" />
</addiere>
```

### Der Header

Wichtig ist auch die erste Zeile in einem XML-Dokument. Aus ihr kann das Computerprogramm erfahren, wie es mit den Daten umzugehen hat (z.B. welcher Zeichensatz benutzt wird). Dieser Header sieht einem Tag sehr ähnlich:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
```

Man nennt so ein Tag, auch _Verarbeitungsinformation_.

Theoretisch darf es in einem XML-Dokument mehrere Verarbeitungsinformationen geben, für die Software-Challenge muss man aber nur den Header kennen.

### Kommentare

Man kann in sein XML-Dokument auch Kommentare einfügen, die beim Einlesen dann ignoriert werden:

```xml
<!-- Ich bin ein XML-Kommentar -->
```

Es darf beliebig viele solcher Kommentare geben und sie dürfen nur zwischen Tags stehen.

### Weiterführende Informationen

-   [Wikipedia-Artikel über XML](https://de.wikipedia.org/wiki/Extensible_Markup_Language)