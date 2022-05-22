---
title: "04 | Die Dinge lokal zusammenfügen"
date: 2022-05-07T12:50:13.000Z
draft: false
type: book
toc: true
weight: 400
summary: Mit GitHub Actions kann kontinuierlich ein neuer Stand der gemeinsamen Arbeit gebaut werden. Für den eigentlichen Bau ist aber weniger GitHub zuständig, sondern die verwendete Software in den Workflows. Dies wird am Beispiel von Pandoc gezeigt, das in dieser Einheit im Mittelpunkt steht.
---

## Pandoc als exemplarische Software in GitHub Actions

In der vorigen Einheit haben Sie gesehen, dass Ihr Beiträge zu den beiden Lexika von GitHub kontinuierlich zu einem neuen temporären Artefakt verarbeitet werden. Das heißt, dass bei ensprechender Konfiguration mit jedem Commit ein Workflow angestoßen wird, der am Ende eine neue Version des gesamten Textes ausgibt.

Dieser Vorgang ist typisch für die Arbeit mit GitHub und GitLab, denn er ist das Zentrum agilen Arbeitens: Aus jedem neuen Artefakt, das aus dem Workflow fällt, kann das Team lernen und das Produkt besser machen.

Die Software, die das jeweils erledigt, ist austauschbar. Während in einem Softwareprojekt ein C-Compiler die Arbeit verrichtet, ist es in einem anderen ein Python-Skript. In unseren Beispielen ist es die Software Pandoc, die aus vielen Markdown-Dokumenten ein HTML-Dokument erstellt.

## Pandoc als exemplarische Software in Workflows begreifen

Ebenfalls typisch für die Zusammenarbeit auf GitHub und GitLab ist der Einsatz der zentralen Software auf dem eigenen Rechner. Denn dadurch steigt die Entwicklungsgeschwindigkeit enorm, weil Sie nicht immer abwarten müssen, bis ein Workflow durchgelaufen ist und Sie das Artefakt herunterladen können. Stattdessen generieren Sie das Artefakt auf Ihrem eigenen Rechner und laden (pushen) es auf GitHub, wenn Sie selbst zufrieden sind.

Um dieses lokale Arbeiten besser verstehen zu können, geht es in dieser Einheit darum, mit Pandoc exemplarisch nachzuvollziehen, was Sie als Entwickler:innen auf Ihrem eigenen Rechner leisten können.

## Ziele

- Sie installieren Pandoc, Git und Git Bash (nur Windows).
- Sie starten die Kommandozeile Ihres Betriebssystems (Terminal (MacOS, Linux) oder PowerShell/Git Bash (Windows)) und geben Textbefehle ein.
- Sie konvertieren verschiedene Quellformate von Textdokumenten mithilfe von Pandoc in andere Zielformate, bspw. Markdown zu HTML oder zu DOCX.
- Sie formatieren Konfigurationsangaben für Pandoc im YAML-Format.
- Sie zitieren Literatur in Markdown-Dokumenten.
- Sie verstehen, wie Pandoc im Rahmen von GitHub Actions verwendet wird.

## Dokumente lokal mit Pandoc konvertieren

Das folgende Video zeigt kurz und knapp die Funktionsweise von Pandoc: 

- Markdown-Dokumente werden zu einem HTML-Dokument konvertiert. 
- Dabei kommt eine Konfigurationsdatei zum Einsatz, die alle wesentlichen Parameter enthalten kann, wiederverwendbar ist und auch in die Versionskontrolle, also in GitHub, eingecheckt werden kann. 
- Im abschließenden Teil zeige ich, wie Sie in Markdown wissenschaftliche Texte samt Zitaten und Quellenverwaltung verfassen und mit Pandoc konvertieren können.

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed/9gJGKjtbfZA' frameborder='0' allowfullscreen></iframe></div>

## Pandoc im Workflow wiedererkennen

Im folgenden Gist (Codeschnipsel, der auf GitHub gehostet wird), sehen Sie die Konfiguration des GitHub Workflows, den wir für das Tierlexikon verwenden. Aus Gründen, die bei GitHub liegen, ist er komplizierter, als wenn Sie Pandoc lokal einsetzen. So ist `Z13` nur notwendig, weil GitHub eine Liste von Dateien nicht aus einer Konfigurationsdatei lesen mag.

Versuchen Sie zunächst nicht, die komplette Datei zu verstehen, da viele Anweisungen enthalten sind, die an dieser Stelle erst einmal nicht wichtig sind. Bemerken Sie zunächst nur:

- Die Konfigurationsdatei ist im YAML-Format notiert.
- `ZZ16ff.` listet Argumente, die an Pandoc übergeben werden.

{{< gist xldrkp fa249f91793d5873a738a9a6dcb32350 >}}

## Weiterführende Informationen

- [Offizielle Pandoc-Dokumentation](https://pandoc.org/)
  - [Default-Dateien und mögliche Konfigurationsparameter](https://pandoc.org/MANUAL.html#defaults-files)
  - [Zitieren in Markdown/Pandoc](https://pandoc.org/MANUAL.html#citations)
- [Wikipedia-Beitrag zu YAML](https://de.wikipedia.org/wiki/YAML)

## Aufträge

{{% task title="Lesen und nachbereiten" %}}
Beschäftigen Sie sich mit den weiterführenden Informationen. Sie helfen Ihnen, die Inhalte des Praxisteils besser zu verstehen und die folgenden Aufträge souverän zu bearbeiten.
{{% /task %}}

{{% task title="Die Inhalte des Videos nachvollziehen" %}}
Vollziehen Sie die Inhalte des Videos "Pandoc 101" auf Ihrem Rechner nach.
{{% /task %}}