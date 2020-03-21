---
title: BNF-Grammatik für den Microsoft-Makro Assembler
description: BNF-Beschreibung von MASM für x64.
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), BNF reference
ms.openlocfilehash: 1a9577292e60db73838e5e6b850a4634db959fd6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075465"
---
# <a name="microsoft-macro-assembler-bnf-grammar"></a>BNF-Grammatik für den Microsoft-Makro Assembler

Diese Seite enthält eine BNF-Beschreibung der MASM-Grammatik. Sie wird als Ergänzung zu den Referenz Themen bereitgestellt und ist nicht garantiert, dass Sie fertiggestellt werden. Ausführliche Informationen zu Schlüsselwörtern, Parametern, Vorgängen usw. finden Sie in den Referenz Themen.

Zur Veranschaulichung der Verwendung des BNF zeigt das folgende Diagramm die Definition der TypeDef-Direktive an, beginnend mit dem *nonterminaltypedefdir*.

![Beispiel für MASM BNF](media/bnf.png)

Die Einträge unter jeder horizontalen geschweifter Klammer sind Terminals (z. b. **NEAR16**, **NEAR32**, **FAR16**und **FAR32**) oder nicht terminale (z. b. *Qualifizierer*, *qualifiedtype*, *Distance*und *protospec*), die weiter definiert werden können. Jedes kursiv formatierte nicht Terminal in der *typedefdir* -Definition ist auch ein Eintrag in BNF. Drei vertikale Punkte geben eine Verzweigungs Definition für ein nicht Terminal an, die aus Gründen der Einfachheit nicht illustriert wird.

Die BNF-Grammatik ermöglicht Rekursive Definitionen. Die Grammatik verwendet beispielsweise qualifiedtype als mögliche Definition für qualifiedtype, bei der es sich auch um eine Komponente der Definition für den Qualifizierer handelt. Das Symbol "|" gibt eine Auswahl zwischen alternativen Ausdrücken an, z. b. *endosline* | *Kommentar*. Doppelte geschweifte Klammern geben einen optionalen Parameter an, z. b. ⟦ *macroparameterlist* ⟧. Die Klammern werden im Quellcode nicht angezeigt.

## <a name="masm-nonterminals"></a>MASM-Nonterminals

*;;* \
&nbsp;&nbsp;&nbsp;&nbsp;*Endo | * *Kommentar*

*= Dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* = *immexpr* ;;

*ADDOP* -\
&nbsp;&nbsp;&nbsp;&nbsp;+ | -

*aexpr* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Begriffs* | der && *Begriff* " *aexpr* "

\ " *altid* "
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

\ von " *arbiarytext* "
&nbsp;&nbsp;&nbsp;&nbsp;*charlist*

*asminkonstruktions*\
&nbsp;&nbsp;&nbsp;&nbsp;*mnetmonic* ⟦ *exprlist* ⟧

" *assumedir* "-\
&nbsp;&nbsp;&nbsp;&nbsp;**annehmen** von " *assumelist* ;; \"
&nbsp;&nbsp;&nbsp;&nbsp;| von **nichts ausgehen** ;;

" *assumelist* "-\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeregiester* | *assumelist* , *assumeregiester*\

*assumereg* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Register* : *assumeval*

" *assumeregiester* "-\
&nbsp;&nbsp;&nbsp; |  *&nbsp;.* *assumeReg*

der *-\*
&nbsp;&nbsp;&nbsp;&nbsp;*Segmentregister* : *.*

*\ für* den
&nbsp;&nbsp;&nbsp;&nbsp;*frameexpr* | **Nothing** | **Fehler**

*assumeval* -\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedtype* | **Nothing** | **Fehler**

*bcdkonstanten* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Sign* ⟧ *decnumber*

*BinaryOp* -\
&nbsp;&nbsp;&nbsp;&nbsp;= = |! = | > = | < = | > | < | &

*bitdef* -\
&nbsp;&nbsp;&nbsp;&nbsp;*bitfieldid* : *bitfieldsize* ⟦ = *constexpr* ⟧

*bitdeflist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*bitdef* | *bitdeflist* , ⟦;; ⟧ *bitdef*

*bitfieldid* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*bitfieldsize* -\
&nbsp;&nbsp;&nbsp;&nbsp;*constexpr*

*blockstatements*\
&nbsp;&nbsp;&nbsp;&nbsp;*directivelist*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Fahren Sie fort** **. Wenn** *cexpr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Brechen** Sie ⟦ ab **. If** *cexpr* ⟧

*bool*\
&nbsp;&nbsp;&nbsp;&nbsp;**true** | **false**

*byteregiester* -\
&nbsp;&nbsp;&nbsp;&nbsp;Al | Ah | CL | CH | DL | DH | BL | BH | R8B | R9B | R10B | R11B | R12B | R13B | R14B | R15B

*cexpr* -\
&nbsp;&nbsp;&nbsp;&nbsp;*aexpr* | *cexpr* || *aexpr*

