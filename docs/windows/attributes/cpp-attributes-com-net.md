---
title: C++-Attribute für COM und .NET
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 734d82a30df3e143a6f47cb1b3eca2cd778830bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214928"
---
# <a name="c-attributes-for-com-and-net"></a>C++-Attribute für COM und .NET

Microsoft definiert einen Satz von C++ Attributen, die die COM-Programmierung vereinfachen und die Entwicklung von .NET Framework Common Language Runtime vereinfachen. Wenn Sie Attribute in die Quelldateien einschließen, arbeitet der Compiler mit Anbieter-DLLs, um Code einzufügen oder den Code in den generierten Objektdateien zu ändern. Diese Attribute helfen bei der Erstellung von IDL-Dateien, Schnittstellen, Typbibliotheken und anderen com-Elementen. In der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) werden Attribute von den Assistenten und vom Eigenschaftenfenster unterstützt.

Attribute, die für das Schreiben von COM-Objekten erforderlich sind, werden zwar durch Attribute entfernt, Sie benötigen aber einen Hintergrund der [com-Grundlagen](/windows/win32/com/the-component-object-model) , um Sie optimal zu verwenden

> [!NOTE]
> Wenn Sie C++ Standard Attribute suchen, finden Sie weitere Informationen unter [Attribute](../../cpp/attributes.md).

## <a name="purpose-of-attributes"></a>Attributzwecke

Attribute erweitern C++ in Richtungen, die derzeit nicht möglich sind, ohne die klassische Struktur der Sprache zu unterbrechen. Attribute ermöglichen es Anbietern (separaten DLLs), die sprach Funktionalität dynamisch zu erweitern. Das Hauptziel von Attributen besteht darin, die Erstellung von COM-Komponenten zu vereinfachen und die Produktivität des Komponenten Entwicklers zu erhöhen. Attribute können auf fast alle C++ Konstrukte angewendet werden, z. b. Klassen, Datenmember oder Element Funktionen. Im folgenden finden Sie eine Hervorhebung der Vorteile dieser neuen Technologie:

- Macht eine vertraute und einfache Aufruf Konvention verfügbar.

- Verwendet eingefügten Code, der im Gegensatz zu Makros vom Debugger erkannt wird.

- Ermöglicht die einfache Ableitung von Basisklassen ohne aufwändige Implementierungsdetails.

- Ersetzt die große Menge an IDL-Code, der für eine COM-Komponente erforderlich ist, mit wenigen präzisen Attributen.

Wenn Sie z. b. eine einfache Ereignis Senke für eine generische ATL-Klasse implementieren möchten, können Sie das [event_receiver](event-receiver.md) -Attribut auf eine bestimmte Klasse, z. b. `CMyReceiver`, anwenden. Das `event_receiver`-Attribut wird dann vom Microsoft C++ -Compiler kompiliert, der den richtigen Code in die Objektdatei einfügt.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

Anschließend können Sie die `CMyReceiver` Methoden `handler1` und `handler2` einrichten, um Ereignisse (mit der intrinsischen Funktion [__hook](../../cpp/hook.md)) aus einer Ereignis Quelle zu behandeln, die Sie mit [event_source](event-source.md)erstellen können.

## <a name="basic-mechanics-of-attributes"></a>Grundlegende Funktionsweise der Attribute

Es gibt drei Möglichkeiten, Attribute in das Projekt einzufügen. Zuerst können Sie Sie manuell in den Quellcode einfügen. Zweitens können Sie Sie mithilfe des Eigenschaften Rasters eines Objekts in Ihrem Projekt einfügen. Schließlich können Sie Sie mit den verschiedenen Assistenten einfügen. Weitere Informationen zur Verwendung des Fensters **Eigenschaften** und der verschiedenen Assistenten finden Sie unter [Visual Studio-Projekte C++- ](../../build/creating-and-managing-visual-cpp-projects.md).

Wenn das Projekt erstellt wird, analysiert der Compiler jede Quelldatei, wobei C++ eine Objektdatei erzeugt wird. Wenn der Compiler jedoch auf ein Attribut trifft, wird er analysiert und syntaktisch überprüft. Der Compiler ruft dann dynamisch einen Attribut Anbieter auf, um zum Zeitpunkt der Kompilierung Code einzufügen oder andere Änderungen vorzunehmen. Die Implementierung des Anbieters variiert abhängig vom Typ des Attributs. Beispielsweise werden ATL-bezogene Attribute von "atlprov. dll" implementiert.

In der folgenden Abbildung wird die Beziehung zwischen dem Compiler und dem Attribut Anbieter veranschaulicht.

![Komponenten Attribut Kommunikation](../media/vccompattrcomm.gif "Komponentenattributkommunikation")

