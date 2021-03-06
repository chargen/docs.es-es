---
title: 'Cómo: Escribir texto en archivos con un objeto StreamWriter en Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 4cb589125286082b9c7d5886a51b0ef8d998474e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Cómo: Escribir texto en archivos con un objeto StreamWriter en Visual Basic
Este ejemplo abre un objeto <xref:System.IO.StreamWriter> con el método `My.Computer.FileSystem.OpenTextFileWriter` y lo usa para escribir una cadena en un archivo de texto con el método <xref:System.IO.TextWriter.WriteLine%2A> de la clase <xref:System.IO.StreamWriter>.  
  
## <a name="example"></a>Ejemplo  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a>Programación sólida  
 Las condiciones siguientes pueden provocar una excepción:  
  
-   El archivo ya existe y es de solo lectura (<xref:System.IO.IOException>).  
  
-   El disco está lleno (<xref:System.IO.IOException>).  
  
-   El nombre de la ruta de acceso es demasiado largo (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 En este ejemplo se crea un nuevo archivo, si este no existe aún. Si una aplicación necesita crear un archivo, precisará acceso `Create` para la carpeta. Si el archivo ya existe, la aplicación necesitará solo acceso `Write`, un privilegio menor. Siempre que sea posible, resulta más seguro crear el archivo durante la implementación y conceder solo acceso `Read` a un único archivo, en lugar de acceso `Create` para una carpeta.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [Leer de archivos de texto](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [Escritura en archivos](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
