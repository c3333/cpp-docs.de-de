---
title: Verwenden von dllimport und dllexport in C++-Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
ms.openlocfilehash: 4687db45c767f4323c97aff0a685aa3aeeb83e94
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227009"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Verwenden von dllimport und dllexport in C++-Klassen

**Microsoft-spezifisch**

Sie können C++-Klassen mit dem-oder dem-Attribut deklarieren **`dllimport`** **`dllexport`** . Hierbei ist impliziert, dass die gesamte Klasse importiert oder exportiert wird. Klassen, die auf diese Weise exportiert werden, werden als exportierbare Klassen bezeichnet.

Im folgenden Beispiel wird eine exportierbare Klasse definiert. All ihre Memberfunktionen und statischen Daten werden exportiert:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Beachten Sie, dass die explizite Verwendung der **`dllimport`** Attribute und für Member einer **`dllexport`** exportierbaren Klasse nicht zulässig ist.

## <a name="dllexport-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>dllexport-Klassen

Wenn Sie eine Klasse deklarieren **`dllexport`** , werden alle zugehörigen Element Funktionen und statischen Datenmember exportiert. Sie müssen die Definitionen all dieser Member im gleichen Programm bereitstellen. Andernfalls wird ein Linkerfehler generiert. Die einzige Ausnahme dieser Regel gilt für rein virtuelle Funktionen, für die keine expliziten Definitionen bereitgestellt werden müssen. Da jedoch ein Destruktor für eine abstrakte Klasse immer vom Destruktor für die Basisklasse aufgerufen wird, müssen rein virtuelle Destruktoren immer eine Definition bereitstellen. Beachten Sie, dass diese Regeln auch für nicht exportierbare Klassen gelten.

Wenn Sie Daten vom Klassentyp oder Funktionen, die Klassen zurückgeben, exportieren, stellen Sie sicher, dass Sie die Klasse exportieren.

## <a name="dllimport-classes"></a><a name="_pluslang_dllexport_classesdllexportclasses"></a>DllImport-Klassen

Wenn Sie eine Klasse deklarieren **`dllimport`** , werden alle zugehörigen Element Funktionen und statischen Datenmember importiert. Im Gegensatz zum Verhalten von **`dllimport`** und **`dllexport`** für nicht Klassentypen können statische Datenmember keine Definition in demselben Programm angeben, in dem eine **`dllimport`** Klasse definiert ist.

## <a name="inheritance-and-exportable-classes"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Vererbungs-und exportierbare Klassen

Alle Basisklassen einer exportierbaren Klasse müssen exportierbar sein. Wenn dies nicht der Fall ist, wird eine Compilerwarnung ausgegeben. Darüber hinaus müssen alle zugreifbaren Member, die auch Klassen sind, exportierbar sein. Diese Regel ermöglicht es **`dllexport`** , dass eine Klasse von einer Klasse erbt **`dllimport`** , und eine **`dllimport`** Klasse, die von einer Klasse erben soll **`dllexport`** (obwohl letztere nicht empfohlen wird). In der Regel sollte alles, auf das der DLL-Client zugreifen kann (gemäß C++-Zugriffsregeln), Teil der exportierbaren Schnittstelle sein. Hierzu zählen die privaten Datenmember, auf die in Inlinefunktionen verwiesen wird.

## <a name="selective-member-importexport"></a><a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Selektives Importieren/Exportieren von Membern

Da Element Funktionen und statische Daten innerhalb einer Klasse implizit über externe Verknüpfungen verfügen, können Sie Sie mit dem-Attribut oder dem-Attribut deklarieren **`dllimport`** **`dllexport`** , es sei denn, die gesamte Klasse wird exportiert. Wenn die gesamte Klasse importiert oder exportiert wird, ist die explizite Deklaration von Element Funktionen und-Daten als **`dllimport`** oder unzulässig **`dllexport`** . Wenn Sie ein statisches Datenmember innerhalb einer Klassendefinition als deklarieren **`dllexport`** , muss eine Definition irgendwo innerhalb desselben Programms (wie bei einer nicht Klassen externen Verknüpfung) vorkommen.

Auf ähnliche Weise können Sie Element Funktionen mit dem-Attribut oder dem-Attribut deklarieren **`dllimport`** **`dllexport`** . In diesem Fall müssen Sie eine **`dllexport`** Definition irgendwo innerhalb desselben Programms angeben.

Es wird empfohlen, einige wichtige Aspekte hinsichtlich des selektiven Memberimports und -exports zu beachten:

- Der selektive Memberimport und -export wird am besten zum Bereitstellen einer Version der exportierten Klassenschnittstelle verwendet, die restriktiver ist, also eine Schnittstelle, für die Sie eine DLL entwerfen können, die weniger öffentliche und private Funktionen verfügbar macht, als die Programmiersprache andernfalls zulassen würde. Er ist auch zum Optimieren der exportierbaren Schnittstelle nützlich: Wenn Sie wissen, dass der Client definitionsgemäß nicht in der Lage ist, auf einige private Daten zuzugreifen, müssen Sie nicht die gesamte Klasse exportieren.

- Wenn Sie eine virtuelle Funktion in einer Klasse exportieren, müssen Sie alle exportieren, oder Sie müssen zumindest Versionen bereitstellen, die der Client direkt verwenden kann.

- Wenn Sie über eine Klasse verfügen, in der Sie selektiven Memberimport und -export mit virtuellen Funktionen verwenden, müssen die Funktionen in der exportierbaren Schnittstelle auftreten oder inline definiert (für den Client sichtbar) sein.

- Wenn Sie einen Member als definieren **`dllexport`** , ihn jedoch nicht in die Klassendefinition einschließen, wird ein Compilerfehler generiert. Sie müssen den Member im Header der Klasse definieren.

- Obwohl die Definition von Klassenmembern als **`dllimport`** oder **`dllexport`** zulässig ist, können Sie die in der Klassendefinition angegebene Schnittstelle nicht überschreiben.

- Wenn Sie eine Member-Funktion an einer anderen Stelle als dem Text der Klassendefinition definieren, in der Sie sie deklariert haben, wird eine Warnung generiert, wenn die Funktion als oder definiert ist **`dllexport`** **`dllimport`** (wenn sich diese Definition von der in der Klassen Deklaration angegebenen unterscheidet).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
