---
title: 'Cómo: buscar la diferencia de conjuntos entre dos listas (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: 77ff74788adddcd28e23028b034cd682f2d94233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Cómo: buscar la diferencia de conjuntos entre dos listas (LINQ) (Visual Basic)
En este ejemplo se muestra cómo usar LINQ para comparar dos listas de cadenas y generar estas líneas, que están en names1.txt pero no en names2.txt.  
  
### <a name="to-create-the-data-files"></a>Para crear los archivos de datos  
  
1.  Copie names1.txt y names2.txt en la carpeta de soluciones, como se muestra en [Cómo: combinar y comparar cadena colecciones (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Ejemplo  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 Algunos tipos de consulta operaciones en Visual Basic, como <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, y <xref:System.Linq.Enumerable.Concat%2A>, sólo se pueden expresar en sintaxis de método.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Cree un proyecto que tenga como destino la versión 3.5 de .NET Framework, o bien una posterior, con una referencia a System.Core.dll y una instrucción `Imports` para el espacio de nombres System.Linq.  
  
## <a name="see-also"></a>Vea también  
 [LINQ y cadenas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
