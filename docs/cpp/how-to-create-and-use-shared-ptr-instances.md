---
title: 'Vorgehensweise: Erstellen und Verwenden von shared_ptr-Instanzen'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 7d6ebb73-fa0d-4b0b-a528-bf05de96518e
ms.openlocfilehash: 44d375f72cf409df1e67b72dd76e196051dacf93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187958"
---
# <a name="how-to-create-and-use-shared_ptr-instances"></a>Vorgehensweise: Erstellen und Verwenden von shared_ptr Instanzen

Der Typ `shared_ptr` ist ein intelligenter Zeiger in der C++-Standardbibliothek für Szenarien, in denen möglicherweise mehrere Besitzer die Lebensdauer des Objekts im Arbeitsspeicher verwalten müssen. Nachdem Sie einen `shared_ptr` initialisiert haben, können Sie ihn kopieren, als Wert an Funktionsargumente übergeben oder anderen `shared_ptr`-Instanzen zuweisen. Alle Instanzen zeigen auf dasselbe Objekt und greifen gemeinsam auf einen "Kontrollblock" zu, der den Verweiszähler erhöht bzw. verringert, wenn ein neuer `shared_ptr` hinzugefügt wird, den Gültigkeitsbereich verlässt oder zurückgesetzt wird. Wenn der Verweiszähler Null erreicht, löscht der Kontrollblock die Speicherressource und sich selbst.

Die folgende Abbildung zeigt mehrere `shared_ptr`-Instanzen, die auf einen Speicherbereich zeigen.

![Diagramm für freigegebenen Zeiger](media/shared_ptr.png "Diagramm für freigegebenen Zeiger")

## <a name="example-setup"></a>Beispielkonfiguration

Bei allen folgenden Beispielen wird davon ausgegangen, dass Sie die erforderlichen Header hinzugefügt und die erforderlichen Typen, wie hier gezeigt, deklariert haben:

```cpp
// shared_ptr-examples.cpp
// The following examples assume these declarations:
#include <algorithm>
#include <iostream>
#include <memory>
#include <string>
#include <vector>

struct MediaAsset
{
    virtual ~MediaAsset() = default; // make it polymorphic
};

struct Song : public MediaAsset
{
    std::wstring artist;
    std::wstring title;
    Song(const std::wstring& artist_, const std::wstring& title_) :
        artist{ artist_ }, title{ title_ } {}
};

struct Photo : public MediaAsset
{
    std::wstring date;
    std::wstring location;
    std::wstring subject;
    Photo(
        const std::wstring& date_,
        const std::wstring& location_,
        const std::wstring& subject_) :
        date{ date_ }, location{ location_ }, subject{ subject_ } {}
};

using namespace std;

int main()
{
    // The examples go here, in order:
    // Example 1
    // Example 2
    // Example 3
    // Example 4
    // Example 6
}
```

## <a name="example-1"></a>Beispiel 1

