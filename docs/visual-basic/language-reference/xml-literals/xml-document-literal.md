---
title: Literal de documento XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: db77cccd26c87e271d6db45ce514ab6dabbc53e3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349379"
---
# <a name="xml-document-literal-visual-basic"></a>Literal de documento XML (Visual Basic)
Um literal que representa um objeto <xref:System.Xml.Linq.XDocument>.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`encoding`|Opcional. Texto literal que declara a codificação usada pelo documento.|  
|`standalone`|Opcional. Texto literal. Deve ser "Yes" ou "no".|  
|`piCommentList`|Opcional. Lista de instruções de processamento XML e comentários XML. Usa o seguinte formato:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Cada `piComment` pode ser um dos seguintes:<br /><br /> [literal de instrução de processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)-   .<br />[literal de comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)-   .|  
|`rootElement`|Necessária. Elemento raiz do documento. O formato é um dos seguintes:<br /><br /> <ul><li>[Literal de elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Expressão inserida do formulário `<%=` `elementExp` `%>`. O `elementExp` retorna um dos seguintes:<br /><br /> <ul><li>Um objeto <xref:System.Xml.Linq.XElement>.</li><li>Uma coleção que contém um objeto <xref:System.Xml.Linq.XElement> e qualquer número de objetos <xref:System.Xml.Linq.XProcessingInstruction> e <xref:System.Xml.Linq.XComment>.</li></ul></li></ul><br /> Para obter mais informações, consulte [expressões inseridas em XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Valor retornado  
 Um objeto <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Comentários  
 Um literal de documento XML é identificado pela declaração XML no início do literal. Embora cada literal de documento XML deva ter exatamente um elemento XML raiz, ele pode ter qualquer número de instruções de processamento XML e comentários XML.  
  
 Um literal de documento XML não pode aparecer em um elemento XML.  
  
> [!NOTE]
> Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Isso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.  
  
 O compilador de Visual Basic converte o literal de documento XML em chamadas para os construtores <xref:System.Xml.Linq.XDocument.%23ctor%2A> e <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um documento XML que tem uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [Literal de Instrução de Processamento XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [Literal de Comentário XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Literal do Elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Expressões Inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
