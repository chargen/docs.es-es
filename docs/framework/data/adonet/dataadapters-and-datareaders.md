---
title: Objetos DataAdapter y DataReader
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 7fd7013478bbf30c2a7e915045e3dd192ca92540
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="dataadapters-and-datareaders"></a>Objetos DataAdapter y DataReader
Puede usar ADO.NET **DataReader** para recuperar un flujo de datos de solo avance de solo lectura de una base de datos. Resultados se devuelven cuando se ejecuta la consulta y se almacenan en el búfer de red en el cliente hasta que se solicitan con el **lectura** método de la **DataReader**. Mediante el **DataReader** puede aumentar el rendimiento de la aplicación mediante la recuperación de datos tan pronto como está disponible y (de forma predeterminada) almacenar solo una fila cada vez en la memoria, reducir la sobrecarga del sistema.  
  
 Un <xref:System.Data.Common.DataAdapter> se utiliza para recuperar datos de un origen de datos y llenar tablas con un <xref:System.Data.DataSet>. `DataAdapter` también resuelve los cambios realizados en `DataSet` de vuelta al origen de datos. Mediante el objeto `DataAdapter` del proveedor de datos .NET Framework, `Connection` se conecta a un origen de datos y utiliza objetos `Command` para recuperar datos del origen de datos y resolver los cambios a dicho origen.  
  
 Cada proveedor de datos .NET Framework incluido con .NET Framework tiene un objeto <xref:System.Data.Common.DbDataReader> y un objeto <xref:System.Data.Common.DbDataAdapter>, el proveedor de datos .NET Framework para OLE DB incluye un objeto <xref:System.Data.OleDb.OleDbDataReader> y un objeto <xref:System.Data.OleDb.OleDbDataAdapter>, el proveedor de datos .NET Framework para SQL Server incluye un objeto <xref:System.Data.SqlClient.SqlDataReader> y un objeto <xref:System.Data.SqlClient.SqlDataAdapter>, el proveedor de datos .NET Framework para ODBC incluye un objeto <xref:System.Data.Odbc.OdbcDataReader> y un objeto <xref:System.Data.Odbc.OdbcDataAdapter>, y el proveedor de datos .NET Framework para Oracle incluyes un objeto <xref:System.Data.OracleClient.OracleDataReader> y un objeto <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
## <a name="in-this-section"></a>En esta sección  
 [Recuperación de datos utilizando un objeto DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 Describe ADO.NET **DataReader** objeto y cómo utilizarlo para devolver una secuencia de resultados desde un origen de datos.  
  
 [Rellenar un conjunto de datos desde un objeto DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Describe cómo llenar un `DataSet`  de tablas, columnas y filas mediante un `DataAdapter`.  
  
 [Parámetros de DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Describe cómo utilizar parámetros con las propiedades de comando de `DataAdapter`, lo que incluye cómo asignar el contenido de una columna de `DataSet` a un parámetro de comando.  
  
 [Agregar restricciones existentes a un conjunto de datos](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Describe cómo agregar restricciones existentes a un `DataSet`.  
  
 [Correspondencias de DataTable y DataColumn en un objeto DataAdapter](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Describe cómo configurar `DataTableMappings` y `ColumnMappings` para `DataAdapter`.  
  
 [Paginación de un resultado de consulta](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Proporciona un ejemplo de cómo ver los resultados de una consulta como páginas de datos.  
  
 [Actualizar orígenes de datos con objetos DataAdapter](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Describe cómo se utiliza `DataAdapter` para resolver modificaciones en `DataSet` en la base de datos.  
  
 [Control de eventos de DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 Describe los eventos de `DataAdapter` y cómo utilizarlos.  
  
 [Realización de operaciones por lotes utilizando objetos DataAdapter](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Describe cómo mejorar el rendimiento de la aplicación mediante la reducción del número de viajes de ida y vuelta (round trip) al servidor SQL Server al aplicar las actualizaciones desde el `DataSet`.  
  
## <a name="see-also"></a>Vea también  
 [Conexión a un origen de datos](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Comandos y parámetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Transacciones y simultaneidad](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Objetos DataSet, DataTable y DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Proveedores administrados de ADO.NET y Centro para desarrolladores de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
