---
title: 'Como: preencher uma forma com uma textura de imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911682"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Como: preencher uma forma com uma textura de imagem
Você pode preencher uma forma fechada com uma textura usando a <xref:System.Drawing.Image> classe e a <xref:System.Drawing.TextureBrush> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir preenche uma elipse com uma imagem. O código constrói um <xref:System.Drawing.Image> objeto e, em seguida, passa o endereço <xref:System.Drawing.Image> desse objeto como um argumento para um <xref:System.Drawing.TextureBrush.%23ctor%2A> Construtor. A terceira instrução redimensiona a imagem e a quarta instrução preenche a elipse com repetidas cópias da imagem dimensionada.  
  
 No código a seguir, a <xref:System.Drawing.TextureBrush.Transform%2A> propriedade contém a transformação que é aplicada à imagem antes de ser desenhada. Suponha que a imagem original possui uma largura de 640 pixels e uma altura de 480 pixels. A transformação reduz a imagem a 75 × 75 configurando os valores de colocação em escala horizontal e vertical.  
  
> [!NOTE]
> No exemplo a seguir, o tamanho da imagem é 75 × 75 e o tamanho da elipse é 150 × 250. Como a imagem é menor do que a elipse que ela está preenchendo, a elipse é organizada lado a lado com a imagem. Lado a lado significa que a imagem é repetida horizontal e verticalmente até o limite da forma ser atingido. Para obter mais informações sobre divisão, [consulte Como: Dividir uma forma com uma imagem](how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que <xref:System.Windows.Forms.Control.Paint> é um parâmetro do manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Usando um pincel para preencher formas](using-a-brush-to-fill-shapes.md)
