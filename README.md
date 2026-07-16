# Dashboard Inventario — Autónomo

Dashboard de inventario tecnológico que se actualiza **directamente desde tus archivos XLS**, sin servidor, sin tokens, sin Claude.

## 🚀 Cómo usar

### 1. Subir a GitHub Pages (una sola vez)

```bash
# 1. Crea un repo en github.com (ej: "dashboard-inventario")
# 2. Sube el archivo
git init
git add DASHBOARD_AUTONOMO.html
git commit -m "Dashboard autónomo"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/dashboard-inventario.git
git push -u origin main

# 3. Activa GitHub Pages:
#    Settings → Pages → Source: Deploy from branch → main → / (root) → Save
#
# Tu URL quedará:
#    https://TU_USUARIO.github.io/dashboard-inventario/DASHBOARD_AUTONOMO.html
```

### 2. Uso diario (sin Claude)

1. Abre la URL de GitHub Pages en tu navegador
2. Arrastra los 3 archivos XLS a la zona de carga:
   - `DISPONIBLE__9_.xls`
   - `RENTADO.xls`
   - `DAÑADO.xls`
3. El dashboard calcula todo automáticamente y agrega el día al historial
4. El historial se guarda en el navegador (`localStorage`) — persiste entre sesiones

## ✅ Qué hace automáticamente

| Función | Detalle |
|---|---|
| **Lee los XLS** | SheetJS procesa los archivos directo en el navegador |
| **Calcula métricas** | Misma lógica que Claude: col 3, 11, 12 — LP/CP/Cat A/B/C |
| **Detecta archivos** | Por nombre: DISPONIBLE, RENTADO, DAÑADO |
| **Registra el día** | Agrega la fecha de hoy al historial |
| **Evita duplicados** | Si ya existe la fecha, la reemplaza |
| **Persiste historial** | localStorage — sobrevive cierres del navegador |
| **Compara vs anterior** | Deltas automáticos ▲▼ vs día previo |
| **Alertas dinámicas** | Se generan según los datos reales |

## 📊 Reglas de negocio embebidas

```
Columna 3  → Categoría del equipo (PORTATIL, ORDENADOR, IMPRESORA...)
Columna 11 → Categorización (A, B, C)
Columna 12 → #Contrato (LP... = Largo Plazo | CP... = Corto Plazo | otro = Incidencia)

Ingreso activo   = (Lap LP + Lap CP) × $900
Potencial renta  = (Cat A + Cat B) × $900
Potencial venta  = Cat C × $2,000
Base monetizable = Pot. renta + Pot. venta + otros × $20
```

## 🔒 Privacidad

**Tus datos nunca salen de tu computadora.** Todo el procesamiento ocurre en el navegador. Los archivos XLS no se envían a ningún servidor.

## 📁 Archivos

| Archivo | Descripción |
|---|---|
| `DASHBOARD_AUTONOMO.html` | Dashboard autónomo — el único archivo que necesitas |
| `README.md` | Este archivo |

## 🗓️ Historial incluido

El dashboard ya incluye datos históricos del **22 Jun → 15 Jul 2026** como base de comparación. Cada vez que subas los XLS se agrega un punto nuevo al historial.

---

*Generado con Claude · Anthropic · Julio 2026*
