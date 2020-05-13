---
title: Schnittstellen (C++/CX)
ms.date: 01/22/2017
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
ms.openlocfilehash: 716bf86eddf621244415033dae1b9c93ad1baba5
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032355"
---
# <a name="interfaces-ccx"></a>Schnittstellen (C++/CX)

Obwohl eine Verweisklasse nur von einer konkreten Basisklasse erben kann, kann sie eine beliebige Anzahl von Schnittstellenklassen implementieren. Eine Schnittstellenklasse (oder Schnittstellenstruktur) kann (oder muss) mehrere Schnittstellenklassen erben, kann ihre Memberfunktionen überladen und darf Typparameter besitzen.

## <a name="characteristics"></a>Merkmale

Eine Schnittstelle verfügt über die folgenden Merkmale:

- Eine Schnittstellenklasse (oder Struktur) muss innerhalb eines Namespace deklariert werden und kann öffentliche oder private Zugreifbarkeit besitzen. Nur öffentliche Schnittstellen werden an Metadaten ausgegeben.

- Die Member einer Schnittstelle können Eigenschaften, Methoden und Ereignisse enthalten.

- Alle Schnittstellenmember sind implizit öffentlich und virtuell.

- Felder und statische Member sind nicht zulässig.

- Typen, die als Eigenschaften, Methodenparameter oder Rückgabewerte verwendet werden, können nur Windows-Runtime-Typen sein. Dies schließt die grundlegenden Typen und Enumeratklassentypen ein.

## <a name="declaration-and-usage"></a>Deklaration und Verwendung

Im folgenden Beispiel wird die Deklaration einer Schnittstelle erläutert. Beachten Sie, dass eine Schnittstelle entweder als Klassen- oder als Strukturtyp deklariert werden kann.

[!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]

Um eine Schnittstelle zu implementieren, deklariert und implementiert eine Verweisklasse oder Verweisstruktur virtuelle Methoden und Eigenschaften. Die Schnittstelle und die implementierende Verweisklasse müssen dieselben Methodenparameternamen verwenden, wie im folgenden Beispiel gezeigt:

[!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]

## <a name="interface-inheritance-hierarchies"></a>Schnittstellenvererbungshierarchien

Eine Schnittstelle kann von einer oder mehreren Schnittstellen erben. Im Gegensatz zu einer Verweisklasse oder -struktur, deklariert eine Schnittstelle nicht die geerbten Schnittstellenmember. Wenn Schnittstelle B von Schnittstelle A erbt und Verweisklasse C von B erbt, muss C sowohl A als auch B implementieren. Dies wird im nächsten Beispiel gezeigt.

[!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]

## <a name="implementing-interface-properties-and-events"></a>Implementieren von Schnittstelleneigenschaften und -ereignissen

Wie im vorherigen Beispiel gezeigt, können Sie triviale virtuelle Eigenschaften verwenden, um Schnittstelleneigenschaften zu implementieren. Sie können auch benutzerdefinierte Getter und Setter in der implementierenden Klasse bereitstellen.  Sowohl der Getter als auch der Setter müssen in einer Schnittstelleneigenschaft öffentlich sein.

[!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]

Wenn eine Schnittstelle eine get-only- oder set-only-Eigenschaft deklariert, dann sollte die implementierende Klasse explizit einen Getter oder Setter bereitstellen.

[!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]

Sie können in der implementierenden Klasse für Ereignisse auch benutzerdefinierte hinzufügen- und entfernen-Methoden implementieren.

## <a name="explicit-interface-implementation"></a>Explizite Schnittstellenimplementierung

Wenn eine Verweisklasse mehrere Schnittstellen implementiert und diese Schnittstellen Methoden verfügen, deren Namen und Signaturen für den Compiler identisch sind, können Sie die folgende Syntax verwenden, um die Schnittstellenmethode explizit angeben, die eine Klassenmethode implementiert.

[!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]

## <a name="generic-interfaces"></a>Generische Schnittstellen

