---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f981b86ed8f5d3b240d9f02380a603eb4f2605bc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623578"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

Definiert mehrere Vorlagen, die dabei helfen, Speicherblöcke für knotenbasierte Container zuzuweisen und freizugeben.

## <a name="syntax"></a>Syntax

```cpp
#include <allocators>
```

> [!NOTE]
> \<allocators>ist veraltet, beginnend mit Visual Studio 2019, Version 16,3.

## <a name="remarks"></a>Hinweise

Der- \<allocators> Header stellt sechs zuordnervorlagen bereit, mit denen Speicher Verwaltungsstrategien für Knoten basierte Container ausgewählt werden können. Für den Gebrauch mit diesen Vorlagen stellt es außerdem mehrere verschiedene Synchronisierungsfilter bereit, mit deren Hilfe Sie Strategien zur Speicherverwaltung an eine Vielzahl von Multithread-Schemas (oder auch an kein Schema) anpassen können. Sie können Ihre APP beschleunigen oder die Arbeitsspeicher Anforderungen verringern, indem Sie eine Speicher Verwaltungs Strategie mit ihren Speicher Verwendungs Mustern und Synchronisierungs Anforderungen vergleichen.

Allocatorvorlagen werden mit wiederverwendbaren Komponenten implementiert, die angepasst oder ersetzt werden können, um weitere Strategien zur Speicherverwaltung bereitzustellen.

Die Knoten basierten Container in der C++-Standard Bibliothek (Std:: List, Std:: Set, Std:: Multiset, Std:: Map und Std:: Multimap) speichern ihre Elemente in einzelnen Knoten. Alle Knoten für einen bestimmten Containertyp sind gleich groß, weshalb die Flexibilität eines allgemeinen Speicher-Managers nicht erforderlich ist. Weil die Größe jedes Speicherblocks beim Kompilierzeitpunkt bekannt ist, ist der Speicher-Manager sehr viel einfacher und schneller.

Bei Verwendung mit nicht Knoten basierten Containern (z. b. den C++-Standard Bibliotheks Containern Std:: Vector Std::d eque und Std:: basic_string) funktionieren die Zuordnungs Vorlagen ordnungsgemäß, aber Sie bieten keine Leistungsverbesserung gegenüber der Standard Zuweisung.

Ein Allocator ist eine Klassen Vorlage, die ein Objekt beschreibt, das die Speicher Belegung und-Freigabe für Objekte und Arrays von Objekten eines bestimmten Typs verwaltet. Zuordnerobjekte werden von mehreren Containerklassen Vorlagen in der C++-Standard Bibliothek verwendet.

Allocators sind alle Vorlagen folgenden Typs:

```cpp
template<class Type>
class allocator;
```

in denen das Vorlagenargument `Type` der von der Allocatorinstanz verwaltete Typ ist. Die C++-Standardbibliothek stellt eine Standard Zuweisung, Klassen Vorlagen [Zuweisung](allocator-class.md), bereit, die in definiert ist [\<memory>](memory.md) . Der- \<allocators> Header stellt die folgenden Zuweisungen bereit:

- [allocator_newdel](allocator-newdel-class.md)

- [allocator_unbounded](allocator-unbounded-class.md)

- [allocator_fixed_size](allocator-fixed-size-class.md)

- [allocator_variable_size](allocator-variable-size-class.md)

- [allocator_suballoc](allocator-suballoc-class.md)

- [allocator_chunklist](allocator-chunklist-class.md)

Verwenden Sie eine passende Istanziierung eines Allocators als zweiten Typargument, während Sie einen Container erstellen, wie z.B. in folgendem Beispiel.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

„_List0“ weist Knoten mit `allocator_chunklist` und dem standardmäßigen Synchronisierungsfilter zu.

Verwenden Sie das Makro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl), wenn Sie Allocatorvorlagen mit anderen als den standardmäßigen Synchronisierungsfiltern erstellen wollen:

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

„_Lst1“ weist Knoten mit `allocator_chunklist` und dem Synchronisierungsfilter [sync_per_thread](sync-per-thread-class.md) zu.

