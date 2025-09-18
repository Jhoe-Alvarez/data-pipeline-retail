# 📊 Pipeline de Datos y Dashboard de Ventas Retail

Pipeline ETL completo para análisis de ventas retail con visualización interactiva en Power BI.

## 🎯 Objetivos
- Implementar pipeline ETL con Python
- Generar dataset limpio y estructurado
- Crear dashboard interactivo con KPIs de negocio

## 🛠️ Stack Tecnológico
- **Python** (Pandas, NumPy) - ETL y transformación
- **Google Colab** - Ejecución del pipeline
- **Power BI Desktop** - Dashboard y visualización

## 📂 Estructura del Proyecto
```
data-pipeline-retail/
├── data/
│   ├── raw/              # Dataset original
│   └── processed/        # Dataset procesado
├── notebook/
│   └── Retail_ETL_Colab_to_CSV.ipynb
├── dashboard/
│   └── Retail_Dashboard.pbix
└── screenshots/
    └── dashboard_overview.png
```

## 🔄 Pipeline ETL

### Transformaciones principales:
- Normalización de nombres de columnas
- Conversión de tipos de datos (fechas, numéricos)
- Limpieza de nulos y duplicados
- Creación de métricas calculadas (UnitPrice, MarginPct, YearMonth)

```python
# Ejemplo de transformación clave
df["UnitPrice"] = np.where(df["Quantity"] > 0, df["Sales"] / df["Quantity"], 0)
df["MarginPct"] = np.where(df["Sales"] != 0, df["Profit"] / df["Sales"], 0)
```

## 📊 Dashboard - KPIs Principales
- **Total Sales** - Ingresos totales
- **Total Profit** - Ganancia total  
- **Margin %** - Porcentaje de margen
- **Avg Ticket** - Ticket promedio por orden

### Visualizaciones incluidas:
- Tendencia de ventas mensuales
- Top 10 productos más vendidos
- Análisis por categoría y región
- Segmentadores interactivos

## 🚀 Uso Rápido

1. **Clonar repositorio**
   ```bash
   git clone https://github.com/tu_usuario/data-pipeline-retail.git
   ```

2. **Ejecutar ETL**
   - Abrir `Retail_ETL_Colab_to_CSV.ipynb` en Google Colab
   - Ejecutar todas las celdas

3. **Abrir Dashboard**
   - Cargar `superstore_clean.csv` en Power BI Desktop
   - Abrir `Retail_Dashboard.pbix`

## 💡 Resultados Clave
- Dataset original procesado de X filas a Y filas limpias
- Identificación de productos top performer
- Análisis de estacionalidad en ventas
- Segmentación de clientes por valor

---
**Autor:** [Tu Nombre](mailto:tuemail@correo.com) | [LinkedIn](tu-linkedin) | [GitHub](tu-github)