In C++/CX `generic` wird das Schlüsselwort verwendet, um einen parametrisierten Windows-Runtime-Typ darzustellen. Ein parametrisierter Typ wird in Metadaten ausgegeben und kann durch jeden Code genutzt werden, der in einer Programmiersprache geschrieben ist, die Typparameter unterstützt. Die Windows-Runtime definiert einige generische Schnittstellen, z. B. [Windows::Foundation::Collections::IVector\<T>](/uwp/api/windows.foundation.collections.ivector-1)– unterstützt jedoch nicht die Erstellung öffentlicher benutzerdefinierter generischer Schnittstellen in C++/CX. Sie können jedoch private generische Schnittstellen erstellen.

So können Windows-Runtime-Typen zum Erstellen einer generischen Schnittstelle verwendet werden:

- Eine generische benutzerdefinierte `interface class` in einer Komponente kann nicht in ihre Windows-Metadatendatei ausgegeben werden. Sie kann daher keine öffentliche Zugreifbarkeit besitzen und nicht von Clientcode in anderen WINMD-Dateien implementiert werden. Sie kann durch nicht öffentliche Verweisklassen in der gleichen Komponente implementiert werden. Eine öffentliche Verweisklasse kann einen generischen Schnittstellentyp als privaten Member besitzen.

   Der folgenden Codeausschnitt zeigt, wie eine generische `interface class` deklariert und dann in einer privaten Verweisklasse implementiert wird, und wie die Verweisklasse als privater Member in einer öffentlichen Verweisklasse verwendet wird.

   [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]

- Eine generische Schnittstelle muss den Standardregeln für Schnittstellen folgen, die Zugreifbarkeit, Member, *erforderliche* Beziehungen, Basisklassen usw. festlegen

- Eine generische Schnittstelle kann eine oder mehrere generischen Typparameter verwenden, denen `typename` oder `class`vorangestellt werden. Nichttypenparameter werden nicht unterstützt.

- Ein Typparameter kann ein beliebiger Windows-Runtime-Typ sein. Das bedeutet, dass der Typparameter ein Verweistyp, ein Werttyp, eine Schnittstellenklasse, ein Delegat, ein fundamentaler Typ oder eine öffentliche Enumeratorklasse sein kann.

- Eine *geschlossene generische Schnittstelle* ist eine Schnittstelle, die von einer generischen Schnittstelle erbt und konkrete Typargumente für alle Typparameter spezifiziert. Sie kann überall verwendet werden, wo eine nicht generische private Schnittstelle verwendet werden kann.

- Eine *geöffnete generische Schnittstelle* ist eine Schnittstelle, die einen oder mehrere Typparameter aufweist, für die noch kein konkreter Typ bereitgestellt wurde. Sie kann überall verwendet werden, wo ein Typ verwendet werden kann. Dies schließt die Verwendung als Typargument einer anderen generischen Schnittstelle ein.

- Sie können nur eine gesamte Schnittstelle, nicht einzelne Methoden parametrisieren.

- Typparameter können nicht beschränkt werden.

- Eine geschlossene generische Schnittstelle verfügt über einen implizit generierten UUID. Benutzer können den UUID nicht angeben.

- In der Schnittstelle wird angenommen, dass jeder Verweis auf die aktuelle Schnittstelle – in einem Methodenparameter, einem Rückgabewert oder einer Eigenschaft – auf die aktuelle Instanziierung verweist. *IMyIntf* bedeutet z. B. *IMyIntf\<T>*.

- Wenn der Typ eines Methodenparameters ein Typparameter ist, verwendet die Deklaration dieses Parameters oder dieser Variablen den Namen des Typparameters ohne Zeiger, systemeigenen Verweis oder Handledeklaratoren. Das heißt, schreiben Sie nie "T^".

- Auf Vorlagen basierende Verweisklassen müssen privat sein. Sie können generische Schnittstellen implementieren und den Vorlagenparameter *T* an das generische Argument *T*übergeben. Jede Instanziierung einer vorlagenierten ref-Klasse ist selbst eine ref-Klasse.

## <a name="see-also"></a>Weitere Informationen

[Typensystem](../cppcx/type-system-c-cx.md)<br/>
[C++-/CX-Programmiersprachenreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)