*Zeichen*\
&nbsp;&nbsp;&nbsp;ein beliebiges Zeichen mit einer Ordinalzahl im Bereich 0 – 255 mit Ausnahme von Zeilenvorschub (10) &nbsp;.

*charlist* -\
&nbsp;&nbsp;&nbsp;Zeichen &nbsp;*Zeichen* | *charlist* -Zeichen

*className* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Zeichenfolge*

*commdecl* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *near far* ⟧ ⟦ *LangType* ⟧ *ID* : *commtype*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦: *constexpr* ⟧

*kommdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**comm**\
&nbsp;&nbsp;&nbsp;&nbsp;*kommlist* ;;

*Kommentar*\
&nbsp;&nbsp;&nbsp;&nbsp;; *Text* ;;

*commentdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Kommentar** *Trennzeichen\*
&nbsp;&nbsp;&nbsp;&nbsp;*Text*\
&nbsp;&nbsp;&nbsp;&nbsp;*Text* *delimiter* Trennzeichen *Text* ;;

*kommlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*kommdecl* - | *kommlist* , *kommdecl*

*commtype* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Typ* | *constexpr*

*Konstante*\
&nbsp;&nbsp;&nbsp;&nbsp;*Ziffern* ⟦ *radixoverride* ⟧

*constexpr* -\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*contextdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**PUSHCONTEXT** *contextitemlist* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;**POPCONTEXT** *contextitemlist* ;;

*ContextItem* -\
&nbsp;&nbsp;&nbsp;&nbsp;**die |  | ** **CPU** - **LISTING** ** | ** **ALL** | 

*contextitemlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*ContextItem* | *contextitemlist* , *ContextItem*

*controlblock* -\
&nbsp;&nbsp;&nbsp;&nbsp;*whileblock* | *repeatblock*

*controldir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*controlif* | *controlblock*

*controlelseif* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Elseif** &nbsp;&nbsp;&nbsp;&nbsp;*cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directivelist* \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlelseif* ⟧

