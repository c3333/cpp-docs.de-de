---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f6be154be68cd5e43fd6f934d88c04fb25be9dc5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754445"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

Definiert mehrere Vorlagen, die dabei helfen, Speicherblöcke für knotenbasierte Container zuzuweisen und freizugeben.

## <a name="syntax"></a>Syntax

```cpp
#include <allocators>
```

> [!NOTE]
> \<Zuallokators> veraltet ist, beginnend mit Visual Studio 2019 Version 16.3.

## <a name="remarks"></a>Bemerkungen

Der Header \<allocators> stellt sechs Allocatorvorlagen bereit, die dazu verwendet werden können, Strategien zur Speicherverwaltung für knotenbasierte Container auszuwählen. Für den Gebrauch mit diesen Vorlagen stellt es außerdem mehrere verschiedene Synchronisierungsfilter bereit, mit deren Hilfe Sie Strategien zur Speicherverwaltung an eine Vielzahl von Multithread-Schemas (oder auch an kein Schema) anpassen können. Sie können Ihre App beschleunigen oder den Speicherbedarf reduzieren, indem Sie eine Speicherverwaltungsstrategie an die Speichernutzungsmuster und Synchronisierungsanforderungen anpassen.

Allocatorvorlagen werden mit wiederverwendbaren Komponenten implementiert, die angepasst oder ersetzt werden können, um weitere Strategien zur Speicherverwaltung bereitzustellen.

Die knotenbasierten Container in der C++-Standardbibliothek (std::list, std::set, std::multiset, std::map und std::multimap) speichern ihre Elemente in einzelnen Knoten. Alle Knoten für einen bestimmten Containertyp sind gleich groß, weshalb die Flexibilität eines allgemeinen Speicher-Managers nicht erforderlich ist. Weil die Größe jedes Speicherblocks beim Kompilierzeitpunkt bekannt ist, ist der Speicher-Manager sehr viel einfacher und schneller.

Bei Verwendung mit Containern, die nicht knotenbasiert sind (z. B. die C++-Standardbibliothekscontainer std::vector std::deque und std::basic_string), funktionieren die Zuweisungsvorlagen ordnungsgemäß, bieten jedoch wahrscheinlich keine Leistungsverbesserungen gegenüber dem Standardzuweisungssystem.

Ein Allokator ist eine Klassenvorlage, die ein Objekt beschreibt, das die Speicherzuweisung und die Freigabe für Objekte und Arrays von Objekten eines bestimmten Typs verwaltet. Allocator-Objekte werden von mehreren Containerklassenvorlagen in der C++-Standardbibliothek verwendet.

Allocators sind alle Vorlagen folgenden Typs:

```cpp
template<class Type>
class allocator;
```

in denen das Vorlagenargument `Type` der von der Allocatorinstanz verwaltete Typ ist. Die C++-Standardbibliothek stellt einen Standardzuweisungszuweisungs-, [Klassenvorlagenallokator](../standard-library/allocator-class.md)bereit, der im [ \<Speicher>](../standard-library/memory.md)definiert ist. Der Header \<allocators> stellt folgende Allocators bereit:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Verwenden Sie eine passende Istanziierung eines Allocators als zweiten Typargument, während Sie einen Container erstellen, wie z.B. in folgendem Beispiel.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

„_List0“ weist Knoten mit `allocator_chunklist` und dem standardmäßigen Synchronisierungsfilter zu.

Verwenden Sie das Makro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl), wenn Sie Allocatorvorlagen mit anderen als den standardmäßigen Synchronisierungsfiltern erstellen wollen:

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

„_Lst1“ weist Knoten mit `allocator_chunklist` und dem Synchronisierungsfilter [sync_per_thread](../standard-library/sync-per-thread-class.md) zu.

Eine Blockzuweisung ist ein Cache oder ein Filter. Ein Cache ist eine Klassenvorlage, die ein Argument vom Typ std::size_t verwendet. Er definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt. Es muss Speicher mit Operator **new**erhalten, aber es muss keinen separaten Aufruf an Operator **neu** für jeden Block machen. Möglicherweise stellt er Unterzuordnungen aus einem größeren Block her, oder er zwischenspeichert möglicherweise freigegebene Blöcke für eine darauffolgende Freigabe.

Bei einem Compiler, der den Wert des std::size_t-Arguments, das beim Instanziieren der Vorlage verwendet wurde, nicht erneut binden kann, ist nicht unbedingt der Wert des Arguments _Sz, das an die Memberfunktionen eines Caches übergeben wird.

\<allocators> stellt folgende Cachevorlagen bereit:

