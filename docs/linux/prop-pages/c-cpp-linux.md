---
title: C/C++-Eigenschaften (Linux C++)
ms.date: 10/14/2020
description: Hier werden die Kompilierungsoptionen für Linux auf der Seite mit C-/C++-Eigenschaften in Visual Studio beschrieben.
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: b8cb1d8c6c585262e966c3015660adeaeab60307
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924561"
---
# <a name="cc-properties-linux-c"></a>C/C++-Eigenschaften (Linux C++)

::: moniker range="msvc-140"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=msvc-150"

## <a name="general"></a>Allgemein

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Zusätzliche Includeverzeichnisse | Gibt mindestens ein Verzeichnis an, das dem Includepfad hinzugefügt werden soll. Verwenden Sie Semikolons, um mehrere Verzeichnisse zu trennen. (-I\[path]). |
| Debuginformationsformat | Gibt den Typ der Debuginformationen an, die vom Compiler generiert werden. | **Keine** : Generiert keine Debuginformationen, sodass die Kompilierung ggf. schneller erfolgt.<br/>**Minimale Debuginformationen** : Generiert minimale Debuginformationen.<br/>**Vollständige Debugging-Informationen(DWARF2)** : Generiert DWARF2-Debuginformationen.<br/> |
| Name der Objektdatei | Gibt einen Namen an, der den Standardobjektdateinamen überschreibt. Dabei kann es sich um einen Datei- oder Verzeichnisnamen handeln. (-o [name]). |
| Warnstufe | Wählt aus, wie streng der Compiler bei Codefehlern sein soll.  Fügen Sie andere Flags direkt zu den **zusätzlichen Optionen** hinzu. (/w, /Weverything). | **Alle Warnungen deaktivieren** : Deaktiviert alle Compilerwarnungen.<br/>**EnableAllWarnings** : Aktiviert alle Warnungen, einschließlich standardmäßig deaktivierter Warnungen.<br/> |
| Warnungen als Fehler behandeln | Behandelt alle Compilerwarnungen als Fehler. Bei einem neuen Projekt ist es empfehlenswert, /Werror in allen Kompilierungen zu verwenden. Alle Warnungen werden aufgelöst, um schwer zu findende Codefehler auf einem Minimum zu halten. |
| Zusätzliche Warnungen für C | Definiert eine Sammlung zusätzlicher Warnmeldungen. |
| Zusätzliche Warnungen für C++ | Definiert eine Sammlung zusätzlicher Warnmeldungen. |
| Ausführlichen Modus aktivieren | Gibt weitere Informationen zur Diagnose des Builds aus, wenn der ausführliche Modus aktiviert ist. |
| C-Compiler | Gibt das Programm an, das beim Kompilieren von C-Quelldateien aufgerufen werden soll, oder den Pfad zum C-Compiler auf dem Remotesystem. |
| C++ Compiler | Gibt das Programm an, das beim Kompilieren von C++-Quelldateien aufgerufen werden soll, oder den Pfad zum C-Compiler auf dem Remotesystem. |
| Kompilierungstimeout | Das Remotekompilierungstimeout in Millisekunden. |
| Objektdateien kopieren | Gibt an, ob die kompilierten Objektdateien vom Remotesystem auf den lokalen Computer kopiert werden sollen. |
| Maximale Anzahl paralleler Kompilierungsaufträge | Hiermit wird die Anzahl an Prozessen angegeben, die während der Kompilierung parallel erstellt werden sollen. Der Standardwert ist 1. Wenn Sie die Version 1 des Windows-Subsystems für Linux verwenden, beträgt das Limit 64. |
| Architektur überprüfen | Hiermit wird angegeben, ob überprüft werden soll, ob die für das Projekt ausgewählte Plattform mit der Plattform des Remotesystems übereinstimmt.|
| AddressSanitizer aktivieren | Hiermit wird das Programm mit AddressSanitizer kompiliert. Dabei handelt es sich um ein Tool für eine schnelle Arbeitsspeicherfehlererkennung, das Probleme des Runtimearbeitsspeichers entdecken kann, z. B. Verwendung nach Freigabe, und Überprüfungen auf Werte außerhalb des gültigen Bereichs durchführt.|