*controlif* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Wenn** &nbsp;&nbsp;&nbsp;&nbsp;*cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directivelist*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *controlelseif* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **. Else** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;[*directivelist*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp; **. Umdif** ;;

*Coprozessor* -\
&nbsp;&nbsp;&nbsp;&nbsp;. 8087 |. 287 |. 387 |. NO87

*\ "*
&nbsp;&nbsp; *&nbsp;&nbsp;".*

*\ für* ""
&nbsp;&nbsp;&nbsp;&nbsp; **.\ für** die
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Xkref** ⟦ *idlist* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Nokref** ⟦ *idlist* ⟧

*cxzexpr* -\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* -\
&nbsp;&nbsp;&nbsp;&nbsp;|! *expr* -\
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* = = expr \
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* ! = expr

*datadecl* -\
&nbsp;&nbsp;&nbsp;&nbsp;DB | DW | DD | DF | DQ | DT | *DataType* | *typeid*

*datadir* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧ *DataItem* ;;

*DataItem* -\
&nbsp;&nbsp;&nbsp;&nbsp;*datadecl* *scalarinstlist*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structtag* *structinstlist*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeid* *structinstlist*\
&nbsp;&nbsp;&nbsp;&nbsp;| *uniontag* *structinstlist*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordtag* " *recordinstlist* ".

*DataType* -\
&nbsp;&nbsp;&nbsp;&nbsp;Byte | SByte | Word | Schwert | DWORD | SDWORD | "F" | QWord | Sqword | TByte | OWord | REAL4 | REAL8 | REAL10 | MMWORD | XMMWORD | YMMWORD

*decdigit* -\
&nbsp;&nbsp;&nbsp;&nbsp;0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 21.00

*decnumber* -\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit* -\
&nbsp;&nbsp;&nbsp;&nbsp;| *decnumber* - *decdigit*

*Trenn* Zeichen\
&nbsp;&nbsp;&nbsp;&nbsp;beliebigen Zeichen außer " *whitespacecharacter* ".

*Ziffern*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit* -\
&nbsp;&nbsp;&nbsp;&nbsp;| *Ziffern* - *decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Ziffern* Hexziffern

*Direktiven\*
&nbsp;&nbsp;&nbsp;&nbsp;*generaldir* | *segmentdef*

*directivelist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Direktive* | *directivelist* - *Direktive*

*Entfernungs*\
&nbsp;&nbsp;&nbsp;&nbsp;*near far* | **NEAR16** | **NEAR32** | **FAR16** | **FAR32**

*E01*\
&nbsp;&nbsp;&nbsp;&nbsp;E01 *orop* *E02* | *E02*

*E02*\
&nbsp;&nbsp;&nbsp;&nbsp;E02 **und** *E03* | *E03*

*E03*\
&nbsp;&nbsp;&nbsp;&nbsp;**nicht** *E04* | *E04*

*E04*\
&nbsp;&nbsp;&nbsp;&nbsp;*E04* *RelOp* *E05* | *E05*

*E05*\
&nbsp;&nbsp;&nbsp;&nbsp;*E05* *ADDOP* *E06* | *E06*

*E06*\
&nbsp;&nbsp;&nbsp;&nbsp;*E06* *mehrop* *E07* | *E06* *shiftop* *E07* | *E07*

*E07*\
&nbsp;&nbsp;&nbsp;&nbsp;*E07* *ADDOP* *E08* | *E08*

*E08*\
&nbsp;&nbsp;&nbsp;&nbsp;**hoch** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **niedrig** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **HighWord** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **lowword** *E09*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09*

*E09*\
&nbsp;&nbsp;&nbsp;&nbsp;**Offset** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ABG** - *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **lroffset** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Typ** " *E10* "\
&nbsp;&nbsp;&nbsp;&nbsp;| **dieses** *E10* -\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* **ptr** *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E09* : *E10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E10*

\ " *E10* "
&nbsp;&nbsp;&nbsp;&nbsp;*E10* . *E11*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E10* ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *E11*

*E11*\
&nbsp;&nbsp;&nbsp;&nbsp;( *expr* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **Width** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Mask** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Größe** *sizearg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **sizeof** *sizearg*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Längen** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **lengthof** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordkonstanten*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Zeichenfolge*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Konstante*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Typ*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **$**\
&nbsp;&nbsp;&nbsp;&nbsp;| *Segmentregister*\
&nbsp;&nbsp;&nbsp;&nbsp;| *registrieren*\
&nbsp;&nbsp;&nbsp;&nbsp;| **St**\
&nbsp;&nbsp;&nbsp;&nbsp;| **St** ( *expr* )

*Echo dir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Echo**\
&nbsp;&nbsp;&nbsp;&nbsp;von " *arbiarytext* ;", \
**aus%von** " *arbiarytext* ;; \"

*ElseIf Block* -\
&nbsp;&nbsp;&nbsp;&nbsp;*elseifistatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directivelist*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifiblock* ⟧ \

*ElseIf Statement* -\
&nbsp;&nbsp;&nbsp;&nbsp;**ElseIf** *constexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseife** *constexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseifb** - *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ElseIf NB** *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ElseIf DEF** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNDEF** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ElseIf DIF** *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseifdifi** *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseifdn** *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **elseimedni** *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF2**

*enddir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Ende** ⟦ *immexpr* ⟧;;

\ " *endpdir* "
&nbsp;&nbsp;&nbsp;&nbsp;*PROCID* **ENDP** ;;

*endsdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* **endet** ;;

*equdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*textmakroid* **EQU** *equtype* ;;

*equtype* -\
&nbsp;&nbsp;&nbsp;&nbsp;*immexpr* | *textliterals*

*errordir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*erroropt* ;;

*erroropt* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Err** ⟦ *Textitem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRE** *constexpr* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNZ** *constexpr* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Errb** *Textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Errnb** *Textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Errdef** - *ID* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRNDEF** - *ID* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIF** *Textitem* , *Textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRDIFI** *Textitem* , *Textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDN** *Textitem* , *Textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERRIDNI** *Textitem* , *Textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR1** ⟦ *Textitem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ERR2** ⟦ *Textitem* ⟧

*exitdir* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Exit** &nbsp;&nbsp;&nbsp;&nbsp;⟦ *expr* ⟧;;

*exitmdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;: exitm | Exitm- *Textitem*

*Exponent*\
&nbsp;&nbsp;&nbsp;&nbsp;E ⟦ *Sign* ⟧ *decnumber*

*expr* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Short** *E05*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Typ** E01 \
&nbsp;&nbsp;&nbsp;&nbsp;| **OPATTR** *E01*\
&nbsp;&nbsp;&nbsp;&nbsp;| *E01*

*exprlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* | *exprlist* , *expr*

*EXTERNDEF* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *LangType* ⟧ *ID* ⟦ ( *altid* ) ⟧: *externtype*

*externdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*externlist* von *externkey* ;;

*externkey* -\
&nbsp;&nbsp;&nbsp;&nbsp;**EXTRN** | **extern** | **EXTERNDEF**

*externlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*EXTERNDEF* | *externlist* , ⟦;; ⟧ *EXTERNDEF*

*externtype* -\
&nbsp;&nbsp;&nbsp;&nbsp;**ABS** | *qualifiedtype*

*fieldalign* -\
&nbsp;&nbsp;&nbsp;&nbsp;*constexpr*

*FieldInit* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *initvalue* ⟧ | *structinstance*

*fieldinitlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*FieldInit* | *fieldinitlist* , ⟦;; ⟧ *FieldInit*

*filechar* -\
&nbsp;&nbsp; *&nbsp;&nbsp;* Trennzeichen

*filecharlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*filechar* | *filecharlist* *filechar*

*filespec* -\
&nbsp;&nbsp;&nbsp;&nbsp;*filecharlist* | *textliterale*

*FlagName*\
&nbsp;&nbsp;&nbsp;&nbsp;**null?** |  **?** | **Überlauf?** | **Sign?** | **Parität?**

*floatnumber* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Sign* ⟧ *decnumber* . ⟦ *decnumber* ⟧ ⟦ *Exponent* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *Ziffern* R | *Ziffern* r

*forcdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**FORC** - | **irren**

*fordir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**für** |  **.**

\ " *forparamem* "
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦: *forparamemtype* ⟧

\ " *forparamemtype* "
&nbsp;&nbsp;&nbsp;&nbsp;**req** | = *textliteral*

\ für die Aufhebung der *Registrierung*
&nbsp;&nbsp;&nbsp;&nbsp;**St.** *expr*

*frameexpr* -\
&nbsp;&nbsp; **&nbsp;&nbsp;-** *ID-ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **DGROUP** : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Segmentregister* : *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ID*

*generaldir*\
&nbsp;&nbsp;&nbsp;&nbsp;*modeldir* | *segOrderDir* der *namedir* | \
&nbsp;&nbsp;&nbsp;&nbsp;| *includelibdir* | *commentdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *groupdir* | *assumedir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structdir* | *recorddir* | *typedefdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *externdir* | *publicdir* | *kommdir* | *prototypedir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *equdir* | = Dir | *textdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;| *contextdir* | *optiondir* | *processordir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *radixdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *titledir* | *pagedir* | *listdir*\
&nbsp;&nbsp;&nbsp; *&nbsp;| " | * *Echo dir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *ifdir* | *errordir* | *includedir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *makrodir* | *makrorufe* | *macrorepeat* | *purgedir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *makrowhile* | Makro *für* | *makroforc*\
&nbsp;&nbsp;&nbsp;&nbsp;| *aliasdir*

*gpregiester* -\
&nbsp;&nbsp;&nbsp;&nbsp;AX | EAX | CX | ECX | DX | EDX | BX | Ebx | DI | EDI | Si | ESI | BP | EBP | SP | ESP | RSP | R8W | R8D | R9W | R9D | R12D | R13W | R13D | R14W | R14D

*groupdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*GroupID* - **Gruppe** " *setgidlist* "

*GroupID* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*Hexziffern*\
&nbsp;&nbsp;&nbsp;&nbsp;a | b | c | d | e | f | A | B | C | D | E | C

*ID* -\
&nbsp;&nbsp;&nbsp;&nbsp;das erste Zeichen des Bezeichners kann ein groß-oder Kleinbuchstabe (`[A–Za-z]`) oder eines der folgenden vier Zeichen sein: `@ _ $ ?` die restlichen Zeichen können ein beliebiges Zeichen oder eine Dezimal Ziffer (`[0–9]`) sein. Die maximale Länge beträgt 247 Zeichen.

*idlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* | *idlist* , *ID*

*ifdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*if-Anweisung* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directivelist*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifiblock* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **else** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directivelist* ⟧;; \

\ der *if-Anweisung*
&nbsp;&nbsp;&nbsp;&nbsp;, **Wenn** *constexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFE** *constexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFB** *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifnb** *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifdef** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifndef** - *ID*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifdif** *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifdifi** *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ifdn** - *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **imedni** *Textitem* , *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF2**

*immexpr* -\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*includedir* -\
&nbsp;&nbsp; **&nbsp;&nbsp;** *File spec* ;;

*includelibdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Includelib** - *Datei Spezifikation* ;;

*initvalue* -\
&nbsp;&nbsp;&nbsp;&nbsp;*immexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Zeichenfolge*\
&nbsp;&nbsp;&nbsp;&nbsp;|? \
&nbsp;&nbsp;&nbsp;&nbsp;| *constexpr* **DUP** ( *scalarinstlist* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *floatnumber*\
&nbsp;&nbsp;&nbsp;&nbsp;| *bcdrest*

*insegdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *labeldef* ⟧ *insegmentdir*

*insegdirlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*insegdir* | *insegdirlist* *insegdir*

*insegmentdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Anweisung*\
&nbsp;&nbsp;&nbsp;&nbsp;| *datadir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *controldir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *startupdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *exitdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *labeldir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *procdir* ⟦ *localdirlist* ⟧ ⟦ *insegdirlist* ⟧ *endpdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *invokedir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generaldir*

*instranprefix* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Rep** | **REPE** | **repz** | **REPNE** Repp | **REPNZ** | - **Sperre**

*Anweisungs*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *instrauprefix* ⟧ *asminkonstruktion*

*invokearg* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Register* :: *Register* | *expr* | **addr** *expr*

*invokedir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**aufrufen** von *expr* ⟦, ⟦;; ⟧ *invokelist* ⟧;;

*invokelist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*invokearg* | *invokelist* , ⟦;; ⟧ *invokearg*

*Schlüsselwort*\
&nbsp;&nbsp;&nbsp;alle reservierten Wörter &nbsp;.

*keywordlist* -\
&nbsp;&nbsp; *&nbsp;&nbsp;Schlüsselwort | * *Schlüsselwort* *Liste*

*labeldef* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID* : | *ID* :: | @@:

*labeldir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* - **Bezeichnung** *qualifiedtype* ;;

*LangType* -\
&nbsp;&nbsp;&nbsp;&nbsp;**C** | **Pascal** | **Fortran** | **Basic** | **syscall** | **StdCall**

*listdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*listOption* ;;

*listOption* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Listen**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. NOLIST** -\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. XLIST** -\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. ListAll** -\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Listif** -\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. LF-** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Nolistif** -\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. SFD-** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. TFD-** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Listmacroall** - |  **. Lall** -\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Nolistmacro** - |  **. Sall** -\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Listmacro** - |  **. Xall** -\

*localdef* -\
&nbsp;&nbsp;&nbsp;&nbsp;**lokalen** *idlist* ;;

*localdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**lokale** *Liste von Parametern* ;;

*localdirlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*localdir* | *localdirlist* *localdir*

*locallist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*localdef* | *locallist* *localdef*

*macroarg*\
 % *constexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*textmacroid*\
&nbsp;&nbsp;&nbsp;&nbsp;| %*macrofuncid* ( *makroarglist* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *Zeichenfolge*\
&nbsp;&nbsp;&nbsp; *&nbsp;| \*
&nbsp;&nbsp;&nbsp;&nbsp;| < von " *arbiarytext* " >

*macroarglist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*macroarg* | *makroarglist* , *macroarg*

*macrobody* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *locallist* ⟧ *macrostmtlist*

*macrocall\*
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *makroarglist* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *ID* ( *makroarglist* )

*Makro dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* - **Makro** ⟦ *makroparamemlist* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macrobody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macrofor* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Forum* *forparamem* , < *makroarglist* >;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macrobody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macroforc* -\
&nbsp;&nbsp;&nbsp;&nbsp;*forcdir* - *ID* , *textliterale* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macrobody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*makrofuncid* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*macroid*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroprocid* | *makrofuncid*

*macroidlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*macroid* | *makroidlist* , *macroid*

*Makro Label* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*makroparameminm*\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* ⟦: *Parametertyp* ⟧

*macroparamemlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*macroparameminm* | *makroparameminlist* , ⟦;; ⟧- *Makro*

*macroprocid* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*macrorepeat* -\
&nbsp;&nbsp;&nbsp;&nbsp;*repeatdir* *constexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macrobody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*macrostmt* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Direktive* \
&nbsp;&nbsp;&nbsp;&nbsp;| *exitmdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| : *Macrolabel* -\
&nbsp;&nbsp;&nbsp;&nbsp;| **goto**\
&nbsp;&nbsp;&nbsp;&nbsp;*Macrolabel*

*macrostmtlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*macrostmt* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *makrostmtlist* *macrostmt* ;; \

*makrowhile*\
&nbsp;&nbsp;&nbsp;&nbsp;, **während** *constexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*macrobody*\
&nbsp;&nbsp;&nbsp;&nbsp;**ENDM** ;;

*maptype* -\
&nbsp;&nbsp;&nbsp;&nbsp;**alle** | **keine** | **NotPublic**

*memoption* -\
&nbsp;&nbsp; **&nbsp;&nbsp;** Small | **Small** | **Medium** | **Compact** | **Large** | **HUGE** Large | **Flat**

*mnetmonisches*\
&nbsp;&nbsp;&nbsp;&nbsp;Anweisungs Name.

*modeldir* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Modell**\
&nbsp;&nbsp;&nbsp;&nbsp;*memoption* ⟦, *modeloptlist* ⟧;;

*modelopt* -\
&nbsp;&nbsp;&nbsp;&nbsp;*LangType* | *stackoption*

*modeloptlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*modelopt* | *modeloptlist* , *modelopt*

*Modul*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *directivelist* ⟧ *enddir*

*mulop* -\
&nbsp;&nbsp;&nbsp;&nbsp;\* | / | **Mod**

*namedir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Namen**\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID* ;; \

*near far*\
&nbsp;&nbsp;&nbsp;&nbsp;**nah** | **FAR**

\ von " *netstedstruct* "
&nbsp;&nbsp;&nbsp;&nbsp;*structhdr* ⟦ *ID* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structbody*\
&nbsp;&nbsp;&nbsp;&nbsp;**endet** ;; \

*offsetdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*offsetdirtype* ;;

*offsetdirtype* -\
&nbsp;&nbsp;&nbsp;&nbsp;**sogar** | **org** *immexpr* | **align** ⟦ *constexpr* ⟧

*OffsetType* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Gruppe** | **Segment** | **flach**

*oldrecordfieldlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constexpr* ⟧ | *oldrecordfieldlist* , ⟦ *constexpr* ⟧

*optiondir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**options** *Liste* ;;

*optionitem* -\
&nbsp;&nbsp;&nbsp;&nbsp;**CaseMap** : *maptype*\
&nbsp;&nbsp;&nbsp;&nbsp;| **dotname** | **nodotname**\
&nbsp;&nbsp;&nbsp;&nbsp;| - **Emulator** | **noemulator**\
&nbsp;&nbsp;&nbsp;&nbsp;| **Epilog** : *makroid*\
&nbsp;&nbsp;&nbsp;&nbsp;| **EXPR16** | **EXPR32**\
&nbsp;&nbsp;&nbsp;&nbsp;| **Sprache** : *LangType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ljmp**
| **noljmp**\
&nbsp;&nbsp;&nbsp;&nbsp;| **M510** | **NOM510**\
&nbsp;&nbsp;&nbsp;&nbsp;| **nokeyword** : < *keywordlist* >\
&nbsp;&nbsp;&nbsp;&nbsp;| **nosignextend**\
&nbsp;&nbsp;&nbsp;&nbsp;| **Offset** : *OffsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **oldmakros** | **nooldmakros**\
&nbsp;&nbsp;&nbsp;&nbsp;| **oldstructs** | **nooldstructs**\
&nbsp;&nbsp;&nbsp;&nbsp;| **proc** : *ovisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Prolog** : *makroid*\
&nbsp;&nbsp;&nbsp; **&nbsp;| Schreib geschützter** | **noreadonly**\
&nbsp;&nbsp;&nbsp; **&nbsp;|  | Bereich**\ **NOSCOPED**
&nbsp;&nbsp;&nbsp;&nbsp;| **Segment** : *segsize*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SETIF2** : bool

*optionlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*optionitem* | *optionlist* , ⟦;; ⟧ *optionitem*

*opttext* -\
&nbsp;&nbsp;&nbsp;&nbsp;, *Textitem*

*orop* -\
&nbsp;&nbsp;&nbsp;&nbsp;**oder** | **Xor**

*ovisibility* -\
&nbsp;&nbsp;&nbsp;&nbsp;**öffentlichen** | **private** | **Export**

*pagedir* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Seite** ⟦ *pageexpr* ⟧;;

*pageexpr* -\
&nbsp;&nbsp;&nbsp;&nbsp;\+ | ⟦ *pagelength* ⟧ ⟦, *PageWidth* ⟧

*pagelength* -\
&nbsp;&nbsp;&nbsp;&nbsp;*constexpr*

*PageWidth*\
&nbsp;&nbsp;&nbsp;&nbsp;*constexpr*

*\ für* den
&nbsp;&nbsp; *&nbsp;&nbsp;⟦* : *qualifiedtype* ⟧ | *Parser* ⟦ *constexpr* ⟧ ⟦: *qualifiedtype* ⟧

*\ der*
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

\ "Element *auflisten* "
&nbsp;&nbsp; *&nbsp;&nbsp;von* " *paramemlist* " | "⟦;;". ⟧ *-* Element

*ParameterType* -\
&nbsp;&nbsp;&nbsp;&nbsp;**req** | = *textliterale* | **vararg**

*poptions* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Distance* ⟧ ⟦ *LangType* ⟧ ⟦ *ovisibility* ⟧

*primärer*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* *BinaryOp* *expr* | *FlagName* | *expr*

\ *procdir*
&nbsp;&nbsp;&nbsp;&nbsp;*PROCID* **proc**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *poptions* ⟧ ⟦ < *makroarglist* > ⟧ \
&nbsp;&nbsp;&nbsp; *&nbsp;⟦-* ) ⟧ ⟦ *procparamemlist* ⟧

*Prozessor*\
&nbsp;&nbsp;&nbsp;&nbsp;|. 386 |. 386p |. 486 |. 486p \
&nbsp;&nbsp;&nbsp;&nbsp;|. 586 |. 586p |. 686 |. 686p |. 387

*processordir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Prozessor* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *Coprozessor* ;;

*PROCID* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*procitem* -\
&nbsp;&nbsp;&nbsp;&nbsp;*instrinprefix* | *datadir* | *labeldir* | *offsetdir* | *generaldir*

*procparamemlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *paramemlist* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧- *Parser* : vararg ⟧

*protoarg* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *ID* ⟧: *qualifiedtype*

*protoarglist* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ *protolist* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, ⟦;; ⟧ ⟦ *ID* ⟧: vararg ⟧

*protolist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*protoarg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *protolist* , ⟦;; ⟧ *protoarg*

*protospec* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Distance* ⟧ ⟦ *LangType* ⟧ ⟦ *protoarglist* ⟧ | *typeid*

*prototypedir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* **Proto** *protospec*

*pubdef* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *LangType* ⟧ *ID*

*publicdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Public** *publist* ;;

*publist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*pubdef* | *publist* , ⟦;; ⟧ *pubdef*

\ *purgedir*
&nbsp;&nbsp; **&nbsp;&nbsp;"** *macroidlist* " Löschen

*qualifiedtype* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Typ* | ⟦ *Distance* ⟧ **ptr** ⟦ *qualifiedtype* ⟧

*Qualifizierer*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedtype* | **Proto** *protospec*

*Anführungs* Zeichen\
&nbsp;&nbsp;&nbsp;&nbsp;"|"

*qwordregister* -\
&nbsp;&nbsp;&nbsp;&nbsp;Rax | RCX | RDX | RBX | RDI | RSI | RBP | R8 | R9 | R10 | R11 | R12 | R13 | R14 | R15

*radixdir* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Radix** *constexpr* ;;

*radixoverride* -\
&nbsp;&nbsp;&nbsp;&nbsp;h | o | q | t | j | H | O | Q | T | Teenie

*recordkonstanten*\
&nbsp;&nbsp;&nbsp;&nbsp;*recordtag* { *oldrecordfieldlist* } | *recordtag* < *oldrecordfieldlist* - >

*recorddir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*recordtag* - **Datensatz** *bitdeflist* ;;

*recordfieldlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constexpr* ⟧ | *recordfieldlist* , ⟦;; ⟧ ⟦ *constexpr* ⟧

*recordinstance*\
 {⟦;; ⟧ *recordfieldlist* ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| < *oldrecordfieldlist* - >\
&nbsp;&nbsp;&nbsp;&nbsp;| *constexpr* **DUP** ( *neuordinstance* )

*recordinstlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*recordinstance* | *recordinstlist* , ⟦;; ⟧- *neuordinstance*

*recordtag*\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

\ *registrieren*
&nbsp;&nbsp;&nbsp;&nbsp;*specialregister* | *gpregister* | *byteregister* | *qwordregister* |  *fpuregister* | *simdregister* | *Segmentregister*

*reglist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*registrieren* | *reglist* - *Register*

*RelOp* -\
&nbsp;&nbsp;&nbsp;&nbsp;EQ | NE | LT | Le | GT | Färbung

*repeatblock* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Wiederholen** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockstatements* ;; untildir;;

*repeatdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**wiederholen** | **rept**

*scalarinstlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*initvalue* | *scalarinstlist* , ⟦;; ⟧ *initvalue*

*segalign*\
&nbsp;&nbsp;&nbsp;**Byte** ** | ** **Word** | Seite ** |  | ** **Seite** &nbsp;

*segattrb* -\
&nbsp;&nbsp;&nbsp;&nbsp;**öffentliche** | **Stapel** | **allgemeiner** | **Speicher** | **bei** *constexpr* | **Privat**

*segdir* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Code**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Segid* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Daten**\
&nbsp;&nbsp;&nbsp;&nbsp;|   **. Daten?** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.** Konstante\
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Fardata**⟦ *Segid* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|   **. Fardata?** ⟦ *Segid* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **. Stack** ⟦ *constexpr* ⟧

*\ der*
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*segIdList* Einstellungs\
&nbsp;&nbsp;&nbsp;\ *&nbsp;*
&nbsp;&nbsp;&nbsp;&nbsp;| " *abgidlist* ", " *ggid* "

*segmentdef* -\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentdir* ⟦ *insegdirlist* ⟧ *endsdir* | *simplesegdir* ⟦ *insegdirlist* ⟧ ⟦ *endsdir* ⟧

*segmentdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Segid* - **Segment** ⟦ *segoptionlist* ⟧;;

*Segmentregister* -\
&nbsp;&nbsp;&nbsp;&nbsp;**CS** | **DS** es | **es** | **FS** | **GS** | **SS**

*segoption*\
&nbsp;&nbsp;&nbsp;&nbsp;*segalign*\
&nbsp;&nbsp;&nbsp; *&nbsp;| -\*
&nbsp;&nbsp;&nbsp;&nbsp;| *segattrb*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segsize*\
&nbsp;&nbsp;&nbsp;&nbsp;| *className*

*segoptionlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*segoption* | *segoptionlist* *segoption*

\ für " *abgorderdir* "
&nbsp;&nbsp;&nbsp;&nbsp; **. Alpha** |  **.** Der- |  **. Dosseg** - | **dosseg**

*\*
&nbsp;&nbsp; **&nbsp;&nbsp;Schreib** geschützt

*segsize* -\
&nbsp;&nbsp;&nbsp;&nbsp;**USE16** | **USE32** | **Flat**

*shiftop* -\
&nbsp;&nbsp;&nbsp;&nbsp;**SHR** | **SHL**

\ *Signieren*
 - | +

*simdregister* -\
&nbsp;&nbsp;&nbsp;&nbsp;mm0 | MM1 | Mm2 | MM3 | MM4 | MM5 | MM6 | MM7 | xmmregister | YMM0 | YMM1 | YMM2 | YMM3 | YMM4 | YMM5 | YMM6 | YMM7 | YMM8 | YMM9 | YMM10 | YMM11 | YMM12 | YMM13 | YMM14 | YMM15

*simpleexpr* -\
 ( *cexpr* ) | *primär*

*simplesegdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*segdir* ;;

*sizearg* -\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* | *Typ* | *E10*

*SpecialChars*\
 : | . | ⟦ | ⟧ | ( | ) | < | > | { | } \
&nbsp;&nbsp;&nbsp;&nbsp;| + | - | / | * | & | % | !\
&nbsp;&nbsp;&nbsp;&nbsp;| "| \ | = | ; | , | "\
&nbsp;&nbsp;&nbsp;&nbsp;| *whitespacecharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;| *endosline*

*specialregister* -\
&nbsp;&nbsp;&nbsp;&nbsp;CR0 | CR2 | CR3 | DR0 | DR1 | DR2 | DR3 | DR6 | DR7 | TR3 | TR4 | TR5 | TR6 | TR7

*stackoption* -\
&nbsp;&nbsp;&nbsp;&nbsp;**nearstack** - | **farstack**

*startupdir* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Wird gestartet** ;;

*sText* -\
&nbsp;&nbsp;&nbsp;&nbsp;*StringChar* | *sText* *StringChar*

*string*\
&nbsp;&nbsp;&nbsp;&nbsp;*Quote* ⟦ *sText* ⟧ *Zitat*

*StringChar* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Anführungs* *Zeichen |* Beliebiges Zeichen außer Anführungszeichen.

*structbody* -\
&nbsp;&nbsp;&nbsp;&nbsp;*structitem* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *structbody* *structitem* ;;

*structdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*structtag* *structhdr* ⟦ *fieldalign* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦, **nicht eindeutig** ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structbody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structtag*\
&nbsp;&nbsp;&nbsp;&nbsp;**endet** ;;

*structhdr* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Struc** | **struct** | **Union**

*structinstance* -\
 < ⟦ *fieldinitlist* ⟧ > \
&nbsp;&nbsp;&nbsp;&nbsp;| {⟦;; ⟧ ⟦ *fieldinitlist* ⟧ ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| *constexpr* **DUP** ( *structinstlist* ) \

*structinstlist* -\
&nbsp;&nbsp;&nbsp;&nbsp;*structinstance* | *structinstlist* , ⟦;; ⟧ *structinstance*

*structitem* -\
&nbsp;&nbsp;&nbsp;&nbsp;*datadir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *generaldir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| - *Struktur*

*structtag* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*Term*\
&nbsp;&nbsp;&nbsp;&nbsp;*simpleexpr* |! *simpleexpr*

*text*\
&nbsp;&nbsp;&nbsp;&nbsp;*textliterale* | *Textzeichen* |! *Zeichen* *Text* | *Zeichen* |! *Zeichen*

*textdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*ID* *textmacrodir* ;;

*Textitem* -\
&nbsp;&nbsp;&nbsp;&nbsp;*textliterale* | *textmacroid* | % *constexpr*

*textlen* -\
&nbsp;&nbsp;&nbsp;&nbsp;*constexpr*

*TextList* -\
&nbsp;&nbsp;&nbsp;&nbsp;*Textitem* | *TextList* , ⟦;; ⟧ *Textitem*

*textliterale*\
&nbsp;&nbsp;&nbsp;&nbsp;< *Text* >;;

*textmacrodir* -\
&nbsp;&nbsp; **&nbsp;&nbsp;⟦** *TextList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **TEXTEQU** ⟦ *TextList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **sizestr** *Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **substr** *Textitem* , *TextStart* ⟦, *textlen* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **InStr** ⟦ *TextStart* , ⟧ *Textitem* , *Textitem*

*textmacroid* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*TextStart* -\
&nbsp;&nbsp;&nbsp;&nbsp;*constexpr*

*titledir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*titletype* - *Text* ;;

*titletype* -\
&nbsp;&nbsp;&nbsp;&nbsp;**Titel** | unter **Titel** | **SUBTTL**

*Typ*\
&nbsp;&nbsp;&nbsp;&nbsp;*structtag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *uniontag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *recordtag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Entfernung*\
&nbsp;&nbsp;&nbsp;&nbsp;| *DataType*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeid*

*typedefdir* -\
&nbsp;&nbsp;&nbsp;&nbsp;*typeid* - **typedef** -Qualifizierer

*typeid* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*uniontag* -\
&nbsp;&nbsp;&nbsp;&nbsp;- *ID*

*untildir* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Bis** *cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. UNTILCXZ** ⟦ *cxzexpr* ⟧;;

*\ "* "
&nbsp;&nbsp;&nbsp;&nbsp;**verwendet** *reglist*

*whileblock* -\
&nbsp;&nbsp;&nbsp;&nbsp; **. Während** der\
&nbsp;&nbsp;&nbsp;&nbsp;*cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*blockstatements* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **. Endw**

*whitespacecharacter* -\
&nbsp;&nbsp;&nbsp;&nbsp;ASCII 8, 9, 11 – 13, 26, 32

*xmmregister* -\
&nbsp;&nbsp;&nbsp;&nbsp;XMM0 | XMM1 | XMM2 | XMM3 | XMM4 | Xmm5 | XMM6 | Xmm7 | XMM8 | XMM9 | XMM10 | XMM11 | XMM12 | XMM13 | XMM14 | XMM15\