Verwenden Sie nach Möglichkeit die Funktion [make_shared](../standard-library/memory-functions.md#make_shared) zum Erstellen eines `shared_ptr`, wenn die Speicherressource zum ersten Mal erstellt wird. `make_shared` ist ausnahmesicher. Die Funktion verwendet den gleichen Aufruf zum Zuweisen des Arbeitsspeichers für den Kontrollblock und die Ressource, wodurch der Konstruktionsmehraufwand verringert wird. Wenn Sie nicht verwenden `make_shared` , müssen Sie einen expliziten Ausdruck verwenden, **`new`** um das Objekt zu erstellen, bevor Sie es an den- `shared_ptr` Konstruktor übergeben. Das folgende Beispiel zeigt verschiedene Möglichkeiten zum Deklarieren und Initialisieren eines `shared_ptr` zusammen mit einem neuen Objekt.

[!code-cpp[stl_smart_pointers#1](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_1.cpp)]

## <a name="example-2"></a>Beispiel 2

Im folgenden Beispiel wird veranschaulicht, wie `shared_ptr`-Instanzen deklariert und initialisiert werden, die den gemeinsamen Besitz eines Objekts übernehmen, das bereits von einem anderen `shared_ptr` zugeordnet wurde. Angenommen, `sp2` ist ein initialisierter `shared_ptr`.

[!code-cpp[stl_smart_pointers#2](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_2.cpp)]

## <a name="example-3"></a>Beispiel 3

`shared_ptr` ist auch in Containern der C++ Standardbibliothek hilfreich, wenn Sie die Algorithmen verwenden, die Elemente kopieren. Sie können Elemente in einem `shared_ptr` umschließen und sie dann in andere Container kopieren. Voraussetzung ist, dass der zugrunde liegende Arbeitsspeicher solange gültig ist, wie Sie ihn benötigen, und nicht länger. Im folgenden Beispiel wird die Verwendung des `remove_copy_if`-Algorithmus für `shared_ptr`-Instanzen in einem Vektor dargestellt.

[!code-cpp[stl_smart_pointers#4](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_3.cpp)]

## <a name="example-4"></a>Beispiel 4

Sie können `dynamic_pointer_cast`, `static_pointer_cast` und `const_pointer_cast` zum Umwandeln eines `shared_ptr` verwenden. Diese Funktionen ähneln den **`dynamic_cast`** **`static_cast`** **`const_cast`** Operatoren, und. Im folgenden Beispiel wird das Testen des abgeleiteten Typs jedes Elements in einem Vektor mit `shared_ptr` für Basisklassen sowie das Kopieren der Elemente und das Anzeigen der zugehörigen Informationen gezeigt.

[!code-cpp[stl_smart_pointers#5](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_4.cpp)]

## <a name="example-5"></a>Beispiel 5

Sie können einen `shared_ptr` folgendermaßen an eine andere Funktion übergeben:

- Übergeben Sie den `shared_ptr` als Wert. Dies ruft den Kopierkonstruktor auf, erhöht den Verweiszähler und macht den Aufgerufenen zum Besitzer. Bei diesem Vorgang kommt es zu einem geringfügigen Mehraufwand, der abhängig von der Anzahl der zu übergebenden `shared_ptr`-Objekte bedeutsam sein kann. Verwenden Sie diese Option, wenn der implizite oder explizite Codevertrag zwischen dem Aufrufer und dem Aufgerufenen erfordert, dass der Aufgerufene ein Besitzer ist.

- Übergeben Sie den `shared_ptr` als Verweis oder konstanter Verweis. In diesem Fall wird der Verweiszähler nicht erhöht, und der Aufgerufene kann auf den Zeiger zugreifen, solange der Aufrufer den Gültigkeitsbereich nicht verlässt. Der Aufgerufene hat auch die Möglichkeit, einen `shared_ptr` auf Basis des Verweises zu erstellen und zu einem freigegebenen Besitzer zu werden. Verwenden Sie diese Option, wenn der Aufrufer den Aufgerufenen nicht kennt oder wenn Sie einen `shared_ptr` übergeben müssen und den Kopiervorgang aus Leistungsgründen vermeiden möchten.

- Übergeben Sie den zugrunde liegenden Zeiger oder einen Verweis auf das zugrunde liegende Objekt. Dadurch kann der Aufgerufene das Objekt verwenden, jedoch nicht den Besitz teilen oder die Lebensdauer erweitern. Wenn der Aufgerufene einen `shared_ptr` auf der Grundlage des Rohdatenzeigers erstellt, ist der neue `shared_ptr` unabhängig vom Original und steuert die zugrunde liegende Ressource nicht. Verwenden Sie diese Option, wenn der Vertrag zwischen dem Aufrufer und dem Aufgerufenen klar festgelegt ist, dass der Aufrufer Besitzer der `shared_ptr`-Lebensdauer bleibt.

- Bei der Entscheidung, wie ein `shared_ptr` übergeben wird, bestimmen Sie, ob der Aufgerufene den Besitz der zugrunde liegenden Ressource teilen muss. Ein "Besitzer" ist ein Objekt oder eine Funktion, die die zugrunde liegende Ressource beibehalten kann, solange sie benötigt wird. Wenn der Aufrufer sicherstellen muss, dass der Aufgerufene die Lebensdauer des Zeigers über dessen Lebensdauer (bzw. die Lebensdauer der Funktion) hinaus verlängern kann, verwenden Sie die erste Option. Wenn es nicht relevant ist, ob der Aufgerufene die Lebensdauer verlängert, übergeben Sie "shared_ptr" als Verweis und überlassen Sie es dem Aufgerufenen, diesen zu kopieren oder nicht.

- Wenn Sie einer Hilfsfunktion Zugriff auf den zugrunde liegenden Zeiger erteilen müssen und Sie wissen, dass die Hilfsfunktion nur den Zeiger verwendet und dann zurückgegeben wird, bevor die aufrufende Funktion zurückgegeben wird, muss die Funktion den Besitz des zugrunde liegenden Zeigers nicht teilen. Sie muss lediglich innerhalb der Lebensdauer des `shared_ptr` des Aufrufers auf den Zeiger zugreifen. In diesem Fall ist es sicher, den `shared_ptr` als Verweis zu übergeben bzw. den Rohdatenzeiger oder einen Verweis an das zugrunde liegende Objekt zu übergeben. Ein Übergeben auf diese Weise bietet einen leichten Leistungsvorteil und hilft Ihnen dabei, Ihre Programmierabsicht besser zum Ausdruck zu bringen.

- Manchmal, beispielsweise in einem `std::vector<shared_ptr<T>>`, müssen Sie jeden `shared_ptr` an einen Text eines Lambda-Ausdrucks oder ein benanntes Funktionsobjekt übergeben. Wenn das Lambda oder die Funktion den Zeiger nicht speichert, übergeben Sie den `shared_ptr` als Verweis, damit der Kopierkonstruktor nicht für jedes Element aufgerufen wird.

## <a name="example-6"></a>Beispiel 6

Das folgende Beispiel zeigt, wie der `shared_ptr` verschiedene Vergleichsoperatoren überlädt, um Zeigervergleiche für den Arbeitsspeicher zu ermöglichen, der im Besitz der `shared_ptr`-Instanzen ist.

[!code-cpp[stl_smart_pointers#3](codesnippet/CPP/how-to-create-and-use-shared-ptr-instances_6.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Intelligente Zeiger (Modern C++)](smart-pointers-modern-cpp.md)
