---
title: Gleitkomma-Migrationsprobleme
ms.date: 05/17/2017
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
ms.openlocfilehash: 40eb08e4f9c7058d6b11700535e1c25f86548a22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215019"
---
# <a name="floating-point-migration-issues"></a>Gleitkomma-Migrationsprobleme

Wenn Sie Ihre Projekte auf eine neuere Version von Visual Studio upgraden, kann es manchmal vorkommen, dass sich die Ergebnisse bestimmter Operationen mit Gleitkommazahlen geändert haben. Dies geschieht in der Regel aus zwei Gründen: Änderungen beim Generieren von Code, die den verfügbaren Prozessor besser nutzen, und Fehlerbehebungen oder Änderungen an den Algorithmen, die in den mathematischen Funktionen der C-Laufzeitbibliothek (CRT) verwendet werden. Im Allgemeinen sind die neuen Ergebnisse innerhalb der Grenzen, die vom Sprachstandard festgelegt wurden, korrekt. Lesen Sie weiter, um herauszufinden, was sich geändert hat, und wenn es wichtig ist, wie Sie die gleichen Ergebnisse für Ihre Funktionen bekommen wie zuvor.

## <a name="new-math-functions-and-universal-crt-changes"></a>Neue mathematische Funktionen und universelle CRT-Änderungen

Die meisten mathematischen CRT-Funktionen sind seit Jahren in Visual Studio verfügbar, jedoch sind ab Visual Studio 2013 alle Funktionen enthalten, die für ISO C99 erforderlich sind. Diese Funktionen werden implementiert, damit die Sprache ebenso leistungsfähig wie korrekt ist. Da das korrekt gerundete Ergebnis in jedem Fall nur sehr teuer errechenbar ist, wurden diese Funktionen dazu entworfen, eine starke Annäherung an das korrekt gerundete Ergebnis zu erzielen. In den meisten Fällen liegt das erzeugte Ergebnis innerhalb der +/-1-Einheit der geringsten Präzision, oder *ulp*, des korrekt gerundeten Ergebnisses, obwohl die Ungenauigkeit auch größer ausfallen kann. Wenn Sie zuvor eine andere math-Bibliothek verwendet haben, um diese Funktionen zu erhalten, können Unterschiede bei der Implementierung für die Änderung in Ihren Ergebnissen verantwortlich sein.

Wenn die mathematischen Funktionen in die universelle CRT in Visual Studio 2015 verschoben wurden, wurden einige neue Algorithmen verwendet und mehrere Fehler in der Implementierung der Funktionen, die in Visual Studio 2013 neu waren, wurden korrigiert. Diese Änderungen können zu feststellbaren Unterschieden in den Ergebnissen von Gleitkommaberechnungen führen, die diese Funktionen verwenden. Die fehlerbehafteten Funktionen waren erf, exp2, remainder, remquo, scalbln, und scalbn, und ihre float- und long double-Varianten.  Andere Änderungen in Visual Studio 2015 haben Probleme bei der Information des beibehaltenen Statuswort des Gleitkommas und des Ausnahmestatus in den Funktionen _clear87, _clearfp, fegetenv, fesetenv, und feholdexcept behoben.

## <a name="processor-differences-and-compiler-flags"></a>Prozessorunterschiede und Compilerflags

Viele der Gleitkommafunktionen in der mathematischen Bibliothek haben unterschiedliche Implementierungen für verschiedene CPU-Architekturen. Die 32-Bit-x86-CRT hat möglicherweise eine andere Implementierung als die 64-Bit x64 CRT. Darüber hinaus haben möglicherweise einige der Funktionen mehrere Implementierungen für eine bestimmte CPU-Architektur. Eine möglichst effiziente Implementierung wird je nach den von der CPU unterstützten Anweisungssets dynamisch zur Laufzeit ausgewählt. In der 32-Bit-x86-CRT haben einige Funktionen eine x87- und eine SSE2-Implementierung. Wenn eine CPU verwendet wird, die SSE2 unterstützt, wird die schnellere SSE2-Implementierung verwendet. Wenn eine CPU verwendet wird, die SSE2 nicht unterstützt, wird die langsamere x87-Implementierung verwendet. Möglicherweise sehen Sie dies bei der Migration von altem Code, da in Visual Studio 2012 die Standardoption der x86-Compilerarchitektur in [/arch:SSE2](../build/reference/arch-x86.md) geändert wurde. Da verschiedene Implementierungen der Funktionen der mathematischen Bibliothek verschiedene CPU-Anweisungen und andere Algorithmen verwenden, um Ergebnisse zu erzielen, unterscheiden sich die Ergebnisse auf den verschiedenen Plattformen möglicherweise. In den meisten Fällen liegen die Ergebnisse innerhalb +/-1 ULP des korrekt gerundeten Ergebnisses, die tatsächlichen Ergebnisse können jedoch in den CPUs variieren.

Die Verbesserungen für Richtigkeit bei der Codeerstellung in verschiedenen Gleitkomma-Modi in Visual Studio können auch die Ergebnisse der Operationen mit Gleitkomma beeinflussen, wenn der alte Code mit dem neuen verglichen wird, auch bei Verwendung der gleichen Compilerflags. Der von Visual Studio 2010 generierte Code beim Festlegen von [/fp:precise](../build/reference/fp-specify-floating-point-behavior.md) (Standard) oder `/fp:strict` hat möglicherweise die fortgeschrittenen NaN-Werte durch die Ausdrücke nicht korrekt weitergegeben. Daher können einige Ausdrücke, die in älteren Compilern ein numerisches Ergebnis ausgegeben haben, jetzt ordnungsgemäß ein NaN-Ergebnis erzeugen. Sie sehen möglicherweise auch Unterschiede, da die für `/fp:fast` aktivierten Codeoptimierungen jetzt weitere Features des Prozessors nutzen. Diese Optimierungen können weniger Anweisungen verwenden, aber Sie können die generierten Ergebnissen beeinflussen, da einige zuvor sichtbare intermediate-Vorgänge entfernt wurden.

## <a name="how-to-get-identical-results"></a>So rufen Sie identische Ergebnisse ab

In den meisten Fällen führen Gleitkomma-Änderungen in den neuesten Compilern und Bibliotheken zu schnellerem oder genauerem Verhalten, oder beides. Sie erkennen möglicherweise auch eine bessere Prozessorleistung, wenn die SSE2-Anweisungen die x87-Anweisungen ersetzen. Wenn Sie jedoch über Code verfügen, der das Gleitkomma-Verhalten eines älteren Codes exakt replizieren muss, sollten Sie lieber die Visual Studio Funktionen zur nativen Festlegung von Zielversionen verwenden und das betroffene Projekt mit älteren Toolsets erstellen. Weitere Informationen finden Sie unter [Use native multi-targeting in Visual Studio to build old projects (Verwenden der nativen Festlegung von Zielversionen in Visual Studio, um alte Projekte zu erstellen)](use-native-multi-targeting.md).

## <a name="see-also"></a>Weitere Informationen

[Aktualisieren von Projekten aus früheren Versionen von VisualC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Überblick über potenzielle Aktualisierungsprobleme (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Änderungsverlauf von Visual C++ von 2003 bis 2015](visual-cpp-change-history-2003-2015.md)