Eine Blockzuweisung ist ein Cache oder ein Filter. Ein Cache ist eine Klassen Vorlage, die ein Argument vom Typ Std:: size_t annimmt. Er definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt. Er muss mithilfe des **New**-Operators Speicher abrufen, er muss jedoch keinen separaten Operator **New** für jeden Block erstellen. Möglicherweise stellt er Unterzuordnungen aus einem größeren Block her, oder er zwischenspeichert möglicherweise freigegebene Blöcke für eine darauffolgende Freigabe.

Ein Compiler, der den Wert des Std:: size_t-Arguments, das beim instanziiert der Vorlage verwendet wurde, nicht erneut binden kann, ist nicht notwendigerweise der Wert des Arguments _Sz der an die Member-Funktionen von Cache zuweisen und deren Freigabe aufgehoben wird.

\<allocators>stellt die folgenden Cache Vorlagen bereit:

- [cache_freelist](cache-freelist-class.md)

- [cache_suballoc](cache-suballoc-class.md)

- [cache_chunklist](cache-chunklist-class.md)

Ein Filter ist eine Block Zuweisung, die seine Member-Funktionen mithilfe eines anderen Block zuordcators implementiert, der als Vorlagen Argument an Sie übermittelt wird. Synchronisierungsfilter sind die häufigste Filterform, die eine Synchronisierungsrichtlinie anwenden, um den Zugriff auf die Memberfunktionen einer Instanz eines anderen Blockallocators zu steuern. \<allocators>stellt die folgenden Synchronisierungs Filter bereit:

- [sync_none](sync-none-class.md)

- [sync_per_container](sync-per-container-class.md)

- [sync_per_thread](sync-per-thread-class.md)

- [sync_shared](sync-shared-class.md)

\<allocators>bietet auch den Filter [Rts_alloc](rts-alloc-class.md), der mehrere blockallocator-Instanzen enthält, und bestimmt, welche Instanz zur Laufzeit anstelle der Kompilierzeit für die Zuordnung oder Aufhebung der Zuordnung verwendet werden soll. Sie wird mit Compilern verwendet, die keine Neubindungen kompilieren können.

Eine Synchronisierungsrichtlinie legt fest, wie Allocatorinstanzen gleichzeitige Belegungs- und Freigabeanforderungen aus verschiedenen Threads verarbeiten. Die einfachste Richtlinie ist, alle Anforderungen direkt an das zugrundeliegende Cacheobjekt zu übergeben; die Synchronisierungsverwaltung wird dem Nutzer überlassen. Eine komplexere Richtlinie wäre z.B. das Verwenden eines Mutex zur Serialisierung des Zugriffs auf den zugrundeliegenden Cache.

Wenn ein Compiler das Kompilieren sowohl von Singlethread- als auch von Multithread-Anwendungen unterstützt, ist der standardmäßige Synchronisierungsfilter für Singlethread-Anwendung `sync_none`; andernfalls ist er `sync_shared`.

Die Cache Vorlage `cache_freelist` nimmt ein Max-Klassen Argument an, das die maximale Anzahl von Elementen bestimmt, die in der freien Liste gespeichert werden sollen.

\<allocators>stellt die folgenden maximalen Klassen bereit:

- [max_none](max-none-class.md)

- [max_unbounded](max-unbounded-class.md)

- [max_fixed_size](max-fixed-size-class.md)

- [max_variable_size](max-variable-size-class.md)

### <a name="macros"></a>Makros

