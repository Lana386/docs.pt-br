---
title: Modificar DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3e811410ea9fdd4be0cbd84b895483f69f58b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786049"
---
# <a name="modifying-dataviews"></a>Modificar DataViews
Você pode usar o <xref:System.Data.DataView> para adicionar, excluir ou modificar linhas de dados na tabela subjacente. A capacidade de usar o **DataView** para modificar os dados na tabela subjacente é controlada definindo uma das três propriedades booleanas do **DataView**. Essas propriedades são <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>e <xref:System.Data.DataView.AllowDelete%2A>. Eles são definidos como **true** por padrão.  
  
 Se **AllowNew** for **true**, você poderá usar o <xref:System.Data.DataView.AddNew%2A> método do **DataView** para criar um novo <xref:System.Data.DataRowView>. Observe que uma nova linha não é realmente adicionada ao subjacente <xref:System.Data.DataTable> até que o <xref:System.Data.DataRowView.EndEdit%2A> método de **DataRowView** seja chamado. Se o <xref:System.Data.DataRowView.CancelEdit%2A> método de **DataRowView** for chamado, a nova linha será descartada. Observe também que você pode editar apenas um **DataRowView** de cada vez. Se você chamar o método **AddNew** ou **BeginEdit** do **DataRowView** enquanto existir uma linha pendente, **EndEdit** será implicitamente chamado na linha pendente. Quando **EndEdit** é chamado, as alterações são aplicadas à **DataTable** subjacente e, posteriormente, podem ser confirmadas ou rejeitadas usando os métodos **AcceptChanges** ou **RejectChanges** do **DataTable**, **DataSet**ou  **Objeto DataRow** . Se **AllowNew** for **false**, uma exceção será gerada se você chamar o método **AddNew** do **DataRowView**.  
  
 Se **AllowEdit** for **true**, você poderá modificar o conteúdo de uma **DataRow** por meio de **DataRowView**. Você pode confirmar as alterações na linha subjacente usando **DataRowView. EndEdit** ou rejeitar as alterações usando **DataRowView. CancelEdit**. Observe que apenas uma linha pode ser editada por vez. Se você chamar os métodos **AddNew** ou **BeginEdit** de **DataRowView** enquanto houver uma linha pendente, **EndEdit** será implicitamente chamado na linha pendente. Quando **EndEdit** é chamado, as alterações propostas são colocadas na versão da linha **atual** da **DataRow** subjacente e, posteriormente, podem ser confirmadas ou rejeitadas usando os métodos **AcceptChanges** ou **RejectChanges** do  **Objeto DataTable**, **DataSet**ou **DataRow** . Se **AllowEdit** for **false**, uma exceção será lançada se você tentar modificar um valor no **DataView**.  
  
 Quando um **DataRowView** existente estiver sendo editado, os eventos da **DataTable** subjacente ainda serão gerados com as alterações propostas. Observe que, se você chamar **EndEdit** ou **CancelEdit** na **DataRow**subjacente, as alterações pendentes serão aplicadas ou canceladas, independentemente de **EndEdit** ou **CancelEdit** ser chamado no **DataRowView**.  
  
 Se **AllowDelete** for **true**, você poderá excluir linhas do **DataView** usando o método **delete** do objeto **DataView** ou **DataRowView** e as linhas serão excluídas da **DataTable**subjacente. Posteriormente, você poderá confirmar ou rejeitar as exclusões usando **AcceptChanges** ou **RejectChanges** , respectivamente. Se **AllowDelete** for **false**, uma exceção será lançada se você chamar o método **delete** do **DataView** ou **DataRowView**.  
  
 O exemplo de código a seguir desabilita o uso de **DataView** para excluir linhas e adiciona uma nova linha à tabela subjacente usando **DataView**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
