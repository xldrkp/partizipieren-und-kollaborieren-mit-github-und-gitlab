---
title: "07 | Einstieg in Hugo"
date: 2022-05-21T12:50:13.000Z
draft: true
type: book
toc: true
weight: 700
summary: Hugo ist ein statischer Webseitengenerator, mit dem sich verschiedenste Projekte umsetzen lassen. Mit einem stark reduzierten Beispielprojekt fällt der Einstieg leicht.
---

Hugo ist ein statischer Webseitengenerator, mit dem sich verschiedenste Projekte umsetzen lassen. Mit einem stark reduzierten Beispielprojekt fällt der Einstieg leicht.

## Ziele

- Sie installieren [Hugo](https://gohugo.io/getting-started/installing/) auf Ihrem Rechner.
- Sie forken und klonen [das Beispielprojekt](https://github.com/participatoryplayground/hugo-map-example).[^1]
- Sie ergänzen im Team weitere Marker unter Nutzung verschiedener Funktionen von Git und GitHub.
- Sie passen das Beispielprojekt an verschiedenen Stellen an, um es für Ihre Zwecke nutzbar zu machen.

[^1]: Das Repository ist nur für die aktuelle Arbeitsgruppe zugänglich. Eine öffentliche Version findet sich unter https://github.com/xldrkp/hugo-map-example.

## Ein Beispielprojekt in Hugo

[Hugo](https://gohugo.io/) ist ein Programm zum Generieren von Webseiten. Er zählt zur Klasse der [*static site generators*](https://www.netlify.com/blog/2020/04/14/what-is-a-static-site-generator-and-3-ways-to-find-the-best-one/), also den statischen Webseitengeneratoren. Davon gibt es [eine Menge](https://jamstack.org/generators/), deren Grundprinzip immer dasselbe ist: Aus einfachen Textdateien, in den meisten Fällen Markdown-Dateien, generieren diese Programme statische HTML-Seiten. Diese Konstrukte sind sehr schnell, stellen keine großen Ansprüche an den Webserver und sind kaum angreifbar.

Statische Webseitengeneratoren werden in Python, Go, Ruby und JavaScript geschrieben. Ihr Gebrauch ist unterschiedlich komplex. Die größte Lernkurve liegt in der Erstellung von Themes, Layouts und Templates, weil dafür die Kenntnis weiterer Template-Sprachen notwendig ist.

Hugo ist für seine Geschwindigkeit und Flexibilität bekannt. Auch viele hundert Seiten werden binnen Sekunden zu komplexen statischen HTML-Konstrukten gewandelt, wie [dieser Bericht des bekannten Smashing Magazines](https://www.smashingmagazine.com/2019/05/switch-wordpress-hugo/) zeigt.

Aufbauend auf dem Theme [Etch](https://github.com/LukasJoswiak/etch) von Lukas Joswiak wird hier eine angepasste Variante für dieses Lernangebot bereitgestellt. Neben der Möglichkeit, mit dem Theme zu bloggen, enthält es eine beispielhafte Karte mit Markern. An diesem Feature soll gezeigt werden, wie mit Hugo strukturierte Daten verarbeitet werden können. 

{{< figure title="Screenshot der beispielhaften Karte" src="./screenshot-map.png" >}}

Sie finden das Repo [auf GitHub](https://github.com/participatoryplayground/hugo-map-example).

### Erläuterung der Dateistruktur

Der Dateibaum entspricht weitestgehend dem Standard, dem bei der Initialisierung eines Projekt mit Hugo gefolgt wird. Es wurden jedoch noch einige Ordner und Dateien ergänzt, mit denen Sie das Beispielprojekt in eine eigene Richtung entwickeln oder sogar schon als Grundlage für eigene Projekt nehmen können.

{{< figure title="Darstellung einer Auswahl von Dateien und Ordnern im Beispielprojekt" src="./screenshot-filetree-map.png" >}}

Die folgende Aufzählung bezieht sich auf die Nummern in der Abbildung des Dateibaums:

1. `custom.css`: Überschreiben des CSS', das vom Theme mitgeliefert wird.
2. `content/_index.md`: Inhalte der Homepage
3. `content/map/index.md`: Beispiel einer Unterseite. Im YAML-Frontmatter der Datei wird mit `type: map` auf die Templatedatei `layouts/map/single.html` verwiesen.
4. `content/posts/`: Sammlung von Markdown-Dateien für die Blogabteilung.
5. `data/places/`: Sammlung von YAML-Dateien mit Daten für die Marker der Karte, pro Marker eine Datei.
6. `layouts/map/single.html`: Für dieses Projekt entwickelte Templatedatei, die das Partial `layouts/partials/place.html` einbindet.
7. `layouts/partials/`: Sammlung von partiellen Templatedateien, die in Templates eingebunden werden können. Ihr Sinn und Zweck ist die Wiederverwendbarkeit in unterschiedlichen Kontexten.  
   `layouts/partials/place.html`: Genutzt, um für jede YAML-Datei in `data/places/` das Markup für einen Marker auf der Karte zu generieren.

### Einsatz von Leaflet.js

Für die Darstellung der Karte auf der Seite wird [Leaflet.js](https://leafletjs.com/) verwendet. Damit [die notwendige CSS- und JavaScript-Datei]() geladen wird, wurde die Datei `layouts/partials/head.html` aus dem ursprünglichen Theme kopiert und erweitert.

Die Karte wird in `layouts/map/single.html` initialisiert. Marker werden darin mithilfe einer Schleife und dem Partial `layouts/partials/place.html` als separate `<script>`-Fragemente generiert. Dabei wird auf die Dateien in `data/places/` zugegriffen. Jede dieser YAML-Dateien enthält die entsprechenden Informationen für einen Marker auf der Karte.

```yaml
meta:
  title: Altonaer Balkon
  lat: 53.54529
  lon: 9.93581
  popuptext: |
    Have a nice view from here.
```

Diese Informationen werden in die Platzhalter des Partials `layouts/partials/place.html` eingefüllt:

```html
<script type="text/javascript">
  L.marker([
      {{ .meta.lat }},
      {{ .meta.lon }}],
      {
          "title": {{ .meta.title }}
        }
    ).addTo(map)
      .bindPopup('{{ .meta.popuptext }}')
</script>
```

## Weiterführende Informationen

- [Leaflet.js-Dokumentation für Marker](https://leafletjs.com/reference.html#marker)
- [Offizielle Dokumentation von Hugo](https://gohugo.io/)
- [Auswahl von Hugo-Themes](https://themes.gohugo.io/)
- [Youtube-Playlist von Mike Dane mit Tutorials zu Hugo](https://www.youtube.com/watch?v=qtIqKaDlqXo&list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3)
- [Sehr gutes Tutorial für ein eigenes Hugo-Theme](https://draft.dev/learn/creating-hugo-themes)

## Aufträge

{{% task title="Übungen" %}}
1. tbd
{{% /task %}}