|Makro|Beschreibung|
|-|-|
|[ALLOCATOR_DECL](allocators-functions.md#allocator_decl)|Ergibt eine zuordnerklassenvorlage.|
|[CACHE_CHUNKLIST](allocators-functions.md#cache_chunklist)|Gibt `stdext::allocators::cache_chunklist<sizeof(Type)>` aus.|
|[CACHE_FREELIST](allocators-functions.md#cache_freelist)|Gibt `stdext::allocators::cache_freelist<sizeof(Type), max>` aus.|
|[CACHE_SUBALLOC](allocators-functions.md#cache_suballoc)|Gibt `stdext::allocators::cache_suballoc<sizeof(Type)>` aus.|
|[SYNC_DEFAULT](allocators-functions.md#sync_default)|Gibt einen Synchronisierungsfilter aus.|

### <a name="operators"></a>Operatoren

|Operator|Beschreibung|
|-|-|
|[Operator! = ( \<allocators> )](allocators-operators.md#op_neq)|Es wird auf Ungleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.|
|[Operator = = ( \<allocators> )](allocators-operators.md#op_eq_eq)|Es wird auf Gleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[allocator_base](allocator-base-class.md)|Definiert die Basisklasse und allgemeine Funktionen, die zum Erstellen einer benutzerdefinierten Zuweisung von einem Synchronisierungsfilter erforderlich sind.|
|[allocator_chunklist](allocator-chunklist-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte, die einen Zwischenspeicher des Typs [cache_chunklist](cache-chunklist-class.md) verwenden.|
|[allocator_fixed_size](allocator-fixed-size-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_freelist](cache-freelist-class.md) mit einer von [max_fixed_size](max-fixed-size-class.md) verwalteten Länge verwenden.|
|[allocator_newdel](allocator-newdel-class.md)|Implementiert einen Allocator, der den **Operator Delete** verwendet, um einen Speicherblock freizugeben, und den **New-Operator** , um einen Speicherblock zuzuweisen.|
|[allocator_suballoc](allocator-suballoc-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_suballoc](cache-suballoc-class.md) verwenden.|
|[allocator_unbounded](allocator-unbounded-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_freelist](cache-freelist-class.md) mit einer von [max_unbound](max-unbounded-class.md) verwalteten Länge verwenden.|
|[allocator_variable_size](allocator-variable-size-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_freelist](cache-freelist-class.md) mit einer von [max_variable_size](max-variable-size-class.md) verwalteten Länge verwenden.|
|[cache_chunklist](cache-chunklist-class.md)|Definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt.|
|[cache_freelist](cache-freelist-class.md)|Definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt.|
|[cache_suballoc](cache-suballoc-class.md)|Definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt.|
|[freelist](freelist-class.md)|Verwaltet eine Liste von Speicherblöcken|
|[max_fixed_size](max-fixed-size-class.md)|Beschreibt ein Objekt der max-Klasse, das ein [freelist](freelist-class.md)-Objekt auf eine maximale Länge begrenzt.|
|[max_none](max-none-class.md)|Beschreibt ein Objekt der max-Klasse, das ein [freelist](freelist-class.md)-Objekt auf eine maximale Länge begrenzt.|
|[max_unbounded](max-unbounded-class.md)|Beschreibt ein Objekt der max-Klasse, das ein [freelist](freelist-class.md)-Objekt nicht auf eine maximale Länge begrenzt.|
|[max_variable_size](max-variable-size-class.md)|Beschreibt ein Objekt der max-Klasse, das die maximale Länge eines [freelist](freelist-class.md)-Objekts auf eine maximale Länge einschränkt, die annähernd proportional zur Anzahl von zugewiesenen Speicherblöcken ist.|
|[rts_alloc](rts-alloc-class.md)|Die Rts_alloc-Klassen Vorlage beschreibt einen [Filter](allocators-header.md) , der ein Array von Cache Instanzen enthält und bestimmt, welche Instanz für die Zuordnung und Aufhebung der Zuordnung zur Laufzeit anstatt zur Kompilierzeit verwendet werden soll.|
|[sync_none](sync-none-class.md)|Beschreibt einen Synchronisierungsfilter, der keine Synchronisierung bietet.|
|[sync_per_container](sync-per-container-class.md)|Beschreibt einen Synchronisierungsfilter, der für jedes Zuweisungsobjekt ein getrenntes Cacheobjekt bereitstellt.|
|[sync_per_thread](sync-per-thread-class.md)|Beschreibt einen Synchronisierungsfilter, der für jeden Thread ein getrenntes Cacheobjekt bereitstellt.|
|[sync_shared](sync-shared-class.md)|Beschreibt einen Synchronisierungsfilter, in dem ein Mutex verwendet wird, um den Zugriff auf ein Cacheobjekt zu steuern, das von allen Allocators gemeinsam verwendet wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Siehe auch

[Headerdateienreferenz](cpp-standard-library-header-files.md)
