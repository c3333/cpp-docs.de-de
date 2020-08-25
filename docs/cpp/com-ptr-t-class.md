---
title: _com_ptr_t-Klasse
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: 2c299ea4a5aaabba847c85500a6023d7b112d492
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838502"
---
# <a name="_com_ptr_t-class"></a>_com_ptr_t-Klasse

**Microsoft-spezifisch**

Ein **_com_ptr_t** -Objekt kapselt einen COM-Schnittstellen Zeiger und wird als "intelligenter" Zeiger bezeichnet. Diese Vorlagen Klasse verwaltet die Zuordnung und Aufhebung der Zuordnung von Ressourcen über Funktionsaufrufe der Element `IUnknown` Funktionen: `QueryInterface` , `AddRef` und `Release` .

Ein intelligenter Zeiger wird in der Regel durch die typedef-Definition verwiesen, die vom _COM_SMARTPTR_TYPEDEF-Makro bereitgestellt wird. Dieses Makro nimmt einen Schnittstellennamen und die IID an und deklariert eine Spezialisierung **_com_ptr_t** mit dem Namen der Schnittstelle sowie einem Suffix von `Ptr` . Beispiel:

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

deklariert die **_com_ptr_t** Spezialisierung `IMyInterfacePtr` .

Eine Reihe von [Funktions Vorlagen](../cpp/relational-function-templates.md), nicht Elemente dieser Vorlagen Klasse, unterstützen Vergleiche mit einem intelligenten Zeiger auf der rechten Seite des Vergleichs Operators.

### <a name="construction"></a>Bauwesen

| Name | Beschreibung |
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Erstellt ein **_com_ptr_t** -Objekt.|

### <a name="low-level-operations"></a>Vorgänge auf niedriger Stufe

| Name | Beschreibung |
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|Ruft die `AddRef` Member-Funktion von `IUnknown` für den gekapselten Schnittstellen Zeiger auf.|
|[Anfügen](../cpp/com-ptr-t-attach.md)|Kapselt einen unformatierten Schnittstellenzeiger vom Typ dieses intelligenten Zeigers.|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Erstellt eine neue Instanz eines-Objekts, wenn ein oder ein angegeben wird `CLSID` `ProgID` .|
|[Trennen](../cpp/com-ptr-t-detach.md)|Extrahiert den gekapselten Schnittstellenzeiger und gibt ihn zurück.|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Hängt an eine vorhandene Instanz eines-Objekts an, wenn ein oder ein angegeben wird `CLSID` `ProgID` .|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Gibt den gekapselten Schnittstellenzeiger zurück.|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Ruft die `QueryInterface` Member-Funktion von `IUnknown` für den gekapselten Schnittstellen Zeiger auf.|
|[Release](../cpp/com-ptr-t-release.md)|Ruft die `Release` Member-Funktion von `IUnknown` für den gekapselten Schnittstellen Zeiger auf.|

### <a name="operators"></a>Operatoren

| Name | Beschreibung |
|-|-|
|[Operator =](../cpp/com-ptr-t-operator-equal.md)|Weist einem vorhandenen **_com_ptr_t** -Objekt einen neuen Wert zu.|
|[Operatoren = =,! =, \<, > , \<=, >=](../cpp/com-ptr-t-relational-operators.md)|Vergleichen Sie das intelligente Zeigerobjekt mit einem anderen intelligenten Zeiger, unformatierten Schnittstellenzeiger oder NULL.|
|[Extractors](../cpp/com-ptr-t-extractors.md)|Extrahieren Sie den gekapselten COM-Schnittstellenzeiger.|

**Ende Microsoft-spezifisch**

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<comip.h>

**Lib:** comsuppw. lib oder comsuppwd. lib (siehe [/Zc: wchar_t (wchar_t ist System eigener Typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , um weitere Informationen zu erhalten)

## <a name="see-also"></a>Weitere Informationen

[Compiler-com-Unterstützungs Klassen](../cpp/compiler-com-support-classes.md)