## <a name="optimization"></a>Optimization

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Optimization | Gibt die Optimierungsstufe für die Anwendung an. | **Benutzerdefiniert** : Benutzerdefinierte Optimierung<br/>**Deaktiviert** : Deaktivieren der Optimierung.<br/>**Größe minimieren** : Größenoptimierung<br/>**Geschwindigkeit maximieren** : Geschwindigkeitsoptimierung<br/>**Vollständige Optimierung** : teure Optimierungen |
| Strenges Aliasing | Nimmt die strengsten Aliasingregeln an.  Bei einem Objekt eines Typs wird niemals davon ausgegangen, dass es sich an derselben Adresse wie ein Objekt eines anderen Typs befindet. |
| Schleifen auflösen | Löst Schleifen auf, um Anwendungen schneller zu machen, indem die Anzahl der ausgeführten Branches verringert wird (dadurch entsteht größerer Code). |
| Linkzeitoptimierung | Aktiviert die Optimierungen zwischen Prozeduren, indem dem Optimierer die Möglichkeit gegeben wird, Objektdateien in Ihrer Anwendung zu durchsuchen. |
| Framezeiger unterdrücken | Unterdrückt die Erstellung von Framezeigern im Anrufstapel. |
| Keine allgemeinen Textblöcke | Weist auch nicht initialisierte globale Variablen im Datenabschnitt der Objektdatei zu, anstatt sie als gemeinsame Blöcke zu generieren. |

## <a name="preprocessor"></a>Präprozessor

| Eigenschaft | BESCHREIBUNG |
|--|--|
| Präprozessordefinitionen | Definiert Vorverarbeitungssymbole für Ihre Quelldatei. (-D) |
| Präprozessordefinitionen aufheben | Gibt mindestens eine aufgehobene Präprozessordefinition an.  (-U \[macro]) |
| Alle Präprozessordefinitionen aufheben | Hebt die Definition aller zuvor definierten Präprozessorwerte auf.  (-undef) |
| Includedateien anzeigen | Generiert eine Liste der Includedateien mit Compilerausgabe.  (-H) |

## <a name="code-generation"></a>Codeerzeugung

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Positionsunabhängiger Code | Generiert positionsunabhängigen Code (Position Independent Code, PIC) für die Verwendung in einer freigegebenen Bibliothek. |
| Statische Elemente sind threadsicher | Gibt zusätzlichen Code auf, um die in C++ ABI angegebene Routinen zur threadsicheren Initialisierung lokaler statischer Elemente zu verwenden. | **Nein** : Threadsichere statische Elemente deaktivieren.<br/>**Ja** : Threadsichere statische Elemente aktivieren. |
| Gleitkommaoptimierung | Ermöglicht Gleitkommaoptimierungen durch die Lockerung der IEEE-754-Konformität. |
| Inlinemethoden ausgeblendet | Wenn aktiviert, werden Out-of-Line-Kopien von Inlinemethoden als `private extern` deklariert. |
| Standardmäßig versteckte Symbole | Alle Symbole werden als `private extern` deklariert, es sei denn, sie sind explizit mit dem Makro `__attribute` für den Export gekennzeichnet. |
| C++-Ausnahmen aktivieren | Gibt das Ausnahmebehandlungsmodell an, das vom Compiler verwendet wird. | **Nein** : Ausnahmebehandlung deaktivieren.<br/>**Ja** :-Ausnahmebehandlung aktivieren. |

## <a name="language"></a>Sprache

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Laufzeit-Typeninformation aktivieren | Fügt Code für die Überprüfung der C++-Objekttypen während der Laufzeit hinzu (Laufzeit-Typinformationen).     (frtti, fno-rtti) |
| C-Sprachstandard | Bestimmt den C-Sprachstandard. | **Default**<br/>**C89** : C89-Sprachstandard.<br/>**C99** : C99-Sprachstandard.<br/>**C11** : C11-Sprachstandard.<br/>**C99 (GNU-Dialekt)** : C99-Sprachstandard (GNU-Dialekt).<br/>**C11 (GNU-Dialekt)** : C11-Sprachstandard (GNU-Dialekt). |
| C++-Sprachstandard | Bestimmt den C++-Sprachstandard | **Standard**<br/>**C++03** : C++03-Sprachstandard.<br/>**C++11** : C++11-Sprachstandard.<br/>**C++14** : C++14-Sprachstandard.<br/>**C++03 (GNU-Dialekt)** : C++03-Sprachstandard (GNU-Dialekt).<br/>**C++11 (GNU-Dialekt)** : C++11-Sprachstandard (GNU-Dialekt).<br/>**C++14 (GNU-Dialekt)** : C++14-Sprachstandard (GNU-Dialekt). |

## <a name="advanced"></a>Erweitert

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Kompilieren als | Wählt die Kompilierungssprachoption für C- und CPP-Dateien aus. (-x c, -x c++) | **Standard** : Die Erkennung erfolgt anhand der Erweiterung „.c“ oder „.cpp“.<br/>**Als C-Code kompilieren** : Als C-Code kompilieren.<br/>**Als C++-Code kompilieren** : als C++-Code kompilieren. |
| Explizite Includedateien | Gibt mindestens eine erzwungene Includedatei (-include \[name]) an. |

::: moniker-end
