---
layout: default
title: "IB-BIM Visibility Manager — Guía del Usuario"

---

<div align="right" style="margin: 4px 0 6px 0;">
  <img src="../Images/IB-BIM_200X200.png" alt="IB-BIM" width="150" style="display:block;">
</div>


## Acerca del Complemento

Texto introductorio breve que explica qué hace Visibility Manager,
para quién es y qué problemas resuelve.

📺 **[Ver Tutorial en Video en YouTube](https://youtu.be/68-bxWQfsUg)** ← ¡Vea la herramienta en acción!

👉 **[Ir a la Guía Paso a Paso Completa](#complete-step-by-step-guide)**

---

## Guía Paso a Paso Completa {#complete-step-by-step-guide}


**Versión 1.0.0 | Última Actualización: Noviembre 2025**

## 📑 Tabla de Contenidos
- [Primeros Pasos](#getting-started)
- [Instalación](#installation)
- [Iniciar la Herramienta](#launching-the-tool)
- [Descripción de la Interfaz](#interface-overview)
- [Trabajar con Filtros](#working-with-filters)
  - [Copiar Filtros](#copying-filters-between-views)
  - [Eliminar Filtros](#removing-filters-from-views)
  - [Exportar Filtros](#exporting-filters)
  - [Importar Filtros](#importing-filters)
- [Trabajar con Anulaciones VG](#working-with-vg-overrides)
  - [Categorías Soportadas](#supported-categories)
  - [Copiar Anulaciones VG](#copying-vg-overrides)
  - [Eliminar Anulaciones VG](#removing-vg-overrides)
  - [Exportar Anulaciones VG](#exporting-vg-overrides)
  - [Importar Anulaciones VG](#importing-vg-overrides)
- [Funciones Avanzadas](#advanced-features)
- [Flujos de Trabajo Reales](#real-world-workflows)
- [Solución de Problemas](#troubleshooting)

---

# Primeros Pasos {#getting-started}

## Instalación {#installation}

### Requisitos:
- Revit **2023, 2024, 2025 o 2026**
- Windows 10 o posterior
- Suscripción activa (prueba gratuita de 30 días disponible)

### Pasos de Instalación:

#### Descargar desde Autodesk App Store:
1. Abrir Autodesk App Store en su navegador
2. Buscar **"Visibility Manager"**
3. Hacer clic en **"Start Trial"** o **"Subscribe"**

#### Instalación Automática:
- App Store descarga e instala automáticamente
- Reiniciar Revit después de la instalación

### Verificar Instalación:
1. Abrir Revit
2. Buscar la pestaña **IB-BIM** en la cinta
3. Debería ver el botón **Visibility Manager**

### Ubicación de Instalación:
- La herramienta se instala en:
  `C:\ProgramData\Autodesk\ApplicationPlugins\`
- Archivos de registro guardados en:
  `C:\ProgramData\IB-BIM\VisibilityManager\Logs\`

---

# Iniciar la Herramienta {#launching-the-tool}

## Dos Formas de Iniciar:

### Método 1: Desde la Cinta
1. Hacer clic en la pestaña **IB-BIM**
2. Hacer clic en el botón **Visibility Manager**

### Método 2: Desde la Pestaña Add-Ins
1. Ir a la pestaña **Add-Ins**
2. Buscar **External Tools**
3. Hacer clic en **Visibility Manager**

> **Nota:** Debe tener una **vista abierta**.
> La herramienta funciona en la **vista activa actual**.

---

# Descripción de la Interfaz {#interface-overview}

Al iniciar Visibility Manager, verá una ventana dividida en tres secciones principales:

```
┌──────────────────────────────────────────────────────┐
│     Copiar/Eliminar Filtros y Anulaciones VG          │
│     Elija elementos de la vista actual y aplique a    │
│     los destinos seleccionados                        │
├─────────────┬─────────────┬──────────────────────────┤
│ ❶ Origen   │ ❷ Vistas   │ ❸ Plantillas Destino     │
│   (Actual)  │   Destino   │                          │
└─────────────┴─────────────┴──────────────────────────┘
```


![Interfaz Modo Filtros](../Images/Filter%20Screen.png)
*Figura 1: Interfaz modo filtros – mostrando el panel de Filtros activo (verde).*

![Interfaz Anulaciones VG](../Images/VG%20Screen.png)
*Figura 2: Modo Anulaciones V/G – mostrando el panel de Anulaciones activo (azul).*

Este panel muestra elementos de su **vista activa actual**:

- **Botones de radio en la parte superior:**
  - ⦿ **Filters** - Trabajar con filtros de visibilidad
  - ○ **V/G Overrides** - Trabajar con anulaciones gráficas de categorías

- **Descripción del modo:**
  - Explica qué hace el modo actual
  - Referencia los paneles [2] y [3] como destinos

- **Cuadro de búsqueda:**
  - Filtrar la lista por nombre
  - Filtrado en tiempo real al escribir

- **Casilla Seleccionar Todo:**
  - Marcar/desmarcar todos los elementos visibles

- **Lista de elementos:**
  - Muestra todos los filtros o anulaciones VG en la vista actual
  - Casillas de verificación para seleccionar elementos

- **Contador inferior:**
  - "X filters selected" o "X categories selected"

**Código de colores:**
- **Fondo verde** = Modo Filtros
- **Fondo azul claro** = Modo Anulaciones V/G

---

#### **Panel ❷: Elegir Vistas Destino (Centro)**

Seleccione a qué vistas aplicar los cambios:

- **Filtros de tipo de vista (Superior):**
  - ☑ 3D Views (10) - El número muestra el total en el proyecto
  - ☐ Floor Plans (7)
  - ☐ Elevations (4)
  - ☐ Ceiling Plans (2)
  - Marque un tipo para mostrar solo esas vistas

- **Contador total:**
  - Muestra el conteo filtrado

- **Seleccionar Todo:**
  - Selecciona todas las vistas visibles en la lista

- **Cuadro de búsqueda:**
  - Filtrar vistas por nombre

- **Lista de vistas:**
  - Todas las vistas del proyecto (filtradas por selecciones de tipo)
  - Formato: "ViewType: View Name"
  - Ejemplo: "3D: 3D View: A10 - Substructure"

---

#### **Panel ❸: Elegir Plantillas Destino (Derecha)**

Seleccione a qué plantillas de vista aplicar los cambios:

- **Filtros de tipo de plantilla (Superior):**
  - ☑ Floor Plans (2)
  - ☐ Sections (2)
  - ☐ 3D Views (1)
  - ☐ Ceiling Plans (0)
  - ☐ Elevations (0)

- **Cuadro de búsqueda:**
  - Filtrar plantillas por nombre

- **Seleccionar Todo:**
  - Selecciona todas las plantillas visibles

---

#### **Botones de Acción (Parte inferior de la ventana)**

**Lado izquierdo — Exportar/Importar:**
```
Export current view Filters        [EXPORT] [XLSX]
Import Filters to current view     [IMPORT]
```

- **EXPORT** - Crea archivo .XLSX (y .PAT si es necesario)
- **XLSX** - Crea archivo .CSV en su lugar
- **IMPORT** - Importar desde archivo previamente exportado

**Lado derecho — Copiar/Eliminar:**
```
Copy to selected targets    [COPY] (botón verde)
Remove from selected       [REMOVE] (botón naranja/rojo)
                          [Cancel]
```

- **COPY** - Copiar elementos seleccionados del Panel ❶ a Paneles ❷+❸
- **REMOVE** - Eliminar elementos seleccionados de Paneles ❷+❸
- **Cancel** - Cerrar ventana sin cambios

---

### Conceptos Básicos

#### **Vista Actual = Referencia**

**Comprensión clave:**
- La vista abierta al iniciar la herramienta es su **vista de referencia**
- El Panel ❶ siempre muestra elementos de esta vista
- **Para COPIAR/ELIMINAR:** La vista actual NO se modifica (es el origen)
- **Para IMPORTAR:** La vista actual SÍ se modifica (es el destino)

#### **Destinos = Donde se Aplican los Cambios**

**Los Paneles ❷ y ❸ son sus destinos:**
- Seleccione vistas y/o plantillas donde desea aplicar cambios
- Puede seleccionar de ambos paneles simultáneamente
- La herramienta procesará todas las selecciones

#### **Filtros vs. Anulaciones VG**

**Filtros (Visibilidad basada en reglas):**
- Controlan qué elementos son visibles según reglas
- Ejemplo: "Mostrar solo muros donde el Nombre de Tipo contiene 'Exterior'"
- Puede tener lógica compleja (condiciones AND/OR)
- Se aplican por vista o mediante plantilla

**Anulaciones VG (Gráficos de categoría):**
- Controlan cómo se muestran categorías completas
- Ejemplo: "Todos los Muros se muestran en rojo con grosor 3"
- Sin lógica condicional — afecta TODOS los elementos de la categoría
- Colores de línea, patrones, grosores, patrones de relleno, transparencia

**¡Ambos se gestionan de la misma manera en esta herramienta!**

#### **Plantillas de Vista**

**Qué son las Plantillas:**
- Configuraciones de vista reutilizables (incluyendo filtros y anulaciones VG)
- Una plantilla puede aplicarse a múltiples vistas
- Cambiar una plantilla afecta todas las vistas que la usan

**Cómo maneja la herramienta las Plantillas:**
- Detecta automáticamente cuando las vistas destino usan plantillas
- Muestra advertencia con conteo de vistas
- Aplica cambios a la plantilla (afectando todas las vistas)
- Este es el comportamiento de Revit, no una limitación de la herramienta

---

## Trabajar con Filtros {#working-with-filters}

### Copiar Filtros entre Vistas {#copying-filters-between-views}

**Caso de uso:** Ha configurado filtros perfectos en una vista y desea aplicarlos a 20 vistas más.

**Paso a paso:**

1. **Abrir la vista origen:**
   - Abrir en Revit la vista que tiene los filtros que desea copiar
   - Esta será su vista de referencia

2. **Iniciar Visibility Manager:**
   - Pestaña IB-BIM → clic en botón Visibility Manager

3. **Seleccionar Modo Filtros:**
   - Panel ❶: Clic en botón de radio **Filters**
   - El panel cambia a verde
   - Muestra todos los filtros en la vista actual

4. **Seleccionar filtros a copiar:**
   - Panel ❶: Marque los filtros que desea copiar
   - Use **Búsqueda** para encontrar filtros específicos rápidamente
   - O clic en **Seleccionar Todo** para copiar todos
   - El contador muestra: "X filters selected"

5. **Seleccionar vistas destino:**
   - Panel ❷: Marque **tipos de vista** para filtrar (opcional)
   - Use **Búsqueda** para encontrar vistas específicas
   - Marque las vistas donde desea estos filtros
   - El contador muestra: "X views selected"

6. **Seleccionar plantillas destino (opcional):**
   - Panel ❸: Marque plantillas si es necesario
   - Puede seleccionar tanto vistas como plantillas
   - El contador muestra: "X templates selected"

7. **Ejecutar la copia:**
   - Clic en botón **[COPY]** (verde)

8. **Manejar advertencias de Plantilla (si aplica):**
   - Si las vistas seleccionadas usan plantillas, se muestra:
```
   ⚠️ Plantillas Detectadas

   Las siguientes vistas usan plantillas:
   • Template: Architectural Plan (15 vistas)
   • Template: MEP Coordination (8 vistas)

   Total de vistas que se afectarán: 23

   Aplicar filtros afectará TODAS las vistas
   que usan estas plantillas.

   ¿Desea continuar?

   [Yes] [No]
```

   - Clic **Yes** para proceder (flujo de trabajo normal)
   - Clic **No** para cancelar y reconsiderar su selección

9. **Resolución de conflictos (si aplica):**
   - Si los filtros con el mismo nombre ya existen:
```
   Ya existen filtros con el mismo nombre.
   ¿Cómo desea proceder?

   ○ Merge - Mantener existentes, agregar solo nuevos
   ⦿ Overwrite - Reemplazar existentes con importados
   ○ New Only - Omitir existentes, agregar solo nuevos

   [OK] [Cancel]
```

   - **Merge:** Opción segura, no cambia lo existente
   - **Overwrite:** Actualiza filtros con su configuración
   - **New Only:** Ignora duplicados
   - Clic en **OK** para proceder

10. **Confirmación:**
    - Se muestra mensaje de éxito
    - Muestra cuántas vistas/plantillas fueron actualizadas
    - La vista actual no cambió

---

### Eliminar Filtros de las Vistas {#removing-filters-from-views}

**Caso de uso:** Necesita eliminar filtros obsoletos de múltiples vistas a la vez.

**Paso a paso:**

1. **Abrir cualquier vista como referencia:**
   - Abrir una vista que muestre los filtros que desea eliminar
   - Cualquier vista sirve — es solo una referencia

2. **Iniciar Visibility Manager**

3. **Seleccionar Modo Filtros:**
   - Panel ❶: Clic en botón de radio **Filters**

4. **Seleccionar filtros a eliminar:**
   - Panel ❶: Marque los filtros que desea eliminar
   - Esto es solo referencia — muestra qué se eliminará

5. **Seleccionar vistas destino:**
   - Panel ❷: Marque las vistas de donde eliminar
   - Panel ❸: Marque las plantillas de donde eliminar (opcional)

6. **Ejecutar la eliminación:**
   - Clic en botón **[REMOVE]** (naranja/rojo)

7. **Confirmar la operación:**
```
   ⚠️ Confirmar Eliminación

   X filtros se eliminarán de Y vistas/plantillas.

   Esta acción no se puede deshacer.

   ¿Desea continuar?

   [Yes] [No]
```

8. **Confirmación:**
   - Mensaje de éxito
   - Muestra cuántos elementos fueron eliminados

**Importante:**
- NO elimina la definición del filtro del proyecto
- Solo elimina el filtro de las vistas seleccionadas
- El filtro sigue existiendo y puede volver a aplicarse después

---

### Exportar Filtros {#exporting-filters}

**Caso de uso:** Guardar la configuración de filtros en un archivo para respaldo, documentación o importación a otro proyecto.

**Paso a paso:**

1. **Abrir la vista a exportar:**
   - Abrir la vista que contiene los filtros a exportar
   - Esta es su origen

2. **Iniciar Visibility Manager**

3. **Seleccionar Modo Filtros:**
   - Panel ❶: Clic en botón de radio **Filters**

4. **Seleccionar filtros a exportar:**
   - Panel ❶: Marque los filtros a exportar
   - Puede exportar todos o solo algunos
   - Use búsqueda para encontrar filtros específicos

5. **Elegir formato de exportación:**

   **Opción A: Excel (.xlsx) — Recomendado**
   - Clic en botón **[EXPORT]**
   - Mejor formato, más fácil de leer

   **Opción B: CSV (.csv)**
   - Clic en botón **[XLSX]** (a pesar del nombre, crea CSV)
   - Para sistemas heredados o control de versiones (compatible con Git)

6. **Elegir ubicación de guardado:**
   - Aparece el diálogo de archivo
   - Seleccionar la carpeta donde guardar
   - Formato de nombre por defecto: `Filters_[ViewType]_[HHMMSS]_[YYYYMMDD]_[ViewName].xlsx`
   - Ejemplo: `Filters_3D_145351_20260109_Section View.xlsx`
   - **Importante:** Mantenga el prefijo `Filters_` — se usa para identificar el contenido del archivo durante la importación
   - Puede cambiar el resto del nombre a su gusto

7. **Exportación completa:**
```
   ✓ Exportación Exitosa

   Elementos exportados:
   • Filters_3D_145351_20260109_Section View.xlsx (15 filtros)
   • Filters_3D_145351_20260109_Section View.pat (patrones de relleno)

   Ubicación: [carpeta seleccionada]

   [Open Folder] [OK]
```

8. **Archivos generados:**
   - **Archivo Excel/CSV:** Contiene todos los datos de filtros (siempre se genera)
   - **Archivo PAT:** Contiene patrones de relleno/sombreado usados en los filtros (solo se genera si los filtros usan patrones personalizados)

**⚠️ Importante: Los nombres de archivo deben coincidir**
- El nombre del archivo PAT debe ser **exactamente igual** al archivo Excel/CSV (excepto la extensión)
- Ejemplo: `Filters_3D_145351_20260109_Office.xlsx` necesita `Filters_3D_145351_20260109_Office.pat`
- **Si renombra el archivo Excel después de exportar, debe renombrar el archivo PAT también**

**Contenido de exportación:**

**Columnas Excel/CSV:**
- Filter_Name
- Enable_Filter (Yes/No)
- Visibility (Yes/No)
- Categories (categorías donde se aplica el filtro)
- Rules (lógica del filtro — condiciones AND/OR)
- Line_Color, Line_Pattern, Line_Weight
- Fill_Foreground_Color, Fill_Foreground_Pattern
- Fill_Background_Color, Fill_Background_Pattern
- Cut_Line_Color, Cut_Line_Pattern, Cut_Line_Weight
- Cut_Fill_Foreground_Color, Cut_Fill_Foreground_Pattern
- Cut_Fill_Background_Color, Cut_Fill_Background_Pattern
- Transparency
- Halftone (Yes/No)
- Custom_Parameters (si existen)

**Biblioteca de Patrones (archivo .pat):**
- Contiene todas las definiciones de patrones de relleno/sombreado usados en los filtros
- Nombre del archivo coincide con el archivo Excel
- **Solo se genera si los filtros usan patrones de relleno personalizados**
- Necesario para que todas las definiciones de patrones se importen correctamente
- Mantener en la misma carpeta que el archivo Excel/CSV

**Mejores prácticas:**
- Exporte a una ubicación de red compartida para acceso del equipo
- Mantenga los archivos Excel/CSV y los archivos de patrones juntos en la misma carpeta
- Al renombrar archivos, **mantenga el prefijo `Filters_` o `VGOverrides_`**
- **Al renombrar el archivo Excel, siempre renombre también el archivo de patrones (.pat o .lin) para que coincidan**
- Considere control de versiones (Git) para archivos CSV

---

### Importar Filtros {#importing-filters}

**Caso de uso:** Cargar filtros desde archivos previamente exportados a su proyecto actual.

**Paso a paso:**

1. **Abrir la vista destino:**
   - Abrir la vista donde desea los filtros
   - **Importante:** Esta vista SERÁ modificada
   - Si usa plantilla, afectará TODAS las vistas que usan esa plantilla

2. **Iniciar Visibility Manager**

3. **Seleccionar Modo Filtros:**
   - Panel ❶: Clic en botón de radio **Filters**

4. **Clic en Importar:**
   - Clic en botón **[IMPORT]**

5. **Seleccionar archivo:**
   - Aparece el diálogo de archivo
   - Navegar al archivo Excel o CSV exportado previamente
   - Seleccionar y clic en Open
   - **Nota:** La herramienta valida el contenido del archivo — si intenta importar un archivo de VG Overrides en modo filtros, mostrará un mensaje de error
   - Asegúrese de que el tipo de archivo coincida con el modo actual

6. **Advertencia de Plantilla (si aplica):**
```
   ⚠️ Plantilla Detectada

   Su vista actual usa la plantilla: "Architectural Plan"
   Esta plantilla es usada por 15 vistas.

   La importación afectará las 15 vistas.

   ¿Desea continuar?

   [Yes] [No]
```

7. **Verificación de Biblioteca de Patrones:**
   - La herramienta lee el contenido del archivo Excel para determinar si se necesita un archivo de patrones
   - **Solo verifica si los filtros realmente usan patrones personalizados**
   - Si se necesitan patrones, busca automáticamente un archivo .pat coincidente
   - Nombre esperado: mismo nombre que el archivo Excel con extensión .pat
   - Debe estar en la misma carpeta que el archivo Excel
   - **Importante:** Si renombró el archivo Excel, renombre también el archivo PAT

   **Si falta el archivo PAT (cuando se necesitan patrones):**
```
   ⚠️ No se encuentra la Biblioteca de Patrones

   Esperado: Filters_3D_145351_20260109_Section View.pat
   Ubicación: [misma carpeta que Excel]

   Los filtros se importarán pero los patrones de relleno
   personalizados pueden faltar.

   ¿Continuar sin patrones?

   [Yes] [No]
```

8. **Diálogo de Parámetros Personalizados (si aplica):**
```
   ⚠️ Parámetros Personalizados Detectados

   Los siguientes parámetros no existen en este proyecto:

   • Wall_Finish
     Tipo: Text
     Categoría: Walls

   • Room_Number_Custom
     Tipo: Text
     Categoría: Rooms

   ¿Crear estos parámetros?

   [Yes] [No] [Cancel]
```

   - **Yes:** La herramienta crea automáticamente los parámetros (recomendado)
   - **No:** Omitir estos parámetros (los filtros que los usan fallarán)
   - **Cancel:** Cancelar toda la importación

9. **Resolución de conflictos:**
```
   Ya existen filtros con el mismo nombre:
   • Filter 1
   • Filter 2

   ¿Cómo desea proceder?

   ○ Merge - Mantener existentes, agregar solo nuevos
   ⦿ Overwrite - Reemplazar existentes con importados
   ○ New Only - Omitir existentes, agregar solo nuevos

   [OK] [Cancel]
```

10. **Importación completa:**
```
    ✓ Importación Exitosa

    15 filtros importados a:
    • Level 1 - Architectural

    A través de plantilla: Architectural Plan
    Total de vistas afectadas: 15

    Parámetros personalizados creados: 2

    [OK]
```

---

## Trabajar con Anulaciones VG {#working-with-vg-overrides}

Las Anulaciones VG (Visibility/Graphics) controlan cómo se muestran categorías completas — colores, grosores de línea, patrones, transparencia. El flujo de trabajo es idéntico a los Filtros, solo con contenido diferente.

### Categorías Soportadas {#supported-categories}

IB-BIM Visibility Manager soporta todos los tipos de categorías principales de Revit:

- ✅ **Categorías de Modelo** — Muros, Puertas, Ventanas, elementos MEP, Estructura, Sitio, etc.
- ✅ **Categorías de Anotación** — Cotas, Etiquetas, Notas de Texto, Símbolos, Elementos de Detalle, etc.
- ✅ **Categorías Analíticas** — Cargas, Enlaces, Nodos, Condiciones de Contorno, etc.

**Ejemplo (Revit 2025/2026):**
292 categorías principales soportadas:
- 96 categorías de Modelo
- 180 categorías de Anotación
- 16 categorías Analíticas

La aplicación detecta y soporta automáticamente todas las categorías disponibles en su versión de Revit.

#### Alcance Actual (v1.0.0)

✅ **Soportado:**
- Todas las categorías principales (Modelo, Anotación, Analítica)
- Copiar y eliminar anulaciones VG
- Operaciones de Exportar/Importar

⚠️ **Limitaciones:**
- Las subcategorías aún no son soportadas (planificado para v2.0)

**Qué significa:**
- ✅ Muros (categoría principal) — Totalmente soportado
- ⚠️ Muros > Exterior (subcategoría) — Disponible en v2.0

La mayoría de los flujos de trabajo BIM dependen principalmente de las anulaciones de categorías principales. Las subcategorías son una granularidad avanzada usada en escenarios específicos.


### Copiar Anulaciones VG {#copying-vg-overrides}

**Caso de uso:** Estandarizar los gráficos de categorías en múltiples vistas (todos los muros rojos, todas las puertas azules, etc.)

**Paso a paso:**

1. **Abrir la vista origen:**
   - Abrir la vista que tiene las anulaciones VG que desea copiar

2. **Iniciar Visibility Manager**

3. **Seleccionar modo V/G Overrides:**
   - Panel ❶: Clic en botón de radio **V/G Overrides**
   - El panel cambia a azul claro
   - Muestra categorías con anulaciones en la vista actual

4. **Seleccionar categorías:**
   - Panel ❶: Marque las categorías que desea copiar

5. **Seleccionar destinos:**
   - Panel ❷: Seleccionar vistas destino
   - Panel ❸: Seleccionar plantillas destino (opcional)

6. **Ejecutar la copia:**
   - Clic en **[COPY]** (botón verde)
   - Manejar advertencias de plantilla si aplica
   - Resolución de conflictos (Merge/Overwrite/New Only)

7. **Confirmación:**
   - Mensaje de éxito mostrando cuántas categorías se copiaron a cuántas vistas

---

### Eliminar Anulaciones VG {#removing-vg-overrides}

**Paso a paso:**

1. **Abrir vista de referencia:**
   - Una vista que muestre las categorías con anulaciones a eliminar

2. **Iniciar Visibility Manager**

3. **Seleccionar modo V/G Overrides:**
   - Panel ❶: Clic en botón de radio **V/G Overrides**

4. **Seleccionar categorías:**
   - Marque las categorías cuyas anulaciones desea eliminar

5. **Seleccionar destinos:**
   - Panel ❷: Vistas de donde eliminar
   - Panel ❸: Plantillas de donde eliminar

6. **Ejecutar eliminación:**
   - Clic en **[REMOVE]** (botón naranja)
   - Confirmar la operación en el diálogo
   - Manejar advertencias de plantilla

**Resultado:**
- Anulaciones de categoría eliminadas de las vistas destino
- Las categorías vuelven a los gráficos predeterminados

---

### Exportar Anulaciones VG {#exporting-vg-overrides}

**Paso a paso:**

1. **Abrir la vista origen:**
   - La vista con las anulaciones VG a exportar

2. **Iniciar Visibility Manager**

3. **Seleccionar modo V/G Overrides:**
   - Panel ❶: Clic en botón de radio **V/G Overrides**

4. **Seleccionar categorías:**
   - Marque las categorías a exportar
   - O seleccionar todo

5. **Exportar:**
   - Para Excel clic **[EXPORT]**
   - Para CSV clic **[XLSX]**

6. **Elegir ubicación:**
   - Aparece el diálogo de archivo — seleccionar la carpeta deseada
   - Formato de nombre por defecto: `VGOverrides_[ViewType]_[HHMMSS]_[YYYYMMDD]_[ViewName].xlsx`
   - **Importante:** Mantenga el prefijo `VGOverrides_`

7. **Archivos generados:**
   - **Archivo Excel/CSV:** Contiene todos los datos de anulaciones VG (siempre se genera)
   - **Archivo LIN:** Contiene patrones de línea usados en anulaciones (solo se genera si se usan patrones de línea personalizados)

**⚠️ Importante: Los nombres de archivo deben coincidir**
- El nombre del archivo LIN debe ser **exactamente igual** al archivo Excel/CSV (excepto la extensión)
- **Al renombrar el archivo Excel, también renombre el archivo LIN para que coincidan**

**Contenido de exportación:**
- Nombre de categoría
- Visibilidad (Mostrar/Ocultar)
- Colores de línea, patrones, grosores
- Colores y patrones de relleno primer plano/fondo
- Configuración de líneas de corte
- Configuración de relleno de corte
- Transparencia
- Medio tono

---

### Importar Anulaciones VG {#importing-vg-overrides}

**Paso a paso:**

1. **Abrir la vista destino:**
   - La vista donde desea las anulaciones VG
   - **Esta vista SERÁ modificada**

2. **Iniciar Visibility Manager**

3. **Seleccionar modo V/G Overrides:**
   - Panel ❶: Clic en botón de radio **V/G Overrides**

4. **Clic en Importar:**
   - Clic en botón **[IMPORT]**

5. **Seleccionar archivo:**
   - Seleccionar el archivo VG Excel/CSV previamente exportado
   - **Nota:** La herramienta valida el contenido del archivo — si intenta importar un archivo de filtros en modo VG Overrides, mostrará un mensaje de error

6. **Manejar diálogos:**
   - Advertencia de plantilla (si aplica)
   - Verificación de biblioteca de patrones (si se necesita archivo .lin)
   - Resolución de conflictos (Merge/Overwrite/New Only)

7. **Confirmación:**
   - Mensaje de éxito
   - Gráficos importados aplicados a las categorías

**Nota:** Las anulaciones VG no usan parámetros personalizados, por lo que ese diálogo no aparecerá.

---

## Funciones Avanzadas {#advanced-features}

### Trabajar con Plantillas de Vista

**Comprender el comportamiento de las Plantillas:**

Cuando selecciona una vista que usa plantilla como destino, la herramienta aplica los cambios a **la plantilla misma**, no solo a la vista. Esto afecta **TODAS las vistas** que usan esa plantilla.

**¿Por qué sucede esto?**
- Es la arquitectura de Revit, no una limitación de la herramienta
- Cuando una vista usa plantilla, los filtros y VG están "bloqueados" por la plantilla
- No se pueden modificar en la vista sin romper el enlace de la plantilla

**Opciones:**

**Opción 1: Continuar (flujo de trabajo normal)**
- Clic en **[Yes]**
- Los cambios se aplican a la plantilla
- Todas las vistas con esa plantilla se actualizan
- **¡Generalmente esto es lo que desea!**

**Opción 2: Cancelar y reconsiderar**
- Clic en **[No]**
- Sin cambios

**Opción 3: Trabajar directamente con Plantillas**
- No seleccione vistas en el Panel ❷
- En su lugar seleccione plantillas en el Panel ❸
- Más claro — sabe que está modificando una plantilla

**Opción 4: Romper el enlace de la plantilla**
- Si desea afectar una sola vista que usa plantilla:
  1. Cerrar Visibility Manager
  2. En Revit: Abrir la vista
  3. Panel de Propiedades → View Template → `<None>`
  4. La vista ahora es independiente
  5. Iniciar Visibility Manager y aplicar cambios
  6. Solo esta vista se afecta

---

### Búsqueda y Filtrado

La herramienta proporciona búsqueda y filtrado potentes para trabajar rápidamente con grandes cantidades de elementos.

**Cómo funciona la búsqueda:**

- **Tiempo real:** Resultados se actualizan al escribir
- **Insensible a mayúsculas:** "Wall" y "wall" ambos funcionan
- **Coincidencia parcial:** Busca dentro del nombre, no solo al inicio
- **Selecciones se mantienen:** Marcar elementos no cambia la búsqueda
- **Limpiar búsqueda:** Al borrar texto, todos los elementos se muestran nuevamente

---

## Flujos de Trabajo Reales {#real-world-workflows}

### Para Gestores BIM

**Escenario 1: Estandarización de Plantillas de Oficina**

**Objetivo:** Crear filtros estándar de la empresa y distribuirlos a todos los proyectos

**Pasos:**

1. **Crear Filtros Maestros:**
   - Abrir plantilla de empresa o proyecto bien configurado
   - Configurar todos los filtros estándar

2. **Exportar Biblioteca Maestra:**
   - Iniciar Visibility Manager
   - Seleccionar Modo Filtros
   - Seleccionar Todo
   - Exportar a ubicación de red

3. **Documentar para el Equipo:**
   - Crear README en la misma carpeta
   - Describir qué hace cada filtro
   - Incluir instrucciones de importación

4. **Distribuir a Proyectos:**
   - Los miembros del equipo abren su proyecto
   - Inician Visibility Manager
   - Importan desde la ubicación de red
   - Todos los filtros estándar aplicados al proyecto

---

### Para Coordinadores BIM

**Escenario 1: Preparación para Reunión de Coordinación**

**Objetivo:** Configurar conjuntos de filtros idénticos en todos los modelos de todas las disciplinas

**Pasos:**

1. **Crear Conjunto de Filtros de Coordinación:**
   - Crear filtros en modelo de Arquitectura
   - Exportar

2. **Distribuir al Equipo:**
   - Enviar archivos Excel + PAT por correo
   - O colocar en carpeta BIM compartida

3. **El Equipo Importa:**
   - Coordinador de Estructura: Abre modelo de estructura, importa filtros
   - Coordinador MEP: Abre modelo MEP, importa filtros
   - Todos tienen los mismos filtros

4. **Resultado de la Reunión:**
   - Todos ven los mismos elementos
   - Mismos códigos de color
   - Sin confusión "en mi pantalla se ve diferente"

---

## Solución de Problemas {#troubleshooting}

### Los filtros no aparecen en la vista después de importar

**Síntoma:**
- La importación reporta éxito
- Pero los filtros no se ven en Visibility/Graphics

**Posibles causas y soluciones:**

**Causa 1: Filtros desactivados**
- **Solución:** En Revit: View → Visibility/Graphics (VG) → pestaña Filters → verificar columna "Visibility"

**Causa 2: La vista usa plantilla sin estos filtros**
- **Solución:** Verificar Properties → View Template, importar en una vista que use esa plantilla

**Causa 3: Las categorías del filtro no coinciden con la vista**
- **Solución:** Verificar categorías del filtro, confirmar que la vista puede mostrar esas categorías

---

### "Value" aparece en lugar de valores reales

**Síntoma:**
- Después de importar, las reglas del filtro muestran "Value" en lugar de valores reales

**Causa:**
- Error en la versión 1.0.0 de la herramienta

**Solución:**
- **Actualizar a la versión 1.0.1 o posterior**
- Re-exportar desde el proyecto de origen
- Re-importar al proyecto de destino

---

### Advertencia "Pattern Not Found"

**Síntoma:**
- Advertencia en Revit después de importar
- **Para Filtros:** Los filtros se importan pero usan patrones de relleno predeterminados en lugar de sombreados personalizados
- **Para Anulaciones VG:** Las categorías se importan pero usan patrones de línea predeterminados en lugar de estilos personalizados

**Solución:**
1. Renombrar el archivo de patrones para que coincida con el archivo Excel
2. Mover el archivo de patrones a la misma carpeta que el archivo Excel
3. Cargar patrones manualmente en Revit
4. Aceptar patrones predeterminados si los personalizados no son críticos

---

### La operación COPY no hace nada

**Posibles causas:**
1. Hizo clic en "No" en la advertencia de plantilla
2. Todavía está mirando la vista original (abra una vista destino)
3. Los filtros ya existen y seleccionó "New Only"

---

### Obtener Ayuda

**Autoservicio:**
1. Consultar esta guía del usuario
2. Revisar FAQ.md
3. Ver tutoriales en video
4. Revisar registros de depuración

**Soporte por correo:**

📧 **itzikb.bim@gmail.com**

**Incluir:**
1. **Detalle del error de la ventana de resultados** (Ctrl+A, Ctrl+C para copiar)
2. Versión de Revit (2023/2024/2025/2026)
3. Versión de la herramienta (se muestra en la ventana: "Ver: 1.0.0")
4. Lo que intentaba hacer (paso a paso)
5. Lo que ocurrió vs. lo esperado
6. Capturas de pantalla (opcional pero ayudan)

**Archivos de registro** (solo si el soporte lo solicita):
- Ubicación: `C:\ProgramData\IB-BIM\VisibilityManager\Logs\`

---

## Apéndice

### Atajos de Teclado

**En la ventana de Visibility Manager:**
- `Ctrl+F` - Enfocar cuadro de búsqueda (Panel ❶)
- `Tab` - Mover entre paneles
- `Space` - Marcar/desmarcar elemento seleccionado
- `Ctrl+A` - Seleccionar todo (cuando la lista tiene foco)
- `Esc` - Cancelar/cerrar ventana

### Ubicaciones de Archivos

**Registros de Depuración:**
```
C:\ProgramData\IB-BIM\VisibilityManager\Logs
```

**Ubicaciones de Archivos (Exportar / Importar):**
```
No hay directorio de salida predefinido.
Al exportar o importar, el usuario selecciona la carpeta
deseada a través del diálogo estándar de archivos.
La herramienta no fuerza ni asume una ruta de exportación predeterminada.
```

**Instalación:**
```
C:\ProgramData\Autodesk\ApplicationPlugins\VisibilityManager.bundle\
```

### Referencia del Formato Excel

**Referencia de columnas:**

| Columna | Descripción | Ejemplo |
|---------|-------------|---------|
| Filter_Name | Nombre del filtro | "Exterior Walls - Phase New" |
| Enable_Filter | Activado en la vista | "Yes" o "No" |
| Visibility | Mostrar u Ocultar | "Yes" o "No" |
| Categories | Nombres de categorías | "Walls; Doors; Windows" |
| Rules | Lógica del filtro | "(Phase Created = New) AND (Type Name Contains 'Ext')" |
| Line_Color | Color de línea de proyección | "RGB(255,0,0)" o "No Override" |
| Transparency | Porcentaje de transparencia | "0"–"100" |
| Halftone | Medio tono on/off | "Yes" o "No" |

### Glosario
- BIM — Modelado de Información de Construcción
- Filter — Regla de visibilidad basada en condiciones para mostrar/ocultar elementos
- VG Overrides — Anulaciones de Visibility/Graphics a nivel de categoría
- View Template — Configuración de vista reutilizable que incluye filtros
- Custom Parameter — Parámetro creado por el usuario (no nativo de Revit)
- Pattern Library — Colección de definiciones de patrones de relleno (archivo .PAT)
- Conflict Resolution — Cómo manejar elementos duplicados (Merge/Overwrite/New Only)
- Current View — La vista activa al iniciar la herramienta (referencia del Panel ❶)
- Target Views — Vistas donde se aplican los cambios (Panel ❷)
- Target Templates — Plantillas donde se aplican los cambios (Panel ❸)

Fin de la Guía del Usuario
¿Tiene preguntas? Correo: itzikb.bim@gmail.com
Última actualización: Noviembre 2025
Versión: 1.0.0
