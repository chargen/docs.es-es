---
title: IMetaDataAssemblyEmit::DefineManifestResource (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48d688b64bbe9330a176ef073e96865b719ff2c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource (Método)
Crea una estructura `ManifestResource` que contiene los metadatos para el recurso de manifiesto especificado y devuelve el token de metadatos asociado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szName`  
 [in] El nombre del recurso.  
  
 `tkImplementation`  
 [in] Un token de metadatos del tipo `mdtFile` o `mdtAssemblyRef` que se asigna al proveedor de recursos. Un valor NULL indica que el archivo en el que se incrustan los metadatos es el proveedor de recursos.  
  
 `dwOffset`  
 [in] El desplazamiento al principio del recurso dentro del archivo. Para obtener recursos en archivos independientes, siempre será cero. Si el recurso está incrustado en un archivo de PE (ejecutable portable), esto es un desplazamiento del recurso BLOB, que comienza en la ubicación especificada en el archivo de encabezado cor.h.  
  
 `dwResourceFlags`  
 [in] Una combinación bit a bit de valores de indicador que especifican los valores de propiedad para la definición de recursos.  
  
 `pmdmr`  
 [out] Un puntero al token de metadatos devuelto.  
  
## <a name="remarks"></a>Comentarios  
 Una `ManifestResource` se debe definir la estructura de los metadatos para cada recurso que se implementa en cada uno de los archivos del ensamblado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Cor.h  
  
 **Biblioteca:** usada como recurso en MsCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [IMetaDataAssemblyEmit (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
