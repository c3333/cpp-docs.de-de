---
title: Programmieren mit CComBSTR (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 020c2d18c721e658d15bb1451039154ae50b99f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321791"
---
# <a name="programming-with-ccombstr-atl"></a>Programmieren mit CComBSTR (ATL)

Die ATL-Klasse [CComBSTR](../atl/reference/ccombstr-class.md) stellt einen Wrapper um den BSTR-Datentyp bereit. Obwohl `CComBSTR` es ein nützliches Werkzeug ist, gibt es mehrere Situationen, die Vorsicht erfordern.

- [Konvertierungsprobleme](#programmingwithccombstr_conversionissues)

- [Bereichsprobleme](#programmingwithccombstr_scopeissues)

- [Explizites Befreien des CComBSTR-Objekts](#programmingwithccombstr_explicitlyfreeing)

- [Verwenden von CComBSTR-Objekten in Schleifen](#programmingwithccombstr_usingloops)

- [Probleme mit Speicherlecks](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a>Konvertierungsprobleme

Obwohl `CComBSTR` mehrere Methoden automatisch ein ANSI-Zeichenfolgenargument in Unicode konvertieren, geben die Methoden immer Unicode-Formatzeichenfolgen zurück. Um die Ausgabezeichenfolge wieder in ANSI zu konvertieren, verwenden Sie eine ATL-Konvertierungsklasse. Weitere Informationen zu den ATL-Konvertierungsklassen finden Sie unter [ATL- und MFC-Zeichenfolgenkonvertierungsmakros](reference/string-conversion-macros.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Wenn Sie ein Zeichenfolgenliteral `CComBSTR` zum Ändern eines Objekts verwenden, verwenden Sie Zeichenfolgen mit breiten Zeichen. Dadurch werden unnötige Konvertierungen reduziert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a>Bereichsprobleme

Wie bei jeder wohlerzogenen `CComBSTR` Klasse, wird seine Ressourcen frei, wenn es aus dem Bereich geht. Wenn eine Funktion einen Zeiger `CComBSTR` auf die Zeichenfolge zurückgibt, kann dies zu Problemen führen, da der Zeiger auf den bereits freigegebenen Speicher verweist. Verwenden Sie in `Copy` diesen Fällen die Methode, wie unten gezeigt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a>Explizites Befreien des CComBSTR-Objekts

Es ist möglich, die im `CComBSTR` Objekt enthaltene Zeichenfolge explizit freizugeben, bevor das Objekt den Bereich verlässt. Wenn die Zeichenfolge freigegeben `CComBSTR` wird, ist das Objekt ungültig.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a>Verwenden von CComBSTR-Objekten in Schleifen

Da `CComBSTR` die Klasse einen Puffer zuweist, um `+=` bestimmte `Append` Vorgänge auszuführen, z. B. den Operator oder die Methode, wird nicht empfohlen, dass Sie DieZeichenfolgenbearbeitung innerhalb einer engen Schleife durchführen. In diesen `CStringT` Situationen, bietet eine bessere Leistung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a>Probleme mit Speicherlecks

Das Übergeben der Adresse `CComBSTR` einer initialisierten funktion an eine Funktion als **[out]-Parameter** verursacht einen Speicherverlust.

Im folgenden Beispiel wird die Zeichenfolge, `"Initialized"` die der Zeichenfolge `MyGoodFunction` zugeordnet ist, durchgesickert, wenn die Funktion die Zeichenfolge ersetzt.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Um das Leck zu `Empty` vermeiden, `CComBSTR` rufen Sie die Methode für vorhandene Objekte auf, bevor Sie die Adresse als **[out]-Parameter** übergeben.

Beachten Sie, dass derselbe Code kein Leck verursachen würde, wenn der Parameter der Funktion **[in, out]** war.

## <a name="see-also"></a>Siehe auch

[Konzepte](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT-Klasse](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Zeichenfolgenkonvertierungsmakros](../atl/reference/string-conversion-macros.md)
