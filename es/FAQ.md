---
layout: default
title: "IB-BIM Visibility Manager — Preguntas Frecuentes"
---

# Preguntas Frecuentes (FAQ)

## 📑 Tabla de Contenidos

1. [Preguntas Generales](#general-questions)
2. [Flujo de Trabajo y Operaciones](#workflow--operations)
3. [Filtros](#filters)
4. [Anulaciones VG](#vg-overrides)
5. [Exportar/Importar](#exportimport)
6. [Rendimiento](#performance)
7. [Solución de Problemas](#troubleshooting)
8. [Licencia y Soporte](#licensing--support)
9. [Consejos y Mejores Prácticas](#tips--best-practices)

---

## Preguntas Generales {#general-questions}

### P: ¿Qué versiones de Revit son compatibles?
**R:** Visibility Manager es compatible con Revit 2023, 2024, 2025 y 2026. Cada versión tiene una compilación dedicada y optimizada.

### P: ¿Funciona con plantillas?
**R:** ¡Sí! La herramienta detecta inteligentemente si una vista usa una plantilla y lee la configuración de filtros de la plantilla automáticamente. Al copiar filtros, puede elegir aplicar directamente a las vistas o a sus plantillas.

### P: ¿Puedo usar esto entre diferentes proyectos?
**R:** ¡Por supuesto! Exporte filtros de un proyecto e impórtelos en cualquier otro proyecto. La herramienta maneja parámetros y patrones faltantes automáticamente.

---

## Flujo de Trabajo y Operaciones {#workflow--operations}

### P: ¿Cómo funciona la función COPY?
**R:** COPY duplica los filtros o anulaciones VG seleccionados de su vista actual a las vistas/plantillas de destino.

**Puntos clave:**
- **Vista actual = Origen (solo referencia)** — Muestra qué copiar pero NO se modifica
- **Columnas 2-3 = Destinos** — Donde se copian los filtros/anulaciones
- Funciona de forma idéntica para Filtros y Anulaciones VG

**Paso a paso:**
1. Abrir una vista que tenga los filtros/anulaciones que desea copiar (origen)
2. **Panel izquierdo**: Seleccionar qué filtros o anulaciones copiar
3. **Columna 2**: Seleccionar vistas de destino
4. **Columna 3**: Seleccionar plantillas de destino (opcional)
5. Hacer clic en **COPY**
6. Elegir resolución de conflictos si los elementos ya existen:
   - **Merge** — Mantener existentes, agregar solo nuevos
   - **Overwrite** — Reemplazar existentes con configuración importada
   - **New Only** — Omitir existentes, agregar solo nuevos

**Nota:** ¡La vista actual nunca se modifica — es su referencia!

---

### P: ¿Cómo funciona la función REMOVE?
**R:** REMOVE elimina los filtros o anulaciones VG seleccionados de las vistas/plantillas de destino.

**Puntos clave:**
- **Vista actual = Solo referencia** — Muestra qué eliminar pero NO se modifica
- **Columnas 2-3 = Destinos** — De donde se eliminan los filtros/anulaciones

**Caso de uso:** Limpiar múltiples vistas eliminando filtros obsoletos o incorrectos de una vez.

---

### P: ¿Qué sucede cuando las vistas de destino usan plantillas?
**R:** La herramienta **detecta plantillas automáticamente** y muestra una advertencia con:
- Nombres de plantillas detectadas
- Número de vistas que usan cada plantilla
- Total de vistas que se verán afectadas

**¿Por qué?** En Revit, cuando una vista usa una plantilla, la configuración de filtros/VG es controlada por la plantilla. Este es el comportamiento de Revit, no una limitación de la herramienta.

---

### P: ¿Debo seleccionar Vistas (Columna 2) o Plantillas (Columna 3)?
**R:** Ambas funcionan:

**Columna 2 — Vistas de destino:**
- Seleccionar vistas por nombre
- Si la vista usa plantilla → la herramienta aplica a la plantilla (le avisa primero)
- Si la vista no tiene plantilla → aplica solo a esa vista

**Columna 3 — Plantillas de destino:**
- Seleccionar plantillas directamente
- Más eficiente para estandarización masiva
- Intención más clara — sabe que está modificando una plantilla

---

## Exportar/Importar {#exportimport}

### P: ¿Cómo funciona la exportación — qué vista es el origen?
**R:** La exportación captura filtros/anulaciones VG de la **vista activa actual** (Panel ❶).
- Seleccione los elementos necesarios
- Haga clic en EXPORT
- Elija la ubicación de guardado
- La vista actual no cambia

### P: ¿Cómo funciona la importación — qué vista se afecta?
**R:** La importación se aplica a la **vista activa actual**:
- Si la vista usa plantilla → se aplica a la plantilla, afecta todas las vistas que la usan
- Si la vista no tiene plantilla → se aplica solo a esa vista

**Diferencia importante con COPY:**
- **COPY**: Selecciona múltiples vistas de destino. Vista actual sin cambios
- **IMPORT**: Solo la vista actual es el destino. La vista actual cambia

### P: ¿Por qué la herramienta exporta un archivo .PAT junto con Excel?
**R:** Los patrones de relleno de Revit se almacenan por separado de los filtros. El archivo .PAT contiene:
- Todos los patrones de relleno usados en sus filtros
- Definiciones de patrones (líneas, ángulos, espaciado)
Esto asegura que al importar filtros a otro proyecto, todos los patrones estén disponibles.

### P: ¿Qué pasa si falta el archivo .PAT durante la importación?
**R:** La herramienta muestra una advertencia pero continúa:
- Los filtros se importan exitosamente
- Verá "Pattern not found" hasta que cargue los patrones manualmente
- Recomendado: Siempre mantenga los archivos .PAT y .XLSX juntos

### P: ¿Puedo editar el archivo Excel antes de importar?
**R:** ¡Sí! Puede:
- ✓ Modificar nombres de filtros
- ✓ Cambiar colores, grosores de línea
- ✓ Actualizar valores de reglas
- ⚠️ No cambie la estructura de columnas ni los nombres de encabezados

### P: ¿Excel o CSV — cuál debo usar?
**R:**
- **Excel (.xlsx)** — ¡Recomendado! Mejor formato, más fácil de leer
- **CSV** — Para sistemas heredados o control de versiones (compatible con Git)

### P: ¿Puedo importar filtros creados en versiones anteriores de Revit?
**R:** ¡Sí! La herramienta maneja las diferencias de API automáticamente. Los filtros exportados de Revit 2023 funcionan perfectamente en Revit 2026 y viceversa.

---

## Rendimiento {#performance}

### P: ¿Cuántos filtros puedo copiar a la vez?
**R:** Probado con más de 100 filtros a más de 50 vistas simultáneamente. ¡Sin límite práctico!

### P: ¿Ralentiza Revit?
**R:** No. Las operaciones están optimizadas y usan la API de Revit eficientemente. Copiar 50 filtros toma ~5 segundos.

---

## Solución de Problemas {#troubleshooting}

### P: La importación dice "Success" pero los filtros no aparecen en mi vista
**R:** Verifique:
1. ¿Los filtros están habilitados? (View → Visibility/Graphics → pestaña Filters)
2. ¿Su vista usa una plantilla que no incluye estos filtros?
3. ¿Las categorías del filtro coinciden con los elementos de su vista?

### P: Los filtros se importan pero muestran "Value" en lugar de valores reales
**R:** Fue un error en v1.0.0, corregido en v1.0.1. Actualice a la última versión.

### P: Advertencias "Pattern not found" después de importar
**R:** El archivo .PAT no fue importado o está en una ubicación diferente. Reimporte y asegúrese de que el archivo .PAT esté en la misma carpeta que el archivo .XLSX.

### P: Los parámetros personalizados no se crearon durante la importación
**R:** Asegúrese de haber hecho clic en "Yes" en el diálogo de parámetros personalizados. Si hizo clic en "No", los parámetros no se crearán.

---

**Para información completa sobre licencias, precios y términos:**
👉 **[Ver Guía de Licencias y Precios](LICENSING.md)**

---

## Consejos y Mejores Prácticas {#tips--best-practices}

### P: ¿Algún consejo para organizar filtros?
**R:** ¡Sí!
- Use nombres consistentes: prefijo por disciplina (ARCH_, STRUCT_, MEP_)
- Exporte conjuntos de filtros a Excel como documentación
- Cree plantillas maestras con todos los filtros estándar de la oficina
- Use nombres descriptivos, no "Filter1", "Filter2"

### P: ¿Cómo configurar filtros para reuniones de coordinación?
**R:**
1. Crear conjuntos de filtros para cada disciplina
2. Exportar todos los conjuntos a Excel
3. Compartir archivos Excel con el equipo de coordinación
4. Cada disciplina importa los filtros relevantes
5. ¡Todos tienen configuraciones de vista idénticas!

### P: ¿Puedo usar esto para plantillas de Revit?
**R:** ¡Por supuesto! Flujo de trabajo común:
1. Construir filtros perfectos en proyecto de prueba
2. Exportar a Excel
3. Importar en la plantilla de la empresa
4. Distribuir plantilla a todos los proyectos

---

## ¿Todavía tiene preguntas?

**Contáctenos:** itzikb.bim@gmail.com

**Documentación:** [enlace]

**Tutoriales en video:** [enlace]