> [!NOTE]
> Die Attribut Verwendung ändert nicht den Inhalt der Quelldatei. Der generierte Attribut Code ist nur während des Debuggens von Sitzungen sichtbar. Außerdem können Sie für jede Quelldatei im Projekt eine Textdatei generieren, in der die Ergebnisse der Attribut Ersetzung angezeigt werden. Weitere Informationen zu diesem Verfahren finden Sie unter [/FX (](../../build/reference/fx-merge-injected-code.md) eingefügten Code zusammenführen) und eingefügten [Code Debuggen](/visualstudio/debugger/how-to-debug-injected-code).

Wie die C++ meisten Konstrukte verfügen Attribute über eine Reihe von Merkmalen, die ihre ordnungsgemäße Verwendung definieren. Dies wird als Kontext des-Attributs bezeichnet und in der Attribut Kontext Tabelle für jedes Attribut Verweis Thema behandelt. Beispielsweise kann das [Co-Klasse](coclass.md) -Attribut nur auf eine vorhandene Klasse oder Struktur angewendet werden, und nicht auf das [cpp_quote](cpp-quote.md) -Attribut, das an beliebiger Stelle in C++ einer Quelldatei eingefügt werden kann.

## <a name="building-an-attributed-program"></a>Erstellen eines attributierten Programms

Nachdem Sie visuelle C++ Attribute in den Quellcode eingefügt haben, möchten Sie möglicherweise, C++ dass der Microsoft-Compiler eine Typbibliothek und eine IDL-Datei für Sie erzeugt. Die folgenden Optionen für den Linker helfen Ihnen beim Erstellen von tlb-und IDL-Dateien:

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

Einige Projekte enthalten mehrere unabhängige IDL-Dateien. Diese werden verwendet, um zwei oder mehr TLB-Dateien zu entwickeln und Sie optional an den Ressourcenblock zu binden. Dieses Szenario wird in Visual C++derzeit nicht unterstützt.

Außerdem gibt der visuelle C++ Linker alle IDL-bezogenen Attributinformationen in eine einzelne Mittel l-Datei aus. Es gibt keine Möglichkeit, zwei Typbibliotheken aus einem einzelnen Projekt zu generieren.

## <a name="attribute-contexts"></a><a name="contexts"></a>Attribut Kontexte

C++Attribute können über vier grundlegende Felder beschrieben werden: das Ziel, auf das Sie angewendet werden können (**gilt für**), wenn Sie wiederholbar sind oder nicht (**wiederholbar**), das erforderliche vorhanden sein weiterer Attribute (**erforderliche Attribute**) und Inkompatibilitäten mit anderen Attributen (**ungültige Attribute**). Diese Felder sind in einer begleitenden Tabelle im Referenz Thema jedes Attributs aufgelistet. Jedes dieser Felder wird unten beschrieben.

### <a name="applies-to"></a>Gilt für

In diesem Feld werden die C++ verschiedenen Sprachelemente beschrieben, die für das angegebene Attribut gültige Ziele sind. Wenn ein Attribut beispielsweise im Feld **gilt für** den Wert "Class" angibt, gibt dies an, dass das Attribut nur auf eine gültige C++ Klasse angewendet werden kann. Wenn das-Attribut auf eine Member-Funktion einer Klasse angewendet wird, würde ein Syntax Fehler entstehen.

Weitere Informationen finden Sie unter [Attribute by Usage (Attribute nach Verwendung](attributes-by-usage.md)).

### <a name="repeatable"></a>Wiederholbar

Dieses Feld gibt an, ob das Attribut wiederholt auf dasselbe Ziel angewendet werden kann. Die meisten Attribute sind nicht wiederholbar.

### <a name="required-attributes"></a>Erforderliche Attribute.

In diesem Feld werden andere Attribute aufgelistet, die vorhanden sein müssen (d. h. auf dasselbe Ziel angewendet), damit das angegebene Attribut ordnungsgemäß funktioniert. Es ist nicht üblich, dass für ein Attribut Einträge für dieses Feld vorhanden sind.

### <a name="invalid-attributes"></a>Ungültige Attribute

In diesem Feld werden andere Attribute aufgelistet, die mit dem angegebenen Attribut nicht kompatibel sind. Es ist nicht üblich, dass für ein Attribut Einträge für dieses Feld vorhanden sind.

## <a name="in-this-section"></a>In diesem Abschnitt

[Fragen und Antworten zur attributierten Programmierung](attribute-programming-faq.md)<br/>
[Attribute nach Gruppen](attributes-by-group.md)<br/>
[Attribute nach Verwendung](attributes-by-usage.md)<br/>
[Alphabetische Attributreferenz](attributes-alphabetical-reference.md)
