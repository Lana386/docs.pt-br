---
title: Source Link e bibliotecas .NET
description: Recomendações de melhores práticas de uso do Source Link para melhorar a depuração de bibliotecas .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744544"
---
# <a name="source-link"></a>Source Link

O Source Link é uma tecnologia que permite a depuração de código-fonte dos assemblies .NET do NuGet por desenvolvedores. O Source Link é executado durante a criação do pacote NuGet e insere os metadados de controle do código-fonte nos assemblies e no pacote. Os desenvolvedores que baixam o pacote e têm o Source Link habilitado no Visual Studio podem intervir no código-fonte. O Source Link fornece metadados de controle do código-fonte para criar uma ótima experiência de depuração.

## <a name="source-link-demo"></a>Demonstração do Source Link

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Usando o Source Link

Encontre instruções sobre como usar o Source Link no repositório GitHub [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).

Use o [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) para confirmar que os metadados do Source Link foram inseridos com êxito no pacote. Verifique `Repository` se os metadados estão presentes com um identificador de confirmação e se os arquivos .pdb estão localizados com o .dll de cada destino.

![Link de origem no NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Link de origem no NuGet Package Explorer")

✔️ CONSIDERE o uso do Source Link para adicionar metadados de controle do código-fonte aos assemblies e pacotes NuGet.

> [!TIP]
> Você ainda pode aprimorar a experiência de depuração do desenvolvedor com a adição de atributos do depurador aos seus tipos.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> pode personalizar como uma classe ou campo é exibido nas janelas de variáveis do depurador.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> instrui o depurador a depurar o código em vez de intervir nele.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> controla se um membro é exibido nas janelas de variáveis do depurador.

✔️ CONSIDERE publicar arquivos de símbolo (`*.pdb`).

> Para proporcionar a melhor experiência de depuração, a biblioteca deverá publicar arquivos de símbolo, além de usar o Source Link. Para obter mais informações sobre arquivos de símbolo e pacotes de símbolos, confira [Pacotes de símbolos](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Próximo](dependencies.md)
>[anterior](publish-nuget-package.md)