- [Cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Ein Filter ist ein Blockallokator, der seine Memberfunktionen mithilfe eines anderen Blockallokators implementiert, der ihm als Vorlagenargument übergeben wird. Synchronisierungsfilter sind die häufigste Filterform, die eine Synchronisierungsrichtlinie anwenden, um den Zugriff auf die Memberfunktionen einer Instanz eines anderen Blockallocators zu steuern. \<allocators> stellt folgende Synchronisierungsfilter bereit:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators> stellt auch den Filter [rts_alloc](../standard-library/rts-alloc-class.md) bereit, der mehrere Blockbelegungsinstanzen enthält und der ermittelt zur Laufzeit, nicht zur Kompilierzeit, welche Instanz für die Belegung oder Freigabe von Speicher zu verwenden ist. Sie wird mit Compilern verwendet, die keine Neubindungen kompilieren können.

Eine Synchronisierungsrichtlinie legt fest, wie Allocatorinstanzen gleichzeitige Belegungs- und Freigabeanforderungen aus verschiedenen Threads verarbeiten. Die einfachste Richtlinie ist, alle Anforderungen direkt an das zugrundeliegende Cacheobjekt zu übergeben; die Synchronisierungsverwaltung wird dem Nutzer überlassen. Eine komplexere Richtlinie wäre z.B. das Verwenden eines Mutex zur Serialisierung des Zugriffs auf den zugrundeliegenden Cache.

Wenn ein Compiler das Kompilieren sowohl von Singlethread- als auch von Multithread-Anwendungen unterstützt, ist der standardmäßige Synchronisierungsfilter für Singlethread-Anwendung `sync_none`; andernfalls ist er `sync_shared`.

Die Cachevorlage `cache_freelist` verwendet ein argument max-Klasse, das die maximale Anzahl von Elementen bestimmt, die in der freien Liste gespeichert werden sollen.

\<allocators> stellt folgende max-Klassen bereit:

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Makros

|Makro|BESCHREIBUNG|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Gibt eine Zuweisungsklassenvorlage ab.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Gibt `stdext::allocators::cache_chunklist<sizeof(Type)>` aus.|
|[Cache_freelist](../standard-library/allocators-functions.md#cache_freelist)|Gibt `stdext::allocators::cache_freelist<sizeof(Type), max>` aus.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Gibt `stdext::allocators::cache_suballoc<sizeof(Type)>` aus.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Gibt einen Synchronisierungsfilter aus.|

### <a name="operators"></a>Operatoren

|Operator|BESCHREIBUNG|
|-|-|
|[Operator!=\<(Zuführer>)](../standard-library/allocators-operators.md#op_neq)|Es wird auf Ungleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.|
|[operator== (\<allocators>)](../standard-library/allocators-operators.md#op_eq_eq)|Es wird auf Gleichheit zwischen Zuweisungsobjekten einer bestimmten Klasse getestet.|

### <a name="classes"></a>Klassen

|Klasse|BESCHREIBUNG|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Definiert die Basisklasse und allgemeine Funktionen, die zum Erstellen einer benutzerdefinierten Zuweisung von einem Synchronisierungsfilter erforderlich sind.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte, die einen Zwischenspeicher des Typs [cache_chunklist](../standard-library/cache-chunklist-class.md) verwenden.|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_freelist](../standard-library/cache-freelist-class.md) mit einer von [max_fixed_size](../standard-library/max-fixed-size-class.md) verwalteten Länge verwenden.|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementiert einen Allokator, der **Operator delete** verwendet, um einen Speicherblock und einen **Operator neu** zuzuweisen, um einen Speicherblock zuzuweisen.|
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_suballoc](../standard-library/cache-suballoc-class.md) verwenden.|
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_freelist](../standard-library/cache-freelist-class.md) mit einer von [max_unbound](../standard-library/max-unbounded-class.md) verwalteten Länge verwenden.|
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Beschreibt ein Objekt, das die Speicherbelegung und -freigabe für Objekte des Typs `Type` verwaltet, die einen Cache des Typs [cache_freelist](../standard-library/cache-freelist-class.md) mit einer von [max_variable_size](../standard-library/max-variable-size-class.md) verwalteten Länge verwenden.|
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt.|
|[Cache_freelist](../standard-library/cache-freelist-class.md)|Definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt.|
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Definiert eine Blockzuweisung, die Speicherblöcke einheitlicher Größe zuweist und freigibt.|
|[freelist](../standard-library/freelist-class.md)|Verwaltet eine Liste von Speicherblöcken|
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Beschreibt ein Objekt der max-Klasse, das ein [freelist](../standard-library/freelist-class.md)-Objekt auf eine maximale Länge begrenzt.|
|[max_none](../standard-library/max-none-class.md)|Beschreibt ein Objekt der max-Klasse, das ein [freelist](../standard-library/freelist-class.md)-Objekt auf eine maximale Länge begrenzt.|
|[max_unbounded](../standard-library/max-unbounded-class.md)|Beschreibt ein Objekt der max-Klasse, das ein [freelist](../standard-library/freelist-class.md)-Objekt nicht auf eine maximale Länge begrenzt.|
|[max_variable_size](../standard-library/max-variable-size-class.md)|Beschreibt ein Objekt der max-Klasse, das die maximale Länge eines [freelist](../standard-library/freelist-class.md)-Objekts auf eine maximale Länge einschränkt, die annähernd proportional zur Anzahl von zugewiesenen Speicherblöcken ist.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|Die rts_alloc-Klassenvorlage beschreibt einen [Filter,](../standard-library/allocators-header.md) der ein Array von Cacheinstanzen enthält, und bestimmt, welche Instanz zur Laufzeit anstelle von Kompilierungszeiten für die Zuweisung und Deallation verwendet werden soll.|
|[sync_none](../standard-library/sync-none-class.md)|Beschreibt einen Synchronisierungsfilter, der keine Synchronisierung bietet.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|Beschreibt einen Synchronisierungsfilter, der für jedes Zuweisungsobjekt ein getrenntes Cacheobjekt bereitstellt.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Beschreibt einen Synchronisierungsfilter, der für jeden Thread ein getrenntes Cacheobjekt bereitstellt.|
|[sync_shared](../standard-library/sync-shared-class.md)|Beschreibt einen Synchronisierungsfilter, in dem ein Mutex verwendet wird, um den Zugriff auf ein Cacheobjekt zu steuern, das von allen Allocators gemeinsam verwendet wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<allocators>

**Namespace:** stdext

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)
